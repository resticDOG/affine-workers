# AFFiNE Workers

This repository contains serverless functions used by AFFiNE and BlockSuite, deployed on Cloudflare Workers.

## Overview

AFFiNE Workers provides a collection of utility services that enhance the AFFiNE application functionality:

- **Image Proxy Service**: Secure image proxying with format optimization
- **Link Preview Service**: Web page metadata extraction and preview generation
- **Telemetry Service**: Analytics and usage tracking
- **Utils Package**: Shared utilities and helper functions

## Architecture

This is a monorepo managed with pnpm workspaces, containing multiple Cloudflare Worker services:

```
packages/
├── worker/           # Main worker service (router and orchestration)
├── image-proxy/      # Image proxying and optimization service
├── link-preview/     # Link preview and metadata extraction service
├── telemetry/        # Analytics and telemetry service
└── utils/            # Shared utilities and types
```

## Features

### Image Proxy Service
- Secure image fetching with origin validation
- Automatic image format optimization (WebP/AVIF)
- Size constraints and scaling
- CORS support for cross-origin requests

### Link Preview Service
- Web page metadata extraction (title, description, images)
- Automatic image proxying for preview images
- URL validation and sanitization
- CORS support for browser integration

### Telemetry Service
- Analytics data collection and forwarding
- Request validation and filtering
- Integration with Customer.io CDP

## Development

### Prerequisites
- Node.js (version specified in `.nvmrc`)
- pnpm package manager
- Cloudflare account for deployment

### Setup

1. Install dependencies:
```bash
pnpm install
```

2. Run development server:
```bash
pnpm dev
```

3. Run tests:
```bash
pnpm test
```

### Deployment

Deploy all workers:
```bash
pnpm deploy
```

Or deploy specific services individually from their respective directories.

## API Endpoints

### Main Worker (`affine-worker.linkzz.workers.dev`)

#### Image Proxy
- `GET /api/worker/image-proxy?url=<image_url>`
- Proxies and optimizes images with automatic format conversion

#### Link Preview
- `POST /api/worker/link-preview`
- `OPTIONS /api/worker/link-preview`
- Extracts metadata from web pages for preview generation

### Telemetry Worker
- Handles analytics and usage tracking
- Validates and forwards telemetry data

## Configuration

Each worker has its own `wrangler.toml` configuration file for:
- Environment variables
- KV namespaces
- D1 databases
- Routing rules

## Security

- Origin validation for CORS requests
- URL sanitization and validation
- Request rate limiting
- Secure header handling

## License

MPL-2.0 License - See LICENSE file for details.

## Contributing

This is a private repository. For contributions or issues, please contact the maintainers.
