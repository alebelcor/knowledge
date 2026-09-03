# Agent Skills

Skills are reusable capabilities for AI agents. They provide procedural knowledge that helps agents accomplish specific tasks more effectively. Think of them as plugins or extensions that enhance what your AI agent can do.

Install and discover skills (across different [agent harnesses](https://en.wikipedia.org/wiki/Agent_harness)) with the `skills` CLI.

```bash
pnpx skills add <package> # install a skill package
pnpx skills add <package>@<skill-name> # install a specific skill from a package
pnpx skills remove # interactive removal of skills
pnpx skills update --global --yes # update all skills
pnpx skills list --global # list global skills
pnpx skills --help # see all commands and options
```

## Skills (global)

```bash
skills=(
	# https://www.skills.sh/addyosmani/web-quality-skills
	addyosmani/web-quality-skills

	# https://www.skills.sh/anthropics/knowledge-work-plugins/system-design
	anthropics/knowledge-work-plugins@system-design

	# https://www.skills.sh/anthropics/knowledge-work-plugins/testing-strategy
	anthropics/knowledge-work-plugins@testing-strategy

	# https://www.skills.sh/anthropics/skills/frontend-design
	anthropics/skills@frontend-design

	# https://www.skills.sh/cloudflare/skills/cloudflare
	cloudflare/skills@cloudflare

	# https://www.skills.sh/cloudflare/skills@workers-best/practices
	cloudflare/skills@workers-best-practices

	# https://www.skills.sh/cloudflare/skills/wrangler
	cloudflare/skills@wrangler

	# https://www.skills.sh/cursor/plugins/typescript-best-practices
	cursor/plugins@typescript-best-practices

	# https://www.skills.sh/emilkowalski/skills/apple-design
	emilkowalski/skills@apple-design

	# https://www.skills.sh/emilkowalski/skills/emil-design-eng
	emilkowalski/skills@emil-design-eng

	# https://www.skills.sh/getsentry/skills/commit
	getsentry/skills@commit

	# https://www.skills.sh/mcollina/skills/typescript-magician
	mcollina/skills@typescript-magician

	# https://www.skills.sh/obra/superpowers/using-git-worktrees
	obra/superpowers@using-git-worktrees

	# https://www.skills.sh/vercel-labs/agent-skills/vercel-react-best-practices
	vercel-labs/agent-skills@vercel-react-best-practices

	# https://www.skills.sh/vercel-labs/agent-skills/vercel-composition-patterns
	vercel-labs/agent-skills@vercel-composition-patterns

	# https://www.skills.sh/vercel-labs/agent-skills/web-design-guidelines
	vercel-labs/agent-skills@web-design-guidelines

	# https://www.skills.sh/vercel-labs/skills/find-skills
	vercel-labs/skills@find-skills

	# https://www.skills.sh/wshobson/agents/modern-javascript-patterns
	wshobson/agents@modern-javascript-patterns

	# https://www.skills.sh/wshobson/agents/typescript-advanced-types
	wshobson/agents@typescript-advanced-types
)

for item in "${skills[@]}"; do pnpx skills add "$item" --global; done
```
## Skills (local)

```bash
skills=(
	# -----------------------------------------------------------------------
	# Hono
	# -----------------------------------------------------------------------

	# https://www.skills.sh/honojs/skills/hono
	honojs/skills@hono

	# -----------------------------------------------------------------------
	# Node.js
	# -----------------------------------------------------------------------

	# https://www.skills.sh/mcollina/skills/node
	mcollina/skills@node

	# -----------------------------------------------------------------------
	# Playwright
	# -----------------------------------------------------------------------

	# https://www.skills.sh/currents-dev/playwright-best-practices-skill/playwright-best-practices
	currents-dev/playwright-best-practices-skill@playwright-best-practices

	# -----------------------------------------------------------------------
	# React Router
	# -----------------------------------------------------------------------

	# https://www.skills.sh/remix-run/react-router/react-router
	remix-run/react-router@react-router

	# https://www.skills.sh/sergiodxa/agent-skills/frontend-react-router-best-practices
	sergiodxa/agent-skills@frontend-react-router-best-practices

	# -----------------------------------------------------------------------
	# shadcn/ui
	# -----------------------------------------------------------------------

	# https://www.skills.sh/google-labs-code/stitch-skills/shadcn-ui
	google-labs-code/shadcn-ui@shadcn-ui

	# https://www.skills.sh/shadcn-ui/ui
	shadcn-ui/ui
)

for item in "${skills[@]}"; do pnpx skills add "$item" --global; done
```

## Links

- [The Open Agent Skills Ecosystem](https://www.skills.sh)
- [`skills` documentation](https://www.skills.sh/docs)
