Generate a new Next.js App Router page.

Arguments: $ARGUMENTS (format: "route-path [description]", e.g. "dashboard/settings User settings page")

Instructions:
1. Parse $ARGUMENTS to extract the route path and optional description.
2. Determine the correct file location: `app/<route-path>/page.tsx`.
3. Create a Server Component by default. Only add `"use client"` if the description explicitly mentions interactivity, forms, or client-side state.
4. Include a `generateMetadata` export with a descriptive title derived from the route or description.
5. Scaffold realistic placeholder UI using Tailwind CSS classes — not just "Hello World".
6. If the page fetches data, show a typed async fetch with proper Next.js cache options.
7. Also create `loading.tsx` (skeleton UI) and `error.tsx` (error boundary) in the same directory.
8. Output the full file contents for each file, clearly labeled with its path.
