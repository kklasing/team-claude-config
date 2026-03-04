# team-claude-config

Shared Claude Code configuration for Team Alpha. This repo is a **Claude plugin marketplace** — it distributes rules and skills that any project can install to give Claude consistent, opinionated behavior across the team.

---

## Adding this marketplace to Claude Code

Run the following command inside Claude Code (any project):

```
/plugin marketplace add kklasing/team-claude-config
```

This registers the repo as a marketplace called **Team-Alpha-Tools**. You only need to do this once — it persists across all your projects.

To confirm it was added:

```
/plugin marketplace list
```

---

## Installing a package

Once the marketplace is registered, install any plugin from it:

```
/plugin install nextjs@Team-Alpha-Tools
```

You'll be prompted to choose a scope:

| Scope | Who it applies to |
|---|---|
| **User** (default) | You, across all projects |
| **Project** | Everyone on the team (saved to `.claude/settings.json`) |
| **Local** | You, in this repo only |

For team-wide consistency, choose **Project** so the plugin is checked into version control.

---

## Packages

### `nextjs` — Next.js Development

> Rules and skills for Next.js App Router development with TypeScript and Tailwind CSS.

Installing this plugin gives Claude two things:

**Rules** — Claude automatically follows these conventions in every response:

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

**Skills** — slash commands available in any Claude Code conversation:

| Command | Usage | Description |
|---|---|---|
| `/new-page` | `/new-page <route-path> [description]` | Scaffold an App Router page with `loading.tsx` and `error.tsx` |
| `/new-component` | `/new-component <ComponentName> [client\|server] [description]` | Generate a typed, Tailwind-styled React component |
| `/new-server-action` | `/new-server-action <action-name> [description]` | Create a Zod-validated Server Action with a wired form component |
| `/new-api-route` | `/new-api-route <route-path> [GET,POST,...] [description]` | Generate a typed `route.ts` handler with validation and error handling |
| `/review-nextjs` | `/review-nextjs [file-path]` | Audit a file for Next.js best-practice violations with fix suggestions |

---

## Managing plugins

```
/plugin              # Open the full plugin UI (Discover / Installed / Marketplaces)
/plugin marketplace update Team-Alpha-Tools   # Pull latest changes from this repo
/plugin uninstall nextjs@Team-Alpha-Tools     # Remove a plugin
```

---

## Repository structure

```
marketplace.json                        # Marketplace catalog
packages/
  nextjs/
    .claude-plugin/
      plugin.json                       # Plugin manifest
    rules.md                            # Next.js coding rules
    skills/
      new-page.md
      new-component.md
      new-server-action.md
      new-api-route.md
      review-nextjs.md
```
