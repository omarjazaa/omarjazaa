# 🛡️ Cybersecurity Portfolio — README

A dark-themed, hacker-aesthetic personal portfolio website for security engineers and penetration testers. Built with pure **HTML, CSS, and Vanilla JavaScript**.

---

## 🚀 Tech Stack

| Layer | Technology |
|-------|-----------|
| Markup | HTML5 |
| Styling | CSS3 (Custom Properties, Grid, Flexbox, Animations) |
| Logic | Vanilla JavaScript (ES6+) |
| Fonts | Google Fonts — Orbitron, Rajdhani, JetBrains Mono |
| 3D (optional) | Three.js r128 (background canvas) |

---

## 🎨 Design Tokens

The entire design is driven by CSS custom properties defined in `:root`:

| Variable | Value | Usage |
|----------|-------|-------|
| `--bg-primary` | `#0a0a0f` | Main background |
| `--bg-secondary` | `#12121a` | Footer, secondary areas |
| `--bg-card` | `#1a1a25` | Card backgrounds |
| `--accent-cyan` | `#00f5ff` | Primary accent, headings, borders |
| `--accent-green` | `#00ff88` | Success, highlights |
| `--accent-purple` | `#bf00ff` | Secondary accent, keywords |
| `--accent-orange` | `#ff6b35` | Code variables |
| `--font-heading` | Orbitron | All headings & titles |
| `--font-body` | Rajdhani | Body text, paragraphs |
| `--font-code` | JetBrains Mono | Code blocks |

---

## 📁 Project Structure

```
portfolio/
├── index.html          # Single HTML file with all sections
├── assets/
│   ├── css/
│   │   └── style.css   # All styles (or embedded in <style> tag)
│   ├── js/
│   │   └── main.js     # All JavaScript logic
│   └── images/
│       ├── profile.jpg # Your profile photo (recommended: 400×400px)
│       └── projects/   # Project screenshots
├── favicon.svg         # SVG favicon
└── README.md
```

---

## 🧩 Sections

| Section | Description |
|---------|-------------|
| **Navbar** | Fixed, glassmorphism, scroll-aware, mobile hamburger |
| **Hero** | Full-viewport, typing animation, rotating profile rings |
| **About** | Bio + stats + interactive code block |
| **Skills** | Hover-reveal cards with tool tags |
| **Experience** | Vertical timeline with pulse animations |
| **Certificates** | Grid cards with gradient badges |
| **Education** | Cards + language proficiency |
| **Tools** | Pill tags with hover fill effect |
| **Projects** | Cards with image overlay + shimmer border |
| **Contact** | Info cards + social links |
| **Footer** | Logo, social icons, copyright |

---

## ⚙️ JavaScript Features

### Typing Animation
```javascript
// Cycles through role titles with typewriter effect
const roles = ["Security Engineer", "Penetration Tester", "CTF Player"];
// Types character by character, pauses, then erases
```

### Scroll Reveal (IntersectionObserver)
```javascript
const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.classList.add('animate-in');
    }
  });
}, { threshold: 0.1 });
```

### Navbar Scroll State
```javascript
window.addEventListener('scroll', () => {
  navbar.classList.toggle('scrolled', window.scrollY > 50);
  scrollToTop.classList.toggle('visible', window.scrollY > 300);
});
```

### Mobile Menu
```javascript
menuToggle.addEventListener('click', () => {
  menuToggle.classList.toggle('active');
  navLinks.classList.toggle('active');
  menuOverlay.classList.toggle('active');
});
```

---

## 🖼️ CSS Techniques Used

### Glassmorphism Cards
```css
.card {
  background: rgba(255, 255, 255, 0.05);
  border: 1px solid rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px);
}
```

### Shimmer Gradient Border (mask trick)
```css
.card::after {
  content: "";
  background: linear-gradient(135deg, cyan, transparent, purple);
  position: absolute;
  inset: -1px;
  border-radius: inherit;
  padding: 1px;
  -webkit-mask: linear-gradient(#000 0 0) content-box,
                linear-gradient(#000 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  opacity: 0;
  transition: opacity 0.4s;
}
.card:hover::after { opacity: 1; }
```

### Shimmer Name Animation
```css
@keyframes shimmer {
  0%, 100% { background-position: 0%; }
  50% { background-position: 100%; }
}
.name {
  background: linear-gradient(135deg, #fff, #00f5ff, #bf00ff);
  background-size: 200%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: shimmer 3s infinite;
}
```

### Rotating Profile Rings
```css
.profile-ring {
  border: 2px solid transparent;
  background: linear-gradient(var(--bg-primary), var(--bg-primary)) padding-box,
              var(--gradient-cyan) border-box;
  animation: rotate 10s linear infinite;
}
@keyframes rotate {
  to { transform: translate(-50%, -50%) rotate(360deg); }
}
```

---

## 📱 Responsive Design

```
Desktop (>1024px)  → 2-column layouts, full animations
Tablet (≤1024px)   → 1-column layouts, stacked sections  
Mobile (≤768px)    → Hamburger menu, reduced sizes
Small (≤480px)     → Full-width buttons, compact padding
```

---

## ♿ Accessibility

- All interactive elements are keyboard-navigable
- `prefers-reduced-motion` disables all animations
- Focus-visible styles: `2px solid #00f5ff`
- Semantic HTML (`<nav>`, `<main>`, `<section>`, `<footer>`)
- Alt text on all images

---

## 🔧 Customization Guide

### 1. Change Colors
Edit the CSS variables in `:root` inside `style.css`

### 2. Update Content
Search for placeholder text in `index.html`:
- `YOUR_NAME` → your full name
- `YOUR_ROLE` → your job title
- `YOUR_EMAIL` → your email
- `YOUR_GITHUB` → your GitHub URL
- `YOUR_LINKEDIN` → your LinkedIn URL

### 3. Add Profile Photo
Replace `assets/images/profile.jpg` with your photo.
Recommended: **square image, minimum 400×400px**

### 4. Add Projects
Duplicate a `.project-card` block and update:
- Project image, title, description
- Tech tags
- GitHub link

### 5. Update Typing Roles
Find the `roles` array in `main.js` and update:
```javascript
const roles = [
  "Security Engineer",
  "Penetration Tester", 
  "Your Custom Role"
];
```

---

## 🌐 Deployment

### Option 1: Vercel (Recommended)
```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel
```

### Option 2: Netlify
Drag and drop the project folder to [netlify.com/drop](https://netlify.com/drop)

### Option 3: GitHub Pages
```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/USERNAME/portfolio
git push -u origin main
# Enable GitHub Pages in repo Settings → Pages
```

---

## 📄 License

MIT License — free to use and modify for personal portfolios.

---

## 🙏 Credits

Design inspired by modern cybersecurity portfolio aesthetics.
Fonts by [Google Fonts](https://fonts.google.com).
