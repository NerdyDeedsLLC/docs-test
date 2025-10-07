# Product B - Web v1.0.0

Welcome to the documentation for Product B version 1.0.0 Web Edition.

## Overview

Product B Web Edition brings the power of Product B to your browser, providing a modern web-based interface for system management and automation.

## Features

- **Dashboard**: Real-time monitoring and analytics
- **Task Management**: Create and manage automation tasks
- **API Integration**: RESTful API for programmatic access
- **Multi-tenancy**: Support for multiple organizations
- **Role-based Access**: Granular permission system

## Getting Started

### Access the Application

Navigate to your Product B Web instance:

```
https://your-domain.com/product-b
```

### First Login

Default credentials (change immediately):
- **Username**: admin
- **Password**: changeme

## Dashboard

The dashboard provides an overview of your system:

- **System Health**: CPU, Memory, Disk usage
- **Active Tasks**: Currently running automation tasks
- **Recent Events**: System events and notifications
- **Quick Actions**: Common operations

## Task Management

### Creating Tasks

1. Click **Tasks** in the navigation menu
2. Click **Create New Task**
3. Fill in task details:
   - Name
   - Description
   - Schedule (cron format)
   - Script/command
4. Click **Save**

### Task Types

- **Scheduled**: Run on a schedule
- **Triggered**: Run based on events
- **Manual**: Run on-demand

### Example Task

Create a backup task:

```yaml
name: Daily Backup
schedule: "0 2 * * *"
script: |
  #!/bin/bash
  tar -czf /backup/$(date +%Y%m%d).tar.gz /data
  find /backup -mtime +7 -delete
notifications:
  email: admin@example.com
```

## API Usage

### Authentication

Get an API token:

```bash
curl -X POST https://your-domain.com/product-b/api/auth/token \
  -H "Content-Type: application/json" \
  -d '{"username": "admin", "password": "your-password"}'
```

### List Tasks

```bash
curl https://your-domain.com/product-b/api/tasks \
  -H "Authorization: Bearer YOUR_TOKEN"
```

### Create Task

```bash
curl -X POST https://your-domain.com/product-b/api/tasks \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "My Task",
    "schedule": "0 * * * *",
    "script": "echo Hello"
  }'
```

### Execute Task

```bash
curl -X POST https://your-domain.com/product-b/api/tasks/123/run \
  -H "Authorization: Bearer YOUR_TOKEN"
```

## User Management

### Adding Users

1. Navigate to **Settings** > **Users**
2. Click **Add User**
3. Enter user details:
   - Username
   - Email
   - Role (Admin, User, Viewer)
4. Click **Create**

### Roles and Permissions

| Role | Permissions |
|------|-------------|
| Admin | Full access to all features |
| User | Create and manage own tasks |
| Viewer | Read-only access |

## Integration

### Webhooks

Configure webhooks for task events:

1. Go to **Settings** > **Webhooks**
2. Add webhook URL
3. Select events to trigger
4. Save configuration

Example webhook payload:

```json
{
  "event": "task.completed",
  "task": {
    "id": 123,
    "name": "Daily Backup",
    "status": "success"
  },
  "timestamp": "2025-01-15T02:00:00Z"
}
```

### External Services

Connect to external services:

- **Slack**: Task notifications
- **PagerDuty**: Alert integration
- **Datadog**: Metrics export
- **GitHub**: Repository integration

## Configuration

### System Settings

Access at **Settings** > **System**:

- **Base URL**: Application base URL
- **Session Timeout**: User session duration
- **Max Tasks**: Concurrent task limit
- **Logging Level**: Debug, Info, Warning, Error

### Email Configuration

Configure SMTP for notifications:

```yaml
email:
  host: smtp.example.com
  port: 587
  username: noreply@example.com
  password: your-password
  from: Product B <noreply@example.com>
  tls: true
```

## Security

### HTTPS

Always use HTTPS in production:

```nginx
server {
    listen 443 ssl http2;
    server_name your-domain.com;
    
    ssl_certificate /path/to/cert.pem;
    ssl_certificate_key /path/to/key.pem;
    
    location /product-b {
        proxy_pass http://localhost:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

### API Security

- Always use HTTPS
- Rotate API tokens regularly
- Use API key restrictions
- Enable rate limiting

## Troubleshooting

### Can't log in

- Verify credentials
- Check browser console for errors
- Clear browser cache and cookies
- Verify backend service is running

### Tasks not running

- Check task schedule format
- Verify task script syntax
- Review task logs
- Check system resources

### API errors

- Verify API token is valid
- Check request format
- Review API documentation
- Check rate limits

## Browser Support

Product B Web supports:

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

## Next Steps

- [API Reference](api-reference.md)
- [User Guide](user-guide.md)
- [Admin Guide](admin-guide.md)

## Support

For support:
- [Documentation](README.md)
- [GitHub Issues](https://github.com/NerdyDeedsLLC/docs-test/issues)
- Email: support@example.com
