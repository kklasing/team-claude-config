# team-claude-config

Shared Claude Code configuration for Team Alpha. This repo provides a **marketplace** of rules and skills that any project can pull in to give Claude consistent, opinionated behaviour across the team.

---

## How it works

The marketplace is defined in [`marketplace.json`](./marketplace.json). Each **package** bundles two things:

- **Rules** — a Markdown file that gets added to a project's `CLAUDE.md`. Rules tell Claude how to write code: conventions, patterns, and things to avoid.
- **Skills** — slash-command prompt files (`.md`) that get copied into a project's `.claude/skills/` directory. Skills give Claude reusable, structured instructions for common tasks.

### Setting up a project

1. **Copy the rules** for the packages you want into your project's `CLAUDE.md` (or `import` them with a `@path` reference if your Claude Code version supports it):

   ```bash
   cat packages/nextjs/rules.md >> /your-project/CLAUDE.md
   ```

2. **Install the skills** by copying the skill files into your project's `.claude/skills/` directory:

   ```bash
   cp packages/nextjs/skills/*.md /your-project/.claude/skills/
   ```

3. Open Claude Code in your project — the rules are active immediately, and the skills are available as slash commands.

---

## Packages

### `nextjs` — Next.js Development

> Rules and skills for Next.js App Router development with TypeScript and Tailwind CSS.

**Rules file:** `packages/nextjs/rules.md`

The rules cover:

| Area | What's enforced |
|---|---|
| Router | App Router only; route group conventions; correct file naming |
| Components | Server Components by default; push `"use client"` to leaf nodes |
| Data fetching | `async/await` in Server Components; `fetch()` cache options; Server Actions over API routes for mutations |
| TypeScript | `.ts`/`.tsx` only; `interface` for props; typed Next.js generics |
| Styling | Tailwind CSS; `cn()` for conditional classes; no inline style objects |
| Images & Fonts | `next/image` and `next/font` required |
| Performance | Avoid unnecessary client boundaries, barrel files, disabled lazy loading |
| Error handling | `notFound()` and `redirect()` from `next/navigation`; segment-level `error.tsx` |
| Env vars | `NEXT_PUBLIC_` prefix rules; Zod validation at startup |

**Skills:**

| Skill | Usage | Description |
|---|---|---|
| `new-page` | `/new-page <route-path> [description]` | Scaffold an App Router page with `loading.tsx` and `error.tsx` |
| `new-component` | `/new-component <ComponentName> [client\|server] [description]` | Generate a typed, Tailwind-styled React component |
| `new-server-action` | `/new-server-action <action-name> [description]` | Create a Zod-validated Server Action with a wired form component |
| `new-api-route` | `/new-api-route <route-path> [GET,POST,...] [description]` | Generate a typed `route.ts` handler with validation and error handling |
| `review-nextjs` | `/review-nextjs [file-path]` | Audit a file for Next.js best-practice violations with fix suggestions |

---

## Repository structure

```
marketplace.json          # Catalog of all packages
packages/
  nextjs/
    rules.md              # Next.js coding rules for CLAUDE.md
    skills/
      new-page.md
      new-component.md
      new-server-action.md
      new-api-route.md
      review-nextjs.md
```
