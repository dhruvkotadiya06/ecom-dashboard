# ShopDash — Authentication-Based E-Commerce Dashboard

A complete React + Vite + Tailwind CSS e-commerce dashboard with authentication, session management, product browsing, and cart management — all powered by localStorage (no backend required).

---

## Features

- **Auth**: Register, Login, session expires in 5 minutes with live countdown
- **Protected Routes**: Dashboard, Products, Cart, Profile
- **Products**: Fetched from Fake Store API with search, filter, sort
- **Cart**: Add, remove, increase/decrease quantity, subtotal/total — persisted in localStorage
- **Profile**: Edit name, email, and password
- **Responsive**: Mobile-first, works on all screen sizes

---

## Installation

### 1. Prerequisites
- Node.js 18+ installed
- npm 9+ (comes with Node)

### 2. Clone / Copy project
```bash
# If using git:
git clone <your-repo-url>
cd ecom-dashboard

# Or just copy the project folder and cd into it
cd ecom-dashboard
```

### 3. Install dependencies
```bash
npm install
```

### 4. Run the development server
```bash
npm run dev
```
Open [http://localhost:5173](http://localhost:5173) in your browser.

---

## Project Structure

```
src/
├── components/
│   ├── Navbar.jsx          # Sidebar (desktop) + top bar (mobile) with session timer
│   ├── ProductCard.jsx     # Product display card with add-to-cart
│   └── ProtectedRoute.jsx  # Route guard — redirects to /login if no session
├── pages/
│   ├── Login.jsx           # Login form with validation
│   ├── Register.jsx        # Registration form with validation
│   ├── Dashboard.jsx       # Welcome + stats + session timer bar
│   ├── Products.jsx        # Product grid with search/filter/sort
│   ├── Cart.jsx            # Cart with quantity controls and order summary
│   └── Profile.jsx         # Edit name, email, password
├── context/
│   ├── AuthContext.jsx     # Auth state, login/logout/register, session countdown
│   └── CartContext.jsx     # Cart state, localStorage sync
├── hooks/
│   ├── useAuth.js          # Consumes AuthContext
│   └── useCart.js          # Consumes CartContext
├── utils/
│   └── session.js          # Session helpers, localStorage CRUD, formatTime
├── App.jsx                 # Router setup with protected layout
├── main.jsx                # React entry point
└── index.css               # Tailwind directives + custom component classes
```

---

## Tailwind Setup (already configured)

The project uses Tailwind CSS v3 with:
- `tailwind.config.js` — custom colors (brand, ink, surface), fonts (Syne + Plus Jakarta Sans), animations
- `postcss.config.js` — autoprefixer + tailwindcss plugins
- Google Fonts loaded via `index.html`

If you ever need to add Tailwind to a fresh Vite project:
```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

---

## How to Build for Production

```bash
npm run build
```
Output goes to `dist/` folder.

To preview the production build locally:
```bash
npm run preview
```

---

## Deploy to Vercel

### Option A — Vercel CLI
```bash
npm install -g vercel
vercel
# Follow the prompts — framework will be auto-detected as Vite
```

### Option B — Vercel Dashboard
1. Push your project to GitHub
2. Go to [vercel.com](https://vercel.com) → New Project
3. Import your GitHub repo
4. Settings:
   - **Framework Preset**: Vite
   - **Build Command**: `npm run build`
   - **Output Directory**: `dist`
5. Click **Deploy**

---

## Deploy to Netlify

### Option A — Netlify CLI
```bash
npm install -g netlify-cli
npm run build
netlify deploy --prod --dir=dist
```

### Option B — Netlify Dashboard
1. Push to GitHub
2. Go to [netlify.com](https://netlify.com) → Add new site → Import from Git
3. Settings:
   - **Build command**: `npm run build`
   - **Publish directory**: `dist`
4. Click **Deploy site**

### Important: Fix client-side routing on Netlify
Create a `public/_redirects` file with:
```
/*  /index.html  200
```

Or add `netlify.toml` at root:
```toml
[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```

---

## Usage Guide

1. Open the app → you'll be redirected to `/login`
2. Click "Sign up free" to go to `/register`
3. Fill in Name, Email, Password → submit
4. You'll be redirected back to `/login`
5. Log in with your credentials
6. You now have a **5-minute session** — visible as a countdown in the sidebar
7. Browse Products, add to Cart, edit your Profile
8. Session auto-expires and logs you out after 5 minutes

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| React 18 | UI library |
| Vite 5 | Build tool & dev server |
| React Router v6 | Client-side routing |
| Tailwind CSS v3 | Utility-first styling |
| localStorage | Auth, session & cart persistence |
| Fake Store API | Product data |
| Google Fonts | Syne + Plus Jakarta Sans |
