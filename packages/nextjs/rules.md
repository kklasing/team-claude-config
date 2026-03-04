# Next.js Development Rules

## Router
- Use the **App Router** (`app/`) for all new projects. Do not use `pages/` unless maintaining legacy code.
- Colocate route segments, layouts, loading states, and error boundaries inside their respective `app/` subdirectory.
- Use route groups `(group)` to organize routes without affecting the URL path.

## Components
- Default to **Server Components**. Only add `"use client"` when the component requires browser APIs, event listeners, or React hooks (`useState`, `useEffect`, etc.).
- Keep Client Components as leaf nodes — push `"use client"` as far down the tree as possible.
- Name component files in PascalCase (`UserCard.tsx`). Name route files in lowercase (`page.tsx`, `layout.tsx`).

## Data Fetching
- Fetch data directly in Server Components using `async/await`. Do not use `useEffect` for data fetching in Server Components.
- Use `fetch()` with Next.js cache options (`{ cache: 'force-cache' }`, `{ next: { revalidate: N } }`, or `{ cache: 'no-store' }`).
- Use React `cache()` to deduplicate requests across a render pass.
- For mutations, use **Server Actions** (`"use server"`) instead of creating API routes unless you need a public HTTP endpoint.

## TypeScript
- All files must be `.ts` or `.tsx`. No `.js` or `.jsx`.
- Define prop types with `interface`, not `type`, unless you need union/intersection types.
- Type page props using the Next.js-provided generics: `PageProps`, `LayoutProps`, `generateMetadata` return type `Metadata`.

## Styling
- Use **Tailwind CSS** utility classes as the primary styling method.
- Do not write inline `style` objects except for truly dynamic values (e.g., CSS custom properties).
- Use `cn()` (from `clsx` + `tailwind-merge`) to conditionally join class names.

## Images & Fonts
- Always use `next/image` for images. Set explicit `width`/`height` or `fill` with a positioned parent.
- Load fonts via `next/font` — never `@import` from Google Fonts directly.

## Performance
- Add `loading="lazy"` semantics via `next/image` default behavior; do not disable it without reason.
- Use `next/dynamic` with `{ ssr: false }` only for components that must be client-side and are not needed on first paint.
- Avoid barrel files (`index.ts` re-exports) in large feature directories — they harm tree-shaking.

## Error Handling
- Provide `error.tsx` boundaries at the segment level for recoverable errors.
- Use `notFound()` from `next/navigation` for 404 cases instead of returning null or throwing manually.
- Use `redirect()` from `next/navigation` for server-side redirects.

## Environment Variables
- Prefix public env vars with `NEXT_PUBLIC_`. Never expose secrets with this prefix.
- Validate env vars at startup using a schema (e.g., `zod`) in `env.ts` — fail fast rather than silently.

## File & Folder Conventions
```
app/
  (marketing)/        # route group
    page.tsx
    layout.tsx
  (dashboard)/
    layout.tsx
    [id]/
      page.tsx
      loading.tsx
      error.tsx
components/
  ui/                 # generic, reusable UI primitives
  features/           # domain-specific components
lib/
  db.ts
  auth.ts
  utils.ts
```
