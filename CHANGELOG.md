# Changelog

All notable changes to One for All TradingView Indicator will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [3.3.1] - 2025-12-05

### Added
- **Status Dashboard**: New visual reference box showing enabled/disabled state of all features
  - Real-time status indicators for: Watermark, Sessions, Kill Zones, Previous Period, HTF Candles
  - Color-coded checkmarks (✓ green = enabled, ✗ red = disabled)
  - 9 customizable positions (Top/Middle/Bottom Left/Center/Right)
  - Customizable background transparency (0-100)
  - Zero performance impact (updates only on last bar)
  - Optional display (disabled by default via `show_status_dashboard` input)
  - Uses only 1 drawing object (same as watermark table)

### Technical Details
- New input group: `GRP_STATUS_DASHBOARD = "═══ STATUS DASHBOARD ═══"`
- New inputs: `show_status_dashboard`, `status_position`, `status_bg_transp`
- New helper function: `get_status_position(pos)` - Converts string position to Pine Script position constant
- Status detection logic: Reads existing input variables to determine feature states
- Table structure: 2 columns × 6 rows (header + 5 feature rows)
- Follows existing watermark table pattern for consistency
- Pine Script v6 compliance maintained (all single-line function calls)
- Total code additions: ~50 lines

---

## [3.2.1] - 2025-11-30

### Changed
- **Indicator Renamed**: "Obsidian" → "One for All"
  - Updated indicator name and shorttitle (OBS → OFA)
  - Updated author to theCodeman
  - File renamed: obsidian_v2.pine → oneforall.pine
  - Complete README.md rewrite with comprehensive documentation

## [3.2.1] - 2025-11-30

### Fixed
- **HTF Visibility Bug**: Fixed M5 (and other HTF) candles not appearing on M3 (and other non-divisible) timeframes
  - Root cause: `ValidTimeframe()` function used overly restrictive divisibility check
  - Previous logic required HTF to be exact integer multiple of chart timeframe
  - New logic: Simply checks if HTF > current timeframe (all higher timeframes now display correctly)
  - Impact: M5 HTF now shows on M1, M2, M3, M4 charts (previously only worked on M1)

### Changed
- Simplified `ValidTimeframe()` function from 8 lines to 1 line for clarity and correctness

---

## [3.1.1] - 2025-11-29 (ROLLBACK)

### Removed - HTF Implementation Rollback
- **Complete HTF Phase 3B Removal**: Rolled back all Higher Timeframe candle implementation to return to stable Phase 3 state
  - Removed 5 HTF candle slots (5m, 15m, 1H, 4H, Daily)
  - Removed HTF custom types (7 types: htf_Candle, htf_Imbalance, htf_Trace, htf_CandleSettings, htf_Settings, htf_CandleSet, htf_Helper)
  - Removed HTF helper methods (new_htf_candle, update_htf_candle, delete_htf_candle, draw_htf_candle, update_htf_candle_position, get_day_of_week)
  - Removed HTF data retrieval (`request.security()` calls for all 5 HTF slots)
  - Removed HTF rendering logic (FIFO array management and candle processing)
  - Removed drawing budget calculator and warning system
  - Removed 5 HTF input groups (HTF Candles, HTF Style, HTF Trace, HTF Imbalances, HTF Budget)
  - Removed all HTF configuration inputs (~50 input parameters)

### Changed - Reverted to v3.1.1 State
- **Drawing Limits**: Reverted from 50/50/50 back to 500/500/500 (removed free tier restrictions)
- **Version**: Rolled back from v3.2.0-beta1 to v3.1.1
- **File Size**: Reduced from ~1230 lines to ~774 lines (-456 lines, -37%)
- **Roadmap**: Phase 3B status changed from "In Progress" to "Planned"

### Reason for Rollback
User requested removal of HTF implementation to return to stable Phase 3 state with only Watermark, Sessions, Kill Zones, and Previous Period H/L features.

### Current State After Rollback
- ✅ Phase 1: Watermark (fully functional)
- ✅ Phase 2: Sessions & Kill Zones (fully functional)
- ✅ Phase 3: Previous Period H/L (fully functional)
- ❌ Phase 3B: HTF Candles (removed, will be reimplemented in future)

### Testing Required
- Verify compilation without errors
- Test watermark display and updates
- Test sessions render correctly
- Test kill zones display properly
- Test Daily/Weekly/Monthly H/L lines work
- Verify all Phase 1-3 features function normally

---

## [3.2.0-beta1] - 2025-11-29 (REMOVED)

### Added - HTF CANDLES NOW FUNCTIONAL! 🎉
- **HTF Candles Rendering**: Higher Timeframe candles now display on chart!
  - Boxes render candle bodies (bullish green, bearish red)
  - Lines render upper and lower wicks
  - Real-time updates as current HTF candle forms
  - FIFO array management with automatic cleanup
- **HTF Data Retrieval**: Complete `request.security()` implementation
  - All 5 HTF slots fetch OHLC data from higher timeframes
  - Change detection triggers new candle creation
  - Continuous updates extend candles to current bar
- **HTF Helper Methods**: Complete candle lifecycle management
  - `new_htf_candle()` - Creates new HTF candle instance
  - `update_htf_candle()` - Updates OHLC and tracking indices
  - `delete_htf_candle()` - Cleans up drawing objects
  - `draw_htf_candle()` - Renders box body and wick lines
  - `update_htf_candle_position()` - Extends candle to current bar
  - `get_day_of_week()` - Returns day abbreviation (SUN-SAT)
- **HTF Style Configuration**: User-customizable appearance
  - Bullish/Bearish candle colors (default: green/red)
  - Wick color (default: gray)
  - Border width (1-5, default: 2)
  - Show/hide day labels toggle
  - Show/hide wicks toggle
- **HTF Array Management**: FIFO with drawing limits
  - Arrays manage up to 6 candles per HTF slot
  - Automatic deletion of oldest candle when limit exceeded
  - Memory-efficient with predictable resource usage

### How to Use HTF Candles
1. Open indicator settings in TradingView
2. Navigate to "═══ HTF CANDLES ═══" group
3. Enable "Show HTF Candles" master toggle
4. Enable 1-2 HTF slots (Free Tier) or more (Essential+)
   - HTF 1: 5m (6 candles max)
   - HTF 2: 15m (6 candles max)
   - HTF 3: 1H (5 candles default)
   - HTF 4: 4H (4 candles default)
   - HTF 5: Daily (3 candles default)
5. Customize colors in "HTF Candle Style" group
6. Monitor "Drawing Budget Warning" to stay within limits

### Technical Details - Beta 1 Architecture
- **Purpose**: Functional HTF candles with core rendering
- **Scope**: Complete data retrieval, array management, and rendering
- **File Size**: ~1230 lines (was ~1030 alpha1 → +200 lines)
- **New Code**: ~200 lines of rendering logic
- **Complexity**: High (request.security + real-time updates)
- **Risk**: Medium (new feature, needs testing across timeframes)

### Performance Characteristics
- **Request.Security Calls**: 5 calls per bar (one per HTF slot)
- **Drawing Objects Per Enabled HTF**:
  - Boxes: Max candles setting (3-6 per slot)
  - Lines: 2× max candles (upper + lower wicks)
  - Total: 3× max candles per slot
- **Free Tier Budget Example** (HTF1 + HTF2 enabled, 6 candles each):
  - Boxes: 12
  - Lines: 24
  - Total: 36/50 boxes, 24/50 lines (SAFE)

### Testing Requirements
- **Compilation**: Verify Pine Script v6 compiles
- **HTF Rendering**: Enable HTF slots and verify candles display
- **Real-time Updates**: Verify candles extend with current bar
- **FIFO Management**: Verify old candles delete when limit reached
- **Budget Warning**: Verify accurate counts and warnings
- **Timeframe Testing**: Test on 1m, 5m, 15m, 1H, 4H, 1D charts
- **Symbol Testing**: Test on stocks, forex, crypto
- **Color Customization**: Verify style changes apply
- **Existing Features**: Ensure sessions, kill zones, prev periods still work

### Known Limitations - Beta 1
- **Day-of-week labels**: Not yet displayed (infrastructure ready)
- **Trace lines**: Not yet implemented (Phase Beta 2)
- **Fair Value Gaps (FVG)**: Not yet implemented (Phase Beta 3)
- **Volume Imbalances (VI)**: Not yet implemented (Phase Beta 3)
- **Timeframe validation**: No warnings if HTF < chart timeframe

### Migration Notes
- **No Breaking Changes**: Existing features unchanged
- **New Feature**: HTF candles disabled by default
- **Budget Impact**: Monitor warning when enabling HTF candles
- **Free Tier**: Enable max 2 HTF slots with other features disabled
- **Essential Tier**: Can enable 3 HTF slots
- **Plus/Premium**: Can enable all 5 HTF slots

### Next Phase - Beta 2
- Day-of-week label display on HTF candles
- Trace lines connecting HTF OHLC to formation bars
- Timeframe validation and warnings
- Performance optimizations

---

## [3.2.0-alpha1] - 2025-11-29

### Added - HTF Foundation & Drawing Budget System
- **HTF Input Groups**: Added 5 new input group constants for Phase 3B HTF Candles integration
  - `GRP_HTF` - Main HTF candles configuration
  - `GRP_HTF_STYLE` - Candle appearance settings
  - `GRP_HTF_TRACE` - Trace line settings
  - `GRP_HTF_IMBALANCE` - FVG/VI settings
  - `GRP_HTF_BUDGET` - Drawing budget warning controls
- **HTF Custom Types**: Defined 7 Pine Script custom types for HTF system
  - `htf_Candle` - Single HTF candle with OHLC, drawing objects, and metadata
  - `htf_Imbalance` - Fair Value Gaps (FVG) and Volume Imbalances (VI)
  - `htf_Trace` - Lines connecting HTF OHLC to formation bars
  - `htf_CandleSettings` - Appearance configuration
  - `htf_Settings` - Master configuration for HTF slot
  - `htf_CandleSet` - Manages candles/imbalances for one HTF slot
  - `htf_Helper` - Utility methods for HTF operations
- **HTF Configuration Inputs**: 5 HTF slots with smart defaults
  - HTF 1: 5m timeframe, 6 candles (Free Tier)
  - HTF 2: 15m timeframe, 6 candles (Free Tier)
  - HTF 3: 1H timeframe, 5 candles (Essential+)
  - HTF 4: 4H timeframe, 4 candles (Plus+)
  - HTF 5: Daily timeframe, 3 candles (Premium+)
- **Drawing Budget Calculator**: Real-time estimation system
  - `get_estimated_usage()` - Calculates boxes/lines/labels based on enabled features
  - `get_declared_limits()` - Returns drawing limits (50/50/50)
  - `get_warning_level()` - Determines SAFE/INFO/WARNING/CRITICAL level
  - `get_warning_color()` - Color coding for warning levels
- **Budget Warning Display**: Live monitoring table (top-right corner)
  - Shows real-time usage vs limits for boxes, lines, labels
  - 4-level color-coded warnings: Green (SAFE), Yellow (INFO), Orange (WARNING), Red (CRITICAL)
  - Percentage usage display and actionable messages
  - Tier-specific guidance (Free/Essential/Plus/Premium limits)

### Changed - Free Tier Optimization
- **Drawing Limits**: Reduced from 500 to 50 for all object types
  - `max_lines_count=50` (was 500)
  - `max_boxes_count=50` (was 500)
  - `max_labels_count=50` (was 500)
- **Version**: Updated to 3.2.0-alpha1 (HTF Foundation)
- **Date**: Updated to 2025-11-29
- **Roadmap**: Split Phase 3B into HTF Candles and Phase 3C for market structure

### Technical Details - Alpha 1 Architecture
- **Purpose**: Foundation phase for HTF integration
- **Scope**: Scaffolding, types, inputs, budget system (NO rendering yet)
- **File Size**: ~1030 lines (was ~770 lines)
- **New Code**: ~260 lines of HTF infrastructure
- **Complexity**: Low (foundation only)
- **Risk**: Low (no rendering logic, compile-only test)

### Testing Requirements
- **Compilation**: Verify Pine Script v6 syntax compiles without errors
- **Input Display**: Confirm all 5 HTF input groups appear correctly in TradingView UI
- **Budget Calculator**: Verify budget warning displays with correct calculations
- **Existing Features**: Ensure all Phase 1-3 features still work correctly
- **Drawing Limits**: Confirm 50/50/50 limits don't break existing features

### Migration Notes
- **Breaking Changes**: Drawing limits reduced - users may need to reduce `max_days` setting
- **Recommended Config for Free Tier**:
  - `max_days = 2` (was 3)
  - Enable 1-2 features maximum (sessions OR kill zones OR prev periods OR HTF)
  - Monitor budget warning to stay under 50/50/50 limits
- **Premium Users**: Limits will be increased in future versions based on tier detection
- **HTF Not Active**: HTF candles do NOT render yet - this is foundation only

### Next Phase - Alpha 2
- HTF helper methods (candle creation, update, reorder)
- HTF rendering infrastructure preparation
- Day-of-week label logic
- OHLC tracking and bar index management

---

## [2.5.0] - 2025-11-28

### Added - Hybrid Architecture Implementation
- **Native Session Detection**: Replaced manual time parsing with Pine's built-in `time()` function for 99% reliability
- **Universal Timezone Support**: Full GMT range (GMT-12 to GMT+14) instead of just 2 timezone options
- **Multi-Day History**: Array-based tracking for sessions and kill zones with configurable history depth
- **Drawing Limit Management**: Automatic cleanup system with `max_days` parameter (1-10 days)
- **Global Settings Group**: New `═══ SETTINGS ═══` section for drawing limits and timezone
- **Session String Format**: Changed to Pine's native `"HHMM-HHMM"` format (e.g., "0930-1700")

### Changed - Input Format and Architecture
- **Session Inputs**: Changed from separate start/end HH:MM strings to single session format
  - OLD: `asianStartTime` + `asianEndTime` (HH:MM format)
  - NEW: `asian_ses` ("HHMM-HHMM" format)
- **Kill Zone Inputs**: Changed to session string format matching inspiration patterns
- **Timezone System**: Expanded from 2 options to 27 options (all GMT offsets)
- **Session Detection Logic**: Completely rebuilt using `math.sign(nz(time()))` pattern
- **Kill Zone Tracking**: Rebuilt with array-based architecture for multi-day support
- **Variable Naming**: Changed to match inspiration patterns (e.g., `show_asian` vs `showAsianSession`)

### Improved - Performance and Reliability
- **Session Detection**: 93% code reduction (40+ lines → 3 lines per session)
- **Edge Case Handling**: Native Pine handling eliminates midnight-crossing bugs
- **Drawing Management**: Automatic cleanup prevents TradingView 500 drawing limit
- **Memory Usage**: Fixed memory footprint based on max_days setting
- **Performance**: O(1) session detection vs O(n) manual parsing

### Technical Details - Architecture Patterns
- **Inspiration Sources**:
  - Session detection from LuxAlgo Sessions indicator
  - Array management from TFO Killzones indicator
  - Drawing limits from both inspiration sources
- **Code Quality**: 51% total line reduction (1115 → 544 lines)
- **Maintainability**: Simplified architecture with 3 core functions vs 5 helpers
- **UI Preservation**: Maintained all custom input group organization

### Migration Notes
- **Breaking Changes**: Input format changed, requires one-time reconfiguration
- **Time Conversion**: HH:MM → HHMM format (e.g., "09:30" → "0930")
- **Session Format**: "HHMM-HHMM" (e.g., "0930-1700" for 9:30 AM to 5:00 PM)
- **Midnight Sessions**: Native support (e.g., "2000-0400" = 8 PM to 4 AM)
- **Migration Guide**: See `docs/V2.5_MIGRATION_GUIDE.md` for detailed instructions

### Documentation
- **Migration Guide**: `docs/V2.5_MIGRATION_GUIDE.md` - User migration instructions
- **Implementation Summary**: `docs/V2.5_IMPLEMENTATION_SUMMARY.md` - Technical details
- **Analysis Report**: Original analysis comparing inspiration vs v2.3.0

### Known Issues Fixed
- ✅ Session detection failures at day boundaries
- ✅ Timezone offset bugs with midnight-crossing sessions
- ✅ Drawing accumulation causing chart slowdowns
- ✅ Limited timezone options for global traders
- ✅ Kill zones only showing current day

---

## [2.3.0] - 2025-11-28

### Removed
- **Trading Days Display Control**: Removed the "Trading Days to Display" feature that limited session and kill zone rendering to recent trading days
  - Removed `GRP_DISPLAY_CONTROL` input group
  - Removed `daysToShow` input parameter
  - Removed `displayPreset` dropdown (Current Day Only, 3-Day View, Week View, Custom)
  - Removed `effectiveDays` calculation
  - Removed `getTradingDayNDaysAgo()` helper function
  - Removed `isWeekend()` helper function
  - Removed `getCurrentTradingDay()` helper function
  - Removed `historicalCutoffTime` calculation
  - Removed `isWithinDisplayWindow()` function
  - Removed all `InWindow` state tracking variables for sessions and kill zones

### Changed
- **Session and Kill Zone Rendering**: Sessions and kill zones now display for all historical bars without day limit restrictions
- **isCurrentTradingDay() Function**: Simplified to only check if bar is on current calendar day (removed weekend checking)

### Technical Details
- All session high/low lines, session boxes, and kill zone boxes are now rendered historically without cutoff
- Live real-time tracking for current day sessions/kill zones remains unchanged
- Improved historical analysis capability by showing all sessions across the entire chart

---

## [Unreleased]

### Added
- **Two-Line Watermark System**: Enhanced watermark with dual-line display capability
  - Line 1 (Title): Symbol, timeframe, and/or custom title text
  - Line 2 (Subtitles): Up to 3 customizable subtitle cells with pipe separators
- **New Input Fields**:
  - `titleText`: Custom title for line 1
  - `subtitle1`, `subtitle2`, `subtitle3`: Three subtitle cells for line 2
- **Enhanced Content Organization**: Separate configuration for title and subtitle content

### Changed
- **Watermark Implementation**: Switched from `label` to `table` for true fixed screen positioning at top of chart
- **Table Structure**: Updated from 1 row to 2 rows to support dual-line display
- **Positioning Method**: Watermark now uses `table.new(position=position.top_center, rows=2)` instead of label with price-based positioning
- **Pine Script Version**: Updated from v5 to v6 for improved compatibility and syntax requirements
- **Text Construction**: Separated logic for line 1 (title) and line 2 (subtitles) with independent content building

### Fixed
- **Critical Fix**: Watermark now remains fixed at top center of chart instead of tracking current market price
- Replaced label-based approach (which is always price-tied) with table-based approach for true fixed screen positioning

---

## [1.0.0] - 2025-11-23

### Added - Phase 1: Watermark Foundation

#### Core Features
- **Watermark Overlay System**: Clean, customizable text overlay fixed at top center of chart
- **Dynamic Content Display**:
  - Symbol ticker display (`syminfo.ticker`)
  - Timeframe display (`timeframe.period`)
  - Custom note input for personalized text
- **Auto-Refresh Mechanism**: Automatic updates on symbol/timeframe changes
- **Toggle Controls**: Individual show/hide for symbol, timeframe, and watermark

#### Style Customization
- **Text Color**: Full color picker for text customization
- **Transparency Control**: 0-100 range for visibility adjustment
- **Font Size Options**: Auto, Tiny, Small, Normal, Large, Huge
- **Position Control**: Left, Center, Right horizontal alignment

#### User Interface
- **Grouped Inputs**: Organized into Display, Content, and Style sections
- **Inline Controls**: Compact layout for related settings
- **Tooltips**: Helpful descriptions for all input controls
- **Clean Organization**: Intuitive settings structure

#### Performance Optimizations
- **Single Table Instance**: Optimized pattern using `var` keyword with fixed screen positioning
- **Last Bar Updates**: `barstate.islast` condition for minimal CPU usage
- **Efficient Text Building**: Conditional string concatenation
- **Memory Efficient**: No redundant table recreation, only cell updates

#### Code Quality
- **Modular Structure**: Clear separation of inputs, logic, and display
- **Comprehensive Comments**: Detailed inline documentation
- **Future-Ready**: Structured for Phase 2-5 expansion
- **Professional Formatting**: Clean, readable code organization

#### Documentation
- **README.md**: Complete user guide with usage examples
- **IMPLEMENTATION_WORKFLOW.md**: Detailed technical implementation guide
- **QUICK_START.md**: Quick reference for developers
- **CHANGELOG.md**: Version history tracking

### Technical Details

#### Pine Script Version
- Built with Pine Script v6
- Overlay indicator (`overlay=true`)
- Compatible with all TradingView chart types

#### Built-in Variables Used
- `syminfo.ticker` - Current symbol
- `timeframe.period` - Current timeframe
- `barstate.islast` - Last bar detection
- `bar_index` - Bar index for positioning
- `high` - Bar high for y-position reference

#### Display Management
- Single persistent table using `var table watermarkTable = table.new(...)`
- Table positioned at fixed screen location (`position.top_center`, `position.top_left`, or `position.top_right`)
- Cell update pattern for efficient rendering
- Transparent background (`color.new(color.black, 100)`)
- Dynamic text color with transparency support
- True fixed positioning independent of price movement

### Acceptance Criteria Met

- [x] Watermark displays correctly
- [x] Custom text updates live
- [x] Symbol auto-updates on instrument change
- [x] Timeframe auto-updates on period change
- [x] Style controls (color, transparency, size, position) functional
- [x] Only one label instance (performance optimized)
- [x] Toggle successfully hides/shows label
- [x] No script errors or compilation issues
- [x] Works on all symbols and timeframes
- [x] Clean grouped input UI
- [x] Modular code structure
- [x] Professional documentation

### Known Limitations

- Position/alignment changes require label recreation (Pine Script limitation - no `label.set_textalign()`)
- Very long symbol names may overflow on small screens (TradingView handles naturally)
- Transparency effectiveness depends on chart background color

### Future Roadmap

#### Phase 2: Kill Zones & Sessions (Planned)
- London/New York/Asia session boxes
- Kill zone highlighting
- Session high/low tracking

#### Phase 3: Market Structure (Planned)
- Fair Value Gaps (FVG)
- Liquidity zones
- Order blocks
- Market structure breaks

#### Phase 4: Alerts & Presets (Planned)
- Custom alert conditions
- Preset configurations
- Widget system

#### Phase 5: Full Trading Suite (Planned)
- Theme system
- Advanced customization
- Multi-indicator coordination

---

## Version Numbering

Obsidian follows [Semantic Versioning](https://semver.org/):
- **MAJOR** version: Incompatible API changes or major feature overhauls
- **MINOR** version: New features added in backward-compatible manner (Phases)
- **PATCH** version: Backward-compatible bug fixes

### Phase Mapping
- v1.x.x - Phase 1: Watermark Foundation
- v2.x.x - Phase 2: Kill Zones & Sessions
- v3.x.x - Phase 3: Market Structure
- v4.x.x - Phase 4: Alerts & Presets
- v5.x.x - Phase 5: Full Trading Suite

---

## Template for Future Releases

```markdown
## [X.Y.Z] - YYYY-MM-DD

### Added
- New features

### Changed
- Changes to existing functionality

### Deprecated
- Soon-to-be removed features

### Removed
- Removed features

### Fixed
- Bug fixes

### Security
- Security vulnerability fixes
```

---

**Initial Release**: v1.0.0 - Phase 1 Complete ✅
