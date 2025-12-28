# Quick Reference Cheat Sheet

## 🚀 Update & Publish Workflow

```bash
# 1. Navigate to project
cd /Users/yonatandegefu/Library/CloudStorage/Box-Box/academic-website

# 2. (Optional) Test locally
npm run dev
# Open http://localhost:4321 in browser
# Press Ctrl+C to stop

# 3. Publish changes
git add .
git commit -m "Brief description of what you changed"
git push

# Wait 30-60 seconds → Live at https://ydegefu-research.vercel.app
```

---

## 📁 Where to Edit What

| To Update... | Edit This File |
|-------------|----------------|
| 🏠 Home page | `src/pages/index.astro` |
| 👤 About page | `src/pages/about.astro` |
| 🔬 Research | `src/pages/research.astro` |
| 📚 Publications | `src/pages/publications.astro` |
| 📄 CV | `src/pages/cv.astro` |
| 🎨 Colors/Theme | `src/layouts/BaseLayout.astro` |
| 🔗 Navigation | `src/layouts/BaseLayout.astro` |

---

## 🎨 Terminal Theme Colors

```css
#00ff41  /* Matrix green (main accent) */
#1a1a1a  /* Dark background */
#0d0d0d  /* Darker cards/sections */
#e0e0e0  /* Light text */
#a0a0a0  /* Secondary text */
```

---

## 🔗 Important Links

- **Live Site:** https://ydegefu-research.vercel.app
- **GitHub:** https://github.com/YonaNeg/academic-website
- **Vercel Dashboard:** https://vercel.com/dashboard
- **Local Preview:** http://localhost:4321 (when running `npm run dev`)

---

## ✅ Common Tasks

### Add a Publication
Edit `src/pages/publications.astro`, copy this template:
```html
<div class="publication">
  <h3>Paper Title</h3>
  <p class="authors"><strong>Degefu YN</strong>, Co-authors</p>
  <p class="venue"><em>Journal Name</em>, Year</p>
  <div class="pub-links">
    <a href="https://doi.org/..." class="pub-link">Paper</a>
  </div>
</div>
```

### Add Your Photo
1. Save photo as `profile.jpg` in `public/` folder
2. Edit `src/pages/about.astro`, replace:
```html
<div class="placeholder-image">YND</div>
```
With:
```html
<img src="/profile.jpg" alt="Yonatan Degefu"
     style="width:200px; height:200px; border-radius:4px; border:2px solid #00ff41;">
```

### Update Your Email/Links
Edit `src/pages/index.astro`, find:
```html
<a href="mailto:your.email@domain.edu" class="btn">Email</a>
```

---

## 🆘 Emergency Fixes

### Undo Last Changes (Not Published Yet)
```bash
git checkout -- filename.astro
```

### Restore to Last Working Version
```bash
git reset --hard HEAD
git push --force
```

### Check What Changed
```bash
git status
git diff
```

---

## 💡 Pro Tips

1. ✅ Always test locally first: `npm run dev`
2. ✅ Make small, frequent commits
3. ✅ Write clear commit messages
4. ✅ Check Vercel dashboard if deploy fails
5. ✅ Hard refresh browser: `Cmd+Shift+R` (Mac) or `Ctrl+Shift+R` (Windows)

---

## 💰 Vercel is FREE ✅

- ✅ Unlimited deployments
- ✅ 100GB bandwidth/month (you'll use ~1-5GB)
- ✅ Automatic HTTPS
- ✅ No credit card needed
- ✅ Custom domains supported

---

**For detailed explanations, see MAINTENANCE_GUIDE.md**
