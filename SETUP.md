# Documentation Site Setup Guide

This document explains the Docsify documentation site setup for multi-version, multi-product, multi-platform documentation.

## What Was Created

### 1. Documentation Structure

```
docs/
├── index.html              # Docsify configuration and main page
├── README.md               # Documentation homepage
├── _sidebar.md             # Navigation sidebar
├── .nojekyll               # Tells GitHub Pages not to use Jekyll
└── <platform>/             # Platform directories
    └── <product>/          # Product directories
        └── <version>/      # Version directories
            └── *.md        # Documentation files
```

### 2. Platforms (4)
- **windows** - Windows desktop applications
- **linux** - Linux distributions
- **macos** - Apple macOS applications
- **web** - Web-based applications

### 3. Products (2+)
- **product-a** - Flagship product
- **product-b** - Specialized solution
- *(easily expandable for more products)*

### 4. Versions (3 per product)
- **1.0.0** - Initial release
- **1.1.0** - Minor updates
- **2.0.0** - Major version

Each platform/product/version combination has its own directory for documentation.

## Features Implemented

### ✅ Docsify Configuration (docs/index.html)

- **Sidebar Navigation**: Hierarchical navigation across all products/platforms/versions
- **Search**: Full-text search across all documentation
- **Auto2Top**: Automatically scroll to top on page change
- **Responsive**: Mobile-friendly design
- **CDN-based**: No build step required

### ✅ Sample Documentation

Created comprehensive sample documentation including:

**Product A - Windows v1.0.0:**
- README.md (main documentation)
- api-reference.md (API documentation)
- tutorials.md (step-by-step guides)
- faq.md (frequently asked questions)

**Product A - Windows v2.0.0:**
- README.md (main documentation with new features)
- migration.md (migration guide from v1.x)

**Product B - Linux v1.0.0:**
- README.md (Linux-specific documentation)

**Product B - Web v1.0.0:**
- README.md (Web application documentation)

### ✅ GitHub Actions Workflow

Created `.github/workflows/deploy-docs.yml` that:
- Triggers on push to main branch (when docs/ changes)
- Can be manually triggered via workflow_dispatch
- Automatically deploys to GitHub Pages
- Uses GitHub's official Pages actions

### ✅ Documentation

- **README.md**: Main repository README with setup instructions
- **CONTRIBUTING.md**: Guidelines for adding and maintaining documentation
- **SETUP.md**: This file - technical setup documentation

### ✅ Configuration Files

- **.gitignore**: Excludes temporary and development files
- **.nojekyll**: Ensures GitHub Pages serves files correctly

## How to Use

### Accessing the Documentation

Once deployed to GitHub Pages (after merging to main), the documentation will be available at:

```
https://nerdydeedsllc.github.io/docs-test/
```

### Local Development

To preview documentation locally:

```bash
# Using Python (recommended)
cd docs
python3 -m http.server 3000

# Using Node.js http-server
npm install -g http-server
cd docs
http-server -p 3000
```

Then open `http://localhost:3000` in your browser.

### Adding New Content

#### Add a New Version

```bash
# Create directory
mkdir -p docs/<platform>/<product>/<new-version>

# Add documentation
echo "# Product - Platform vX.Y.Z" > docs/<platform>/<product>/<new-version>/README.md

# Update sidebar in docs/_sidebar.md
```

#### Add a New Product

```bash
# Create directories for all platforms and versions
mkdir -p docs/{windows,linux,macos,web}/<new-product>/1.0.0

# Add documentation to each
# Update docs/_sidebar.md with new product section
# Update docs/README.md with product information
```

#### Add a New Platform

```bash
# Create directories for all products and versions
mkdir -p docs/<new-platform>/{product-a,product-b}/{1.0.0,1.1.0,2.0.0}

# Add documentation to each
# Update docs/_sidebar.md with new platform entries
```

## GitHub Pages Setup

### First-Time Setup

1. Go to repository **Settings** > **Pages**
2. Under "Source", select **GitHub Actions**
3. Save the settings

The workflow will automatically deploy when:
- Changes are pushed to the main branch in the `docs/` directory
- The workflow is manually triggered

### Subsequent Deployments

Every push to main that modifies files in `docs/` will automatically trigger a deployment.

## Docsify Features

### Search

The search plugin indexes all documentation and provides instant search results. Users can:
- Type keywords in the search box
- Search across all products, platforms, and versions
- Navigate directly to matching pages

### Sidebar

The sidebar provides hierarchical navigation:
- Organized by Product > Platform > Version
- Collapsible sections
- Active page highlighting
- Persistent across page navigation

### Custom Configuration

Edit `docs/index.html` to customize:

```javascript
window.$docsify = {
  name: 'Documentation',        // Site name
  repo: 'github-url',           // GitHub repo link
  loadSidebar: true,            // Enable sidebar
  subMaxLevel: 3,               // Sidebar depth
  auto2top: true,               // Auto-scroll to top
  search: { /* ... */ },        // Search configuration
}
```

## Directory Structure Example

Here's how the structure looks with sample content:

```
docs/
├── index.html
├── README.md
├── _sidebar.md
├── .nojekyll
├── windows/
│   ├── product-a/
│   │   ├── 1.0.0/
│   │   │   ├── README.md
│   │   │   ├── api-reference.md
│   │   │   ├── tutorials.md
│   │   │   └── faq.md
│   │   ├── 1.1.0/
│   │   │   └── README.md
│   │   └── 2.0.0/
│   │       ├── README.md
│   │       └── migration.md
│   └── product-b/
│       └── 1.0.0/
│           └── README.md
├── linux/
│   ├── product-a/
│   │   └── 1.0.0/
│   │       └── README.md
│   └── product-b/
│       └── 1.0.0/
│           └── README.md
├── macos/
│   └── (similar structure)
└── web/
    └── (similar structure)
```

## Best Practices

1. **Always include README.md**: Each version directory should have at least a README.md
2. **Use consistent naming**: Use lowercase with hyphens (e.g., `api-reference.md`)
3. **Link related docs**: Cross-reference related documentation pages
4. **Update sidebar**: Always update `_sidebar.md` when adding new content
5. **Test locally**: Preview changes before committing
6. **Semantic versioning**: Use X.Y.Z format for versions

## Troubleshooting

### Documentation not showing up

1. Check that README.md exists in the directory
2. Verify file is committed and pushed
3. Check that path in sidebar matches actual path
4. Ensure no typos in links

### Search not working

1. Wait a few minutes after deployment for index to build
2. Clear browser cache
3. Check browser console for errors

### Sidebar not updating

1. Verify `_sidebar.md` syntax is correct
2. Ensure paths start with `/` (e.g., `/windows/product-a/1.0.0/`)
3. Check that `loadSidebar: true` in index.html

### GitHub Pages not deploying

1. Check Actions tab for workflow errors
2. Verify GitHub Pages is enabled in Settings
3. Ensure source is set to "GitHub Actions"
4. Check that workflow file is in `.github/workflows/`

## Customization Options

### Themes

Change the theme by editing the CSS link in `docs/index.html`:

```html
<!-- Available themes: vue, buble, dark, pure -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4/lib/themes/vue.css">
```

### Plugins

Add more Docsify plugins before the closing `</body>` tag:

```html
<!-- Code copy button -->
<script src="//cdn.jsdelivr.net/npm/docsify-copy-code"></script>

<!-- Pagination -->
<script src="//cdn.jsdelivr.net/npm/docsify-pagination/dist/docsify-pagination.min.js"></script>

<!-- Zoom images -->
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/zoom-image.min.js"></script>
```

### Custom Domain

To use a custom domain:

1. Create a `CNAME` file in `docs/` with your domain
2. Configure DNS at your domain registrar
3. Update repository settings

## Resources

- [Docsify Documentation](https://docsify.js.org/)
- [Docsify Themes](https://docsify.js.org/#/themes)
- [Docsify Plugins](https://docsify.js.org/#/plugins)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

## Support

For questions or issues:
- Check [CONTRIBUTING.md](CONTRIBUTING.md)
- Review [README.md](README.md)
- Open an issue on GitHub
