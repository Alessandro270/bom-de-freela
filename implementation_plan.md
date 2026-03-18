# Bom de Freela — Frontend MVP Implementation Plan

Build the full NuxtJS frontend for the Bom de Freela digital freelancing platform, including ~30 pages across public, client, freelancer, and admin areas, with Pinia state management, TailwindCSS styling, and VeeValidate + Zod form validation. All UI in Portuguese (PT).

## User Review Required

> [!IMPORTANT]
> This is a large frontend build (~30 pages + infrastructure). I will implement all pages as described in the README spec. The API calls will use `useApi` composable pointing to `API_URL` from runtime config — please confirm the backend API base URL if different from `http://localhost:3001`.

> [!WARNING]  
> The project currently uses Nuxt 4 (`nuxt ^4.3.1`). TailwindCSS v4 will be used via `@nuxtjs/tailwindcss` module. Pinia via `@pinia/nuxt`.

---

## Proposed Changes

### 1. Project Setup & Dependencies

#### [MODIFY] [package.json](file:///c:/Users/propr/OneDrive/Documentos/projetos/bom-de-freela/package.json)
Install: `@pinia/nuxt`, `pinia`, `@nuxtjs/tailwindcss`, `tailwindcss`, `@vee-validate/nuxt`, `@vee-validate/zod`, `vee-validate`, `zod`, `@nuxt/icon`, `@nuxt/fonts`

#### [MODIFY] [nuxt.config.ts](file:///c:/Users/propr/OneDrive/Documentos/projetos/bom-de-freela/nuxt.config.ts)
Configure modules, runtime config for API_URL, and app head metadata.

#### [NEW] [tailwind.config.ts](file:///c:/Users/propr/OneDrive/Documentos/projetos/bom-de-freela/tailwind.config.ts)
Custom theme with Bom de Freela brand colors and typography.

---

### 2. Core Infrastructure — Layouts, Composables, Stores, Middleware

#### [NEW] app/assets/css/main.css
TailwindCSS base imports + global styles.

#### [MODIFY] [app.vue](file:///c:/Users/propr/OneDrive/Documentos/projetos/bom-de-freela/app/app.vue)
Replace `NuxtWelcome` with `<NuxtLayout><NuxtPage /></NuxtLayout>`.

#### Layouts
- [NEW] `app/layouts/default.vue` — Main layout with navbar + footer
- [NEW] `app/layouts/auth.vue` — Centered layout for login/register
- [NEW] `app/layouts/dashboard.vue` — Sidebar + topbar for private area
- [NEW] `app/layouts/admin.vue` — Admin panel layout

#### Composables
- [NEW] `app/composables/useApi.ts` — Wrapper around `useFetch` with JWT token injection
- [NEW] `app/composables/useToast.ts` — Simple toast notification system

#### Pinia Stores
- [NEW] `app/stores/auth.ts` — `useAuthStore` (JWT, login, logout, register)
- [NEW] `app/stores/profile.ts` — `useProfileStore` (client + freelancer profiles)
- [NEW] `app/stores/projects.ts` — `useProjectsStore` (CRUD, filters)
- [NEW] `app/stores/proposals.ts` — `useProposalsStore`
- [NEW] `app/stores/contracts.ts` — `useContractsStore`
- [NEW] `app/stores/notifications.ts` — `useNotificationsStore`

#### Middleware
- [NEW] `app/middleware/auth.ts` — Redirect to `/login` if not authenticated
- [NEW] `app/middleware/guest.ts` — Redirect to `/dashboard` if already logged in
- [NEW] `app/middleware/admin.ts` — Redirect if not admin role
- [NEW] `app/middleware/freelancer.ts` — Redirect if no freelancer profile

---

### 3. Shared Components

- [NEW] `app/components/ui/` — Button, Input, Card, Badge, Modal, StarRating, Pagination, EmptyState, StatusBadge
- [NEW] `app/components/layout/Navbar.vue` — Public navigation bar
- [NEW] `app/components/layout/Footer.vue` — Site footer  
- [NEW] `app/components/layout/Sidebar.vue` — Dashboard sidebar
- [NEW] `app/components/layout/DashboardTopbar.vue` — Dashboard top bar with notifications

---

### 4. Public Pages (7 pages)

| Route | File |
|---|---|
| `/` | `app/pages/index.vue` — Landing page with hero, features, CTA |
| `/login` | `app/pages/login.vue` |
| `/register` | `app/pages/register.vue` |
| `/forgot-password` | `app/pages/forgot-password.vue` |
| `/reset-password` | `app/pages/reset-password.vue` |
| `/about` | `app/pages/about.vue` |
| `/contact` | `app/pages/contact.vue` |

---

### 5. Dashboard & Account (3 pages)

| Route | File |
|---|---|
| `/dashboard` | `app/pages/dashboard.vue` |
| `/account/settings` | `app/pages/account/settings.vue` |
| `/notifications` | `app/pages/notifications.vue` |

---

### 6. Client Area (10 pages)

| Route | File |
|---|---|
| `/client/profile` | `app/pages/client/profile.vue` |
| `/client/projects` | `app/pages/client/projects/index.vue` |
| `/client/projects/new` | `app/pages/client/projects/new.vue` |
| `/client/projects/:id` | `app/pages/client/projects/[id].vue` |
| `/client/projects/:id/edit` | `app/pages/client/projects/[id]/edit.vue` |
| `/client/contracts` | `app/pages/client/contracts/index.vue` |
| `/client/contracts/:id` | `app/pages/client/contracts/[id].vue` |
| `/client/payments` | `app/pages/client/payments.vue` |
| `/freelancers` | `app/pages/freelancers/index.vue` |
| `/freelancers/:id` | `app/pages/freelancers/[id].vue` |

---

### 7. Freelancer Area (8 pages)

| Route | File |
|---|---|
| `/freelancer/profile` | `app/pages/freelancer/profile/index.vue` |
| `/freelancer/profile/edit` | `app/pages/freelancer/profile/edit.vue` |
| `/freelancer/projects` | `app/pages/freelancer/projects/index.vue` |
| `/freelancer/projects/:id` | `app/pages/freelancer/projects/[id].vue` |
| `/freelancer/proposals` | `app/pages/freelancer/proposals.vue` |
| `/freelancer/contracts` | `app/pages/freelancer/contracts/index.vue` |
| `/freelancer/contracts/:id` | `app/pages/freelancer/contracts/[id].vue` |
| `/freelancer/payments` | `app/pages/freelancer/payments.vue` |

---

### 8. Admin Panel (6 pages)

| Route | File |
|---|---|
| `/admin/dashboard` | `app/pages/admin/dashboard.vue` |
| `/admin/users` | `app/pages/admin/users/index.vue` |
| `/admin/users/:id` | `app/pages/admin/users/[id].vue` |
| `/admin/projects` | `app/pages/admin/projects.vue` |
| `/admin/contracts` | `app/pages/admin/contracts.vue` |
| `/admin/payments` | `app/pages/admin/payments.vue` |

---

## Verification Plan

### Automated Tests
- Run `npm run dev` and verify the dev server starts without errors
- Run `npm run build` to verify no build-time errors

### Browser Verification
Using the browser tool:
1. Navigate to `http://localhost:3000/` — verify landing page renders with hero section
2. Navigate to `/login` — verify login form renders
3. Navigate to `/register` — verify registration form renders
4. Navigate to `/dashboard` — verify redirect to `/login` (auth middleware)
5. Navigate to `/about` and `/contact` — verify pages render
6. Navigate to `/admin/dashboard` — verify redirect (admin middleware)

### Manual Verification
- The user can start `npm run dev` and browse all pages to verify design and functionality
