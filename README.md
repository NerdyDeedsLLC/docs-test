# docs-test

A multi-version, multi-product, multi-platform documentation site built with [Docsify](https://docsify.js.org/) and hosted on GitHub Pages.

## 📚 Documentation Structure

This repository hosts documentation organized by:

```
/docs/
├── <platform>/          # Platform (windows, linux, macos, web)
│   ├── <product>/       # Product (product-a, product-b)
│   │   ├── <version>/   # Version (1.0.0, 1.1.0, 2.0.0)
│   │   │   ├── README.md
│   │   │   └── ... (other documentation files)
```

## 🌟 Features

- **Multi-Version Support**: Documentation for multiple semantic versions (X.Y.Z)
- **Multi-Product**: Separate docs for different products
- **Multi-Platform**: Platform-specific documentation (Windows, Linux, macOS, Web)
- **Search**: Full-text search across all documentation
- **Sidebar Navigation**: Easy navigation through the documentation structure
- **GitHub Pages**: Automatically deployed via GitHub Actions

## 🚀 View Documentation

Once deployed, the documentation will be available at:
```
https://nerdydeedsllc.github.io/docs-test/
```

## 📖 Supported Products

### Product A
A comprehensive solution for productivity and automation.

**Platforms**: Windows, Linux, macOS, Web  
**Versions**: 1.0.0, 1.1.0, 2.0.0

### Product B
A specialized solution optimized for system administration.

**Platforms**: Windows, Linux, macOS, Web  
**Versions**: 1.0.0, 1.1.0, 2.0.0

## 🛠️ Adding New Documentation

### Adding a New Version

1. Create a new directory: `docs/<platform>/<product>/<version>/`
2. Add your markdown files (at minimum `README.md`)
3. Update `docs/_sidebar.md` to include the new version
4. Commit and push your changes

### Adding a New Product

1. Create directories for all platforms and versions
2. Add documentation files
3. Update `docs/_sidebar.md` to include the new product
4. Update `docs/README.md` with product information

### Adding a New Platform

1. Create directories for all products and versions
2. Add platform-specific documentation
3. Update `docs/_sidebar.md` to include the new platform

## 🔧 Local Development

To preview the documentation locally:

1. Install a local web server (e.g., `http-server`, `python -m http.server`)

   ```bash
   # Using Python
   cd docs
   python -m http.server 3000
   ```

   ```bash
   # Using Node.js http-server
   npm install -g http-server
   cd docs
   http-server -p 3000
   ```

2. Open your browser to `http://localhost:3000`

## 📝 Documentation Format

All documentation files are written in Markdown and support:

- GitHub Flavored Markdown
- Code syntax highlighting
- Tables
- Task lists
- Emoji

### Example Structure

Each version directory should contain:

```
<version>/
├── README.md           # Main documentation page
├── api-reference.md    # API documentation
├── tutorials.md        # Getting started guides
├── faq.md             # Frequently asked questions
└── ... (other files)
```

## 🚢 Deployment

Documentation is automatically deployed to GitHub Pages when changes are pushed to the `main` branch:

1. Commit your changes to `docs/`
2. Push to the `main` branch
3. GitHub Actions will automatically build and deploy

### GitHub Pages Setup

Ensure GitHub Pages is configured in your repository settings:

1. Go to **Settings** > **Pages**
2. Source should be set to **GitHub Actions**
3. The workflow will handle deployment automatically

## 🤝 Contributing

To contribute to the documentation:

1. Fork the repository
2. Create a feature branch
3. Add or update documentation
4. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔗 Links

- [Docsify Documentation](https://docsify.js.org/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)