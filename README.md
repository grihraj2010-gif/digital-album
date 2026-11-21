# My Photo Album (React + Supabase)

Flip-book photo albums with hearts, flowers and sparkles. People sign up, keep albums online,
share a link, and download a PDF.

## 1. Install the tools (once)
- Node.js LTS: https://nodejs.org
- VS Code: https://code.visualstudio.com

## 2. Create the free Supabase project
1. Go to https://supabase.com, sign up, click **New project**. Save the database password.
2. Open **SQL Editor -> New query**, paste everything from `supabase/schema.sql`, click **Run**.
3. Open **Project Settings -> API**. Copy the **Project URL** and the **anon public** key.
4. (Easier testing) **Authentication -> Providers -> Email**: turn off "Confirm email".
   Turn it back on before you share the site with real people.

## 3. Run it on your computer
Open this folder in VS Code, open the Terminal, then:

    copy .env.example .env        (Mac/Linux: cp .env.example .env)

Edit `.env` and paste your two values. Then:

    npm install
    npm run dev

Open the address it prints (usually http://localhost:5173). Sign up, create an album, add photos.

## 4. Put it online (free)
1. Push the folder to a GitHub repository (the `.env` file is ignored on purpose).
2. On https://vercel.com choose **Add New -> Project**, pick the repository.
3. Under **Environment Variables** add `VITE_SUPABASE_URL` and `VITE_SUPABASE_ANON_KEY`.
4. Deploy. In Supabase go to **Authentication -> URL Configuration** and set **Site URL**
   to your Vercel address.

## How sharing works
Each album has a **Sharing** button. When it is On, anyone with the album link can view it
(no login). Photo files are stored in a public bucket under hard-to-guess names, so a photo's
direct link works for anyone who has it. Do not upload anything you need to keep strictly private.

## Folder guide
- `supabase/schema.sql`  tables, privacy rules and photo storage
- `src/components/Album.jsx`  the flip book, effects, uploads, sharing
- `src/effects.js`  heart / flower / sparkle animations
- `src/pdf.js`  PDF download
