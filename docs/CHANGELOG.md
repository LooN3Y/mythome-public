## [0.4.7.4] — 2025-08-29

### Added EVE user economy page
- **Economy** page functionality:
  - Wallet, Market, Contracts, Industry, Mining, Assets tabs functional
  - Single / Combined modes for each tab
  - Individual filters
- **Wallet Tab**
  - Wallet functionality migrated
  - Shared hooks: useWalletSingle, useWalletCombined; helpers like fmtISK, wallet category tagging.
  - Fixed hooks ordering / SWR key guards when toggling Single ↔ Combined.
- **Market Tab**
  - Rebuilt MarketTab using three sub-tabs: Active Orders, Completed Orders, Stats.
  - Per-list filters: buy/sell, search, timeframe (independent per list).
  - Stats has its own timeframe and shows counts plus ISK sums (sell, buy, Δ).
  - UI polish: aligned stat card + timeframe; pagination resets on tab switch.
  - Item names now provided server-side for both active and completed orders.
- **Contracts Tab**
  - New ContractsTab with sub-tabs: Active, Completed, Stats.
  - Stats: timeframe selector (defaults to All) with totals: count, completed count, incoming ISK (sells), outgoing ISK (buys), and Δ.
  - Row emphasis uses text color only (no colored glyphs), so copy/paste stays clean.
  - Stability fixes (toon lookup, hook order).
- **Industry Tab**
  - New IndustryTab with Active Jobs, Job History, Stats.
  - Client-side filters: search, activity, status, timeframe; plus pagination.
  - Helpers added: timeframeToSinceMs, isIndustryCompleted, isIndustryActive.
  - Names attached where available for blueprints/products.
- **Mining Tab**
  - New MiningTab with Overview, Ledger, Stats.
  - Shows ore totals, per-ore breakdowns, timeframe controls (charts placeholder ready).
  - Supports combined summaries across selected characters.
- **Assets Tab**
  - New AssetsTab (single + combined).
  - Client filters: structure multi-select (by location_id), search, sort (value/name/qty/location), pagination.
  - Summary cards: Total Value (All) vs Filtered Value, item count, distinct types.
  - Toggle: Include blueprints — when off, blueprints are hidden and excluded from totals.
  - Item names + unit prices (average→adjusted) attached server-side; totals computed client-side.

### Changed
- Skills tab removed from economy page.

### Fixed
  - Guarded SWR keys & memo deps to eliminate “Rendered more hooks than during the previous render” and undefined key crashes on mode switches.
  - Correct toon-selection flow when switching between Single and Combined modes.

### API
  - Added
      - src/pages/api/games/eve/esi/eveToonIndustryJobs.ts — returns active + completed jobs; dataset industry:character:jobs; name enrichment.
      - src/pages/api/games/eve/esi/eveToonMiningLedger.ts — returns character mining ledger; dataset mining:character.
      - src/pages/api/games/eve/esi/eveToonAssets.ts — returns all character assets (multi-page), attaches itemName and unitPrice from CCP /markets/prices (average→adjusted), plus totalValue; dataset assets:character.
  - Updated
      - src/pages/api/games/eve/esi/eveToonMarketOrders.ts — always attaches itemName; supports history=1 for completed orders; cache/diagnostic headers remain.
      - src/pages/api/games/eve/esi/eveToonContracts.ts — (from 0.4.7.4) list + section=items for details with attachItemNames().
