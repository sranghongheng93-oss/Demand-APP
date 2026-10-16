# Retail Demand Planning Studio — Phase 1 starter

Includes Supabase email/password auth, CSV/XLSX import preview and validation, persistent sales records, per-SKU Naive vs 4-period moving-average backtesting, saved 8-week forecasts and CSV export. It is not the complete 12-module platform.

## 1. Create Supabase
1. Open https://database.new and create a project.
2. In SQL Editor, run all of `supabase/schema.sql`.
3. Copy Project URL and publishable key from Project Settings / API (or Connect). Keep secret/service-role keys private.

## 2. Run locally
Install Node.js LTS (20.9+). Extract the ZIP and run `npm install`. Copy `.env.example` to `.env.local`, then set `NEXT_PUBLIC_SUPABASE_URL` and `NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY`. Run `npm run dev`; open http://localhost:3000; create an account and sign in. Confirm your email if required. Never commit `.env.local`.

## 3. Test
Try a small copy first. Required columns: SKU (or Item Code), week/date, actual sales (or quantity/units). Use consistent weekly dates. Upsert key: user + SKU + week + channel + location. At least five periods per SKU are required for forecasts. Refresh and sign in again to check persistence. Compare calculations manually before relying on them.

## 4. Deploy to Vercel
1. Create a new private GitHub repository and push these files; do not include `.env.local`.
2. In Vercel choose Add New → Project and import the GitHub repository.
3. Add `NEXT_PUBLIC_SUPABASE_URL` and `NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY` in Project Settings → Environment Variables for Preview and Production.
4. Deploy and test the Preview URL first: sign-in, import, forecast, refresh persistence and account isolation. Redeploy after environment variable changes.

## Limits before daily operations
The import limit is 10,000 rows per commit. The import history table is defined but not yet populated by the UI. Error report downloads, larger staged imports, advanced forecasting, inventory, safety stock, reorder points, MOQ/case pack, replenishment approvals, MRP and S&OP are not yet implemented. This starter has not been deployed or tested against your real workbook.

Official docs: https://supabase.com/docs/guides/getting-started/quickstarts/nextjs · https://supabase.com/docs/guides/auth/server-side · https://vercel.com/docs/environment-variables