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

## Skills

```bash
skills=(
	# https://www.skills.sh/anthropics/skills/frontend-design
	anthropics/skills@frontend-design

	# https://www.skills.sh/cloudflare/skills/cloudflare
	cloudflare/skills@cloudflare

	# https://www.skills.sh/cloudflare/skills@workers-best/practices
	cloudflare/skills@workers-best-practices

	# https://www.skills.sh/cloudflare/skills/wrangler
	cloudflare/skills@wrangler

	# https://www.aihero.dev/skills
	# https://www.skills.sh/mattpocock/skills
	mattpocock/skills

	# https://www.skills.sh/vercel-labs/agent-skills/vercel-react-best-practices
	vercel-labs/agent-skills@vercel-react-best-practices

	# https://www.skills.sh/vercel-labs/agent-skills/vercel-composition-patterns
	vercel-labs/agent-skills@vercel-composition-patterns

	# https://www.skills.sh/vercel-labs/agent-skills/web-design-guidelines
	vercel-labs/agent-skills@web-design-guidelines

	# https://www.skills.sh/vercel-labs/skills/find-skills
	vercel-labs/skills@find-skills
)

for item in "${skills[@]}"; do pnpx skills add "$item" --global; done
```

## Links

- [The Open Agent Skills Ecosystem](https://www.skills.sh)
- [`skills` documentation](https://www.skills.sh/docs)
