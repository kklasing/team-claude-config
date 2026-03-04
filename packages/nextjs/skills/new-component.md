Scaffold a new reusable Next.js component.

Arguments: $ARGUMENTS (format: "ComponentName [client|server] [description]", e.g. "UserAvatar client Displays user profile picture with fallback initials")

Instructions:
1. Parse $ARGUMENTS to extract the component name (PascalCase), type (client/server, default server), and description.
2. Place UI primitives in `components/ui/<ComponentName>.tsx` and domain-specific components in `components/features/<ComponentName>.tsx`. Use `ui/` unless the description implies domain logic.
3. Add `"use client"` only if type is "client" or the description requires browser APIs/interactivity.
4. Define a TypeScript `interface` for props — no `any`, no implicit types.
5. Style with Tailwind CSS. Use `cn()` for conditional classes.
6. Export the component as a named export, not a default export.
7. If the component accepts children, type them as `React.ReactNode`.
8. Include a brief JSDoc comment describing the component's purpose.
9. Output the complete file contents labeled with its path.
