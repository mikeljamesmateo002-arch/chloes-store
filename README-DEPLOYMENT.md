# Chloe's Store — V3.0.0 Deployment

## Architecture

GitHub → Netlify → Supabase

- `index.html` = application frontend
- `version.json` = lightweight version/update signal
- `netlify.toml` = deployment + cache/security headers
- Supabase = authentication + tenant-isolated data

## First production setup

1. Put `index.html`, `version.json`, and `netlify.toml` in a GitHub repository.
2. Connect that repository to Netlify.
3. In `index.html`, set:
   - `APP_SUPABASE_URL` = Supabase project URL
   - `APP_SUPABASE_KEY` = Supabase publishable/anon key
   - `APP_CONFIG_LOCKED = true`
4. Never place the Supabase `service_role` key in the frontend.
5. Deploy the repository to Netlify.

## Future updates

For V3.1.0, change `APP_VERSION` and `version.json` to `3.1.0`, commit/push to GitHub, and Netlify will deploy automatically.

Existing client records remain in Supabase; the frontend deployment does not replace database data.

## Important

Before production, test login, sale, stock movement, return/restock, customer history, expenses, and reports with a test account.
