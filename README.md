# Empyrean Consulting — Website

Static single-page site for empyreanconsulting.com. Hosted on GitHub Pages.

---

## Repo Contents

| File | Purpose |
|---|---|
| `index.html` | The entire site — HTML, CSS, content in one file. Edit here to change anything. |
| `CNAME` | Tells GitHub Pages to serve the site from `empyreanconsulting.com`. Do not rename or delete. |
| `README.md` | This file. |

---

## Deployment — First-Time Setup

Conservative estimate: **2–3 hours** including DNS propagation wait time.

### Step 1 — Create the GitHub repo (5 minutes)

1. Sign in to github.com (or create an account if needed)
2. Click "New repository"
3. Name it `empyrean-site` (or anything you prefer)
4. Make it **Public** (required for free GitHub Pages — keeps everything else simple)
5. Do not initialize with a README — you'll upload these files instead
6. Click "Create repository"

### Step 2 — Upload these files (5 minutes)

1. On the empty repo page, click "uploading an existing file"
2. Drag `index.html`, `CNAME`, and `README.md` into the upload area
3. Commit message: "Initial site"
4. Click "Commit changes"

### Step 3 — Enable GitHub Pages (5 minutes)

1. In the repo, go to **Settings → Pages** (left sidebar)
2. Under "Build and deployment":
   - **Source:** Deploy from a branch
   - **Branch:** `main` · `/ (root)` · Save
3. GitHub will start building the site. Wait 1–2 minutes.
4. Refresh the Pages settings page. You'll see a URL like `https://[your-username].github.io/empyrean-site/` — click it. The site should load with a temporary URL.

**Confirm everything works at the github.io URL before moving to the next step.** This isolates "is the site working" from "is the domain configured" — much easier to debug.

### Step 4 — Configure DNS at your registrar (20–45 minutes)

This is the trickiest step. The exact UI varies by registrar (GoDaddy, Namecheap, Cloudflare, etc.). The concepts are the same.

You need to point `empyreanconsulting.com` and `www.empyreanconsulting.com` to GitHub's servers.

#### A. For the apex domain (empyreanconsulting.com)

Add four **A records** pointing to GitHub Pages' IPs:

| Type | Host / Name | Value | TTL |
|---|---|---|---|
| A | `@` (or blank, depending on registrar) | `185.199.108.153` | Default |
| A | `@` | `185.199.109.153` | Default |
| A | `@` | `185.199.110.153` | Default |
| A | `@` | `185.199.111.153` | Default |

#### B. For the www subdomain

Add one **CNAME record**:

| Type | Host / Name | Value | TTL |
|---|---|---|---|
| CNAME | `www` | `[your-username].github.io` | Default |

(Replace `[your-username]` with your actual GitHub username — no `https://`, no trailing slash.)

#### C. Remove any conflicting records

If your registrar has any parking page redirects, default A records, or old CNAME entries on `@` or `www`, **delete them**. Conflicts here are the most common reason DNS fails.

### Step 5 — Tell GitHub about the custom domain (5 minutes)

1. Back in **Settings → Pages**
2. Under "Custom domain", enter: `empyreanconsulting.com`
3. Click Save
4. GitHub will run a DNS check. If DNS hasn't propagated yet, this is fine — it will keep checking.
5. Once the check passes, **enable "Enforce HTTPS"** (a checkbox below the domain field). This may take up to 24 hours to be available after DNS propagates — come back and enable it once it's clickable.

The `CNAME` file in this repo (containing `empyreanconsulting.com`) reinforces this setting. GitHub will see it and use it automatically.

### Step 6 — Wait for DNS propagation

Usually under an hour. Sometimes up to 24 hours.

Check propagation:
- Try the site in a private/incognito browser window (avoids cached DNS)
- Use https://dnschecker.org/ and enter `empyreanconsulting.com` — you want to see GitHub's IPs appearing globally

### Step 7 — Verify (15 minutes)

Test:
- [ ] `https://empyreanconsulting.com` loads
- [ ] `https://www.empyreanconsulting.com` loads (or redirects to the apex)
- [ ] HTTPS works (green padlock in browser)
- [ ] Site looks correct on desktop
- [ ] Site looks correct on phone
- [ ] Email link in the CTA button opens a mail client

---

## Editing the Site Later

Three ways, in order of difficulty:

### Option 1 — Edit in GitHub web UI (easiest)
1. Open the repo on github.com
2. Click `index.html`
3. Click the pencil icon (top right) to edit
4. Make changes
5. Scroll to bottom, commit with a short message
6. Changes go live in ~30 seconds

### Option 2 — Edit locally with Git
Clone the repo, edit locally, push back. Standard Git workflow.

### Option 3 — Have an agent do it
Once you're working in Claude Code or a similar tool, you can give it repo access and have it make edits, commit, and push. This is the path you mentioned wanting.

---

## Common Issues

**Site shows "404" at the GitHub Pages URL after step 3**
- Wait two more minutes; Pages can be slow on first build
- Check Settings → Pages and make sure the branch is set correctly

**Site shows "improperly configured" at the custom domain**
- DNS hasn't propagated yet, or A records are wrong
- Verify the four A records exactly match the IPs above
- Remove any other A records on `@`

**HTTPS doesn't work / "Enforce HTTPS" checkbox is greyed out**
- GitHub needs to issue an SSL certificate after DNS propagates
- This usually takes 15 minutes to a few hours after the domain check passes
- Come back later — the checkbox will become clickable

**Old "parked" page is still showing**
- Your registrar's default parking page is overriding the new DNS
- Look for "domain forwarding" or "parking" settings at the registrar and disable them
- DNS records take precedence once parking is off

---

## What This Site Is Not

- **Not a blog.** Articles should go on LinkedIn and Medium first; link to them from here when you're ready to add a "Writing" section.
- **Not a CMS.** Content lives in `index.html`. For now, that's fine — when content gets heavier, consider migrating to a static site generator (Astro, 11ty) with the same hosting.
- **Not a marketing funnel.** No tracking, analytics, or popups by design. Add analytics later if/when needed (Plausible and Fathom are good privacy-respecting options).

---

## Future Enhancements

When you're ready:
- Add a `/writing` section linking to LinkedIn/Medium articles
- Add a real contact form (Formspree, Basin, or similar — both have free tiers)
- Add an `og:image` for richer social link previews (1200×630 PNG)
- Set up Plausible or Fathom analytics if you want metrics
- Migrate to a static site generator when you have 5+ pages of content
