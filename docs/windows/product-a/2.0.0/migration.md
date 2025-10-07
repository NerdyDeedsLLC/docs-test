# Migration Guide: v1.x to v2.0.0

This guide helps you migrate from Product A v1.x to v2.0.0.

## Overview

Product A v2.0.0 includes breaking changes that require updates to your configuration and code.

## Before You Begin

1. **Backup your data**: Always backup before upgrading
2. **Review changes**: Read this entire guide first
3. **Test in staging**: Test the migration in a non-production environment

## Configuration Migration

### File Format Change

Configuration has moved from JSON to YAML.

**v1.x (config.json):**
```json
{
  "version": "1.0.0",
  "settings": {
    "autoUpdate": true,
    "telemetry": false
  }
}
```

**v2.0.0 (config.yaml):**
```yaml
version: "2.0.0"
settings:
  autoUpdate: true
  telemetry: false
```

### Automated Migration

Use the built-in migration tool:

```bash
product-a migrate --from 1.x --config "C:\Users\<username>\AppData\Roaming\ProductA\config.json"
```

This will:
1. Read your v1.x configuration
2. Convert it to v2.0.0 format
3. Create a backup of the old config
4. Generate the new config.yaml

## API Changes

### Renamed Methods

| v1.x Method | v2.0.0 Method |
|-------------|---------------|
| `productA.initialize()` | `productA.init()` |
| `productA.execute()` | `productA.run()` |
| `productA.getVersion()` | `productA.version()` |

### Updated Signatures

#### initialize → init

**v1.x:**
```javascript
productA.initialize(config)
```

**v2.0.0:**
```javascript
productA.init({
  config: config,
  plugins: []
})
```

#### execute → run

**v1.x:**
```javascript
productA.execute(command, options)
```

**v2.0.0:**
```javascript
productA.run({
  command: command,
  options: options,
  async: true
})
```

## CLI Changes

### Updated Commands

| v1.x Command | v2.0.0 Command |
|--------------|----------------|
| `product-a create` | `product-a init` |
| `product-a workflow run` | `product-a run` |

### New Commands

- `product-a plugin` - Manage plugins
- `product-a cloud` - Cloud integration
- `product-a migrate` - Migration tool

## Deprecated Features

The following features have been removed in v2.0.0:

1. **Legacy sync mode**: Use the new async mode
2. **XML configuration**: Use YAML instead
3. **Old event system**: Replaced with new event emitter

## Step-by-Step Migration

### Step 1: Install v2.0.0

Install alongside v1.x for testing:

```bash
# Download v2.0.0 installer
ProductA-2.0.0-Setup.exe

# Choose custom installation path
C:\Program Files\ProductA-2.0.0\
```

### Step 2: Migrate Configuration

```bash
cd "C:\Program Files\ProductA-2.0.0\"
product-a migrate --from 1.x
```

### Step 3: Update Your Code

Update your scripts and applications to use the new API:

```javascript
// Old v1.x code
const productA = require('product-a');
await productA.initialize(config);
const result = await productA.execute('process', options);

// New v2.0.0 code
const productA = require('product-a');
await productA.init({ config });
const result = await productA.run({ command: 'process', options });
```

### Step 4: Test

Test your application with v2.0.0:

```bash
# Run in test mode
product-a run --dry-run

# Check logs
product-a logs --level debug
```

### Step 5: Deploy

Once testing is successful, deploy to production:

1. Uninstall v1.x (if not needed)
2. Use v2.0.0 as primary version
3. Update documentation and scripts

## Rollback

If you need to rollback to v1.x:

1. Keep v1.x installation available
2. Restore backed-up v1.x configuration
3. Switch PATH to point to v1.x

## Common Issues

### Configuration not migrating

**Issue**: Migration tool fails
- **Solution**: Manually convert configuration using the examples above

### Plugins not compatible

**Issue**: v1.x plugins don't work
- **Solution**: Check plugin documentation for v2.0.0 versions

### Performance degradation

**Issue**: v2.0.0 slower than v1.x
- **Solution**: Enable performance optimization in config.yaml

## Getting Help

If you encounter issues during migration:

1. Check the [FAQ](faq.md)
2. Review [What's New](whats-new.md)
3. [Open an issue](https://github.com/NerdyDeedsLLC/docs-test/issues)

## Next Steps

- Read [What's New](whats-new.md) for new features
- Explore the updated [API Reference](api-reference.md)
- Check out new [Tutorials](tutorials.md)
