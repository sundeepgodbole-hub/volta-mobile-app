# VOLTA mobile app package

This is an installable Progressive Web App (PWA) for GitHub Pages. GitHub Pages serves static files only; it does not host an HDFC market-data server or live news service.

## Feed status

Index quotes, 200-day and 200-week EMAs, trend breadth, chart history, volatility, Greeks, weekly expiry, option-chain OI, market headlines and trade signals require live sources. The app withholds these readings when sources are missing instead of presenting stale samples. Capital guardrails are user settings.

The **Refresh All** button and five-minute default timer request `./api/dashboard?exchange=NSE` (or `BSE`). This route must be supplied by a separately hosted secure backend. The OI response shape is `{ "connected": true, "exchange": "NSE", "oi": { "symbol": "NIFTY 50", "spot": 25412.8, "atm": 25400, "rows": [[strike, callOiChange, callOi, callLtp, putLtp, putOi, putOiChange]] } }`. The same response may include `marketPulse: { "updatedAt": "...", "items": [{ "title": "...", "summary": "...", "impact": "high|medium|low", "publishedAt": "ISO timestamp", "source": "Publisher", "url": "https://..." }] }`. A separate news/macro source is needed for geopolitics, crude oil, currency and RBI items.

An optional backend URL can be set as `window.VOLTA_API_BASE` before the dashboard loads. Keep API keys and access tokens on the secure backend, never in this public repository or the browser. OI change alone cannot determine whether positions are long or short. VOLTA does not place orders and is not trading advice.
