# DOA GLOBAL BRIDGE — Website

A complete, responsive website for DOA GLOBAL BRIDGE, ready to publish on **GitHub Pages** for free. No build tools, no server, no monthly hosting bill — just plain HTML, CSS and JavaScript.

**Pages:** Home · About · Products · Gallery · Contact · Admin
**Built in:** plain HTML/CSS/JS (works on any static host, GitHub Pages included)

---

## 1. See it before you publish

Because browsers block some file-loading tricks when you just double-click an HTML file, the easiest way to preview the whole site locally is a tiny local server:

```bash
cd doa-global-bridge
python3 -m http.server 8000
```

Then open **http://localhost:8000** in your browser. (Node users can use `npx serve` instead.)

You can also just double-click `index.html` — it will work, but always test the real thing with a local server before you judge it.

---

## 2. Publish it on GitHub Pages (free hosting)

1. Create a new repository on GitHub (e.g. `doa-global-bridge`).
2. Upload **everything inside this folder** to the repository — `index.html` must sit at the top level of the repo (not inside a subfolder).
3. In the repo, go to **Settings → Pages**.
4. Under "Build and deployment", set **Source: Deploy from a branch**, branch **main**, folder **/ (root)**. Save.
5. GitHub gives you a live link within a minute or two, usually:
   `https://your-username.github.io/doa-global-bridge/`
6. Optional: connect a custom domain (e.g. `doaglobalbridge.com`) under the same Pages settings.

That's it — no build step, no npm install, nothing to configure.

---

## 3. Adding, editing or removing products (no coding needed)

Go to **`your-site-url/admin.html`**.

- **Default password:** `doa2026admin` — change this before you publish (see below).
- Fill in the product form and click **Save Product** — it previews instantly on your own browser's Products page.
- Add a photo either by **uploading it from your device** (it gets embedded directly into the product data — no separate image file to manage) or by pasting an **image URL**.
- When you're happy with your changes, click **"Download products-data.js"**. This saves a file to your computer.
- In your GitHub repository, open the `js` folder, upload the downloaded file, and let it **replace** the existing `products-data.js`, then commit.
- GitHub Pages redeploys automatically — your changes are live for every visitor within a minute or two.

**Why the extra step?** GitHub Pages is a *static* host — it has no live database. The Admin page can't silently save to your GitHub repo on its own, so it hands you a ready-made file instead. This is completely normal for a free, no-monthly-cost site like this one. (If you'd rather have one-click publishing with no download/upload step, look into a static-site CMS such as **Decap CMS**, or a small backend — either is a reasonable next upgrade later.)

### Changing the admin password
Open `js/admin.js` and edit this line near the top:
```js
const ADMIN_PASSWORD = "doa2026admin";
```
Note: this is a simple, convenient lock — not bank-level security, since anyone can view a website's source code. Don't store anything truly sensitive behind it.

### Editing products by hand instead
You can also open `js/products-data.js` directly and edit the list — every product is a plain block like:
```js
{
  id: "adaeze-wrap-dress",
  name: "Adaeze Wrap Dress",
  category: "Womenswear",
  price: 450,
  featured: true,
  image: "images/products/adaeze-wrap-dress.svg",
  description: "Hand-dyed batik wrap dress..."
}
```
Copy a block, change the details, give it a unique `id`, and add your photo to `images/products/`.

---

## 4. About the product photos

Every photo on this site right now is a **placeholder graphic** in your brand colours (gold hanger mark on indigo/rust/teal), not a real product photo — that includes the hero background, the "About" illustration, the gallery, and every product card. They're there so the site looks complete and on-brand out of the box.

**Replace them with real photography before you launch:** add your photos to `images/products/` (and `images/gallery/` for the lookbook), then update the `image` field for each product in `js/products-data.js`, or just use the Admin panel's photo upload.

---

## 5. WhatsApp, Call, and Contact form

- The number used everywhere (floating buttons, header, footer, "Order" buttons, contact form) is **+233 50 095 8763**.
- To change it, open `js/main.js` and edit these two lines near the top:
  ```js
  const WHATSAPP_NUMBER = "233500958763"; // digits only, country code first, no +
  const PHONE_NUMBER = "+233500958763";   // used for the Call Now / tel: links
  ```
- The Contact page form doesn't need any backend or email service — clicking **"Send via WhatsApp"** opens WhatsApp with the customer's name, phone, email and message already filled in, ready to send to you.

---

## 6. Other quick edits

- **Email address / studio hours / social links:** search for `hello@doaglobalbridge.com` and the social `href="#"` links across the HTML files and update them.
- **Map location:** the Contact page embeds a plain Google Maps view centred on "Drobo, Ghana" — edit the `src` on the `<iframe>` in `contact.html` to change the location, e.g. `https://www.google.com/maps?q=YOUR+ADDRESS&output=embed`.
- **Colours and fonts:** all defined once at the top of `css/style.css` under `:root`, e.g. `--indigo`, `--gold`, `--rust`. Change a value there and it updates everywhere.
- **Trust-badge numbers** ("500+ Orders Delivered", "30+ Countries") on the homepage are illustrative placeholders — swap in your real numbers in `index.html` once you have them.

---

## File structure

```
doa-global-bridge/
├── index.html            Home
├── about.html            About
├── products.html         Products / Services
├── gallery.html          Gallery / lookbook
├── contact.html          Contact (WhatsApp-powered form + map)
├── admin.html            Owner-only product manager
├── css/style.css         All styling (responsive, one file)
├── js/
│   ├── main.js           Shared site behaviour (nav, WhatsApp links, rendering, lightbox)
│   ├── products-data.js  Your product catalogue — the single source of truth
│   └── admin.js          Admin panel logic
└── images/                Placeholder art — swap for real photography
```

Built for phones, tablets, laptops and desktops alike — every page is fully responsive.
