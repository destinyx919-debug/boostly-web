# Boostly — Frontend (the actual website)

This is the real, standalone version of the app you've been testing in
Claude — same design, now built with Vite so it can be deployed as a real
website that talks to the real backend.

## 1. Test it locally first

Make sure the backend (`boostly-server`) is running locally first (see its
README), then:

```bash
cd boostly-web
npm install
cp .env.example .env
```

Open `.env` — by default it points at `http://localhost:3001`, which matches
the local backend. Then:

```bash
npm run dev
```

Open the URL it prints (usually `http://localhost:5173`). Try creating an
account — it should hit your local backend and actually persist to
`boostly.db`.

## 2. Deploy it for real (using Vercel, free tier)

1. Push this `boostly-web` folder to a GitHub repository (same idea as the
   backend — can be a separate repo, or a second folder in the same one).
2. Go to https://vercel.com, sign up (free), click **Add New → Project**.
3. Import your repo. Vercel auto-detects Vite — leave the defaults.
4. Under **Environment Variables**, add:
   - `VITE_API_URL` = your Render backend URL (e.g. `https://boostly-api.onrender.com`)
5. Click **Deploy**. Vercel gives you a live URL like `https://boostly.vercel.app`.

## 3. Add a custom domain (optional)

If you want something like `boostly.com` instead of the free Vercel URL:

1. Buy a domain from any registrar (Namecheap, Google Domains successor
   Squarespace Domains, Cloudflare Registrar, etc.) — this step needs your
   own payment info, it's not something I can do for you.
2. In Vercel, go to your project → **Settings → Domains → Add**, type your
   domain, and Vercel will show you DNS records to add.
3. Add those records in your registrar's DNS settings. It can take a few
   minutes to a few hours to go live.

## Before you tell people it's live

A few things worth doing before real strangers start creating accounts:

- **Add a real Terms of Service / Privacy Policy.** You're collecting
  usernames and passwords now — even hashed, you should say what you do with
  data. I can draft these with you.
- **Reconsider the engagement-exchange mechanic.** As discussed earlier,
  using this to trade likes/followers on real TikTok/Instagram/YouTube
  accounts can violate those platforms' terms of service and get users'
  accounts penalized. Worth deciding how upfront you want to be about that
  risk, or whether to pivot the mechanic.
- **No real payments are wired up.** The "Buy coins" screen is still a
  placeholder — connecting real Stripe checkout is a separate, sizeable
  project on its own (requires a registered business in most cases). Ask if
  you want to scope that out next.
