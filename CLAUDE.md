# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a personal portfolio website built with Hugo (static site generator). It showcases Jason Hutchens' projects, resume, and various links to online profiles. The site uses the "Prologue" theme from HTML5 UP and is deployed to AWS S3.

## Key Commands

### Development
```bash
hugo server
```
Starts the local development server with live reload. The site will be available at http://localhost:1313/

### Deployment
```bash
hugo deploy --target production
```
Builds the static site and deploys it to the production S3 bucket (s3://www.kranzky.com in ap-southeast-2 region).

## Architecture

### Hugo Configuration
- **config.toml**: Main configuration file containing:
  - Site metadata (baseurl, title, theme)
  - Personal information (name, description)
  - Social media links (medium, github, stackoverflow, linkedin, youtube)
  - Project listings organized in a 3-column grid layout (projects1, projects2, projects3)
  - AWS S3 deployment target configuration

### Directory Structure
- **content/**: Currently minimal (contains .gitkeep), content is primarily defined in config.toml
- **data/projects/**: Project-related data files
- **static/**: Static assets (images in static/img/, jason_hutchens.pdf resume)
- **themes/prologue/**: The HTML5 UP Prologue theme
  - **layouts/index.html**: Main page template with hardcoded navigation and project grid
  - **static/**: Theme assets (CSS, JS, images)
- **public/**: Generated site output (created by hugo build, not version controlled)

### Theme Customization
The main layout (themes/prologue/layouts/index.html) has been customized with:
- Navigation links to external resources (resume, papers, diary, blog, lab, code, games, podcast, photos, videos, rides, books, movies, blogger, web1.0)
- 3-column responsive project grid using Hugo's templating to iterate over .Site.Params.projects1/2/3
- Social icons rendered from config.toml params

### Content Management
- Projects are defined in config.toml as params.projects1/2/3 arrays (organized in rows)
- Each project has: title, alt, source (image path), url
- Navigation menu is hardcoded in themes/prologue/layouts/index.html
- To add/modify projects: edit config.toml
- To change navigation or layout: edit themes/prologue/layouts/index.html

## Hugo Version
The site uses Hugo v0.147.9+extended+withdeploy (installed via Homebrew on macOS ARM64).
