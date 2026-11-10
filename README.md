# AURA — Modern E-Commerce Frontend

An ultra-modern, responsive e-commerce web application frontend built with clean semantic HTML5, modern CSS3 (Custom Properties, Flexbox, CSS Grid, Glassmorphism, animations), and vanilla JavaScript (ES6+ modular architecture).

---

## ⚡ Cloudflare Deployment Guide

You can deploy this site to **Cloudflare Pages** for free with a global CDN, free SSL certificate, and custom domain support in under 2 minutes.

### Option 1: Direct Drag & Drop Upload (Fastest — 30 Seconds)
1. Go to [Cloudflare Dashboard](https://dash.cloudflare.com/) and log in (or sign up for free).
2. On the left sidebar, click **Compute (Workers & Pages)** &rarr; **Create application**.
3. Select the **Pages** tab and click **Upload assets**.
4. Set a Project Name (e.g. `aura-store`).
5. Drag and drop the ready-made archive **`cloudflare-pages-deploy.zip`** (located in this project root) or drag the whole project folder.
6. Click **Deploy site**.
7. Your site is instantly live at `https://aura-store.pages.dev`!

---

### Option 2: Connect via GitHub / GitLab (Continuous Deployment)
1. Create a new repository on your GitHub or GitLab account.
2. Link your local project and push your code:
   ```bash
   git remote add origin https://github.com/<your-username>/<your-repo-name>.git
   git branch -M main
   git push -u origin main
   ```
3. In the [Cloudflare Dashboard](https://dash.cloudflare.com/), go to **Workers & Pages** &rarr; **Create application** &rarr; **Pages** &rarr; **Connect to Git**.
4. Select your repository.
5. In **Build Settings**:
   - **Framework preset**: `None`
   - **Build command**: *(leave blank)*
   - **Build output directory**: `/` (or leave blank)
6. Click **Save and Deploy**. Every future `git push` will automatically trigger a new deployment.

---

## 📊 Google Analytics 4 (GA4) Setup & Live Dashboard

This website is pre-configured with **Google Analytics 4 (GA4)** and tracks standard e-commerce events out of the box (`page_view`, `view_item`, `add_to_cart`, `remove_from_cart`, `begin_checkout`, `purchase`, `apply_coupon`).

### Step 1: Get Your GA4 Measurement ID
1. Go to [Google Analytics](https://analytics.google.com/) and sign in with your Google account.
2. Click **Admin** (gear icon at bottom-left) &rarr; **Data Streams**.
3. Select your **Web stream** (or click **Add stream** &rarr; **Web**, enter your website URL like `https://aura-store.pages.dev`).
4. Copy your **Measurement ID** (it looks like `G-XXXXXXXXXX`).

### Step 2: Add Your ID to `index.html`
Open `index.html` and replace `G-XXXXXXXXXX` in lines 10 & 17 with your real Measurement ID:

```html
<!-- Google Analytics 4 (GA4) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-YOUR_ACTUAL_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  window.GA_MEASUREMENT_ID = 'G-YOUR_ACTUAL_ID';
  gtag('config', window.GA_MEASUREMENT_ID, {
    send_page_view: true
  });
</script>
```

### Step 3: View Real-Time Analytics
1. Open your deployed website or run it locally.
2. Go to your [Google Analytics](https://analytics.google.com/) account.
3. In the left navigation, click **Reports** &rarr; **Realtime**.
4. Within 10 to 30 seconds, you will see:
   - **Active Users Right Now**: Shows your current visit and location on the live world map.
   - **Event Count by Event Name**:
     - `page_view`: Triggered when visitors browse.
     - `view_item`: Triggered when an item modal is opened.
     - `add_to_cart`: Triggered when items are added to the bag.
     - `remove_from_cart`: Triggered when items are removed.
     - `begin_checkout`: Triggered when the checkout drawer is opened.
     - `purchase`: Triggered when an order is completed.
     - `apply_coupon`: Triggered when promo codes (`AURA10`, etc.) are used.

---

## ✨ Features Overview

- **Interactive Product Inspection**: High-resolution image galleries, thumbnail previews, color swatches, size selectors, live stock counter, and specs tabs.
- **Cart Drawer**: Slide-out cart displaying selected items with thumbnails, variants, quantity controls, and free shipping progress meter.
- **Promo Code Engine**: Test with codes `AURA10` (10% off), `SAVE20` (20% off), or `VIP30` (30% off).
- **Search & Filtering**: Real-time keyword search, category pills, price slider, and in-stock toggles.
- **Wishlist & Checkout**: Heart toggle wishlist drawer and multi-step simulated checkout with confirmation receipt.
- **Theme**: Dark and Light mode toggler with persistent localStorage settings.

---

## 📁 File Structure

```
Project/
├── index.html                   # Main semantic structure & GA4 tracking tags
├── _headers                     # Cloudflare Pages security & caching headers
├── _redirects                   # Cloudflare Pages SPA rewrite rules
├── cloudflare-pages-deploy.zip  # Ready-to-upload zip for Cloudflare Pages
├── css/
│   └── style.css                # Design system, CSS variables, dark/light theme
├── js/
│   ├── products.js              # Catalog dataset with specs, reviews, and images
│   └── app.js                   # Reactive state, cart, wishlist, & GA4 event triggers
└── README.md                    # Deployment & analytics instructions
```
