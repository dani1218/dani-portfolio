# Dani — Portfolio Website
## Deployment Guide & Project Structure

---

## 🚀 Quick Start (Single HTML File)

The portfolio is delivered as a single optimized `dani-portfolio.html` file.
Open it in any browser — no build step, no dependencies, no server needed.

```bash
# Simply open in browser
open dani-portfolio.html        # macOS
start dani-portfolio.html       # Windows
xdg-open dani-portfolio.html    # Linux
```

---

## 📁 Next.js Project Structure (Production Upgrade)

To convert to a full Next.js project for maximum performance and SEO:

```
dani-portfolio/
├── public/
│   ├── favicon.ico
│   ├── og-image.png              # Open Graph preview image
│   ├── cv-dani.pdf               # Downloadable CV
│   └── assets/
│       └── project-thumbnails/   # Project screenshots
│
├── src/
│   ├── app/
│   │   ├── layout.tsx            # Root layout + metadata
│   │   ├── page.tsx              # Main page (all sections)
│   │   └── globals.css           # CSS variables & resets
│   │
│   ├── components/
│   │   ├── layout/
│   │   │   ├── Navbar.tsx
│   │   │   ├── Footer.tsx
│   │   │   └── MobileMenu.tsx
│   │   │
│   │   ├── sections/
│   │   │   ├── Hero.tsx
│   │   │   ├── Stats.tsx
│   │   │   ├── About.tsx
│   │   │   ├── Skills.tsx
│   │   │   ├── Projects.tsx
│   │   │   ├── Experience.tsx
│   │   │   ├── Achievements.tsx
│   │   │   └── Contact.tsx
│   │   │
│   │   ├── ui/
│   │   │   ├── Cursor.tsx
│   │   │   ├── ScrollProgress.tsx
│   │   │   ├── Loader.tsx
│   │   │   ├── Toast.tsx
│   │   │   ├── SkillCard.tsx
│   │   │   ├── ProjectCard.tsx
│   │   │   └── AchievementCard.tsx
│   │   │
│   │   └── effects/
│   │       ├── BgMesh.tsx
│   │       ├── GridPattern.tsx
│   │       └── TypingAnimation.tsx
│   │
│   ├── data/
│   │   ├── skills.ts             # Skills array
│   │   ├── projects.ts           # Projects array
│   │   ├── experience.ts         # Timeline data
│   │   └── achievements.ts       # Achievements array
│   │
│   ├── hooks/
│   │   ├── useScrollReveal.ts    # Intersection Observer hook
│   │   ├── useTypingEffect.ts    # Typing animation hook
│   │   └── useCounterAnimation.ts
│   │
│   └── lib/
│       └── utils.ts              # Helper functions
│
├── .env.local                    # Environment variables
├── next.config.js                # Next.js config
├── tailwind.config.js            # Tailwind + custom colors
├── tsconfig.json
├── package.json
└── README.md
```

---

## 📦 Next.js Setup Commands

```bash
# 1. Create Next.js project
npx create-next-app@latest dani-portfolio \
  --typescript --tailwind --eslint --app --src-dir

cd dani-portfolio

# 2. Install dependencies
npm install framer-motion            # Animations
npm install @emailjs/browser         # Contact form emails
npm install react-intersection-observer  # Scroll reveals
npm install next-themes              # Dark/light mode toggle

# 3. Install dev dependencies
npm install -D @types/node

# 4. Run development server
npm run dev
```

---

## 🎨 Color Palette

```css
:root {
  /* Backgrounds */
  --bg-0:      #060608;    /* Deepest black */
  --bg-1:      #0d0d12;    /* Section alt bg */
  --bg-2:      #13131a;    /* Card bg */
  --bg-3:      #1a1a24;    /* Input bg */
  --bg-4:      #22222e;    /* Hover states */

  /* Accent Colors */
  --accent-1:  #7b61ff;    /* Purple — primary */
  --accent-2:  #00d4ff;    /* Cyan — secondary */
  --accent-3:  #ff6b6b;    /* Coral — tertiary */

  /* Text */
  --text-primary:    #f0f0f8;   /* Main content */
  --text-secondary:  #9090aa;   /* Supporting text */
  --text-muted:      #55556a;   /* Placeholders */

  /* Borders */
  --border:         rgba(255,255,255,0.06);
  --border-hover:   rgba(255,255,255,0.12);
}
```

---

## 🚀 Vercel Deployment

### Method 1: Drag & Drop (HTML file)
1. Go to [vercel.com](https://vercel.com) → Sign up / Log in
2. Click **"Add New Project"**
3. Drag `dani-portfolio.html` onto the upload zone
4. Click **Deploy** — live in 30 seconds ✅

### Method 2: GitHub + Vercel (Next.js)
```bash
# Push to GitHub
git init
git add .
git commit -m "Initial portfolio commit"
git branch -M main
git remote add origin https://github.com/yourusername/dani-portfolio.git
git push -u origin main

# Deploy on Vercel
# 1. Go to vercel.com → "New Project"
# 2. Import your GitHub repository
# 3. Framework: Next.js (auto-detected)
# 4. Click Deploy
# ✅ Auto-deploys on every push to main
```

### Method 3: Vercel CLI
```bash
npm i -g vercel
vercel login
vercel                # First deploy
vercel --prod         # Production deploy
```

---

## 🌐 Custom Domain Setup

```
1. Buy domain (e.g., dani.dev) from Namecheap / GoDaddy / Cloudflare
2. In Vercel Dashboard → Project → Settings → Domains
3. Add your domain → Follow DNS instructions
4. Add CNAME record:
   Name: www    Value: cname.vercel-dns.com
   Name: @      Value: 76.76.19.61 (Vercel IP)
5. Wait 5–15 min for propagation ✅
```

---

## ✅ Customization Checklist

Before going live, update these in `dani-portfolio.html`:

- [ ] Replace `dani@example.com` with your real email
- [ ] Replace GitHub/LinkedIn/Instagram URLs with your profiles
- [ ] Add your actual CV PDF (update Download CV button href)
- [ ] Update project GitHub links to your real repos
- [ ] Add project live demo links
- [ ] Update stats counters with real numbers
- [ ] Upload your photo and replace the avatar placeholder
- [ ] Update location in contact section
- [ ] Update education details (university name, GPA)

---

## ⚡ Performance Tips

- **Images**: Use `.webp` format, compress with [squoosh.app](https://squoosh.app)
- **Fonts**: Already using `font-display: swap` via Google Fonts
- **Lazy loading**: Add `loading="lazy"` to project thumbnail images
- **EmailJS**: Set up [emailjs.com](https://emailjs.com) for the contact form
- **Analytics**: Add Vercel Analytics or Google Analytics via `<script>`

---

## 📧 Contact Form (EmailJS Setup)

```javascript
// Install: npm install @emailjs/browser
import emailjs from '@emailjs/browser';

emailjs.send(
  'YOUR_SERVICE_ID',
  'YOUR_TEMPLATE_ID',
  { from_name: name, reply_to: email, message: message },
  'YOUR_PUBLIC_KEY'
);
```

Get keys free at [emailjs.com](https://emailjs.com) — 200 emails/month free.

---

*Built with ❤️ for Dani — CS Student & ML Engineer*
