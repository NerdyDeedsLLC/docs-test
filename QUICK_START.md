# Quick Start Guide

Get up and running with the documentation site in 5 minutes.

## 🚀 View the Documentation

After merging this PR to main, your documentation will be available at:

```
https://nerdydeedsllc.github.io/docs-test/
```

## 📝 Add Your First Documentation

### Step 1: Choose Your Target

Decide which platform, product, and version you're documenting:
- Platform: `windows`, `linux`, `macos`, or `web`
- Product: `product-a`, `product-b`, or your own
- Version: Use semantic versioning like `1.0.0`

### Step 2: Create the Directory

```bash
mkdir -p docs/<platform>/<product>/<version>
```

**Example:**
```bash
mkdir -p docs/windows/my-product/1.0.0
```

### Step 3: Write Documentation

Create a `README.md` file in your version directory:

```bash
cat > docs/windows/my-product/1.0.0/README.md << 'EOF'
# My Product - Windows v1.0.0

## Overview
Brief description of your product.

## Installation
How to install your product.

## Getting Started
Quick start guide.

## Features
Key features and capabilities.
EOF
```

### Step 4: Update the Sidebar

Edit `docs/_sidebar.md` and add your product:

```markdown
* **My Product**
  * Windows
    * [v1.0.0](/windows/my-product/1.0.0/)
```

### Step 5: Commit and Push

```bash
git add docs/
git commit -m "Add My Product v1.0.0 documentation for Windows"
git push
```

That's it! Your documentation will automatically deploy to GitHub Pages.

## 🔍 Test Locally

Before pushing, test your documentation locally:

```bash
cd docs
python3 -m http.server 3000
```

Open http://localhost:3000 in your browser.

## 📚 Common Tasks

### Add a New Version

```bash
# Copy previous version as template
cp -r docs/windows/product-a/1.0.0 docs/windows/product-a/2.0.0

# Edit the new version
vim docs/windows/product-a/2.0.0/README.md

# Update sidebar
vim docs/_sidebar.md
```

### Add Documentation to Existing Version

```bash
# Create new markdown file
echo "# API Reference" > docs/windows/product-a/1.0.0/api-reference.md

# Link from README.md
echo "- [API Reference](api-reference.md)" >> docs/windows/product-a/1.0.0/README.md
```

### Copy Documentation Across Platforms

```bash
# If docs are similar across platforms, copy and customize
cp -r docs/windows/product-a/1.0.0 docs/linux/product-a/1.0.0

# Then customize platform-specific sections
vim docs/linux/product-a/1.0.0/README.md
```

## 🎨 Customize Appearance

### Change Theme

Edit `docs/index.html` and change the CSS link:

```html
<!-- Options: vue.css, buble.css, dark.css, pure.css -->
<link rel="stylesheet" href="//cdn.jsdelivr.net/npm/docsify@4/lib/themes/vue.css">
```

### Change Site Name

Edit `docs/index.html`:

```javascript
window.$docsify = {
  name: 'Your Site Name',  // Change this
  repo: 'your-github-url', // Change this
  // ... rest of config
}
```

## 🆘 Troubleshooting

### My page isn't showing up

1. ✅ Check that `README.md` exists in the directory
2. ✅ Verify the path in `_sidebar.md` matches exactly
3. ✅ Make sure changes are committed and pushed
4. ✅ Check GitHub Actions completed successfully

### Search isn't working

1. ✅ Wait 1-2 minutes after deployment
2. ✅ Clear browser cache (Ctrl+F5 or Cmd+Shift+R)
3. ✅ Check browser console for errors

### GitHub Pages isn't deploying

1. ✅ Go to Settings → Pages
2. ✅ Ensure "Source" is set to "GitHub Actions"
3. ✅ Check the Actions tab for errors
4. ✅ Verify changes are in the `main` branch

## 📖 Next Steps

- Read [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines
- Review [SETUP.md](SETUP.md) for technical details
- Check [README.md](README.md) for complete documentation
- Browse sample documentation in `docs/windows/product-a/`

## 💡 Tips

1. **Use templates**: Copy existing documentation as a starting point
2. **Test locally**: Always preview before pushing
3. **Link related pages**: Use relative links like `[API](api-reference.md)`
4. **Keep it simple**: Focus on clarity over complexity
5. **Update regularly**: Keep documentation in sync with releases

## 🔗 Useful Links

- [Markdown Guide](https://www.markdownguide.org/)
- [Docsify Documentation](https://docsify.js.org/)
- [GitHub Flavored Markdown](https://github.github.com/gfm/)

---

**Need help?** Open an issue on GitHub!
