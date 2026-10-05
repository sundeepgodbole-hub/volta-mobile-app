# VOLTA mobile app package

This is an installable Progressive Web App (PWA) package for GitHub Pages. It opens in a standalone app window and caches the dashboard shell for offline viewing.

## Publish with GitHub Pages

1. Create or choose a GitHub repository for VOLTA.
2. Upload the contents of this folder to the repository root.
3. In the repository, open **Settings → Pages** and publish from the `main` branch, `/ (root)`.
4. Open the resulting HTTPS `github.io` address on your phone. Use the browser menu to install/add VOLTA to the home screen.

The page currently contains simulated market data. The OI panel can switch between NSE and BSE, highlights net call and put OI change across the visible 11 strikes, offers a manual refresh button, and auto-checks every 5 minutes by default (15 minutes is selectable). Until a secure authorized data service is connected, refresh attempts only check for that service and the displayed option chain remains simulated. The client expects a same-origin `GET /api/dashboard?exchange=NSE` (or `BSE`) response shaped as `{ "connected": true, "exchange": "NSE", "oi": { "symbol": "NIFTY 50", "spot": 25412.8, "atm": 25400, "rows": [[strike, callOiChange, callOi, callLtp, putLtp, putOi, putOiChange]] } }`. Keep API keys and tokens on a secure backend; never put them in this static app or a public repository. OI change alone does not identify whether positions are long or short. The sample values are not suitable for trading decisions.
