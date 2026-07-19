# GT Development — Website + Editing Panel Setup

This package contains the full website plus a free content-editing panel, so you (or anyone on the team) can update text and photos without touching code.

## What's inside
- `index.html` — the site. It reads all text and image paths from `content.json` when it loads.
- `content.json` — every editable piece of text and every image path, in one file.
- `images/` — the current photos.
- `admin/` — the editing panel (Decap CMS), free and open-source.

## The plan (one-time setup, ~15 minutes)
1. Upload this folder to a new GitHub repository (free).
2. Connect that repository to Netlify (free hosting).
3. Turn on **Identity** and **Git Gateway** in Netlify (two clicks) — this is what gives you a login for the editing panel.
4. Connect your domain (e.g. `www.gtdevelopment.com`).
5. Go to `yourdomain.com/admin`, log in, and you'll see a form with every text field and photo on the site — change what you want, hit **Publish**, and the live site updates in under a minute.

---

## Step 1 — GitHub
1. Go to [github.com](https://github.com) and log in (or create a free account).
2. Click **New repository**. Name it something like `gt-development-website`. Keep it **Public** or **Private** (either works with Netlify). Click **Create repository**.
3. On the empty repo page, click **uploading an existing file**, drag in everything from this folder (keeping the `admin/` and `images/` folders intact), and commit.

## Step 2 — Netlify
1. Go to [netlify.com](https://netlify.com) and log in (or create a free account) — sign in with GitHub to make step 3 easier.
2. Click **Add a new site → Import an existing project → Deploy with GitHub**.
3. Pick the `gt-development-website` repo you just created.
4. Leave the build settings blank (no build command, publish directory is the root `/`) and click **Deploy**.
5. Wait about a minute — Netlify will give you a temporary URL like `random-name-12345.netlify.app`. Open it to confirm the site loads.

## Step 3 — Turn on the editing panel
1. In your Netlify site dashboard, go to **Site configuration → Identity** and click **Enable Identity**.
2. Scroll to **Registration preferences** and set it to **Invite only** (so strangers can't sign up).
3. Scroll to **Services → Git Gateway** and click **Enable Git Gateway**.
4. Go to the **Identity** tab and click **Invite users**. Enter your email address.
5. Check your email for the invite. **Click the link directly from the email** (don't retype or edit it). It should take you to a page to set a password.
   - If instead it just sends you to a login screen with no password form, the token wasn't processed — go back to Identity, delete the pending invite, and re-invite yourself to get a fresh link (this is a known quirk with the confirmation link landing on a page before the Identity script loads; this package already includes the fix, so this shouldn't happen, but if it does, this is the way out).
6. Once you've set a password, go to `your-netlify-url.netlify.app/admin`, log in, and you should see **"GT Development Website Content"** — click it to open the editing form.

## Step 4 — Connect your domain
1. In Netlify, go to **Domain management → Add a domain** and enter `gtdevelopment.com`.
2. Netlify will show you DNS records to add. At your domain registrar (GoDaddy, Namecheap, etc.):
   - Add an **A record** for `@` pointing to the IP Netlify gives you (commonly `75.2.60.5`).
   - Add a **CNAME record** for `www` pointing to your Netlify site URL (`your-site.netlify.app`).
3. Wait for DNS to propagate (can take a few minutes to a few hours). Netlify will auto-provision an SSL certificate once it detects the domain is pointed correctly.

---

## Using the editing panel day-to-day
1. Go to `gtdevelopment.com/admin` (once your domain is connected — or the Netlify URL before that).
2. Log in with your email and password.
3. Click **"GT Development Website Content"**.
4. You'll see every section of the site as a form: Hero, Stats, Origin story, Projects, Capital Stack, Partners, Founders, FAQ, Contact, and Footer.
5. Change any text, swap any photo, add or remove list items (like FAQ questions or project locations), then scroll down and click **Publish**.
6. Give it under a minute, then refresh the live site to see your change.

### What you can edit yourself
- Every headline, paragraph, and label on the site
- All photos (hero, the "Discover" section photo, the 5 project location photos, founder photos)
- The stats numbers and labels
- The 5-step process descriptions
- The 5 project locations (add, remove, or rename)
- The capital stack rows
- The partner firms in every category
- Both founder bios
- The 3 "Who We Serve" cards
- All 5 FAQ questions and answers
- Contact info, email, and footer text

### What still needs a developer (me, or someone else)
- Layout or design changes (colors, fonts, section order, adding a brand-new section)
- Adding new pages
- Anything structural beyond text and photo swaps

---

**A note on GT Group site consistency:** this uses the same Decap CMS + Netlify + Git Gateway pattern as the Rähle Cars site, so the workflow will feel familiar if you've used that panel already.
