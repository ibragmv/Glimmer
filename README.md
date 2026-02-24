# Multi-Tenant E-Commerce with Platform Fees

![7](https://github.com/user-attachments/assets/cc429a6b-ae9a-43d1-ac22-15a15cc4955a)

A modern e-commerce platform built with Next.js, Payload CMS, and Stripe, featuring multi-tenant architecture and platform fees capabilities.

## Features

- 🏬 Multi-tenant architecture
- 🌐 Vendor subdomains
- 🎨 Custom merchant storefronts
- 💳 Stripe Connect integration
- 💰 Automatic platform fees
- ⭐ Product ratings & reviews
- 📚 User purchase library
- 🧑‍💼 Role-based access control
- 🛠️ Admin dashboard
- 🧾 Merchant dashboard
- 🧱 Payload CMS backend
- 🗂️ Category & product filtering
- 🔍 Search functionality
- 🖼️ Image upload support
- ⚙️ Built with Next.js 15
- 🎨 TailwindCSS V4 styling
- 💅 ShadcnUI components

## Prerequisites

- Node.js 18+ or Bun 1.0+
- MongoDB Atlas account
- Stripe account
- Vercel account (for Blob storage)

## Getting Started

### Installation

#### Using Bun (Recommended)

```bash
# Clone the repository
git clone https://github.com/code-with-antonio/next15-multitenant-ecommerce.git
cd multitenant-ecommerce

# Install dependencies
bun install

# Copy environment variables
cp .env.example .env
```

#### Using npm

```bash
# Clone the repository
git clone https://github.com/code-with-antonio/next15-multitenant-ecommerce.git
cd multitenant-ecommerce

# Install dependencies
npm install

# Copy environment variables
cp .env.example .env
```

#### Using yarn

```bash
# Clone the repository
git clone https://github.com/code-with-antonio/next15-multitenant-ecommerce.git
cd multitenant-ecommerce

# Install dependencies
yarn install

# Copy environment variables
cp .env.example .env
```

### Environment Variables

Update the `.env` file with your configuration:

```env
# Database
DATABASE_URI=your_mongodb_uri
PAYLOAD_SECRET=your_payload_secret

# Global
NEXT_PUBLIC_APP_URL=http://localhost:3000
NEXT_PUBLIC_ROOT_DOMAIN=localhost:3000
NEXT_PUBLIC_ENABLE_SUBDOMAIN_ROUTING=false

# Stripe
STRIPE_SECRET_KEY=your_stripe_secret_key
STRIPE_WEBHOOK_SECRET=your_stripe_webhook_secret

# Vercel Blob
BLOB_READ_WRITE_TOKEN=your_vercel_blob_token
```

### Subdomain Routing Configuration

The platform supports wildcard subdomain routing, allowing each vendor to have their own unique subdomain (e.g., `vendorname.yourdomain.com`). This feature is controlled by the `NEXT_PUBLIC_ENABLE_SUBDOMAIN_ROUTING` environment variable.

#### Development
By default, subdomain routing is disabled in development (`NEXT_PUBLIC_ENABLE_SUBDOMAIN_ROUTING="false"`), and all stores are accessed through routes like:
```
http://localhost:3000/tenants/[tenant-slug]
```

#### Production
To enable subdomain routing in production:

1. Configure your DNS provider with a wildcard subdomain record:
   ```
   *.yourdomain.com  →  your-vercel-deployment.vercel.app
   ```

2. Update your environment variables:
   ```env
   NEXT_PUBLIC_ROOT_DOMAIN=yourdomain.com
   NEXT_PUBLIC_ENABLE_SUBDOMAIN_ROUTING="true"
   ```

Once enabled, stores will be accessible through their unique subdomains:
```
https://tenantslug.yourdomain.com
```

#### Notes
- Make sure your hosting provider (e.g., Vercel) supports wildcard subdomains
- Each subdomain will automatically serve the corresponding store's content
- SSL certificates should be configured to support wildcard subdomains
- The main marketplace will remain accessible at your root domain

### Database Setup

```bash
# Using Bun
bun run db:fresh
bun run db:seed

# Using npm
npm run db:fresh
npm run db:seed

# Using yarn
yarn db:fresh
yarn db:seed
```

### Development

```bash
# Using Bun
bun run dev

# Using npm
npm run dev

# Using yarn
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.


## Available Scripts

- `dev` - Start development server
- `build` - Build for production
- `start` - Start production server
- `lint` - Run ESLint
- `generate:types` - Generate Payload CMS types
- `db:fresh` - Reset and migrate database
- `db:seed` - Seed database with initial data
