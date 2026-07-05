# Personal Site — Setup Guide

Your setup:
- GitHub account: **wildcatandromeda**
- Main site: **michaelholdsworth.com**
- Redirects to main site: **michaeltholdsworth.com**

## 1. Create the GitHub repository
1. Go to github.com (signed in as wildcatandromeda) and create a **new
   repository** named exactly: `wildcatandromeda.github.io`
   (This specific name is what gives you a free `.github.io` URL as a
   fallback/preview — your custom domain will layer on top of it.)
2. Upload every file in this folder to that repository (drag-and-drop
   works on the GitHub website — use "Add file" > "Upload files").
   Make sure the files land in the root of the repo, not in a subfolder.

## 2. Turn on GitHub Pages
1. In the repo, go to **Settings > Pages**.
2. Under "Build and deployment," set Source to **Deploy from a branch**,
   branch `main`, folder `/ (root)`. Save.
3. GitHub will build the site (takes 1-2 minutes). You can preview it at
   `https://wildcatandromeda.github.io` before the custom domain is live.

## 3. Connect michaelholdsworth.com
1. A `CNAME` file containing `michaelholdsworth.com` is already included
   in this folder, so once you upload it GitHub Pages will pick it up
   automatically. (You can double check it's set under Settings > Pages >
   Custom domain — it should already show `michaelholdsworth.com`.)
2. In Porkbun, open **michaelholdsworth.com > DNS records** and add:
   - Four `A` records, host `@`, pointing to:
     - 185.199.108.153
     - 185.199.109.153
     - 185.199.110.153
     - 185.199.111.153
   - One `CNAME` record: host `www`, answer `wildcatandromeda.github.io`
   - Remove any existing "parked" A or ALIAS/ANAME records on `@` that
     Porkbun may have set by default, so they don't conflict.
3. Wait 15-60 minutes for DNS to update, then go back to GitHub
   **Settings > Pages** and check the box for "Enforce HTTPS." (It may be
   greyed out for a few minutes until GitHub verifies the DNS — that's
   normal, just check back later.)
4. Visit `https://michaelholdsworth.com` to confirm it loads your site.

## 4. Redirect michaeltholdsworth.com to the main site
1. In Porkbun, open **michaeltholdsworth.com**.
2. Find **URL Forwarding** and set it to forward to
   `https://michaelholdsworth.com`, type "Permanent (301)."
3. No DNS records or coding needed for this one — Porkbun handles it
   entirely. Give it 15-30 minutes to take effect.

## 5. Writing a new weekly post
1. In GitHub, open the `_posts` folder.
2. Click "Add file" > "Create new file."
3. Name it: `YYYY-MM-DD-a-short-title.md` (e.g. `2026-07-12-my-week.md`).
4. Paste this at the top, then write your post below it:

   ```
   ---
   layout: post
   title: "My Week"
   date: 2026-07-12
   ---

   Your post text goes here.
   ```
5. Click "Commit changes." The site rebuilds automatically in about a minute.

## 6. Adding a photo
1. In GitHub, open `assets/images`, click "Add file" > "Upload files,"
   and upload your photo.
2. In your post, reference it:
   `![description](/assets/images/your-photo.jpg)`

## Editing the About page or homepage text
Just open `about.md` or `index.md` in GitHub, click the pencil (edit) icon,
change the text, and commit.
