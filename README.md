# Pepfound — Static HTML + Supabase

A medically-reviewed peptide knowledge base built with static HTML and Supabase database.

## Files

- **index.html** — Main website (all pages in one)
- **.nojekyll** — GitHub configuration file
- **README.md** — This file

## Setup

### Step 1: Supabase Configuration

1. Create a Supabase project at https://supabase.com
2. Create the tables using SQL Editor:

```sql
CREATE TABLE peptides (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  name TEXT NOT NULL,
  slug TEXT NOT NULL UNIQUE,
  short_description TEXT,
  description TEXT,
  category TEXT,
  fda_status TEXT,
  mechanism TEXT,
  clinical_applications TEXT,
  safety_profile TEXT,
  references TEXT,
  created_at TIMESTAMP DEFAULT NOW()
);
```

3. Go to Settings → API
4. Copy:
   - `NEXT_PUBLIC_SUPABASE_URL` (Project URL)
   - `NEXT_PUBLIC_SUPABASE_ANON_KEY` (anon key)

### Step 2: Update index.html

Open `index.html` and find this section:

```javascript
// Supabase Configuration
const SUPABASE_URL = 'https://YOUR_SUPABASE_URL.supabase.co';
const SUPABASE_KEY = 'YOUR_ANON_KEY';
```

Replace with your actual values:

```javascript
const SUPABASE_URL = 'https://xxx.supabase.co';
const SUPABASE_KEY = 'eyJxxx...';
```

### Step 3: Push to GitHub

1. Create a new repo: `YashKshirsagar1/pepfound` (or similar)
2. Add these 3 files to repo root:
   - index.html
   - .nojekyll
   - README.md
3. Push to GitHub

### Step 4: Deploy on Vercel

1. Go to https://vercel.com
2. Click "Add New" → "Project"
3. Select your GitHub repo
4. Click "Deploy"
5. Done! Your site will be live in seconds ✓

## Features

- 🧬 **Single HTML File** — No build process, no Node.js needed
- 📊 **Supabase Database** — Store and fetch peptides dynamically
- 🔍 **Search & Filter** — Filter by name, category, FDA status
- 📱 **Responsive** — Works on mobile and desktop
- 🎨 **Clean Design** — Teal/neutral color scheme
- ⚡ **Fast** — Static HTML loads instantly

## Pages

- **Home** — Hero section with features
- **Guides** — Browse all peptides with search/filter
- **Peptide Detail** — Click any peptide to view full details
- **About** — Information about Pepfound
- **Safety** — Medical disclaimer and safety info
- **Ask** — Submit questions to medical team

## Database

To add peptide data, insert into `peptides` table:

```sql
INSERT INTO peptides (name, slug, short_description, description, category, fda_status, mechanism, clinical_applications, safety_profile, references)
VALUES (
  'BPC-157',
  'bpc-157',
  'Body Protection Compound discovered in gastric juice',
  'BPC-157 is a synthetic peptide...',
  'Regenerative',
  'Research Chemical',
  'Mechanisms include...',
  'Applications...',
  'Safety profile...',
  'References...'
);
```

## Troubleshooting

**Site shows 404:**
- Make sure index.html is at repo root (not in subfolder)
- Vercel should auto-deploy when you push

**Peptides not loading:**
- Check Supabase URL and key are correct in index.html
- Make sure `peptides` table exists in Supabase
- Check browser console for errors (F12)

**Search/filters not working:**
- Open browser console (F12) for error messages
- Make sure peptide data has `name`, `slug`, `category`, `fda_status` fields

## Next Steps

- Add more peptides to the database
- Customize colors/branding in the CSS
- Add newsletter signup
- Build out the question submission feature to save to Supabase
- Add user authentication if needed

---

Questions? Issues? Check your Supabase dashboard and browser console for error messages!
