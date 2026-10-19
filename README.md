# SARJ | Land Intelligence — Assessment Build

Investor property discovery and admin portfolio intelligence, grounded in **120 original parcel records** and **48 original inquiry records** (snapshot 11 August 2026). The data is imported without altering the underlying records; no synthetic properties or inquiries.

## Run locally
`npm install && npm run dev`

## Public deployment (required for submission)
1. Push this folder to a private GitHub repository and import it into Vercel.
2. Set framework **Vite**, build command `npm run build`, output directory `dist`.
3. Add `OPENAI_API_KEY` to Vercel environment variables (server-side only). Optional `OPENAI_MODEL` (default `gpt-4o-mini`). Redeploy.
4. Test public URL without login, both views, parcel details, filters, and the live AI in each role.
5. Keep the URL online for at least two weeks after deadline.

**Security:** Never put the API key in source or `VITE_` variables. Investor AI does not receive the private inquiry records. The admin demo is intentionally public per assessment rules; therefore **the admin UI shows aggregated inquiry information only**. Its AI receives inquiry records server-side; for real production use add role-based authentication and remove private contact fields from the LLM context.

## Verification checklist
- [x] Original 120 parcels imported
- [x] Original 48 inquiries imported
- [x] Search, land type, transaction type, availability filtering
- [x] Property detail overlay and coordinates link
- [x] Investor and admin views
- [x] Admin inventory and pipeline indicators
- [ ] Live LLM tested with configured API key
- [ ] Public deployment URL tested
- [ ] Cross-browser/mobile QA

## Known limitations
The investor inquiry creation flow is not persisted; this prototype demonstrates discovery and AI guidance, not a live CRM. Data is historical and status should not be represented as real-time. Public admin mode is a demo, not production-grade authorization. Map links show dataset coordinates, not verified parcel boundaries.
