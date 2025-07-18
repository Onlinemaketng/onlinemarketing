# GitHub + Vercel Deployment Guide

## Step 1: Download Your Code
1. Click the three dots (⋯) in Replit file explorer
2. Select "Download as zip"  
3. Extract the files on your computer

## Step 2: Set Up Supabase Database
1. Go to https://supabase.com
2. Create account and new project
3. Go to Settings → API and copy your **anon/public** key
4. Go to Settings → Database and copy your **Connection string**
5. Your URL is: `https://jtnkzyemlhfwaithjbmd.supabase.co`

### Option B: Neon (Free tier)
1. Go to https://neon.tech
2. Create account and database
3. Copy connection string from dashboard

## Step 3: Set Up GitHub Repository
1. **Create GitHub Repository:**
   - Go to https://github.com
   - Click "New repository"
   - Name it (e.g., "marketing-website")
   - Make it public or private
   - Don't initialize with README (you already have one)

2. **Upload Your Code:**
   - Extract your downloaded zip file
   - Open terminal/command prompt in the folder
   - Run these commands:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/yourusername/marketing-website.git
   git push -u origin main
   ```

## Step 4: Set Up Supabase Database Tables
1. In your Supabase dashboard, go to **SQL Editor**
2. Run this SQL to create your tables:

```sql
CREATE TABLE contacts (
  id SERIAL PRIMARY KEY,
  name TEXT NOT NULL,
  email TEXT NOT NULL,
  phone TEXT,
  service TEXT NOT NULL,
  message TEXT NOT NULL,
  created_at TIMESTAMP DEFAULT NOW() NOT NULL
);

CREATE TABLE testimonials (
  id SERIAL PRIMARY KEY,
  name TEXT NOT NULL,
  title TEXT NOT NULL,
  company TEXT NOT NULL,
  message TEXT NOT NULL,
  rating TEXT NOT NULL,
  image_url TEXT
);

-- Insert sample testimonials
INSERT INTO testimonials (name, title, company, message, rating, image_url) VALUES 
('Sarah Johnson', 'CEO', 'Johnson & Associates', 'DigitalBoost Pro transformed our online presence. Our website traffic increased by 200% and we''re getting more qualified leads than ever before.', '5', 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=150&h=150'),
('Michael Chen', 'Owner', 'Chen''s Restaurant', 'The social media management has been outstanding. Our engagement rates have skyrocketed and we''re seeing real business results.', '5', 'https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=150&h=150'),
('David Rodriguez', 'Founder', 'Rodriguez Consulting', 'Professional, responsive, and results-driven. Our Google Business listing is now ranking #1 for our key terms. Highly recommended!', '5', 'https://images.unsplash.com/photo-1500648767791-00dcc994a43e?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=150&h=150');
```

## Step 5: Deploy to Vercel
1. **Connect to Vercel:**
   - Go to https://vercel.com
   - Sign up with GitHub
   - Click "Import Project"
   - Select your repository

2. **Set Environment Variables:**
   - In Vercel dashboard, go to Settings → Environment Variables
   - Add: `DATABASE_URL` = `postgresql://postgres:[password]@db.jtnkzyemlhfwaithjbmd.supabase.co:5432/postgres`
   - Add: `SUPABASE_URL` = `https://jtnkzyemlhfwaithjbmd.supabase.co`
   - Add: `SUPABASE_KEY` = your anon/public key from Supabase
   - Add: `NODE_ENV` = `production`

3. **Deploy:**
   - Click "Deploy"
   - Your website will be live at a .vercel.app URL

## Step 5: Custom Domain (Optional)
- In Vercel, go to Settings → Domains
- Add your custom domain (e.g. yourcompany.com)
- Follow DNS setup instructions

## Alternative: Railway Deployment

1. Go to https://railway.app
2. Connect GitHub repository
3. Add environment variables
4. Deploy with built-in database

## Contact Form Data Access

After deployment, view contact submissions at:
`https://yoursite.com/api/contacts`

## Support

If you need help:
- Check Vercel/Railway documentation
- Database provider support docs
- Most hosting providers have excellent tutorials