# Otis agent skills

These skills connect your coding agent to [Otis](https://www.runotis.com), the product analytics agent for AI applications. With them, your agent can ask Otis how your product is used. It can also instrument your app with the Otis SDK: choose what to measure, add the code, and check that data arrives.

The skills use the open [Agent Skills](https://agentskills.io) format. They work in Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, and other agents that support it.

Each skill needs the Otis MCP server. MCP (Model Context Protocol) is the standard way coding agents connect to outside tools. The server gives your agent live data from your Otis project and the current instructions for each skill. You need an Otis account to sign in to it.

## Install

Use one install method for each agent. If you install the skills twice for the same agent, it gets two copies of every skill.

### Claude Code

The plugin installs the skills and the MCP server together.

```bash
claude plugin marketplace add runotis/agent-skills
claude plugin install otis@otis
```

Start Claude Code and run `/mcp` to sign in to Otis.

### Codex

The plugin installs the skills and the MCP server together.

```bash
codex plugin marketplace add runotis/agent-skills
codex plugin add otis@otis
```

Then sign in to Otis:

```bash
codex mcp login otis
```

### Cursor, GitHub Copilot, Gemini CLI, and other agents

Install the skills with the [skills CLI](https://github.com/vercel-labs/skills), then add the MCP server. Run the first command from the root of your repository. Name your agent with `-a`, so that the command writes skills for that agent only.

```bash
npx skills add runotis/agent-skills -a cursor
```

Use `-a github-copilot` for GitHub Copilot and `-a gemini-cli` for Gemini CLI. The skills CLI documentation lists the name for every agent it supports.

Then add the Otis MCP server at `https://app.runotis.com/mcp`. The command for each agent is in the [Otis MCP server documentation](https://www.runotis.com/docs/integrations/mcp-server#connect-your-agent).

## Skills

| Skill | What it does |
|-------|--------------|
| `otis` | Asks Otis about product usage, metrics, and the insights Otis has found. |
| `otis-analyze` | Profiles your codebase and recommends what to measure. |
| `otis-instrument` | Installs the SDK, adds instrumentation, runs your tests, and opens one pull request. |
| `otis-verify` | Checks the instrumentation and confirms that data is arriving. |
| `otis-status` | Shows instrumentation progress for each measurement. |

Describe the task to your agent in plain language, such as "analyze this repo with Otis". Your agent also chooses a skill on its own when your request matches it. For what each skill does in detail, see the [coding agents documentation](https://www.runotis.com/docs/integrations/coding-agents).

## How the skills stay current

Each skill file is short. It tells your agent to fetch the full instructions from the Otis MCP server, so your agent always follows the current version. You do not need to update the skills to get new instructions.

An update changes only a skill's name, its description, or the plugin's settings. To update:

- **Claude Code:** run `claude plugin marketplace update otis`, then `claude plugin update otis@otis`, and restart Claude Code.
- **Codex:** run `codex plugin marketplace upgrade otis`, then `codex plugin add otis@otis`.
- **Skills CLI:** run `npx skills update`.

## Contributing

This repository is published from Otis's main codebase, and each release overwrites it. Pull requests here cannot be merged. To report a problem or suggest a change, write to support@runotis.com.

## License

[MIT](LICENSE)
