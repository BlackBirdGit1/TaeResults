# TAE Results — Website

## What's in this folder

```
taeresults-site/
├── index.html              ← Homepage (landing page)
├── audits.html             ← Audit archive page
├── services.html           ← Services page
├── styles.css              ← All styles
└── audits/
    └── example-business.html  ← Template for individual audit posts
```

## Deploy to Cloudflare Pages (5 minutes)

1. Go to https://dash.cloudflare.com
2. In the sidebar, click **Compute (Workers)** → **Workers & Pages**
3. Click **Create** → then the **Pages** tab
4. Choose **Upload assets** (the drag-and-drop option)
5. Name your project: `taeresults` (or whatever you want)
6. Drag this entire `taeresults-site` folder into the upload area
7. Click **Deploy**

Your site will be live at `taeresults.pages.dev` within seconds.

## Connect your custom domain

1. In Cloudflare Pages, go to your project → **Custom domains**
2. Click **Set up a custom domain**
3. Enter `taeresults.com` (or your domain)
4. Cloudflare will automatically configure the DNS since your domain is already on Cloudflare

## Set up the contact form

The form currently uses FormSubmit.co (free, no account needed):

1. Open `index.html`
2. Find `action="https://formsubmit.co/YOUR_EMAIL_HERE"`
3. Replace `YOUR_EMAIL_HERE` with your taeresults Gmail address
4. Deploy again (re-upload the folder)
5. The first submission will send you a confirmation email — click to activate

Other free form options:
- **Formspree** (formspree.io) — 50 submissions/month free
- **Basin** (usebasin.com) — 100 submissions/month free
- **Google Forms** — embed or redirect to a Google Form

## Adding a new audit post

1. Copy `audits/example-business.html`
2. Rename it: `audits/business-name.html` (lowercase, hyphens)
3. Edit the title, meta description, video embed URL, and written summary
4. Add a card to `audits.html` pointing to the new post
5. Re-upload the folder to Cloudflare Pages

## Embedding videos

Replace the iframe `src` with your embed URL:

- **Loom:** `https://www.loom.com/embed/VIDEO_ID`
- **YouTube:** `https://www.youtube.com/embed/VIDEO_ID`
- **Vimeo:** `https://player.vimeo.com/video/VIDEO_ID`
- **Bunny Stream:** `https://iframe.mediadelivery.net/embed/LIBRARY_ID/VIDEO_ID`

## Updating the site

Every time you make changes, just re-upload the folder through Cloudflare Pages dashboard. Alternatively, connect a GitHub repo for automatic deploys on every push.
