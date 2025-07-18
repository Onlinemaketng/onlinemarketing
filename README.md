# Marketing Agency Website

A professional marketing agency website built with React, TypeScript, Express.js, and PostgreSQL.

## Features

- Modern responsive design
- Contact form with database storage
- Customer testimonials
- Service showcase (Web Development, Social Media, Google Business)
- Portfolio section
- Pricing packages

## Quick Setup

1. **Clone/Download the project**
2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Set up environment variables:**
   ```bash
   cp .env.example .env
   ```
   Edit `.env` and add your database URL

4. **Set up database:**
   ```bash
   npm run db:push
   ```

5. **Start development server:**
   ```bash
   npm run dev
   ```

## Environment Variables

Create a `.env` file with:

```
DATABASE_URL=your_postgresql_connection_string
NODE_ENV=production
```

## Database Providers

- **Supabase** (Free tier): https://supabase.com
- **Neon** (Free tier): https://neon.tech  
- **Railway**: https://railway.app
- **PlanetScale**: https://planetscale.com

## Hosting Options

- **Vercel** (Recommended): Connect GitHub repo for auto-deploy
- **Netlify**: Drag & drop deployment
- **Railway**: Full-stack hosting with database
- **DigitalOcean App Platform**: Professional hosting

## Contact Form Data

Contact submissions are saved to PostgreSQL database and can be viewed at:
`/api/contacts`

## Customization

Edit contact details in:
- `client/src/components/contact.tsx` - Contact information
- `client/src/components/navigation.tsx` - Company name
- `client/src/components/footer.tsx` - Company details

## Build for Production

```bash
npm run build
```

Static files will be in `dist/` directory.