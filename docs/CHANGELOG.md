## [0.4.7.3] — 2025-08-29

### Added in character page:
- **Contracts tab** improvements:
  - Row expander (“Show info”) with **Financials + Items** for each contract.
  - Sticky **“Hide info”** control that appears **only after scrolling** the expanded section.
  - Clicking **“Show info”** now **scrolls/focuses** to the expanded section.
- **Item names** for contract contents
- **Wallet → Overview** enhancements:
  - Timeframe dropdown (1d/1w/1m/1y) with delta display.
  - Scrollable transactions list (shows 20, then scroll).
  - Filters: **market**, **contracts**, **pve** (checkboxes).
  - Small search bar (type/status/title).
  - Clickable date to restore timeframe snapshot.

### Changed
- **Contract history** now sorts **newest first** (by `dateIssued`).
- **Reward/Price** column logic:
  - `courier` → **reward**
  - `item_exchange` → **price**
  - `auction` → **buyout** (fallback: price)
  - Otherwise: first finite of reward/price/buyout.

### Fixed
- Details fetch now uses the existing route  
- Correctly renders ISK amounts even if upstream provides numeric strings.

### API
- `src/pages/api/games/eve/esi/eveToonContracts.ts`
  - Added `section=items` to return contract items; gated by **`contracts:character`**.
  - Enriches items with `itemName` via `attachItemNames()` (from seeded JSON).
  - Diagnostic headers: `X-ESI-Status`, `X-Character-Id`, `X-Contract-Id`, `X-Type-Names-Resolved`.
- `src/pages/api/games/eve/esi/eveToonWalletTxs.ts`
  - Provides wallet deltas + transactions with timeframe support (used by Wallet Overview).
