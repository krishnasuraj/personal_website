# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal website and blog for krishnasuraj.com, built with Astro and deployed to GitHub Pages via GitHub Actions.

## Commands

- `npm run dev` — Start dev server (localhost:4321)
- `npm run build` — Production build to `dist/`
- `npm run preview` — Preview production build locally

## Architecture

**Astro static site** using the blog template. Zero client-side JS by default.

- `src/content/blog/` — Blog posts as Markdown (`.md`) or MDX (`.mdx`) files with frontmatter
- `src/pages/` — File-based routing. Each `.astro` file becomes a page
- `src/layouts/BlogPost.astro` — Layout wrapper for all blog posts
- `src/components/` — Reusable Astro components (Header, Footer, BaseHead, etc.)
- `src/consts.ts` — Site-wide constants (title, description)
- `src/content.config.ts` — Content collection schema defining blog frontmatter fields
- `src/styles/global.css` — Global styles
- `public/` — Static assets served as-is (includes `CNAME` for custom domain)

**Blog post frontmatter schema** (defined in `content.config.ts`):
- `title` (string, required)
- `description` (string, required)
- `pubDate` (date, required)
- `updatedDate` (date, optional)
- `heroImage` (image, optional)

**Deployment**: Push to `main` triggers `.github/workflows/deploy.yml` which builds and deploys to GitHub Pages. Custom domain `krishnasuraj.com` is configured via `public/CNAME`.

## Adding a Blog Post

Create a new `.md` or `.mdx` file in `src/content/blog/` with the required frontmatter. It will automatically appear on the blog index page, sorted by `pubDate` (newest first).
