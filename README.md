# DAKAT SIR setup

## 1. Supabase keys
Open `index.html` and replace:
- `PASTE_YOUR_PROJECT_URL_HERE`
- `PASTE_YOUR_PUBLISHABLE_KEY_HERE`

Use only the Supabase Project URL and `sb_publishable_...` key. Never put an `sb_secret_...` key in browser code.

## 2. Existing profiles table
The website expects `public.profiles` with columns:
`id` uuid primary key referencing `auth.users.id`, `full_name`, `institution`, `education_level`, `group_name`, `avatar_url`, `created_at`, `updated_at`.
If you already created this table and its own-user RLS policies, do not recreate it.

## 3. Email confirmation
If Supabase Email confirmation is enabled, new users must click the confirmation email before logging in.
In Supabase Authentication > URL Configuration, add your real GitHub Pages URL to Site URL and Redirect URLs.

## 4. Profile photos
For photo upload, create a **public** Storage bucket named `avatars` in Supabase, then apply the Storage policies in `supabase-setup.sql`. If you don't set up Storage, profiles still work without a photo.

## 5. Publish
Commit `index.html` to the `main` branch. GitHub Settings > Pages should deploy from `main` and `/(root)`.

Note: Category cards are currently outlines only. Lesson content, chapter pages, quizzes/exams, progress tracking and admin dashboard are not yet built.
