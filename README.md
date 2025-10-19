# Franklin.Dev

[![Netlify Status](https://api.netlify.com/api/v1/badges/8350bcc2-4bf4-4ec7-b68c-a17a63a07110/deploy-status)](https://app.netlify.com/sites/franklin-dev-astro/deploys)

David Franklin's personal website built with Astro 5.x. A modern static site featuring a landing page and blog with type-safe content management.

## 🛠️ Tech Stack

- **Framework**: Astro 5.x
- **Styling**: Tailwind CSS
- **Content**: MDX with Content Collections
- **Language**: TypeScript with strict null checks
- **Package Manager**: pnpm 9.x
- **Deployment**: Netlify

## 🚀 Project Structure

```text
├── public/              # Static assets (images, favicon, etc.)
├── src/
│   ├── components/      # Reusable Astro components
│   ├── content/
│   │   ├── blog/       # Blog posts (Markdown/MDX)
│   │   ├── bio.md      # Bio content
│   │   └── config.ts   # Content collection schemas
│   ├── layouts/        # Page layouts
│   ├── pages/          # File-based routes
│   ├── styles/         # Global styles
│   └── consts.ts       # Site-wide constants
├── astro.config.mjs    # Astro configuration
├── tailwind.config.mjs # Tailwind configuration
├── CLAUDE.md           # Claude Code project guidance
└── tsconfig.json       # TypeScript configuration
```

### Key Directories

- **`src/pages/`**: File-based routing. Each `.astro` or `.md` file becomes a route.
- **`src/content/blog/`**: Blog posts managed via Content Collections with type-safe frontmatter validation.
- **`src/components/`**: Shared components like `Header`, `Footer`, `BaseHead`, and `FormattedDate`.
- **`src/layouts/`**: Page templates, including `BlogPost.astro` for blog post rendering.

See [Astro's Content Collections docs](https://docs.astro.build/en/guides/content-collections/) for more information on content management.

## 🧞 Commands

All commands are run from the root of the project, from a terminal:

| Command                    | Action                                           |
| :------------------------- | :----------------------------------------------- |
| `pnpm install`             | Installs dependencies                            |
| `pnpm dev`                 | Starts local dev server at `localhost:4321`      |
| `pnpm start`               | Alias for `pnpm dev`                             |
| `pnpm build`               | Build your production site to `./dist/`          |
| `pnpm preview`             | Preview your build locally, before deploying     |
| `pnpm astro ...`           | Run CLI commands like `astro add`, `astro check` |
| `pnpm astro --help`        | Get help using the Astro CLI                     |

**Note for devcontainer users**: When running the dev server from inside the devcontainer, use `pnpm dev -- --host` to make the server accessible from your host machine's browser.

## 📝 Content Management

### Adding Blog Posts

Create new blog posts in `src/content/blog/` as Markdown or MDX files. Each post requires frontmatter with the following schema (defined in [src/content/config.ts](src/content/config.ts)):

```yaml
---
title: 'Your Post Title'
description: 'A brief description of your post'
pubDate: 2025-01-15
updatedDate: 2025-01-16  # Optional
heroImage: '/blog-placeholder.jpg'  # Optional
---
```

Blog posts are automatically processed through the Content Collections API and rendered using the `BlogPost` layout via dynamic routing at `src/pages/blog/[...slug].astro`.

### Site Configuration

Update site-wide constants like `SITE_TITLE` and `SITE_DESCRIPTION` in [src/consts.ts](src/consts.ts).

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

Check out [Astro's documentation](https://docs.astro.build) or jump into the [Astro Discord server](https://astro.build/chat).
