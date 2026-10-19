# SARJ | Land Intelligence — Product Requirements Document
**Version:** 1.0 | **Dataset:** 11 August 2026 snapshot | **Client:** Sarj Real Estate | **Scope:** Four-day assessment MVP

## 1. Problem, users, and outcomes
**Problem:** Sarj Real Estate has 120 Riyadh land parcels across 88 districts, but its website presents static listings. Investors cannot quickly identify suitable opportunities, and leadership lacks an actionable view of inventory and investor demand. The existing pipeline contains 48 inquiries.

**Investor job:** “Help me find land suitable for my intended use, within my budget and preferred location, and understand why it fits.” **Admin job:** “Help me understand the state of our portfolio and what investor inquiries reveal about demand.”

**North-star outcome:** qualified investor inquiries per eligible property view. **Supporting metrics:** search-to-property-detail rate, AI recommendation-to-detail rate, inquiry intent, available-inventory engagement, inquiry status distribution, and long-on-market inventory exposure. The MVP does not claim measured uplift without analytics.

## 2. MVP experiences and requirements
**Investor discovery:** Browse the portfolio; default to available listings; filter by residential/commercial and sale/lease; search district or parcel ID; open a parcel detail with district, area, size, street width, status, asking sale price or annual lease rent, and a map-coordinate link. Show snapshot date and avoid implying real-time availability.

**Investor AI advisor:** Natural-language Arabic/English assistance using the provided inventory. Interpret purpose, preferred area, budget and transaction type; suggest matching **available** parcel IDs with evidence, and explain when no exact match exists. Never fabricate property attributes, geographic distances, ROI or market valuations. Never disclose private inquiry records.

**Admin intelligence:** Overview of all 120 parcels, 62 available properties, 48 inquiries, available sale asking-value (separate from lease annual rents), status distribution, days on market, area inventory and pipeline stages. Admin AI supports questions about inventory and inquiry demand, using inquiry details with names/phone numbers removed from the LLM context.

**Shared interaction requirements:** Responsive design; meaningful empty states; accurate status and price basis; functional LLM service; no sign-in barrier to the demo; all original records retained. The admin view is public for evaluation only and must be protected by authorization before real production use.

## 3. Product decisions, trade-offs, and acceptance criteria
**Why two views:** The investor experience optimizes discovery and confidence; the admin experience optimizes visibility and portfolio decisions. Both share the same authoritative inventory but differ in permitted data and questions.

**Why AI plus structured filters:** Filters are predictable for known constraints; conversational AI helps translate vague intent (“open a showroom”) into evidence-based recommendations. The assistant is a guide, not a source of independent market valuations or legal investment advice.

**What is intentionally out of scope:** CRM writes, account creation, production admin authorization, parcel-boundary maps, real-time listing sync, property photographs, predictive ROI, market scraping and payment flows. The initial prototype does not persist new investor inquiries. This avoids presenting unimplemented conversion tracking as operational functionality.

**Acceptance tests:** (1) All 120 unique parcel IDs and 48 inquiry IDs are present; (2) investor default shows only the 62 available parcels; (3) sale and lease listings show correct price basis; (4) sold/leased/reserved parcels are never suggested as available; (5) chatbot answers unscripted questions grounded in parcel records in both views; (6) investor chatbot never reveals inquiry contact data; (7) admin metrics reconcile with source data; (8) public URL works without login for two weeks; (9) product behaves on desktop and mobile.

**Risks and mitigations:** Stale snapshot → clear date labeling; model hallucination → strict system constraints and exact parcel references; token/context size → optimize retrieval for production; exposed admin demo → use only aggregated pipeline UI and remove personal contact fields from AI context; LLM outage → explicit error rather than a fake scripted answer; external API spend → server-side secret and provider usage limits.

**Future iteration:** Implement a consent-based inquiry capture API and CRM, event instrumentation, map clustering and parcel boundaries, analytics by inquiry source, evidence-backed demand matching, and authenticated admin access.
