# Franklin.Dev

[![Netlify Status](https://api.netlify.com/api/v1/badges/8350bcc2-4bf4-4ec7-b68c-a17a63a07110/deploy-status)](https://app.netlify.com/sites/franklin-dev-astro/deploys)


## 🚀 Project Structure

Inside of your Astro project, you'll see the following folders and files:

```text
├── public/
├── src/
│   ├── components/
│   ├── content/
│   ├── layouts/
│   └── pages/
├── astro.config.mjs
├── README.md
├── package.json
└── tsconfig.json
```

Astro looks for `.astro` or `.md` files in the `src/pages/` directory. Each page is exposed as a route based on its file name.

There's nothing special about `src/components/`, but that's where we like to put any Astro/React/Vue/Svelte/Preact components.

The `src/content/` directory contains "collections" of related Markdown and MDX documents. Use `getCollection()` to retrieve posts from `src/content/blog/`, and type-check your frontmatter using an optional schema. See [Astro's Content Collections docs](https://docs.astro.build/en/guides/content-collections/) to learn more.

Any static assets, like images, can be placed in the `public/` directory.

## 🧞 Commands

All commands are run from the root of the project, from a terminal:

| Command                    | Action                                           |
| :------------------------- | :----------------------------------------------- |
| `pnpm install`             | Installs dependencies                            |
| `pnpm dev`                 | Starts local dev server at `localhost:4321`      |
| `pnpm build`               | Build your production site to `./dist/`          |
| `pnpm preview`             | Preview your build locally, before deploying     |
| `pnpm astro ...`           | Run CLI commands like `astro add`, `astro check` |
| `pnpm astro --help`        | Get help using the Astro CLI                     |

## 🐳 Development Container

This project includes a secure development container configuration for VS Code with Claude Code integration.

### Features

- **Claude Code**: AI-powered coding assistant pre-installed and ready to use
- **Enhanced Security**: Network firewall restricts outbound connections to trusted services only
- **Persistent Configuration**: Claude Code settings and command history preserved between sessions
- **Developer Tools**: Includes zsh, fzf, git-delta, GitHub CLI, and more
- **Node 20 Environment**: Production-ready setup with pnpm package manager

### Getting Started

1. Install [VS Code](https://code.visualstudio.com/) and the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
2. Open this repository in VS Code
3. When prompted, click "Reopen in Container" (or press `Cmd+Shift+P` → "Dev Containers: Reopen in Container")
4. Wait for the container to build and initialize

### Using Claude Code

Once inside the container, you can use Claude Code safely with enhanced permissions:

```bash
claude --dangerously-skip-permissions
```

The firewall configuration provides security by restricting network access to:
- Claude API (api.anthropic.com)
- npm registry
- GitHub
- VS Code marketplace
- DNS and SSH

All other external traffic is blocked for safety.

### Security Notes

- The devcontainer runs with network isolation via iptables firewall
- Container runs as non-root `node` user
- Only use `--dangerously-skip-permissions` in this protected environment
- Only develop with trusted repositories in this container

For more details, see the [Claude Code devcontainer documentation](https://docs.claude.com/en/docs/claude-code/devcontainer).

## 👀 Want to learn more?

Check out [our documentation](https://docs.astro.build) or jump into our [Discord server](https://astro.build/chat).