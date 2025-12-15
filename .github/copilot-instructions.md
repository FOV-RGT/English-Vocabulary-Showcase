# Copilot instructions for slidev-demo

This repo is a small Slidev presentation. Keep guidance concise and project-specific.

- **Big picture:** The app is a Slidev slide deck driven by `slides.md` (Markdown + Vue). Slides may embed Vue components from `components/` and external code snippets from `snippets/`.

- **How to run:** follow `README.md`:
  - install: `pnpm install`
  - dev: `pnpm dev` (opens Slidev, default port 3030)
  - build/export: `pnpm build` / `pnpm export`
  See scripts in [package.json](package.json#L1).

- **Key files:**
  - Slides entry: [slides.md](slides.md#L1)
  - Example component: [components/Counter.vue](components/Counter.vue#L1)
  - External snippets: [snippets/external.ts](snippets/external.ts#L1)
  - Docs / quick start: [README.md](README.md#L1)

- **Patterns & conventions (do not invent):**
  - Slides use frontmatter for global options (e.g. `theme`, `mdc`, `transition`) — see top of [slides.md](slides.md#L1).
  - Vue components placed in `components/` are referenced directly in Markdown, e.g. `<Counter :count="10" />` (see `slides.md` "Components" section).
  - External code blocks are embedded via the triple-chev `<<<` include, for example `<<< @/snippets/external.ts#snippet` (see [slides.md](slides.md#L1)).
  - Keep component props and exports TypeScript-friendly (example in `Counter.vue`).

- **What Copilot should do when editing:**
  - Prefer editing `slides.md` and `components/*` files. Avoid modifying Slidev internals or changing global deps unless requested.
  - When adding code examples, respect the existing code-block metadata (e.g. `twoslash`, `shiki` lines) used for highlighting and magic-move snippets.
  - When adding snippets, add them under `snippets/` and reference via `<<< @/snippets/<file>#<id>`; keep `#region`/`#endregion` markers if used for snippet extraction.

- **Build / dev gotchas:**
  - The project uses Slidev CLI (`@slidev/cli`); runtime behaviors (themes, layouts) are configured via `slides.md` frontmatter and installed theme packages.
  - Use `pnpm` (not `npm`/`yarn`) by default to run scripts shown in `package.json`.

- **Examples to follow:**
  - Add a new slide using the same frontmatter structure and layout keys as existing slides: follow patterns in [slides.md](slides.md#L1).
  - Add interactive component: create `components/MyWidget.vue` and use `<MyWidget/>` directly inside `slides.md` (see `Counter.vue`).

If anything in this summary is unclear or you want more detail on a specific area (build, theme, component API), tell me which part to expand.
