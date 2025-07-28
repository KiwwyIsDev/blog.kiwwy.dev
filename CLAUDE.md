# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

This is an Astro-based blog built with the Fuwari template. Use pnpm as the package manager.

| Command | Purpose |
|---------|---------|
| `pnpm install` | Install dependencies |
| `pnpm dev` | Start development server at localhost:4321 |
| `pnpm build` | Build production site (includes pagefind indexing) |
| `pnpm preview` | Preview production build locally |
| `pnpm check` | Run Astro checks for errors |
| `pnpm type-check` | Run TypeScript type checking |
| `pnpm lint` | Lint and auto-fix code with Biome |
| `pnpm format` | Format code with Biome |
| `pnpm new-post <filename>` | Create new blog post with template |

## Architecture Overview

### Core Structure
- **Astro-based**: Static site generator with component islands
- **Content System**: Blog posts in `src/content/posts/` with frontmatter configuration
- **Styling**: Tailwind CSS with custom CSS variables and Stylus preprocessing
- **Theming**: Dynamic theme colors with light/dark mode support
- **Search**: Pagefind integration for static search functionality

### Key Configuration Files
- `src/config.ts` - Main site configuration (title, theme, navigation, profile)
- `astro.config.mjs` - Astro build configuration with plugins and markdown processing
- `biome.json` - Code formatting and linting rules (uses tabs, double quotes)

### Component Architecture
- **Layout System**: `Layout.astro` → `MainGridLayout.astro` for consistent structure
- **Component Types**:
  - Page components in `src/components/` (Astro + Svelte)
  - Control components for UI interactions
  - Widget components for sidebar functionality
  - Misc components for utilities

### Content Management
- Posts use Astro's content collections with TypeScript validation
- Frontmatter schema defined in `src/content/config.ts`
- Support for drafts, categories, tags, and multi-language content
- Custom Markdown plugins for enhanced syntax (admonitions, GitHub cards, math)

### Plugin System
- Custom Expressive Code plugins for syntax highlighting
- Remark/Rehype plugins for extended Markdown processing
- Custom components rendered through rehype-components

### Internationalization
- Multi-language support configured in `src/i18n/`
- Language files in `src/i18n/languages/`
- Site language set in `src/config.ts`

### Build Process
- Standard Astro build pipeline
- Post-build Pagefind indexing for search
- Optimized for static deployment (Vercel, Netlify, etc.)

## Development Notes

- Uses pnpm workspaces and requires pnpm 9+
- Code style enforced by Biome (tabs, double quotes, organized imports)
- Svelte components mixed with Astro for interactive elements
- CSS uses custom properties for theming with Tailwind utilities
- Content schema validation prevents malformed posts