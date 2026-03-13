# Magic Math Master — Jekyll + Sass Site

## Project structure

```
jekyll-site/
├── _config.yml              # Site config, URL, Sass settings
├── _layouts/
│   └── default.html         # Single master layout (nav + footer)
├── _includes/
│   ├── head.html            # <head> meta, CSS link
│   ├── nav.html             # Sticky topbar + language switcher
│   └── footer.html          # Footer with copyright + links
│
├── _sass/
│   ├── base/
│   │   ├── _variables.scss  # ★ All design tokens (colours, spacing, breakpoints)
│   │   ├── _reset.scss      # Box-sizing, body background, container
│   │   ├── _typography.scss # Headings, gradient text, emoji fix
│   │   └── _utilities.scss  # Overflow fixes, helpers
│   ├── layout/
│   │   ├── _topbar.scss     # Nav bar + responsive wrapping
│   │   ├── _hero.scss       # All hero variants
│   │   ├── _footer.scss     # Footer
│   │   └── _grid.scss       # .grid, .two-grid
│   ├── components/
│   │   ├── _buttons.scss    # All .btn variants
│   │   ├── _cards.scss      # .card, .mini-card, .diff-card, .club-summary
│   │   ├── _accordion.scss  # details.acc / summary.acc-sum
│   │   ├── _badges.scss     # .badge, .club-badge
│   │   ├── _forms.scss      # .form-group, input, select, textarea
│   │   ├── _lang-switcher.scss # Language dropdown + flags
│   │   ├── _quicklinks.scss # .ql-grid / .ql-btn
│   │   └── _modal.scss      # Thank-you modal
│   └── pages/
│       ├── _home.scss       # .h2-center, .sub-center
│       ├── _programs.scss   # Programs-specific styles
│       ├── _pricing.scss    # Pricing-specific styles
│       └── ...              # One file per page for overrides
│
├── assets/
│   ├── css/main.scss        # Sass entry point (imports all partials)
│   ├── js/
│   │   ├── script.js        # Nav active state + language switcher
│   │   └── nav-active.js    # Nav highlight helper
│   └── images/              # All images (logo, banners, flags, etc.)
│
├── index.html               # Home page
├── about.html
├── programs.html
├── pricing.html
├── mathclub.html
├── philosophy.html
├── policies.html
├── contact.html
├── enquiry.html
├── register.html
├── demo/
│   ├── index.html
│   ├── 3-6/index.html
│   ├── 7-10/index.html
│   └── 11-12/index.html
├── vi/                      # Vietnamese translations
│   ├── index.html
│   └── ...
├── favicon.ico / favicon.png
└── CNAME                    # magicmathmaster.com.au
```

---

## Setup

### 1. Install Ruby + Jekyll

```bash
# macOS (with Homebrew)
brew install ruby
gem install jekyll bundler

# Ubuntu/Debian
sudo apt install ruby-full build-essential
gem install jekyll bundler
```

### 2. Install dependencies

```bash
cd jekyll-site
bundle install
```

### 3. Run locally

```bash
bundle exec jekyll serve
# → http://localhost:4000
```

### 4. Build for production

```bash
bundle exec jekyll build
# Output goes to _site/
```

---

## Making changes

### Change a colour or spacing token
Edit `_sass/base/_variables.scss` — one change updates the entire site.

### Edit navigation links
Edit `_includes/nav.html` — one file, updates all pages.

### Edit footer
Edit `_includes/footer.html`.

### Add a new page
1. Create `new-page.html` with front matter:
```yaml
---
layout: default
title: "Page Title | Magic Math Master"
description: "Page description."
---
```
2. Add link to `_includes/nav.html`.
3. Add any page-specific Sass to `_sass/pages/_new-page.scss` and import it in `assets/css/main.scss`.

### Add a Vietnamese translation
Create `vi/new-page.html` with `lang: vi` in front matter.

---

## Deployment (GitHub Pages)

```bash
# Push to GitHub — Pages will build automatically
git add .
git commit -m "Update site"
git push origin main
```

Make sure `CNAME` file contains: `magicmathmaster.com.au`
