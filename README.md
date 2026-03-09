# Acme Dashboard

A modern, full-stack Next.js dashboard application for managing invoices and customers with authentication, built with the latest Next.js 16 features.

## Features

- 🔐 **Authentication**: NextAuth.js integration with secure login
- 📊 **Dashboard**: Real-time metrics and charts showing revenue trends
- 💼 **Invoice Management**: Create, read, update, and delete invoices
- 👥 **Customer Management**: Manage customer information and details
- 🔍 **Search & Pagination**: Filter invoices with search and pagination support
- 📱 **Responsive Design**: Mobile-friendly UI with Tailwind CSS
- ⚡ **Fast Performance**: Built with Next.js 16 and Turbopack
- 🎨 **Modern UI**: Clean, professional interface with Heroicons

## Tech Stack

- **Framework**: [Next.js](https://nextjs.org/) 16.0.10
- **Language**: [TypeScript](https://www.typescriptlang.org/)
- **Database**: PostgreSQL
- **Authentication**: [NextAuth.js](https://next-auth.js.org/)
- **Styling**: [Tailwind CSS](https://tailwindcss.com/)
- **Icons**: [Heroicons](https://heroicons.com/)
- **Package Manager**: pnpm

## Prerequisites

Before you begin, ensure you have the following installed:
- Node.js 18+ and npm/pnpm
- PostgreSQL database running locally or remotely
- Git

## Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/JackSawyerWATX/nextjs-dashboard.git
   cd nextjs-dashboard
   ```

2. **Install dependencies**
   ```bash
   pnpm install
   ```

3. **Set up environment variables**
   Create a `.env.local` file in the root directory and add:
   ```
   POSTGRES_URL="postgresql://user:password@localhost:5432/acme_db"
   NEXTAUTH_SECRET="your-secret-key-here"
   NEXTAUTH_URL="http://localhost:3000"
   ```

4. **Set up the database**
   ```bash
   pnpm run seed
   ```
   This will populate your database with sample data.

## Running the Project

### Development Mode
Start the development server with hot-reload:
```bash
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Production Build
Build the project for production:
```bash
pnpm build
pnpm start
```

## Project Structure

```
app/
├── dashboard/           # Dashboard pages and layouts
│   ├── (overview)/     # Dashboard overview with charts
│   ├── customers/      # Customers management
│   └── invoices/       # Invoices management
├── login/              # Login page
├── ui/                 # Reusable UI components
│   ├── dashboard/      # Dashboard-specific components
│   └── invoices/       # Invoice form components
├── lib/                # Utility functions and data fetching
│   ├── actions.ts      # Server actions
│   ├── data.ts         # Database queries
│   └── utils.ts        # Helper utilities
└── layout.tsx          # Root layout
public/                 # Static files
```

## Key Pages

- **`/`**: Home page redirects to login or dashboard
- **`/login`**: User login page
- **`/dashboard`**: Main dashboard with overview metrics
- **`/dashboard/customers`**: View all customers
- **`/dashboard/invoices`**: View and manage invoices
- **`/dashboard/invoices/[id]/edit`**: Edit specific invoice
- **`/dashboard/invoices/create`**: Create new invoice

## Database Schema

### Invoices Table
- `id`: UUID primary key
- `customer_id`: Foreign key to customers
- `amount`: Invoice amount in cents
- `status`: 'pending' or 'paid'
- `date`: Invoice date

### Customers Table
- `id`: UUID primary key
- `name`: Customer name
- `email`: Customer email
- `image_url`: Customer avatar URL

### Revenue Table
- `month`: Month string
- `revenue`: Revenue amount

## Authentication

The application uses NextAuth.js with middleware protection. Users must log in to access the dashboard.

Default credentials (after seed):
- Email: `user@example.com`
- Password: `password` (update in your database)

## Development

### File Updates
- Login page has been converted from `.jsx` to `.tsx` to support TypeScript type annotations

### Middleware
The NextAuth middleware is configured in `proxy.ts` and intercepts requests to protect authenticated routes.

## Build & Deploy

### Deploy to Vercel
The easiest way to deploy is with [Vercel](https://vercel.com):

```bash
pnpm build
vercel deploy
```

### Environment Variables for Production
Set the following in your Vercel environment variables:
- `POSTGRES_URL`: Production PostgreSQL connection string
- `NEXTAUTH_SECRET`: A secure random string
- `NEXTAUTH_URL`: Your production domain

## Troubleshooting

### Favicon not loading
- Clear browser cache (Ctrl+Shift+Delete)
- Restart the development server
- Check that `.ico` files are excluded from the auth middleware

### Database connection errors
- Verify `POSTGRES_URL` is correct
- Ensure PostgreSQL is running
- Check database credentials

### Build errors
- Clear `.next` folder: `rm -rf .next`
- Reinstall dependencies: `pnpm install`
- Restart dev server

## Contributing

Feel free to open issues and create pull requests for any improvements!

## License

This project is open source and available under the MIT License.

## Resources

- [Next.js Documentation](https://nextjs.org/docs)
- [NextAuth.js Documentation](https://next-auth.js.org/)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)

---

**Made with ❤️ using Next.js 16**
