# TAE Results — Website

## What's in this folder

```
taeresults-site/
├── index.html              ← Homepage (landing page)
├── audits.html             ← Audit archive + Blog page
├── services.html           ← Services page
├── styles.css              ← All styles
├── logo.png                ← Site logo (trimmed, transparent background)
└── audits/
    └── example-business.html  ← Template for individual audit posts
```

---

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
2. Find `action="https://formsubmit.co/taeresults1@gmail.com"`
3. The first submission will send you a confirmation email — click to activate
4. Deploy again (re-upload the folder)

Other free form options:
- **Formspree** (formspree.io) — 50 submissions/month free
- **Basin** (usebasin.com) — 100 submissions/month free
- **Google Forms** — embed or redirect to a Google Form

---

## Adding a New Audit Video

Audit videos live on the **audits.html** page in the "Audit Grid" section.

### Step 1 — Add a card to audits.html

Open `audits.html` and find the comment `<!-- Add more cards as you complete audits -->`. Right above it, paste a new card:

```html
<a href="/audits/business-name.html" class="audit-card">
  <div class="audit-thumb">
    <img src="thumbnail.jpg" alt="Business Name audit">
  </div>
  <div class="audit-card-body">
    <h3>Business Name</h3>
    <p>City &middot; Industry</p>
  </div>
</a>
```

Replace:
- `business-name.html` → the URL for the full audit page
- `thumbnail.jpg` → path to a screenshot/thumbnail image (put it in an `images/` folder)
- `Business Name` → the actual business name
- `City` → the city (Knoxville, Maryville, etc.)
- `Industry` → industry type (Plumbing, Dental, HVAC, etc.)

### Step 2 — Create the individual audit page

1. Copy `audits/example-business.html`
2. Rename it: `audits/business-name.html` (lowercase, hyphens, no spaces)
3. Edit the title, meta description, video embed URL, and written summary
4. Save and re-upload the folder

### Embedding videos

Replace the iframe `src` with your embed URL:

| Platform       | Embed URL format                                            |
|----------------|-------------------------------------------------------------|
| **Loom**       | `https://www.loom.com/embed/VIDEO_ID`                       |
| **YouTube**    | `https://www.youtube.com/embed/VIDEO_ID`                    |
| **Vimeo**      | `https://player.vimeo.com/video/VIDEO_ID`                   |
| **Bunny Stream** | `https://iframe.mediadelivery.net/embed/LIBRARY_ID/VIDEO_ID` |

To get a YouTube embed URL: open the video → click Share → Embed → copy the `src` value from the iframe code.

---

## Adding a New Blog Post

Blog posts live on the **audits.html** page in the "Blog" section below the audit videos.

### Step 1 — Add a blog card to audits.html

Open `audits.html` and find the comment `<!-- Add more blog cards here -->`. Right above it, paste:

```html
<a href="/blog/your-post-slug.html" class="blog-card">
  <div class="blog-card-body">
    <span class="blog-date">Month Year</span>
    <h3>Your Blog Post Title</h3>
    <p>A short 1-2 sentence description of what the post covers.</p>
    <span class="blog-read-more">Read more &rarr;</span>
  </div>
</a>
```

Replace:
- `your-post-slug.html` → the filename for your blog post (lowercase, hyphens)
- `Month Year` → e.g. "July 2026"
- Title and description with your actual content

### Step 2 — Create the blog post page

Create a new file at `blog/your-post-slug.html`. Here's a full template:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <script async src="https://www.googletagmanager.com/gtag/js?id=G-WWNTYYCS59"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', 'G-WWNTYYCS59');
  </script>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Your Post Title — TAE Results</title>
  <meta name="description" content="A brief description for search engines (under 160 characters).">
  <link rel="stylesheet" href="../styles.css">
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "BlogPosting",
    "headline": "Your Post Title",
    "description": "A brief description for search engines.",
    "author": { "@type": "Person", "name": "TAE Results" },
    "publisher": { "@type": "Organization", "name": "TAE Results" },
    "datePublished": "2026-07-01"
  }
  </script>
</head>
<body>

  <header class="site-header">
    <div class="container header-inner">
      <a href="/" class="logo"><img src="../logo.png" alt="TAE Results" class="logo-img"></a>
      <button class="mobile-toggle" onclick="document.querySelector('nav').classList.toggle('open')" aria-label="Toggle menu">&#9776;</button>
      <nav>
        <a href="/audits.html">Audits</a>
        <a href="/services.html">Services</a>
        <a href="/#free-audit" class="btn btn-primary">Get Free Audit</a>
      </nav>
    </div>
  </header>

  <section class="page-header">
    <div class="container">
      <h1>Your Post Title</h1>
      <p>July 2026</p>
    </div>
  </section>

  <section>
    <div class="container">
      <div class="audit-post">
        <!-- Write your blog content here using <h2>, <p>, <ul>, <li> tags -->

        <p>Your intro paragraph goes here.</p>

        <h2>First Section Heading</h2>
        <p>Section content goes here.</p>

        <h2>Second Section Heading</h2>
        <p>More content here.</p>

        <!-- Link back to audits page -->
        <p style="margin-top: 48px;"><a href="/audits.html#blog" style="color: var(--accent-soft); font-weight: 600;">&larr; Back to all posts</a></p>
      </div>
    </div>
  </section>

  <footer class="site-footer">
    <div class="container">
      <p>TAE Results</p>
      <p>Local SEO for businesses in East Tennessee &middot; &copy; 2026</p>
    </div>
  </footer>

</body>
</html>
```

### Step 3 — Deploy

Re-upload your entire site folder to Cloudflare Pages.

---

## SEO Schema Markup

The site includes structured data (JSON-LD) for search engines:

- **index.html** — `LocalBusiness` schema with your services, service area (9 East Tennessee cities), geo coordinates, and contact info
- **audits.html** — `CollectionPage` schema
- **services.html** — `WebPage` schema

### To customize the schema:

1. Open `index.html` and find the `<script type="application/ld+json">` block
2. Update the `"url"` fields to your actual domain once it's live
3. Add your social media links to the `"sameAs"` array, e.g.:
   ```json
   "sameAs": [
     "https://www.facebook.com/taeresults",
     "https://www.instagram.com/taeresults"
   ]
   ```
4. Add or remove cities from the `"serviceArea"` array as needed
5. If you get a physical address or phone number, add `"telephone"` and full `"address"` fields

### Validate your schema:

After deploying, paste your URL into [Google's Rich Results Test](https://search.google.com/test/rich-results) to make sure everything is picked up correctly.

---

## Updating the site

Every time you make changes, just re-upload the folder through the Cloudflare Pages dashboard. Alternatively, connect a GitHub repo for automatic deploys on every push.
