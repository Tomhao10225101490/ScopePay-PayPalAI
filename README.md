# ScopePay

**Clear scope. Confident checkout.** Local AI turns client briefs into reviewed service proposals, with real PayPal sandbox checkout and verified payment receipts. Original entry for the PayPal AI Hackathon 2026.

## Get the complete runnable source

This repository distributes the complete source tree in **[ScopePay-source.zip](ScopePay-source.zip)**. The archive is the canonical editable application, not a compiled binary. It includes all JavaScript, HTML/CSS, tests, package.json/lockfile, setup instructions and MIT license.

1. Download ScopePay-source.zip and extract it (or clone this repository and unzip the archive).
2. Open a terminal in the extracted **ScopePay/** directory.
3. Install Node.js22+, run `npm ci`, then copy `.env.example` to `.env`.
4. Obtain your own free **sandbox** application's client ID and secret from the [PayPal Developer Dashboard](https://developer.paypal.com/dashboard/applications/sandbox). Put these only in the local .env. Use a personal sandbox buyer from [Sandbox accounts](https://developer.paypal.com/dashboard/accounts) to approve checkout. No shared keys or real payment accounts are required for testing.
5. Run `npm run warmup` (first download needs internet), then `npm start`. Open **http://localhost:4317** in your browser.
6. Follow the extracted README walkthrough: example brief → AI draft → review/save → PayPal sandbox approval → verify/capture → receipt. The example's test total is430.00USD. Keep the local server running while PayPal redirects back to localhost.

The full extracted README documents runtime architecture, tests, setup, limitations and licenses. `npm test` runs five tests; `node test/http.integration.mjs` checks the running server. Judges can run a working build without public hosting, as allowed by the rules.

## What is implemented

- Real local MiniLM neural semantic matching with source evidence and visible similarity scores. Human review controls selected services and quantities.
- Server-owned catalog prices, fixed reviewed scope snapshot and itemized Orders v2 checkout. Persisted create/capture idempotency keys and explicit reconciliation.
- Reference/currency/exact-amount/completed-status verification before a paid receipt. Browser return alone never marks payment completed.
- Browser workspace isolation, origin/CSRF checks, persisted records and receipt JSON download.

[Verification](VERIFICATION.md) · [AI/prior work](AI_AND_PRIOR_WORK.md) · [Source manifest](SOURCE_MANIFEST.json) · [MIT license](LICENSE). The receipt example uses only synthetic service data and actual sandbox identifiers; it grants no access.

## Honest scope

A single-computer prototype, sandbox-only. No live payments, webhook listener, taxes/refunds/disputes, hosted multi-tenant access, customer sharing, real client pilot or demonstrated business benefit. AI is semantic catalog retrieval, not generative legal/financial advice. Initial matching can miss negations or multiple requirements in one sentence; people must review. No real money moves.

## Media

The demo uses genuine native Chrome-window recordings at normal speed, labeled stills, English captions and synthetic macOS Daniel narration. Public demo and Devpost links will accompany the final submission.
