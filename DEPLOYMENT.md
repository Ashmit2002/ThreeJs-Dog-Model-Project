# 🚀 Deployment Guide

## Quick Deploy Options

### Option 1: Vercel (Recommended - Easiest)

1. **Push to GitHub:**
```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR_USERNAME/threejs-portfolio.git
git push -u origin main
```

2. **Deploy to Vercel:**
- Go to [vercel.com](https://vercel.com)
- Click "New Project"
- Import your GitHub repository
- Vercel auto-detects Vite config
- Click "Deploy"
- Done! Your site is live at `https://your-project.vercel.app`

**Update README with your link:**
```bash
# Replace YOUR_DEPLOYED_LINK_HERE in README.md with your Vercel URL
```

---

### Option 2: Netlify

1. **Build the project:**
```bash
npm run build
```

2. **Deploy via Netlify CLI:**
```bash
npm install -g netlify-cli
netlify login
netlify init
netlify deploy --prod
```

Or drag and drop the `dist` folder to [netlify.com/drop](https://app.netlify.com/drop)

---

### Option 3: GitHub Pages

1. **Install gh-pages:**
```bash
npm install --save-dev gh-pages
```

2. **Update vite.config.js:**
```javascript
export default defineConfig({
  plugins: [react()],
  base: '/threejs-portfolio/', // Your repo name
})
```

3. **Add deploy scripts to package.json:**
```json
{
  "scripts": {
    "predeploy": "npm run build",
    "deploy": "gh-pages -d dist"
  }
}
```

4. **Deploy:**
```bash
npm run deploy
```

Your site will be at: `https://YOUR_USERNAME.github.io/threejs-portfolio/`

---

## 📋 Pre-Deployment Checklist

- [ ] Remove `markers: true` from ScrollTrigger (line 155 in Dog.jsx)
- [ ] Test build locally: `npm run build && npm run preview`
- [ ] Check console for errors
- [ ] Test on different browsers (Chrome, Firefox, Safari)
- [ ] Optimize images if needed
- [ ] Update README with actual deployment link
- [ ] Add your personal info to README (name, GitHub, LinkedIn)

---

## 🔧 Important: Remove Debug Markers

Before deploying, remove the debug markers from Dog.jsx:

```javascript
// In Dog.jsx, line ~155, change this:
scrollTrigger: {
  trigger: "#section-1",
  endTrigger: "#section-4",
  start: "top top",
  end: "bottom bottom",
  markers: true,  // ❌ REMOVE THIS LINE
  scrub: true,
},

// To this:
scrollTrigger: {
  trigger: "#section-1",
  endTrigger: "#section-4",
  start: "top top",
  end: "bottom bottom",
  scrub: true,
},
```

---

## 📝 Post-Deployment Steps

1. **Update README.md:**
   - Replace `YOUR_DEPLOYED_LINK_HERE` with actual URL
   - Add your name and social links
   - Optional: Add a screenshot/GIF

2. **Test the deployed site:**
   - Check all 7 project hovers work
   - Verify scroll animation is smooth
   - Test on mobile (if responsive features added)

3. **Share:**
   - Add to your LinkedIn portfolio
   - Tweet about it with #ThreeJS #WebGL
   - Share in web dev communities

---

## 🎨 Optional: Add Preview Image

Create a preview GIF or image:

1. **Record screen:**
   - Use [ScreenToGif](https://www.screentogif.com/) (Windows)
   - Use [Kap](https://getkap.co/) (Mac)
   - Use [Peek](https://github.com/phw/peek) (Linux)

2. **Save as `preview.gif` in project root**

3. **Update README:**
```markdown
![Project Preview](./preview.gif)
```

---

## 📊 Analytics (Optional)

Add Google Analytics to track visitors:

1. **Create GA4 property** at [analytics.google.com](https://analytics.google.com)

2. **Add to `index.html`:**
```html
<head>
  <!-- ... -->
  <script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
  <script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());
    gtag('config', 'G-XXXXXXXXXX');
  </script>
</head>
```

---

## 🐛 Troubleshooting

### Build fails with "out of memory"
```bash
# Increase Node memory
NODE_OPTIONS=--max-old-space-size=4096 npm run build
```

### Assets not loading (404 errors)
- Check `vite.config.js` base path
- Ensure files are in `/public` folder
- Verify file names match (case-sensitive on Linux servers)

### Performance issues
- Check Network tab for large files
- Compress textures further
- Consider lazy loading textures

---

## ✅ Final Command Sequence

```bash
# 1. Fix the markers issue
# (Edit Dog.jsx manually)

# 2. Test build locally
npm run build
npm run preview

# 3. Commit changes
git add .
git commit -m "Ready for deployment"
git push

# 4. Deploy to Vercel (easiest)
# Go to vercel.com and import your repo

# 5. Update README with deployed URL
# (Edit README.md manually)

# Done! 🎉
```

---

**Recommended:** Use Vercel for the easiest deployment experience with automatic SSL, CDN, and continuous deployment.

**Your deployed link will be:** `https://your-project-name.vercel.app`
