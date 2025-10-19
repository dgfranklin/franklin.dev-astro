# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is David Franklin's personal website built with Astro 5.x. It's a static site featuring a landing page and blog with Markdown/MDX content management.

**Tech Stack:**
- Astro 5.x with MDX and Tailwind CSS
- TypeScript with strict null checks
- Content Collections for type-safe blog posts
- pnpm 9.x as package manager
- Deployed to Netlify

## Development Commands

```bash
# Install dependencies
pnpm install

# Start dev server (http://localhost:4321)
pnpm dev
# or
pnpm start

# Build for production
pnpm build

# Preview production build
pnpm preview
```

## Content Architecture

### Content Collections

Blog posts live in `src/content/blog/` as Markdown/MDX files. The collection schema is defined in `src/content/config.ts`:

```typescript
{
  title: string
  description: string
  pubDate: Date
  updatedDate?: Date
  heroImage?: string
}
```

To add a new blog post, create a new `.md` or `.mdx` file in `src/content/blog/` with the required frontmatter fields.

### Route Generation

Blog posts use dynamic routing via `src/pages/blog/[...slug].astro`:
1. `getStaticPaths()` queries all blog posts via `getCollection('blog')`
2. Each post is rendered using the `BlogPost` layout
3. MDX content is rendered via the `<Content />` component

### Site Configuration

Global constants (site title, description) are centralized in `src/consts.ts` for easy updates across the site.

## Component Structure

**Layouts:**
- `src/layouts/BlogPost.astro` - Blog post template with metadata, hero images, and date formatting

**Shared Components:**
- `BaseHead.astro` - SEO metadata and base HTML head elements
- `Header.astro` - Site navigation
- `Footer.astro` - Site footer
- `FormattedDate.astro` - Date formatting utility
- `HeaderLink.astro` - Navigation link component
- `SocialLinks.astro` - Social media links

The homepage (`src/pages/index.astro`) is standalone and includes profile information and career history.

## Styling

Uses Tailwind CSS configured via `tailwind.config.mjs`. Global styles live in `src/styles/global.css`. Component-specific styles can be scoped within Astro components using `<style>` tags.

## Development Container

This project includes a secure devcontainer configuration for VS Code with Claude Code integration. The devcontainer includes:
- Network firewall restricting outbound connections to trusted services
- Pre-installed Claude Code CLI
- Node 20 environment with pnpm
- Enhanced developer tools (zsh, fzf, git-delta, GitHub CLI)

To use the devcontainer:
1. Open the project in VS Code with the Dev Containers extension
2. Click "Reopen in Container" when prompted
3. Wait for the firewall initialization to complete

Inside the devcontainer, you can safely use:
```bash
claude --dangerously-skip-permissions
```

The firewall restricts access to only: Claude API, npm registry, GitHub, VS Code marketplace, DNS, and SSH.
