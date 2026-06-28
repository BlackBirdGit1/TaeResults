# Tae Results — Website

Local SEO audits and blog for East Tennessee businesses.  
Live at [taeresults.com](https://taeresults.com)

---

## Site Structure

```
TaeResults-main/
├── index.html            ← Homepage
├── audits.html           ← Audits listing (carousel + searchable grid)
├── blog.html             ← Blog listing (carousel + searchable grid)
├── services.html         ← Services page
├── styles.css            ← All styles
├── logo.png              ← Site logo
├── audits/               ← Individual audit pages
│   ├── sunrise-plumbing-and-remodel.html
│   ├── winkles-plumbing.html
│   ├── jj-professional-tree-service.html
│   ├── lm-tree-service.html
│   └── anthonys-hughes-tree-stump-grinding.html
└── blog/                 ← Individual blog post pages (create as needed)
```

---

## How to Add a New Audit

You need to do 3 things: add a card to the carousel, add a card to the grid, and create the detail page.

### 1. Get your YouTube embed info

Upload your audit video to YouTube and grab two things:
- **Video ID** — the part after `v=` in the URL (e.g. `https://youtu.be/abc123` → video ID is `abc123`)
- **Thumbnail URL** — `https://img.youtube.com/vi/VIDEO_ID/hqdefault.jpg`
- **Embed URL** — `https://www.youtube.com/embed/VIDEO_ID`

### 2. Add a card to the featured carousel

Open `audits.html` and find the comment `<!-- FEATURED CARDS -->`.  
Paste this block right after that comment (so it appears first/newest):

```html
<a href="/audits/business-name.html" class="featured-card">
  <div class="featured-thumb">
    <img src="https://img.youtube.com/vi/VIDEO_ID/hqdefault.jpg" alt="Business Name audit">
    <span class="featured-badge">New</span>
  </div>
  <div class="featured-card-body">
    <h3>Business Name</h3>
    <p>City &middot; Industry</p>
  </div>
</a>
```

Keep only the newest 5 audits in the carousel. When you add a new one, remove the oldest one from this section (it still shows in the grid below).

Remove the `<span class="featured-badge">New</span>` line from older cards when they're no longer new.

### 3. Add a card to the "All Audits" grid

In the same `audits.html`, find the `<!-- Audit Grid -->` section.  
Paste this block at the top of the grid (right after the HTML comment):

```html
<a href="/audits/business-name.html" class="audit-card" data-industry="plumbing" data-city="knoxville">
  <div class="audit-thumb">
    <img src="https://img.youtube.com/vi/VIDEO_ID/hqdefault.jpg" alt="Business Name audit">
  </div>
  <div class="audit-card-body">
    <h3>Business Name</h3>
    <p>City &middot; Industry</p>
  </div>
</a>
```

**Important:** The `data-industry` and `data-city` attributes power the search and filter tabs.
- `data-industry` must be **lowercase and hyphenated**: `tree-service`, `plumbing`, `hvac`, `dental`, `roofing`
- `data-city` must be **lowercase**: `knoxville`, `maryville`, `sevierville`
- Use `&amp;` in place of `&` inside business names (e.g. `J&amp;J Professional`)

### 4. Add a filter tab (if it's a new industry)

If this is the first audit for a new industry, add a filter tab button in `audits.html`.  
Find the `<div class="filter-tabs">` section and add:

```html
<button class="filter-tab" data-filter="new-industry">New Industry</button>
```

The `data-filter` value must exactly match the `data-industry` value on the cards.

### 5. Create the detail page

Copy any existing file from `audits/` (e.g. `audits/winkles-plumbing.html`) and save it as `audits/your-business-name.html`.

In the new file, replace:
- The `<title>` tag with the business name
- The `<meta name="description">` content
- The `<h1>` with the business name
- The `<p>` subtitle with the city and industry
- The `iframe src` with `https://www.youtube.com/embed/VIDEO_ID`
- The `iframe title` with the business name
- The audit summary `<p>` tags with your written notes
- The schema.org JSON-LD: name, description, thumbnailUrl, embedUrl, uploadDate

**Filename rules:** lowercase, hyphens instead of spaces, no special characters.  
Examples: `sunrise-plumbing-and-remodel.html`, `jj-professional-tree-service.html`

### Embedding videos from other platforms

| Platform     | Embed URL format                                                |
|-------------|----------------------------------------------------------------|
| YouTube      | `https://www.youtube.com/embed/VIDEO_ID`                       |
| Loom         | `https://www.loom.com/embed/VIDEO_ID`                          |
| Vimeo        | `https://player.vimeo.com/video/VIDEO_ID`                      |
| Bunny Stream | `https://iframe.mediadelivery.net/embed/LIBRARY_ID/VIDEO_ID`   |

---

## How to Add a New Blog Post

Same pattern as audits: add a card to the carousel, add a card to the grid, and create the detail page.

### 1. Add a card to the featured carousel

Open `blog.html` and find the comment `<!-- FEATURED BLOG CARDS -->`.  
Paste this block right after that comment:

```html
<a href="/blog/your-post-slug.html" class="featured-card featured-card--blog">
  <div class="featured-card-body">
    <span class="blog-date">Month Year</span>
    <h3>Your Blog Post Title</h3>
    <p>A 1-2 sentence excerpt or summary of the post.</p>
  </div>
</a>
```

Keep only the newest 3-5 posts in the carousel.

### 2. Add a card to the "All Posts" grid

In the same `blog.html`, find the `<!-- Blog Grid -->` section.  
Paste this block at the top of the grid:

```html
<a href="/blog/your-post-slug.html" class="blog-card" data-topic="seo">
  <div class="blog-card-body">
    <span class="blog-date">Month Year</span>
    <h3>Your Blog Post Title</h3>
    <p>A 1-2 sentence excerpt or summary of the post.</p>
    <span class="blog-read-more">Read more &rarr;</span>
  </div>
</a>
```

**The `data-topic` attribute** powers the filter tabs. Current topics:
- `gbp` — Google Business Profile
- `seo` — General SEO
- `reviews` — Reviews
- `strategy` — Strategy

Add new topic filter tabs the same way as audit industry tabs (see step 4 above).

### 3. Create the blog post page

Create a new folder called `blog/` if it doesn't exist yet.  
Create a file like `blog/your-post-slug.html`.  
Use the same page structure as the audit detail pages but replace the video embed with your blog content.

Here's a minimal template:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Post Title — Tae Results Blog</title>
  <meta name="description" content="Short summary of the post.">
  <link rel="stylesheet" href="../styles.css">
</head>
<body>
  <header class="site-header">
    <div class="container header-inner">
      <a href="/" class="logo"><img src="../logo.png" alt="Tae Results" class="logo-img"></a>
      <button class="mobile-toggle" onclick="document.querySelector('nav').classList.toggle('open')" aria-label="Toggle menu">&#9776;</button>
      <nav>
        <a href="/audits.html">Audits</a>
        <a href="/blog.html">Blog</a>
        <a href="/services.html">Services</a>
        <a href="/#free-audit" class="btn btn-primary">Get Free Audit</a>
      </nav>
    </div>
  </header>

  <section class="page-header">
    <div class="container">
      <h1>Post Title</h1>
      <p>Month Year</p>
    </div>
  </section>

  <section>
    <div class="container">
      <div class="audit-post">
        <!-- Your blog content goes here -->
        <p>Write your post content here using regular HTML.</p>

        <h2>Subheading</h2>
        <p>More content...</p>
      </div>
      <div style="margin-top:2rem;">
        <a href="/blog.html">&larr; Back to all posts</a>
      </div>
    </div>
  </section>

  <section class="cta-section" style="text-align:center;padding:3rem 1rem;">
    <div class="container">
      <h2>Want a free audit for your business?</h2>
      <p>See exactly how you show up on Google — and what to fix.</p>
      <a href="/#free-audit" class="btn btn-primary">Get Your Free Audit</a>
    </div>
  </section>

  <footer class="site-footer">
    <div class="container">
      <p>Tae Results</p>
      <p>Local SEO for businesses in East Tennessee &middot; &copy; 2026</p>
    </div>
  </footer>
</body>
</html>
```

---

## Deploying

Push this repo to GitHub and connect to Cloudflare Pages (or your host). Every push to `main` auto-deploys.

---

## Quick Reference

| Task | Files to edit |
|------|--------------|
| Add an audit | `audits.html` (carousel + grid) + create `audits/business-name.html` |
| Add a blog post | `blog.html` (carousel + grid) + create `blog/post-slug.html` |
| Add a new industry filter | `audits.html` → add a `<button class="filter-tab">` |
| Add a new blog topic filter | `blog.html` → add a `<button class="filter-tab">` |
| Change styles | `styles.css` |
| Update nav links | Edit the `<nav>` in every `.html` file |
