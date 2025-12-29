<!-- Copilot instructions for AI coding agents: concise, action-oriented guidance tailored to this repository -->
# Copilot Instructions — my-portfolio

Purpose
- Help maintain and evolve this personal portfolio site. The repository currently contains no source files in the workspace root; these instructions assume a static-site / frontend project (React/Next/Vite/Gatsby) named `my-portfolio` — verify the actual stack before making large changes.

What to check first
- Look for these files (in order) to discover the real stack and workflows: `package.json`, `README.md`, `next.config.js`, `vite.config.js`, `gatsby-config.js`, `netlify.toml`, `.github/workflows/*`, `src/`, `public/`, `projects/`, `content/`, `src/pages`.
- If `package.json` exists, read `scripts` to find `dev`, `build`, `start`, `lint`, `test` commands — prefer using those exact commands.

Big-picture assumptions (verify them)
- This is a single-page/personal site: source usually lives under `src/` or at project root. Content for projects/blogs may live in `content/`, `data/`, or `src/content/`.
- Deployment is likely to Vercel/Netlify/GitHub Pages — check `netlify.toml`, `.github/workflows` or `vercel.json` for CI/deploy hooks.

Agent action rules (precise, testable)
- NEVER change build/deploy scripts without: (a) confirming there's a CI workflow file, and (b) running the build locally (`npm ci` then `npm run build`) and reporting any errors in the PR description.
- If files are missing (e.g., no `package.json`), open an issue instead of scaffolding a new project; ask the repo owner which stack to use.

Patterns & conventions to follow
- Routing/pages: prefer `src/pages/` (Next/Gatsby) or `src/routes` (others). For Next.js, use `pages` or `app` conventions depending on `next` version found in `package.json`.
- Styling: look for `tailwind.config.js` or `postcss.config.js`. If Tailwind present, follow its utility-first patterns rather than introducing new CSS frameworks.
- Content: project entries should be placed in `content/projects/*.md` or `src/data/projects.*` — mirror existing structure if present.

Examples (how to run common tasks)
- Install dependencies (if `package.json` exists):
  - `npm ci` (preferred for CI), or `npm install` locally
  - `npm run dev` to start a dev server
  - `npm run build` to build; `npm start` or framework-specific serve command to preview

Integration points
- CI: check `.github/workflows/*.yml` for build/test steps — replicate the same `npm` script names when adding tests or linters.
- External CMS or APIs: look for environment variables in `.env*` or references in code to `process.env` — do not commit secrets; create `.env.example` if missing and needed.

PR guidance for agents
- When you modify scripts, tests, or deploy config, include in the PR body: commands you ran, build output errors/warnings, and a one-line summary of the change impact.
- For content-only edits (projects, text), keep changes isolated to `content/` or `data/` and avoid touching build/config files.

If uncertain
- Stop and ask: "Which framework is this project using? Should I scaffold missing config or open an issue?"

Contact / follow-up
- After applying changes, add a short note to the PR describing what files you inspected and what assumptions you made.

-- End of file
