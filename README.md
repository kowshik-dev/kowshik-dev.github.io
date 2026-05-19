# Kowshik Portfolio

Personal portfolio website for Ikram Hossain Kowshik — Systems Developer specializing in C, Java, Python, and the MERN stack.

Built with React + Vite + Tailwind CSS + Framer Motion. Dark cyberpunk aesthetic with neon red accents.

---

## Running Locally

### Prerequisites

Make sure you have these installed:

- [Node.js](https://nodejs.org/) v18 or later
- [pnpm](https://pnpm.io/) v8 or later

Install pnpm if you don't have it:

```bash
npm install -g pnpm
```

### Steps

**1. Clone the repository**

```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
```

**2. Install dependencies**

```bash
pnpm install
```

**3. Set required environment variables**

The Vite dev server needs two environment variables. Create a `.env` file inside the `artifacts/portfolio/` folder:

```bash
# artifacts/portfolio/.env
PORT=5173
BASE_PATH=/
```

**4. Start the development server**

```bash
pnpm --filter @workspace/portfolio run dev
```

Then open your browser and go to: **http://localhost:5173**

---

## Project Structure

```
artifacts/portfolio/
├── public/              # Static assets (favicon, og image, robots.txt)
├── src/
│   ├── pages/
│   │   └── home.tsx     # Main portfolio page (all sections)
│   ├── components/ui/   # shadcn/ui component library
│   ├── hooks/           # Custom React hooks
│   ├── lib/             # Utility functions
│   ├── App.tsx          # App root with routing
│   ├── main.tsx         # Entry point
│   └── index.css        # Global styles + Tailwind theme
├── index.html           # HTML shell + meta tags
├── vite.config.ts       # Vite configuration
└── package.json
```

---

## Customizing Content

All portfolio content lives in one file: `artifacts/portfolio/src/pages/home.tsx`

| Section | What to edit |
|---|---|
| **Hero** | Your name, tagline, and description near the top |
| **About** | Bio paragraphs and skill bars |
| **Projects** | Project titles, descriptions, tags, GitHub links, and image imports |
| **Tech Stack** | The icon/name grid in the "Technology Matrix" section |
| **Contact** | The mailto address used in `onSubmit` |
| **Footer** | Copyright year and social links |

---

## Connecting a Custom Domain

### If hosted on Replit

1. Go to your Replit project → **Deployments** tab
2. Click **Custom domain**
3. Enter your domain (e.g. `kowshik.dev`)
4. Copy the CNAME record Replit provides
5. Go to your domain registrar's DNS settings and add:
   - **Type:** CNAME
   - **Name:** `@` (or `www` for a subdomain)
   - **Value:** the CNAME Replit gave you
6. Wait up to 24–48 hours for DNS to propagate
7. Replit will automatically provision an SSL certificate

### If self-hosting (VPS / Netlify / Vercel)

**Build the site first:**

```bash
# Set env vars, then build
PORT=4173 BASE_PATH=/ pnpm --filter @workspace/portfolio run build
```

The output goes to `artifacts/portfolio/dist/public/`.

**Netlify:**
- Drag and drop the `dist/public` folder into Netlify
- Go to Site settings → Domain management → Add custom domain

**Vercel:**
```bash
npx vercel --prod
```
Then add your domain in the Vercel dashboard under Project → Settings → Domains.

**Nginx (VPS):**
```nginx
server {
    listen 80;
    server_name kowshik.dev www.kowshik.dev;
    root /var/www/portfolio/dist/public;
    index index.html;
    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

Run `certbot --nginx` to add free SSL via Let's Encrypt.

---

## Tech Stack

| Tool | Purpose |
|---|---|
| React 18 | UI framework |
| Vite | Build tool + dev server |
| Tailwind CSS v4 | Utility-first styling |
| Framer Motion | Scroll + entrance animations |
| React Hook Form | Contact form handling |
| react-icons | Tech stack icons |
| lucide-react | UI icons |
| wouter | Client-side routing |

---

## License

MIT — feel free to use this as a template for your own portfolio.
