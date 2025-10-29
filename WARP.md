# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a Hugo-based academic CV/portfolio website built with the Hugo Blox Builder (formerly Hugo Academic). It uses Tailwind CSS v4 for styling and is designed to be deployed on GitHub Pages or Netlify.

**Tech Stack:**
- Hugo Extended v0.152.1 (static site generator)
- Go 1.21.5+ (Hugo modules dependency)
- pnpm (package manager)
- Tailwind CSS v4
- Preact (for interactive components)

## Development Commands

### Local Development
```bash
# Install dependencies
pnpm install

# Run development server (disables fast render for accuracy)
pnpm dev
# OR
hugo server --disableFastRender

# View site at http://localhost:1313
```

### Building
```bash
# Build for production (minified)
pnpm build
# OR
hugo --minify

# Output directory: public/
```

### Testing Build
```bash
# Build with verbose logging (useful for debugging)
hugo --gc --minify --logLevel debug --printI18nWarnings --printPathWarnings

# Test that Go modules are working
hugo mod verify
```

## Architecture

### Content Organization
- **`content/`** - All site content in Markdown
  - `_index.md` - Homepage with section blocks (biography, publications, talks, news)
  - `authors/admin/` - Main profile data (replace with your info)
  - `publications/` - Research papers (supports BibTeX import via GitHub Actions)
  - `blog/` - Blog posts
  - `projects/` - Project showcases
  - `events/` - Talks and presentations
  - `courses/` - Course materials
  - `experience.md` - Work experience section

### Configuration Structure
- **`config/_default/`** - Main configuration directory
  - `hugo.yaml` - Core Hugo settings, taxonomies, output formats
  - `params.yaml` - Site parameters (appearance, SEO, header/footer)
  - `module.yaml` - Hugo modules configuration (imports Hugo Blox)
  - `menus.yaml` - Navigation menu structure
  - `languages.yaml` - Multi-language support

### Hugo Modules
This site uses Hugo modules (not git submodules) to import:
- `github.com/HugoBlox/hugo-blox-builder/modules/blox-plugin-netlify`
- `github.com/HugoBlox/hugo-blox-builder/modules/blox-tailwind`

**Note:** Changes to module configuration require `hugo mod get -u` to update.

### Layouts and Blocks
The site uses a block-based system where pages are composed of reusable sections:
- Biography blocks (`resume-biography-3`)
- Collection blocks (for publications, blog posts, events)
- Markdown content blocks
- Call-to-action cards

Custom layouts can be added to `layouts/` and will override Hugo Blox defaults.

### Content Front Matter Structure
All content uses YAML front matter. Key fields:
- **Authors:** `title`, `role`, `organizations`, `profiles`, `interests`, `education`, `work`, `skills`, `awards`
- **Publications:** Support `featured: true` for highlighting, custom citation formats
- **Pages:** Use `sections:` array to define block layout

## Key Files to Modify

### Personalizing Your Site
1. **`content/authors/admin/_index.md`** - Your profile (name, bio, education, work, skills)
2. **`config/_default/params.yaml`** - Site title, colors, SEO settings
3. **`config/_default/hugo.yaml`** - Site title and base URL
4. **`config/_default/menus.yaml`** - Navigation menu items
5. **`content/_index.md`** - Homepage layout and sections

### Adding Content
- Publications: Add folders to `content/publications/` with `index.md` + optional `cite.bib`
- Blog posts: Add folders to `content/blog/` with `index.md`
- Projects: Add folders to `content/projects/` with `index.md`

## Deployment

### GitHub Pages (via GitHub Actions)
The `.github/workflows/deploy.yml` workflow builds and deploys automatically on push to main branch.

### Netlify (Recommended)
Configuration in `netlify.toml`:
- Auto-builds on push
- Runs Pagefind indexing for search
- Uses Hugo v0.152.1 and Node v22

**Important:** The Netlify build process includes Pagefind search indexing - don't remove `pnpm dlx pagefind` from build commands.

## Important Notes

### Hugo Extended Required
This site requires Hugo Extended (not standard Hugo) due to SCSS/Sass processing in Hugo Blox.

### Module Updates
To update Hugo Blox modules:
```bash
hugo mod get -u
hugo mod tidy
```

### Git Info
If you want to show "last modified" dates, enable in `config/_default/hugo.yaml`:
```yaml
enableGitInfo: true
```

### BibTeX Import
There's a GitHub Action (`.github/workflows/import-publications.yml`) that can automatically import publications from BibTeX sources.

### Customization
- Custom icons: Add SVG files to `assets/media/icons/custom/`
- Custom colors: Modify Tailwind config or use built-in color themes in `params.yaml`
- Custom blocks: Add to `layouts/_partials/blox/` (requires understanding Hugo Blox structure)

## Common Issues

1. **Module errors:** Run `hugo mod clean` then `hugo mod get -u`
2. **Build fails locally but works on Netlify:** Check Hugo version matches `hugoblox.yaml` (v0.152.1)
3. **Styling not applied:** Ensure `pnpm install` was run to install Tailwind CSS
4. **Changes not showing:** Hugo caches aggressively - use `--disableFastRender` or `hugo server --noHTTPCache`
