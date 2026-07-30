---
name: angular-architect
category: dev
description: Use for Angular architecture and implementation — standalone components (Angular 17+), signals, computed, effect, RxJS, NgRx, NgRx Signal Store, dependency injection with inject(), lazy loading with loadComponent and functional guards, SSR with Angular Universal and hydration, change detection strategy (OnPush, signal-driven), reactive and typed forms, control flow (@if, @for, @switch), deferred views (@defer), and Nx monorepo layout. Triggers on mentions of Angular, ng, RxJS, NgRx, signal(), standalone component, @Component, Nx, Angular Universal, or Angular CLI.
---

# Angular Architect

## Load Order
Read `shared-kernel/SKILL.md` first.

## Core Competencies

### Modern Angular (17+)
- **Standalone components** by default — NgModules only when integrating with legacy code
- **Signals** (`signal`, `computed`, `effect`) as primary reactive primitive
- **New control flow**: `@if`, `@for` with `track`, `@switch`, `@defer`
- **`inject()` function** instead of constructor injection in most cases
- **Functional guards and resolvers** (`CanActivateFn`, `ResolveFn`)
- **Deferrable views** (`@defer`) for lazy-loading below-the-fold UI

### Signals vs RxJS — When to Use What

| Use Case | Primitive |
|---|---|
| Component-local state | `signal()` |
| Derived state | `computed()` |
| Side effects from state change | `effect()` |
| HTTP request | `HttpClient` returns `Observable` — bridge with `toSignal()` |
| User input streams (debounce, throttle) | RxJS (`fromEvent`, `debounceTime`) |
| WebSocket / SSE | RxJS |
| Complex event coordination | RxJS operators |

Bridge: `toSignal(observable$)` and `toObservable(signalRef)`.

### Change Detection Strategy
- `OnPush` everywhere — the cost of not using it compounds
- Signal reads inside a template mark that template for re-check automatically
- With OnPush: component re-renders only when inputs change (reference) or signals it reads update
- Avoid mutation — always produce new references (spread, immer, or signal `.update()`)

### Reactive Forms (Typed)

```typescript
import { FormBuilder, Validators } from '@angular/forms';

const form = this.fb.group({
  email: ['', [Validators.required, Validators.email]],
  password: ['', [Validators.required, Validators.minLength(12)]],
});
// form is FormGroup<{ email: FormControl<string | null>; password: FormControl<string | null> }>
```

- Never use template-driven forms in production
- Always strongly typed — no `FormGroup<any>`
- Validators composed, never inline logic in templates

### Lazy Loading

```typescript
// app.routes.ts
export const routes: Routes = [
  {
    path: 'dashboard',
    loadComponent: () => import('./dashboard/dashboard.component').then(m => m.DashboardComponent),
    canActivate: [authGuard],
  },
];
```

- `loadComponent` for standalone components
- `loadChildren` only for legacy NgModule features
- Functional guards via `CanActivateFn`, not class-based

### SSR + Hydration
- `provideClientHydration()` in `app.config.ts` enables full app hydration
- `@defer (on viewport)` for incremental hydration of below-the-fold content
- Avoid `document` / `window` access in universal code — guard with `isPlatformBrowser`

## Version Verification (Required First Step)

Before writing Angular code:
- Read `package.json` for `@angular/core` version
- Confirm Angular CLI version matches (`ng version`)
- Check `angular.json` for builder: `@angular-devkit/build-angular:application` (esbuild, modern) or `browser` (webpack, legacy)
- Determine project posture: fully standalone, hybrid, or NgModule-based
- Check for Nx workspace (`nx.json` present) — Nx changes file layout and commands

## Common Failure Modes

| Symptom | Root Cause |
|---|---|
| Memory leak over time | `.subscribe()` in component without `takeUntilDestroyed()` or async pipe |
| Signal value not updating | Used `.set()` with same reference (mutated object) — use spread or new object |
| `ExpressionChangedAfterItHasBeenCheckedError` | State changed during the same CD cycle — move to `effect()` or `ngAfterViewInit` with care |
| OnPush component not refreshing | Parent passed mutated object with same reference |
| Infinite loop in effect | `effect()` writes to a signal it also reads — split into two signals |
| `@for` performance degraded | Missing `track` expression — always provide `track item.id` |
| SSR hydration mismatch | Browser-only API used during SSR, or non-deterministic value in template |
| Change detection running constantly | Event listener triggering CD without OnPush + signal boundary |

## Non-Negotiables

- `strict: true` in `tsconfig.json`
- `strictTemplates: true` in Angular compiler options
- No `any` in component public API (inputs, outputs, exposed methods)
- Every HTTP call goes through a service — never in a component
- Every `@for` block has a `track` expression
- Every subscription uses `takeUntilDestroyed()` or the `async` pipe
- Every route has a guard appropriate to its access level
- No logic in templates beyond boolean checks and simple property access

## Deliverables

### Standalone Component (Modern Shape)

```typescript
import { Component, inject, signal, computed, input, output } from '@angular/core';
import { UserService } from './user.service';

@Component({
  selector: 'app-user-card',
  standalone: true,
  changeDetection: ChangeDetectionStrategy.OnPush,
  template: `
    @if (user(); as u) {
      <article>
        <h2>{{ u.displayName }}</h2>
        <p>{{ subtitle() }}</p>
        <button type="button" (click)="edit.emit(u.id)">Edit</button>
      </article>
    } @else {
      <p>Loading…</p>
    }
  `,
})
export class UserCardComponent {
  userId = input.required<string>();
  edit = output<string>();

  private userService = inject(UserService);

  user = computed(() => this.userService.userById(this.userId()));
  subtitle = computed(() => {
    const u = this.user();
    return u ? `${u.role} · Joined ${u.joinedAt.toLocaleDateString()}` : '';
  });
}
```

### Service with Signal Store Pattern

```typescript
import { Injectable, computed, inject, signal } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { firstValueFrom } from 'rxjs';

@Injectable({ providedIn: 'root' })
export class UserService {
  private http = inject(HttpClient);

  private _users = signal<User[]>([]);
  private _loading = signal(false);
  private _error = signal<string | null>(null);

  readonly users = this._users.asReadonly();
  readonly loading = this._loading.asReadonly();
  readonly error = this._error.asReadonly();

  readonly userCount = computed(() => this._users().length);

  userById(id: string) {
    return computed(() => this._users().find(u => u.id === id));
  }

  async load(): Promise<void> {
    this._loading.set(true);
    this._error.set(null);
    try {
      const data = await firstValueFrom(this.http.get<User[]>('/api/users'));
      this._users.set(data);
    } catch (err) {
      this._error.set(err instanceof Error ? err.message : 'Unknown error');
    } finally {
      this._loading.set(false);
    }
  }
}
```

### Functional Guard

```typescript
import { CanActivateFn, Router } from '@angular/router';
import { inject } from '@angular/core';
import { AuthService } from './auth.service';

export const authGuard: CanActivateFn = () => {
  const auth = inject(AuthService);
  const router = inject(Router);
  if (auth.isAuthenticated()) return true;
  router.navigate(['/login']);
  return false;
};
```

## Performance Checklist
- OnPush change detection on every component
- `@defer` for below-the-fold content
- Route-level lazy loading for every feature area
- `@for` uses `track` with a stable identifier
- Images use `NgOptimizedImage` directive
- Bundle analyzed with `source-map-explorer` or Nx `webpack-bundle-analyzer`
- Lighthouse score measured in CI

## Testing Standard
- Unit tests with Jest or Karma + Jasmine (Jest preferred for speed)
- Component tests with Angular Testing Library — test behavior, not implementation
- E2E with Playwright or Cypress
- Mock `HttpClient` with `provideHttpClientTesting()` — never hit real network

## Reference Links to Verify
- https://angular.dev (primary — the new docs site)
- https://angular.dev/guide/signals
- https://angular.dev/guide/hydration
- https://nx.dev (for Nx workspaces)
