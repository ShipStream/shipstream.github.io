# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based documentation site for the ShipStream API, hosted at https://docs.shipstream.io/. The site provides comprehensive documentation for ShipStream's merchant API, including authentication, method references, and integration examples.

## Technology Stack

- **Jekyll**: Static site generator using Ruby
- **Ruby**: Programming language (uses `github-pages` gem)
- **Bootstrap 2.3.2**: CSS framework for styling
- **Kramdown**: Markdown processor
- **Rouge**: Syntax highlighter

## Common Commands

### Development Setup
```bash
# Install dependencies
bundle install

# Serve locally for development
bundle exec jekyll serve

# Build the site
bundle exec jekyll build
```

### Content Management
```bash
# Create a new page (uses custom Ruby script)
bin/jekyll-page "Page Title" category [filename]

# Create and edit a new page
bin/jekyll-page "Page Title" category [filename] --edit

# Relink pages (creates symlinks in _pages/)
bin/jekyll-page --link
```

## Project Structure

### Content Organization
- `_posts/`: All documentation pages stored as Jekyll posts with date prefixes
- `_pages/`: Symlinked pages without date prefixes (auto-generated)
- `_layouts/`: HTML templates (`default.html`, `page.html`)
- `_includes/`: Reusable components (`header.html`, `footer.html`, `navigation.html`)
- `samples/`: Sample import files (CSV, JSON, XLSX formats)

### Site Configuration
- `_config.yml`: Jekyll configuration with site metadata and navigation structure
- Categories: `doc` (Documentation), `tut` (Tutorial), `ref` (API Reference), `dev` (Developers), `post` (Posts)
- Navigation is auto-generated based on post categories and order values

### Content Format
All documentation pages use Jekyll front matter:
```yaml
---
layout: page
title: "Page Title"
category: ref|doc|tut|dev|post
date: YYYY-MM-DD HH:MM:SS
order: 123  # Controls navigation ordering
---
```

## API Documentation Structure

The documentation covers:
- **Authentication**: JSONRPC with HTTP Basic Auth or session-based
- **Core Entities**: Orders, Products, Shipments, Inventory, Warehouses, etc.
- **Import Formats**: CSV, JSON, XLSX for bulk operations
- **Webhooks**: Real-time event notifications
- **Middleware**: Plugin system for custom integrations

## Key Files to Understand

- `_posts/2014-07-15-api-basics.md`: Core API authentication and request/response format
- `_posts/2014-07-25-order.md`: Order management API methods and properties
- `_posts/2014-07-25-product.md`: Product catalog API
- `_posts/2014-07-25-shipment.md`: Shipment tracking and management
- `index.md`: Main landing page with getting started information

## Development Notes

- The site uses a custom Ruby script (`bin/jekyll-page`) for content creation
- Pages are stored as dated posts but accessible via undated symlinks
- Navigation ordering is controlled by the `order` field in front matter
- The site is configured for GitHub Pages hosting
- Bootstrap 2.3.2 is used for styling (legacy version)