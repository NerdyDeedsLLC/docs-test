# Contributing to Documentation

Thank you for your interest in contributing to our documentation! This guide will help you understand how to add and maintain documentation.

## Documentation Structure

Our documentation follows this structure:

```
docs/
├── <platform>/       # Platform: windows, linux, macos, web
│   ├── <product>/    # Product: product-a, product-b, etc.
│   │   ├── <version>/ # Semantic version: X.Y.Z (e.g., 1.0.0)
│   │   │   ├── README.md
│   │   │   └── ... (additional documentation files)
```

## Adding New Documentation

### 1. Adding a New Version

When releasing a new version of a product:

```bash
# Create the directory structure
mkdir -p docs/<platform>/<product>/<new-version>

# Copy template or previous version as starting point
cp docs/<platform>/<product>/<old-version>/README.md docs/<platform>/<product>/<new-version>/README.md

# Edit the documentation for the new version
# Update version numbers and new features
```

Update the sidebar navigation in `docs/_sidebar.md`:

```markdown
* **Product Name**
  * Platform
    * [v1.0.0](/platform/product/1.0.0/)
    * [v2.0.0](/platform/product/2.0.0/)
    * [v3.0.0](/platform/product/3.0.0/)  <!-- Add this -->
```

### 2. Adding a New Product

When adding documentation for a new product:

```bash
# Create directories for all platforms and versions
mkdir -p docs/{windows,linux,macos,web}/new-product/1.0.0

# Add README.md to each version directory
touch docs/windows/new-product/1.0.0/README.md
# ... repeat for each platform
```

Update the sidebar in `docs/_sidebar.md`:

```markdown
* **New Product**  <!-- Add this section -->
  * Windows
    * [v1.0.0](/windows/new-product/1.0.0/)
  * Linux
    * [v1.0.0](/linux/new-product/1.0.0/)
  * macOS
    * [v1.0.0](/macos/new-product/1.0.0/)
  * Web
    * [v1.0.0](/web/new-product/1.0.0/)
```

Update the main docs homepage in `docs/README.md` to include the new product.

### 3. Adding a New Platform

When adding support for a new platform:

```bash
# Create directories for all products and versions
mkdir -p docs/new-platform/{product-a,product-b}/{1.0.0,1.1.0,2.0.0}

# Add documentation for each product/version
touch docs/new-platform/product-a/1.0.0/README.md
# ... repeat for each product and version
```

Update the sidebar and main README accordingly.

## Documentation Guidelines

### File Naming

- Use lowercase with hyphens: `api-reference.md`, `getting-started.md`
- Main page should always be `README.md`
- Keep names descriptive and concise

### Writing Style

1. **Be Clear and Concise**: Use simple language and short sentences
2. **Use Examples**: Include code examples and command-line snippets
3. **Structure Content**: Use headings, lists, and tables to organize information
4. **Link Related Content**: Cross-reference related documentation pages

### Markdown Format

Use GitHub Flavored Markdown:

```markdown
# Heading 1
## Heading 2
### Heading 3

**Bold text**
*Italic text*
`inline code`

- Bullet list
- Item 2

1. Numbered list
2. Item 2

[Link text](url)

| Column 1 | Column 2 |
|----------|----------|
| Data 1   | Data 2   |
```

### Code Blocks

Always specify the language for syntax highlighting:

````markdown
```bash
echo "Hello, World!"
```

```javascript
console.log("Hello, World!");
```

```python
print("Hello, World!")
```
````

### Common Documentation Sections

A typical README.md should include:

1. **Title and Overview**: What is this product/version?
2. **Installation**: How to install
3. **Getting Started**: Quick start guide
4. **Features**: Key features and capabilities
5. **Configuration**: Configuration options
6. **Troubleshooting**: Common issues and solutions
7. **Next Steps**: Links to related documentation
8. **Support**: How to get help

## Testing Locally

Before submitting changes, test locally:

```bash
# Option 1: Python
cd docs
python -m http.server 3000

# Option 2: Node.js
npm install -g http-server
cd docs
http-server -p 3000
```

Open `http://localhost:3000` in your browser and verify:

- [ ] All links work correctly
- [ ] Navigation works properly
- [ ] Search finds your content
- [ ] Code blocks are formatted correctly
- [ ] Images load (if any)

## Submitting Changes

### Process

1. **Fork** the repository
2. **Create a branch**: `git checkout -b docs/add-product-x-v2`
3. **Make changes**: Add or update documentation
4. **Test locally**: Verify everything works
5. **Commit**: Use clear commit messages
6. **Push**: Push to your fork
7. **Pull Request**: Open a PR with description of changes

### Commit Messages

Use clear, descriptive commit messages:

```
Add Product X v2.0.0 documentation for Windows
Update Product A v1.1.0 API reference
Fix broken links in Product B Linux docs
```

### Pull Request Template

When opening a PR, include:

- **Summary**: What documentation was added/changed
- **Product/Version**: Which product and version affected
- **Platform**: Which platform(s) affected
- **Testing**: How you tested the changes

## Documentation Checklist

Before submitting, verify:

- [ ] README.md exists in the version directory
- [ ] All links work correctly (no 404s)
- [ ] Code examples are correct and tested
- [ ] Sidebar updated (if adding new content)
- [ ] Main docs homepage updated (if adding product)
- [ ] Spelling and grammar checked
- [ ] Tested locally
- [ ] Follows existing documentation style

## Version Management

### Semantic Versioning

We use semantic versioning (X.Y.Z):

- **Major (X)**: Breaking changes, incompatible API changes
- **Minor (Y)**: New features, backwards-compatible
- **Patch (Z)**: Bug fixes, backwards-compatible

### Documentation Versions

- Create documentation for each **minor** and **major** version
- Patch versions typically use the same docs as their minor version
- Example: v1.0.0, v1.0.1, v1.0.2 all use `/docs/platform/product/1.0.0/`

### Deprecation

When deprecating a version:

1. Add a deprecation notice to the top of README.md
2. Keep the documentation available
3. Link to the migration guide for newer versions

Example notice:

```markdown
> ⚠️ **Deprecation Notice**: This version is deprecated. Please upgrade to [v2.0.0](/platform/product/2.0.0/).
```

## Need Help?

If you have questions:

- Review existing documentation for examples
- Check [Docsify documentation](https://docsify.js.org/)
- Open an issue for discussion
- Ask in pull request comments

## Code of Conduct

Please be respectful and constructive in all contributions and communications.

Thank you for contributing to our documentation! 🎉
