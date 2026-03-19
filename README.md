# Swapnacharon Photography

A single-page wedding photography portfolio website for **Dip Das** of Swapnacharon Photography. Built with vanilla HTML, CSS, and JavaScript — no build tools, no framework, no backend.

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| Tailwind CSS | Utility-first styling |
| AOS | Scroll-triggered animations |
| Feather Icons | UI icons |
| PapaParse | Google Sheets CSV parsing |
| EmailJS | Contact form email delivery |
| Google Sheets | No-code content management |
| Netlify | Hosting and deployment |

---

## Project Structure

```
/
├── index.html              # Entire site — single file
├── public/
│   └── images/
│       ├── client.jpg      # Photographer portrait (About section)
│       └── OG.jpg          # Social share preview image (1200×630px)
└── static/
    └── favicon.ico
```

---

## No-Code Content Management

This is the most important feature for the client. **All dynamic content on the site — hero images, portfolio photos, videos, and wedding stories — is managed entirely through a Google Sheet.** The client never needs to touch the code.

### How it works

The site reads from a Google Sheet published as a CSV. Every time a visitor loads the page, the latest version of the sheet is fetched automatically. The client simply opens the sheet, adds or removes a row, and the site reflects the change instantly — no deployment, no developer needed.

### Sheet Structure

Each row in the sheet represents one piece of content. The columns are:

| Column | What to put here |
|--------|-----------------|
| `Category` | One of: `Hero`, `Portfolio`, `Video`, `Story` |
| `ImageLink` | A Google Drive file ID or a direct image URL (Cloudinary recommended) |
| `RedirectLink` | Optional. For Portfolio: a link to open when clicked. Leave blank to use the built-in lightbox instead |
| `Tag` | For Stories: a location label e.g. `Kolkata, India` |
| `Title` | For Stories: the wedding title e.g. `Rahul & Priya's Wedding` |
| `Subtitle` | For Stories: a short description |

### What each Category does

- **Hero** — the image appears in the animated full-screen marquee on the homepage
- **Portfolio** — the image appears in the gallery grid. Clicking opens a fullscreen lightbox viewer with swipe support. If a `RedirectLink` is provided, clicking opens that link instead
- **Video** — paste a YouTube video ID or URL. The site automatically fetches the thumbnail and adds it to the film carousel
- **Story** — creates a featured wedding story card with the title, tag, subtitle, and image

### Adding images — two options

**Option 1 — Google Drive (easiest)**
Upload the photo to Google Drive, get the file ID from the sharing link, paste just the ID into the `ImageLink` column. The site handles the rest.

**Option 2 — Cloudinary (recommended for reliability)**
Upload the photo to Cloudinary (free, 25GB storage), copy the direct image URL, paste it into `ImageLink`. Cloudinary is a dedicated image CDN so images load faster and more reliably.

---

## Sections

| Section | Description |
|---------|-------------|
| **Hero** | Full-screen animated photo marquee with headline and CTA buttons |
| **About** | Photographer portrait and bio |
| **Gallery** | Photo grid, 8 images per page, load more button, fullscreen lightbox |
| **Films** | Auto-scrolling YouTube video carousel, click to play in modal |
| **Stories** | Featured wedding story cards |
| **Packages** | Three pricing tiers — Basic, Standard, Premium |
| **Contact** | Inquiry form, phone numbers, email address |

---

## Contact Form

The inquiry form collects name, phone, email, package interest, and event details. On submission it sends directly to the client's email via EmailJS — no server required. The form shows a loading state during send and a success modal on completion.

---

## Deployment

The site deploys automatically on every push to the main GitHub branch. Netlify picks up the change within about 30 seconds. Since the entire site is one `index.html` file, updating the site is as simple as pushing that one file.

---

## Updating Static Content

| What to change | Where |
|---------------|-------|
| Package prices | Edit the Packages section in `index.html` |
| Phone numbers | Search and replace in `index.html` |
| Email address | Search and replace in `index.html` |
| Photographer bio | Edit the About section in `index.html` |
| Photographer portrait | Replace `public/images/client.jpg` |
| Social share image | Replace `public/images/OG.jpg` (must be 1200×630px) |

---

## Client Quick Reference

> For the client — everything below is all you need to know day-to-day.

**To add a new portfolio photo:**
1. Upload the photo to Google Drive or Cloudinary
2. Open the Google Sheet
3. Add a new row — set `Category` to `Portfolio`, paste the image link into `ImageLink`
4. Done — the photo appears on the site immediately

**To add a new wedding film:**
1. Upload the video to YouTube
2. Open the Google Sheet
3. Add a new row — set `Category` to `Video`, paste the YouTube video ID into `ImageLink`
4. Done — the film appears in the carousel immediately

**To add a wedding story:**
1. Open the Google Sheet
2. Add a new row — set `Category` to `Story`, fill in `ImageLink`, `Tag`, `Title`, `Subtitle`
3. Done — the story card appears on the site immediately

**To remove any content:**
Simply delete the row from the Google Sheet.