## [0.5.0] — 2025-01-XX

### Added
- **EVE Application Management System**: Complete leadership audit interface with section-by-section review, visual status indicators, and full workflow management (Submit → Under Review → Accept/Reject)
- **EVE Corporation Wallet System**: New wallet management for leadership including divisions, balance snapshots, transactions, and journal entries
- **Application Resubmission Support**: Applicants can address rejected sections and resubmit while maintaining review status
- **Auditor Notes System**: Leadership can add review notes visible to applicants during the review process
- **Application History & Reopen**: Complete view of decided applications with ability to reopen for re-evaluation
- **Form Question Templates**: Dynamic form rendering from JSON templates with leadership-editable question sets

### Changed
- **Application Progress Calculation**: Fixed progress calculation discrepancies between client and server
- **Section State Management**: Enhanced tracking with auditor information and timestamps
- **UI/UX Improvements**: Streamlined application management interface with better visual feedback

### Fixed
- **Resubmission Logic**: Applications can now be resubmitted when sections are rejected
- **Form Data Persistence**: Fixed form question labels storage in database
- **Real-time Updates**: Proper SWR configuration for live updates between applicant and auditor views
- **TypeScript Errors**: Resolved various type safety issues in application management components

### API
- **Added**: `manageApplication.ts` — Unified API for application management actions
- **Added**: `eve-apps-qs-template.json` — JSON template for dynamic form rendering
- **Added**: Corporation wallet APIs (`localCorpWalletTxs.ts`, `localCorpWalletDivisions.ts`, `localCorpWalletBalances.ts`, `localCorpWalletJournal.ts`)
- **Updated**: Application submission and management APIs with enhanced functionality

## [0.4.7.9] — 2025-01-XX

### Added EVE Application Management System
- **Leadership Audit Interface**: Comprehensive application review system for corp leadership.
- **Section-by-Section Review**: Individual approval/rejection of application sections (Characters and Scopes, Application Form, Verification, Skills, Killboard).
- **Visual Status Indicators**: Color-coded section status badges with auditor information and decision timestamps.
- **Application Workflow Management**: Complete workflow from Submit → Under Review → Accept/Reject with full audit trail.
- **Resubmission Support**: Applicants can address rejected sections and resubmit while maintaining UNDER_REVIEW status.
- **Auditor Notes System**: Leadership can add review notes that are visible to applicants during the review process.
- **Application History Tracking**: Complete view of accepted/rejected applications with decision dates and auditor information.
- **Reopen Functionality**: Leadership can reopen decided applications (ACCEPTED/REJECTED) for re-evaluation.
- **Real-time Updates**: Live status updates between applicant and auditor perspectives using SWR refresh intervals.
- **Enhanced Bootcamp Tab**: Added decided applications section with search and filtering capabilities.
- **Form Question Templates**: Dynamic form rendering from JSON templates with leadership-editable question sets.
- **Unified Data Structure**: Refactored form storage to use unified question/answer arrays with backward compatibility.

### Changed
- **Application Progress Calculation**: Fixed progress calculation discrepancies between client and server for resubmission scenarios.
- **Section State Management**: Enhanced section state tracking with auditor information and timestamps.
- **UI/UX Improvements**: Streamlined application management interface with better visual feedback and status indicators.

### Fixed
- **Resubmission Logic**: Applications can now be resubmitted when sections are rejected, regardless of progress percentage.
- **Form Data Persistence**: Fixed form question labels not being stored correctly in the database.
- **Real-time Updates**: Implemented proper SWR configuration for live updates between applicant and auditor views.
- **TypeScript Errors**: Resolved various type safety issues in application management components.

### API
- **Added**
  - `src/pages/api/games/eve/management/manageApplication.ts` — Unified API for all application management actions (approve/reject sections, add notes, reopen applications).
  - `src/data/eve-apps-qs-template.json` — JSON template for dynamic form question rendering.
- **Updated**
  - `src/pages/api/games/eve/applications/submitUserApplication.ts` — Added resubmission support with isResubmission flag.
  - `src/pages/api/games/eve/management/applications.ts` — Enhanced to include auditor information in responses.

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
  - Guarded SWR keys & memo deps to eliminate "Rendered more hooks than during the previous render" and undefined key crashes on mode switches.
  - Correct toon-selection flow when switching between Single and Combined modes.

### API
  - Added
      - src/pages/api/games/eve/esi/eveToonIndustryJobs.ts — returns active + completed jobs; dataset industry:character:jobs; name enrichment.
      - src/pages/api/games/eve/esi/eveToonMiningLedger.ts — returns character mining ledger; dataset mining:character.
      - src/pages/api/games/eve/esi/eveToonAssets.ts — returns all character assets (multi-page), attaches itemName and unitPrice from CCP /markets/prices (average→adjusted), plus totalValue; dataset assets:character.
  - Updated
      - src/pages/api/games/eve/esi/eveToonMarketOrders.ts — always attaches itemName; supports history=1 for completed orders; cache/diagnostic headers remain.
      - src/pages/api/games/eve/esi/eveToonContracts.ts — (from 0.4.7.4) list + section=items for details with attachItemNames().