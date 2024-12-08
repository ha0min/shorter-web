# URL Shortener with GitHub Authentication

A secure URL shortener service built with Next.js, Cloudflare Workers, and GitHub OAuth authentication. Create, manage, and track shortened URLs with analytics.

## Features

- 🔐 Secure GitHub authentication
- 🔗 Custom URL shortening with optional custom codes
- ⏰ URL expiration support
- 📊 Click analytics tracking
- 🌍 Geographic data collection
- 🎯 Dashboard for URL management

## Prerequisites

- Node.js 18 or higher
- A GitHub account
- A Cloudflare account
- wrangler CLI tool (`npm install -g wrangler`)

## Setup

### 1. GitHub OAuth Setup

1. Go to GitHub Developer Settings
2. Create a new OAuth App
3. Set the homepage URL to your domain
4. Set the callback URL to `{your-domain}/auth`
5. Save the Client ID and Client Secret

### 2. Environment Variables

Create `.env.local` in the root directory:
```env
NEXT_PUBLIC_BASE_URL=http://localhost:3000
NEXT_PUBLIC_API_URL=http://localhost:8787
GitHub OAuth
GITHUB_CLIENT_ID=your_github_client_id
GITHUB_CLIENT_SECRET=your_github_client_secret
THE_GITHUB_USERNAME=your_github_username
```

Create `worker/.dev.vars` for the Cloudflare Worker:
```env
GITHUB_CLIENT_ID=your_github_client_id
GITHUB_CLIENT_SECRET=your_github_client_secret
THE_GITHUB_USERNAME=your_github_username
```

### 3. Install Dependencies

```bash
# Install frontend dependencies
npm install
# Install worker dependencies
cd worker
npm install
```

## Development

1. Start the Next.js development server:
```bash
npm run dev
```


2. Start the Cloudflare Worker:
```bash
cd worker
npm run dev
```

The application will be available at:
- Frontend: http://localhost:3000
- API: http://localhost:8787

## Deployment

### Frontend (Next.js)

Deploy to Vercel:
```bash
vercel
```

### Backend (Cloudflare Worker)

1. Create KV namespace and Analytics Engine dataset:
```bash
wrangler kv:namespace create URL_SHORTENER
wrangler analytics:dataset create URL_CLICK_TRACKING
```

2. Update `wrangler.toml` with your KV and Analytics bindings

3. Deploy the worker:
```bash
cd worker
wrangler deploy
```


## Usage

1. Visit your deployed application
2. Login with GitHub
3. Create shortened URLs from the dashboard
4. View analytics for your URLs

## License

MIT

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.