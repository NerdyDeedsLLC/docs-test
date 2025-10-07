# Product B - Linux v1.0.0

Welcome to the documentation for Product B version 1.0.0 on Linux.

## Overview

Product B is a specialized solution optimized for Linux environments, providing powerful tools for system administration and automation.

## Installation

### Ubuntu/Debian

```bash
# Add repository
curl -fsSL https://example.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/productb.gpg
echo "deb [signed-by=/usr/share/keyrings/productb.gpg] https://example.com/apt stable main" | sudo tee /etc/apt/sources.list.d/productb.list

# Install
sudo apt update
sudo apt install product-b
```

### RHEL/CentOS/Fedora

```bash
# Add repository
sudo dnf config-manager --add-repo https://example.com/rpm/productb.repo

# Install
sudo dnf install product-b
```

### From Source

```bash
# Clone repository
git clone https://github.com/example/product-b.git
cd product-b

# Build
./configure
make
sudo make install
```

## Getting Started

After installation, verify the installation:

```bash
product-b --version
# Output: Product B 1.0.0
```

### Quick Start

Initialize Product B:

```bash
# Initialize with default configuration
product-b init

# Start the service
sudo systemctl start product-b
sudo systemctl enable product-b
```

## Features

### System Monitoring

Monitor system resources in real-time:

```bash
product-b monitor --metrics cpu,memory,disk
```

### Automation

Create automated tasks:

```bash
# Create a task
product-b task create backup --schedule "0 2 * * *"

# List tasks
product-b task list

# Run task manually
product-b task run backup
```

### Integration

Integrate with existing Linux tools:

```bash
# Export to Prometheus
product-b export prometheus --port 9090

# Send logs to syslog
product-b logs --output syslog
```

## Configuration

Configuration file location: `/etc/product-b/config.conf`

```ini
[general]
log_level = info
data_dir = /var/lib/product-b

[monitoring]
enabled = true
interval = 60

[automation]
enabled = true
max_concurrent = 5
```

### Environment Variables

- `PRODUCTB_HOME`: Installation directory
- `PRODUCTB_CONFIG`: Custom config file path
- `PRODUCTB_LOG_LEVEL`: Override log level

## Service Management

Product B runs as a systemd service:

```bash
# Start service
sudo systemctl start product-b

# Stop service
sudo systemctl stop product-b

# Restart service
sudo systemctl restart product-b

# Check status
sudo systemctl status product-b

# View logs
sudo journalctl -u product-b -f
```

## Security

### Permissions

Product B requires specific permissions:

```bash
# Create product-b user
sudo useradd -r -s /bin/false product-b

# Set ownership
sudo chown -R product-b:product-b /var/lib/product-b
sudo chown -R product-b:product-b /etc/product-b
```

### SELinux

If using SELinux:

```bash
# Install policy
sudo semodule -i product-b.pp

# Check context
ls -Z /usr/bin/product-b
```

## Troubleshooting

### Service won't start

Check the logs:

```bash
sudo journalctl -u product-b -n 50 --no-pager
```

Common issues:
- Permission problems: Check file ownership
- Port conflicts: Verify no other service uses the ports
- Configuration errors: Validate config.conf syntax

### High resource usage

```bash
# Check resource usage
product-b stats

# Reduce monitoring interval
sudo sed -i 's/interval = 60/interval = 300/' /etc/product-b/config.conf
sudo systemctl restart product-b
```

## Next Steps

- [CLI Reference](cli-reference.md)
- [Configuration Guide](configuration.md)
- [API Documentation](api.md)

## Support

For support, please visit:
- [GitHub Issues](https://github.com/NerdyDeedsLLC/docs-test/issues)
- [Community Forum](https://forum.example.com)
- Email: support@example.com
