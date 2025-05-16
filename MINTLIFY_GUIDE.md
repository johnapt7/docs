# Mintlify Documentation Platform - Complete Guide

## Overview

Mintlify is a modern documentation platform that allows you to create beautiful, interactive documentation sites. It's AI-native, optimized for user engagement, and built specifically for developers.

## Key Features

- **Modern Design**: Beautiful out-of-the-box with customizable themes
- **Developer-Friendly**: Uses MDX (Markdown + React) for content
- **AI-Native**: Built-in search and AI capabilities
- **Interactive Components**: Rich library of UI components
- **API Documentation**: First-class support for OpenAPI and manual API docs

## Getting Started

### Prerequisites
- Node.js version 19 or higher
- Git for version control
- A Mintlify account (create at mintlify.com)

### Installation

```bash
# Install Mintlify CLI globally
npm i -g mintlify

# Or with yarn
yarn global add mintlify
```

### Project Setup

1. **Clone your docs repository** (created during onboarding)
2. **Navigate to the docs folder** containing `docs.json`
3. **Start local development**:
   ```bash
   mintlify dev
   ```
4. **View at** `http://localhost:3000`

### Custom Port
```bash
mintlify dev --port 3333
```

## Configuration (docs.json)

The `docs.json` file is the heart of your Mintlify documentation configuration.

### Basic Configuration

```json
{
  "$schema": "https://mintlify.com/docs.json",
  "theme": "mint",
  "name": "Your Project Name",
  "favicon": "/favicon.svg",
  "colors": {
    "primary": "#16A34A",    // Main brand color
    "light": "#07C983",      // Light mode accent
    "dark": "#15803D"        // Dark mode accent
  },
  "logo": {
    "light": "/logo/light.svg",
    "dark": "/logo/dark.svg",
    "href": "https://yoursite.com"
  }
}
```

### Navigation Structure

```json
{
  "navigation": {
    "tabs": [
      {
        "tab": "Documentation",
        "groups": [
          {
            "group": "Getting Started",
            "pages": ["index", "quickstart", "installation"]
          },
          {
            "group": "Advanced Features",
            "pages": [
              "features/authentication",
              "features/api-integration"
            ]
          }
        ]
      },
      {
        "tab": "API Reference",
        "groups": [
          {
            "group": "Endpoints",
            "pages": ["api/overview", "api/users", "api/products"]
          }
        ]
      }
    ],
    "global": {
      "anchors": [
        {
          "anchor": "GitHub",
          "href": "https://github.com/yourcompany",
          "icon": "github"
        }
      ]
    }
  }
}
```

### API Configuration

```json
{
  "api": {
    "baseUrl": "https://api.yourcompany.com",
    "auth": {
      "method": "bearer",
      "name": "Authorization"
    },
    "playground": {
      "mode": "show"
    }
  },
  "openapi": "/api-reference/openapi.json"
}
```

## MDX Components

Mintlify provides a rich library of components for creating interactive documentation.

### Content Components

#### Card
```mdx
<Card title="Quick Start" icon="rocket" href="/quickstart">
  Get up and running in 5 minutes
</Card>
```

#### Card Group
```mdx
<CardGroup cols={2}>
  <Card title="Installation" icon="download" href="/install">
    Step-by-step installation guide
  </Card>
  <Card title="Configuration" icon="gear" href="/config">
    Configure your documentation
  </Card>
</CardGroup>
```

#### Accordion
```mdx
<Accordion title="Can I use custom domains?">
  Yes! You can configure custom domains in your Mintlify dashboard.
</Accordion>
```

#### Accordion Group
```mdx
<AccordionGroup>
  <Accordion title="What is Mintlify?">
    Mintlify is a documentation platform...
  </Accordion>
  <Accordion title="How much does it cost?">
    Check our pricing page for details...
  </Accordion>
</AccordionGroup>
```

#### Tabs
```mdx
<Tabs>
  <Tab title="npm">
    ```bash
    npm install my-package
    ```
  </Tab>
  <Tab title="yarn">
    ```bash
    yarn add my-package
    ```
  </Tab>
  <Tab title="pnpm">
    ```bash
    pnpm add my-package
    ```
  </Tab>
</Tabs>
```

#### Code Groups
```mdx
<CodeGroup>
  ```javascript example.js
  console.log("Hello World");
  ```
  
  ```python example.py
  print("Hello World")
  ```
  
  ```ruby example.rb
  puts "Hello World"
  ```
</CodeGroup>
```

#### Callout Boxes
```mdx
<Note>
  This is an informational note
</Note>

<Tip>
  Pro tip: Use keyboard shortcuts for faster navigation
</Tip>

<Warning>
  Be careful when modifying this configuration
</Warning>

<Info>
  Additional information about this feature
</Info>

<Check>
  Successfully completed this step!
</Check>
```

### API Documentation Components

#### Response Field
```mdx
<ResponseField name="userId" type="string" required>
  Unique identifier for the user
</ResponseField>
```

#### Expandable
```mdx
<Expandable title="Advanced Options">
  Additional configuration options...
</Expandable>
```

## MDX Page Structure

Every MDX page should have frontmatter metadata:

```mdx
---
title: 'Page Title'
description: 'Brief description of the page content'
icon: 'book'
---

# Main Content

Your documentation content goes here...
```

### API Endpoint Pages

```mdx
---
title: 'Create User'
api: 'POST /users'
---

Create a new user in the system.
```

Or for OpenAPI:

```mdx
---
title: 'Get Users'
openapi: 'GET /users'
---
```

## Development Workflow

### Commands

- `mintlify dev` - Start local development server
- `mintlify broken-links` - Check for broken links
- `mintlify upgrade` - Upgrade from mint.json to docs.json
- `mintlify build` - Build for production

### File Organization

```
docs/
├── docs.json           # Main configuration
├── index.mdx          # Homepage
├── quickstart.mdx     # Quick start guide
├── api-reference/     # API documentation
│   ├── introduction.mdx
│   └── endpoints/
│       ├── users.mdx
│       └── products.mdx
├── guides/            # User guides
│   ├── installation.mdx
│   └── advanced/
│       └── authentication.mdx
├── images/           # Image assets
└── logo/            # Logo files
    ├── light.svg
    └── dark.svg
```

## Deployment

### GitHub Integration

1. Install the Mintlify GitHub app
2. Push changes to your main branch
3. Automatic deployment occurs
4. Check deployment status in Mintlify dashboard

### Manual Deployment

Available through the Mintlify dashboard for immediate updates.

## Best Practices

### Content Guidelines

1. **Use clear, descriptive titles**
2. **Include code examples** where relevant
3. **Break content into sections** with headers
4. **Use components** to enhance readability
5. **Add navigation breadcrumbs** for complex docs

### Configuration Tips

1. **Organize navigation logically**
2. **Use consistent naming conventions**
3. **Group related pages together**
4. **Provide search-friendly descriptions**
5. **Test locally before deploying**

### Performance Optimization

1. **Optimize images** before uploading
2. **Use lazy loading** for heavy content
3. **Keep pages focused** on single topics
4. **Implement proper caching**

## Troubleshooting

### Common Issues

1. **Sharp module error**
   - Solution: Update to Node.js v19+
   - Reinstall Mintlify after updating Node

2. **Port already in use**
   - Solution: Use `--port` flag with different port
   - Or kill process using port 3000

3. **Unknown errors**
   - Solution: Delete `~/.mintlify` folder
   - Run `mintlify dev` again

4. **Version mismatch**
   - Solution: Update CLI with `npm i -g mintlify@latest`

### Getting Help

- Documentation: https://mintlify.com/docs
- Community: https://mintlify.com/community
- Support: hi@mintlify.com
- GitHub Issues: Report bugs on GitHub

## Advanced Features

### Custom Components

You can create custom React components and use them in MDX:

```jsx
// components/MyComponent.jsx
export const MyComponent = ({ title }) => {
  return <div className="custom-component">{title}</div>;
};
```

### Analytics Integration

Add analytics tracking to understand user behavior:

```json
{
  "analytics": {
    "ga4": {
      "trackingId": "G-XXXXXXXXXX"
    }
  }
}
```

### SEO Optimization

Configure SEO settings for better search visibility:

```json
{
  "metadata": {
    "og:title": "Your Documentation",
    "og:description": "Comprehensive guides and API reference",
    "twitter:card": "summary_large_image"
  }
}
```

This guide covers all essential aspects of using Mintlify for documentation. Remember to check the official documentation for the most up-to-date information and new features.