# YEERS Case Studies Website

## File Structure

```
yeers-site/
├── index.html                          ← Homepage (case study listing)
├── README.md
├── assets/
│   ├── css/
│   │   └── style.css                  ← All styles
│   ├── js/
│   │   └── main.js                    ← Filter + scroll reveal
│   └── images/
│       ├── solar-hull.jpg             ← Card thumbnail
│       ├── solar-hull-roof.jpg        ← Gallery image
│       ├── solar-hull-inverter.jpg    ← Gallery image
│       ├── solar-hull-battery.jpg     ← Gallery image
│       ├── heatpump-york.jpg
│       ├── warm-homes-goole.jpg
│       ├── ev-leeds.jpg
│       ├── commercial-beverley.jpg
│       └── heatpump-doncaster.jpg
└── case-studies/
    ├── solar-battery-hull.html        ← Full case study (done)
    ├── heatpump-york.html             ← Add next
    ├── warm-homes-goole.html
    ├── ev-charger-leeds.html
    ├── commercial-solar-beverley.html
    └── heatpump-battery-doncaster.html
```

---

## Deploying to GitHub + Cloudflare Pages

### Step 1 — Push to GitHub

If you haven't already created the repo:
```bash
git init
git add .
git commit -m "Initial YEERS case studies site"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/yeers-case-studies.git
git push -u origin main
```

Or simply drag-and-drop all files into your GitHub repo via the browser.

### Step 2 — Connect Cloudflare Pages

1. Go to **Cloudflare Dashboard → Pages → Create a project**
2. Click **Connect to Git → Authorize GitHub**
3. Select your `yeers-case-studies` repository
4. Build settings:
   - **Framework preset**: None
   - **Build command**: *(leave blank)*
   - **Build output directory**: `/` (or leave blank)
5. Click **Save and Deploy**

Cloudflare will give you a `*.pages.dev` URL within 30 seconds.

### Step 3 — Connect your domain

1. In Cloudflare Pages → your project → **Custom Domains**
2. Click **Set up a custom domain**
3. Enter your domain (e.g. `yeers.co.uk` or `projects.yeers.co.uk`)
4. Cloudflare will auto-configure DNS since your domain is already on Cloudflare

**After this, every time you push to GitHub, the site updates automatically.**

---

## Adding Photos

Drop real project photos into `/assets/images/`. Name them to match the `src` attributes in the HTML. Images will automatically replace the placeholder backgrounds.

**Recommended sizes:**
- Card thumbnails: 800×450px (16:9)
- Hero images: 1600×900px minimum
- Gallery images: 1200×900px

**Free AI image generators for placeholder/filler images:**
- https://firefly.adobe.com — best quality, commercially safe
- https://ideogram.ai — good for text overlays
- https://designer.microsoft.com — free, quick

---

## Adding Videos

In each case study HTML, find the video section:

```html
<!-- Uncomment and replace VIDEO_ID when ready:
<iframe src="https://www.youtube.com/embed/VIDEO_ID" allowfullscreen loading="lazy"></iframe>
-->
```

1. Upload your video to YouTube (can be unlisted)
2. Copy the video ID from the URL (e.g. `dQw4w9WgXcQ`)
3. Replace `VIDEO_ID` in the HTML and remove the comment tags

---

## Adding a New Case Study

1. Copy `case-studies/solar-battery-hull.html` to a new file
2. Update: title, meta description, hero image, stats, content, specs sidebar
3. Add a new card to `index.html` with matching `data-category` tags
4. Add the image to `/assets/images/`
5. Push to GitHub — live in 30 seconds

---

## Category Tags (for filtering)

Use these in the card's `data-category` attribute and in `<span class="tag">` elements:

| Category | data-category value | tag class |
|---|---|---|
| Solar | `solar` | `tag--solar` |
| Heat Pumps | `heatpump` | `tag--heatpump` |
| Battery Storage | `battery` | `tag--battery` |
| EV Charging | `ev` | `tag--ev` |
| Warm Homes | `warmhomes` | `tag--warmhomes` |
| Electrical | `electrical` | `tag--electrical` |

Multiple categories: `data-category="solar battery"` (space separated)
