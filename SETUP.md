# IMSON Toner Finder — Online Shared Database Setup

## What this version does

- Anyone with the website link can search printer/toner models.
- The latest selling rate and stock come from one online Supabase database.
- You can update rate/stock from the Owner Update section.
- Dealers do NOT need a Supabase account.
- The database is protected with Row Level Security.
- GitHub Pages hosts the HTML; Supabase stores the shared data.

GitHub Pages itself is static hosting, so the shared database is kept in Supabase.

## 1. Create Supabase project

Open https://supabase.com/ and create a project.

Then open SQL Editor and paste the complete contents of `database.sql`.
Run it.

## 2. Create your owner login

In Supabase:
Authentication -> Users -> Add user

Create your owner email/password.

Do NOT give this password to dealers.

## 3. Get API values

Supabase Dashboard -> Project Settings -> API

Copy:
- Project URL
- Publishable key (or legacy anon key)

Do NOT copy or expose:
- service_role key
- secret key

Open `index.html` and replace:

const SUPABASE_URL = "PASTE_YOUR_SUPABASE_PROJECT_URL";
const SUPABASE_KEY = "PASTE_YOUR_SUPABASE_PUBLISHABLE_OR_ANON_KEY";

with your values.

## 4. Upload to GitHub

Create a repository and upload `index.html`.

Enable GitHub Pages from:
Repository -> Settings -> Pages -> Deploy from branch -> main -> /root

Your website will become:
https://YOUR-GITHUB-USERNAME.github.io/REPOSITORY-NAME/

## 5. How you will use it

Dealer:
- Open website
- Type 2725
- See NPG-87, rate and stock.

You:
- Open same website
- Owner Update
- Login
- Change rate/stock
- Save

Everyone then sees the latest database value.

## Important

Do not put purchase cost or other confidential information in public fields.
The public page shows only toner model, alternate code, compatible printers, selling rate and stock.

If you want different rates for different dealers, this needs a dealer/login system and should be added later.
