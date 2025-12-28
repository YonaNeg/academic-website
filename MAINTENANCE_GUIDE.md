# Academic Website Maintenance Guide

**Your Live Site:** https://ydegefu-research.vercel.app
**GitHub Repo:** https://github.com/YonaNeg/academic-website

---

## Table of Contents
1. [Project Structure](#project-structure)
2. [How to Make Updates](#how-to-make-updates)
3. [Common Edits](#common-edits)
4. [Publishing Changes](#publishing-changes)
5. [Tech Stack Overview](#tech-stack-overview)
6. [Troubleshooting](#troubleshooting)
7. [Vercel Info](#vercel-info)

---

## Project Structure

```
academic-website/
├── src/
│   ├── layouts/
│   │   └── BaseLayout.astro          # Main layout (header, footer, nav)
│   └── pages/
│       ├── index.astro                # Home page
│       ├── about.astro                # About page
│       ├── research.astro             # Research page
│       ├── publications.astro         # Publications page
│       └── cv.astro                   # CV page
├── public/                            # Static files (images, PDFs, etc.)
├── package.json                       # Dependencies
└── astro.config.mjs                  # Astro configuration
```

### Key Files Explained

**`src/layouts/BaseLayout.astro`**
- Contains the navigation bar, header, and footer
- Defines the global dark terminal theme
- If you change your name here, it updates everywhere

**`src/pages/*.astro`**
- Each `.astro` file = one page on your website
- Contains both content (HTML-like) and styling (CSS)
- Top section (between `---`) is JavaScript/data
- Bottom section is the page content

---

## How to Make Updates

### Step 1: Open Your Project
```bash
cd /Users/yonatandegefu/Library/CloudStorage/Box-Box/academic-website
```

### Step 2: Edit Files
Use any text editor:
- **VS Code** (recommended): `code .`
- **Any text editor**: Open the `.astro` files directly

### Step 3: Test Locally (Optional but Recommended)
```bash
npm run dev
```
Then open http://localhost:4321 in your browser to preview changes.

Press `Ctrl+C` to stop the server when done.

### Step 4: Publish Changes (See [Publishing Changes](#publishing-changes))

---

## Common Edits

### 📝 Update Your Bio or Text

**File:** `src/pages/index.astro` (or any page)

Find the text you want to change and edit it:
```html
<p class="bio">
  Your current text here  <!-- Change this -->
</p>
```

### 📄 Add a New Publication

**File:** `src/pages/publications.astro`

Copy an existing publication block and modify:
```html
<div class="publication">
  <h3>Your Paper Title</h3>
  <p class="authors"><strong>Degefu YN</strong>, Co-authors</p>
  <p class="venue"><em>Journal Name</em>, Year</p>
  <p class="description">Brief description</p>
  <div class="pub-links">
    <a href="https://doi.org/..." class="pub-link" target="_blank">Paper</a>
  </div>
</div>
```

### 🎨 Change Colors

**File:** `src/layouts/BaseLayout.astro`

Find the color values and change them:
```css
/* Current terminal green theme */
#00ff41  /* Main green */
#1a1a1a  /* Dark background */
#0d0d0d  /* Darker sections */

/* Example: Change to blue theme */
#00ff41 → #00a8ff  /* Change all instances */
```

### 📧 Update Contact Info

**File:** `src/pages/index.astro`

Find the links section:
```html
<a href="mailto:njr7jk@virginia.edu" class="btn">Email</a>
<a href="https://scholar.google.com/..." class="btn btn-secondary">Google Scholar</a>
```

### 🏆 Add New Award

**File:** `src/pages/cv.astro`

Find the Awards section and add:
```html
<div class="cv-item">
  <div class="cv-main">
    <h3>Award Name</h3>
    <p class="institution">Organization</p>
  </div>
  <div class="cv-date">2025</div>
</div>
```

### 🖼️ Add Your Photo

1. Save your photo as `profile.jpg` in the `public/` folder
2. **File:** `src/pages/about.astro`
3. Replace the placeholder:
```html
<!-- Old: -->
<div class="placeholder-image">YND</div>

<!-- New: -->
<img src="/profile.jpg" alt="Yonatan Degefu" style="width: 200px; height: 200px; border-radius: 4px; border: 2px solid #00ff41;">
```

### 📎 Add PDF CV Download

1. Save your CV PDF as `cv.pdf` in the `public/` folder
2. The download button in `src/pages/cv.astro` will automatically work:
```html
<a href="/cv.pdf" class="download-btn" download>Download PDF</a>
```

---

## Publishing Changes

Every time you make changes, follow these steps to publish them:

```bash
# 1. Navigate to your project
cd /Users/yonatandegefu/Library/CloudStorage/Box-Box/academic-website

# 2. Save your changes to git
git add .

# 3. Describe what you changed
git commit -m "Updated publications with new paper"

# 4. Push to GitHub (this automatically deploys!)
git push
```

**Wait 30-60 seconds** and your site will automatically update at https://ydegefu-research.vercel.app!

### Common Commit Message Examples
```bash
git commit -m "Added new publication"
git commit -m "Updated bio on about page"
git commit -m "Added profile photo"
git commit -m "Updated CV with new award"
git commit -m "Fixed typo on research page"
```

---

## Tech Stack Overview

### What is Astro?
- A modern web framework for building fast websites
- Files end in `.astro` (similar to HTML but more powerful)
- Combines HTML, CSS, and JavaScript in one file

### Structure of an .astro File
```astro
---
// Top section: JavaScript/imports (between ----)
import BaseLayout from '../layouts/BaseLayout.astro';
const myData = "some data";
---

<!-- Middle section: HTML content -->
<BaseLayout title="Page Title">
  <h1>My Content</h1>
  <p>Text here</p>
</BaseLayout>

<style>
  /* Bottom section: CSS styling */
  h1 {
    color: #00ff41;
  }
</style>
```

### The Terminal Theme
Your site uses:
- **Monospace fonts**: JetBrains Mono, Fira Code, Consolas
- **Color scheme**:
  - Background: `#1a1a1a` (dark gray)
  - Text: `#e0e0e0` (light gray)
  - Accent: `#00ff41` (matrix green)
  - Borders: Green glow effects
- **Terminal elements**: `>`, `$`, `#`, `##`, `[`, `]` prefixes

---

## Troubleshooting

### "Changes aren't showing up on the live site"
1. Did you `git push`? Run: `git status` to check
2. Check Vercel dashboard: https://vercel.com/dashboard
3. Wait 60 seconds - deployments take time
4. Hard refresh your browser: `Cmd+Shift+R` (Mac) or `Ctrl+Shift+R` (Windows)

### "Git says there are conflicts"
```bash
# Get latest changes from GitHub
git pull

# If there are conflicts, you'll need to resolve them
# Then:
git add .
git commit -m "Resolved conflicts"
git push
```

### "I broke something!"
```bash
# See what changed
git status

# Undo uncommitted changes
git checkout -- filename.astro

# Restore to last working version
git reset --hard HEAD

# Then push to restore live site
git push --force
```

### "Local preview not working"
```bash
# Reinstall dependencies
npm install

# Try again
npm run dev
```

---

## Vercel Info

### Is Vercel Really Free?
**YES!** 100% free for projects like yours.

**Free Tier Includes:**
- Unlimited deployments
- Automatic HTTPS/SSL
- Global CDN (fast worldwide)
- 100GB bandwidth/month (way more than you'll use)
- Custom domains (if you buy one)
- No credit card required

**Your site will use ~1-5GB/month** (academic sites get very little traffic compared to the 100GB limit).

### Vercel Dashboard
- **URL:** https://vercel.com/dashboard
- See deployment status
- View analytics (visitors, page views)
- Manage domains
- Check build logs

### Deployment Process
1. You push to GitHub: `git push`
2. Vercel detects the change
3. Vercel builds your site (~20 seconds)
4. Vercel deploys to global CDN (~10 seconds)
5. Your site updates automatically!

### Build Status
Check if deployment succeeded:
- Green checkmark ✅ = Deployed successfully
- Red X ❌ = Build failed (check logs)
- Yellow spinner 🔄 = Building...

---

## Quick Reference Commands

```bash
# Navigate to project
cd /Users/yonatandegefu/Library/CloudStorage/Box-Box/academic-website

# Preview locally
npm run dev                    # Start server at localhost:4321
# Press Ctrl+C to stop

# Publish changes
git add .                      # Stage all changes
git commit -m "description"    # Save changes
git push                       # Deploy to live site

# Check status
git status                     # See what changed
git log                        # See commit history

# View your site
# Local: http://localhost:4321
# Live: https://ydegefu-research.vercel.app
# GitHub: https://github.com/YonaNeg/academic-website
```

---

## File Locations Quick Reference

| What to Update | File Location |
|---------------|--------------|
| Home page content | `src/pages/index.astro` |
| About page bio | `src/pages/about.astro` |
| Research areas | `src/pages/research.astro` |
| Publications | `src/pages/publications.astro` |
| CV | `src/pages/cv.astro` |
| Navigation links | `src/layouts/BaseLayout.astro` |
| Your name (appears everywhere) | `src/layouts/BaseLayout.astro` |
| Colors/theme | `src/layouts/BaseLayout.astro` |
| Add images/PDFs | Put in `public/` folder |

---

## Tips for Success

1. **Make small changes** - Edit one thing at a time, test, then publish
2. **Test locally first** - Run `npm run dev` to preview before publishing
3. **Commit often** - Better to have many small commits than one huge one
4. **Write good commit messages** - Future you will thank you!
5. **Keep backups** - GitHub is your backup, but you can also copy the folder

---

## Need Help?

- **Astro Docs:** https://docs.astro.build
- **Vercel Docs:** https://vercel.com/docs
- **Git Basics:** https://git-scm.com/doc
- **This file!** Re-read this guide whenever you need to make changes

---

## Adding New Pages (Advanced)

Want to add a blog or teaching page?

1. Create new file: `src/pages/blog.astro`
2. Copy structure from existing page
3. Add nav link in `src/layouts/BaseLayout.astro`:
```html
<li><a href="/blog">Blog</a></li>
```
4. Publish: `git add . && git commit -m "Added blog page" && git push`

---

**Remember:** You built this! Every update you make is just editing text files and running `git push`. You've got this! 💪

Last updated: December 28, 2025
