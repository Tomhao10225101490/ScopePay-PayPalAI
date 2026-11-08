# Verification — 2026-11-08

Completed evidence only. All payments below use PayPal's sandbox, with simulated accounts and no real money.

- Existing sandbox application's OAuth2 credentials authenticated successfully (HTTP 200); values remain in ignored local .env with mode0600.
- Real local ONNX MiniLM inference ran. The example brief matched landing-page, booking and analytics services and did not auto-select the unrelated accessibility or identity services after tightening nearest-sentence selection.
- `npm test`: 5 tests passed, including real model paraphrase matching, invalid briefs, integer/server-owned pricing, invalid quantities and capture validation. Unit receipt fixtures are synthetic and are not PayPal evidence.
- `node test/http.integration.mjs`: passed origin/CSRF enforcement, per-browser ownership separation, review-required guard, server-owned pricing despite client-supplied price, invalid quantity rejection. This script did not create payments.
- Actual native local Chrome walkthrough: local model returned evidence-linked services; attempting to save without review failed; review saved immutable scope, quantity1 for each service, total430.00USD.
- Actual PayPal sandbox Orders v2: order `8UM96354RK8647812` created; initial PAYER_ACTION_REQUIRED did not produce a paid receipt. Official personal sandbox buyer approved in PayPal checkout. The application fetched and captured the approved order, then verified completed status/reference/currency/amount.
- Actual sandbox capture `87M77230Y0111004K` completed for430.00USD at2026-11-08T15:04:22Z. Local verification occurred at15:04:23.363Z. The UI showed Payment verified in sandbox and receipt download.

Additional checks passed: native Chrome reload retained paid workspace records, reopening a proposal restored the verified receipt, and receipt JSON downloaded and matched the stored quote/capture. Two repeated reconciliation requests returned the same completed capture without repeating a payment; internal idempotency keys were omitted from API responses.

A second genuine sandbox checkout was recorded: order5X415157XF069122J and capture79B230430C593651J,430.00USD. Capture used an official generated personal sandbox buyer. Native Chrome interaction was recorded from the application window only, without microphone audio or background chat content.

The 390×844 responsive layout was visually checked in native Chrome device emulation: header, progress, proposal amounts and verified receipt fit the narrow column. This was emulation, not physical-phone testing.

The canonical source ZIP was extracted into a separate clean directory. `npm ci` succeeded, and all five tests passed again with a fresh local model download. No .env, sessions, model cache or node_modules were included in the archive.

Media assembly and public publication records are maintained outside the source archive; final formal submission must be verified on Devpost. Public links and final submission must be recorded separately when they exist.

Limitations: local single-computer prototype; no production hosting/security audit, real client pilot, live payments, tax, refunds, webhooks, disputes, external customer sharing or user-benefit measurement. AI is nearest-catalog semantic matching, not general reasoning or automatic contract interpretation. Initial model download requires internet access. The application runs loopback only.
