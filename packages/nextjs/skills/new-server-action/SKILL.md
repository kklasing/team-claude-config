---
name: new-server-action
description: Create a Zod-validated Next.js Server Action with a wired-up form component
argument-hint: "<action-name> [description]"
---

Create a Next.js Server Action for a form mutation.

Arguments: $ARGUMENTS (format: "action-name [description]", e.g. "createPost Create a new blog post")

Instructions:
1. Parse $ARGUMENTS to extract the action name and optional description.
2. Create the server action in `lib/actions/<action-name>.ts` with `"use server"` at the top.
3. Accept `FormData` or a typed plain object as input — prefer typed input with a Zod schema.
4. Define a Zod schema for validation. Return structured errors using `{ success: false, errors: {...} }` on failure.
5. On success return `{ success: true, data: {...} }`.
6. Show how to call the action from a Client Component using `useActionState` (React 19 / Next.js 15+).
7. Include a sample form component at `components/features/<action-name>-form.tsx` that wires up the action.
8. Output all files clearly labeled with their paths.
