# PR #33686 Transak buy evidence notes

## Environment
- Branch: feat/ramps-dev-env-for-mobile-dev (merged up-to-date with origin/main)
- Sim: mm-33357
- METAMASK_ENVIRONMENT=dev (from .js.env / Metro)
- Recipe: transak-staging-buy (session-reuse variant for email skip)

## Proved
- UB2 BuildQuote opened (Transak Staging provider label visible)
- $30 amount + payment sheet + Continue
- Session reuse skipped email/OTP → Confirm order (VISA ****1519, ETH)
- After Confirm, Order Details error shows callback fetch to **on-ramp.dev-api.cx.metamask.io** (confirms RAM Dev API routing from this PR)

## Failed / gaps
- Recipe harness timed out waiting for checkout-close-button (checkout appeared slightly after timeout); flow completed via agent taps while recording continued
- Debit row not selected via recipe (agent gap); Confirm still used saved VISA card (session reuse)
- Terminal: `getOrderFromCallback` → **HTTP 500** from Dev API
- Callback `url=` query used **on-ramp-content.api.cx.metamask.io** (production content host), not Dev API fake-callback — investigate getRampCallbackBaseUrl inlining / provider redirect allowlist

## Artifacts
- recordings/buy.mp4
- screenshots/01-buildquote-default.png
- screenshots/02-payment-sheet-debit.png
- screenshots/03-checkout-confirm.png
- screenshots/04-order-details-terminal.png (loading)
- screenshots/05-after-payment-wait.png (error)
