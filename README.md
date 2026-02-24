# Glimmer | Multi-Tenant E-Commerce Platform

Glimmer is a modern, high-performance e-commerce platform built with Next.js 15, Payload CMS, and Stripe. It features a robust multi-tenant architecture with support for vendor subdomains and automatic platform fees.

## Features

- 🏬 **Multi-tenant architecture**: Host multiple independent stores on a single instance.
- 🌐 **Vendor subdomains**: Support for custom subdomains (e.g., `store.glimmer.com`).
- 🎨 **Custom merchant storefronts**: Unique branding for every vendor.
- 💳 **Stripe Connect integration**: Seamless onboarding for sellers.
- 💰 **Automatic platform fees**: Monetize your platform by taking a cut of every sale.
- ⭐ **Product ratings & reviews**: Built-in social proof system.
- 📚 **User purchase library**: Digital products and order history management.
- 🧑‍💼 **Role-based access control**: Admin, Merchant, and Customer roles.
- 🛠️ **Admin dashboard**: Global platform management.
- 🧾 **Merchant dashboard**: Specialized tools for vendors to manage products and sales.
- 🧱 **Payload CMS backend**: Type-safe, headless content management.
- 🔍 **Search & Filtering**: Advanced category and product discovery.
- 🖼️ **Image upload support**: Integrated media management.
- ⚙️ **Modern Stack**: Built with Next.js 15 and TailwindCSS V4.
- 💅 **ShadcnUI components**: Beautifully designed, accessible UI components.

## Prerequisites

- Node.js 18+ or Bun 1.0+
- MongoDB Atlas account (or local MongoDB)
- Stripe account
- Vercel account (for Blob storage)

## Getting Started

### Installation

#### Using Bun (Recommended)

```bash
# Clone the repository
git clone https://github.com/ibragmv/Glimmer.git
cd Glimmer

# Install dependencies
bun install

# Copy environment variables
cp .env.example .env
```

#### Using npm

```bash
# Clone the repository
git clone https://github.com/ibragmv/Glimmer.git
cd Glimmer

# Install dependencies
npm install

# Copy environment variables
cp .env.example .env
```

#### Using yarn

```bash
# Clone the repository
git clone https://github.com/ibragmv/Glimmer.git
cd Glimmer

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

Glimmer supports wildcard subdomain routing, allowing each vendor to have their own unique subdomain.

#### Development
By default, subdomain routing is disabled in development (`NEXT_PUBLIC_ENABLE_SUBDOMAIN_ROUTING="false"`). Stores are accessed via:
```
http://localhost:3000/tenants/[tenant-slug]
```

#### Production
To enable subdomain routing in production:

1. Configure your DNS provider with a wildcard record:
   ```
   *.yourdomain.com  →  your-vercel-deployment.vercel.app
   ```

2. Update environment variables:
   ```env
   NEXT_PUBLIC_ROOT_DOMAIN=yourdomain.com
   NEXT_PUBLIC_ENABLE_SUBDOMAIN_ROUTING="true"
   ```

Once enabled, stores will be accessible at:
```
https://tenantslug.yourdomain.com
```

### Database Setup

```bash
# Reset and seed the database (Careful: this deletes existing data)
bun run db:fresh
bun run db:seed
```

### Development

```bash
bun run dev
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

## License

This project is licensed under the MIT License.
