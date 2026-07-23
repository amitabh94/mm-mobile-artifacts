# NOTES — $15 Transak Staging buy on PR #33686 (post-fix)

- Branch: `feat/ramps-dev-env-for-mobile-dev` (Dev env + `transak-native-staging` remap + payment-method testIDs)
- Amount: **$15** base → **$16.84** total (fees $1.84)
- Recipe: 23/23 harness PASS through checkout; Confirm order tapped manually (WebView)
- Terminal: **Order details → Complete**; “Your purchase of 0.00744 ETH was successful!”
- Provider: Transak (Staging); payment VISA ****1519
- Order ID suffix: `...6e2367`
- Proves Dev API routing works after remapping to `transak-native-staging` (prior run failed with bare `transak-native` HTTP 500)

## Artifacts
- `recordings/buy.mp4` — recipe through Confirm screen
- `recordings/buy-confirm.mp4` — Confirm → Order Details Complete
- Screenshots: BuildQuote, payment sheet Debit, Confirm, Order Details Complete
