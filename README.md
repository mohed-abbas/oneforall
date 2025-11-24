# 🖤 Obsidian - TradingView All-in-One Indicator

**Version**: 2.0.0 (Phase 1 + 2)
**Platform**: TradingView
**Language**: Pine Script v6

---

## 📖 Overview

Obsidian is an ICT-focused TradingView indicator combining a customizable watermark with powerful session and kill zone visualization. Perfect for traders who need clean, professional chart overlays with precise session timing and kill zone identification.

### ✨ Phase 1 Features (Completed)

- ✅ **Two-Line Watermark**: Clean overlay fixed at top center of chart with dual-line display
- ✅ **Title Line**: Display symbol, timeframe, and/or custom title text
- ✅ **Subtitle Cells**: Up to 3 customizable subtitle fields with pipe separators
- ✅ **Auto-Refresh**: Automatically updates when switching symbols or timeframes
- ✅ **Full Style Control**: Customize color, transparency, size, and position
- ✅ **Performance Optimized**: Single table instance for minimal CPU usage
- ✅ **Clean UI**: Organized grouped inputs for intuitive configuration

### ✨ Phase 2 Features (Completed)

- ✅ **Three Major Sessions**: Asian (Tokyo), London, and New York trading sessions
- ✅ **Customizable Timezone**: User-selectable timezone (UTC-12 to UTC+12) with auto-adjustment
- ✅ **Session Visualization**:
  - Session high/low horizontal lines with custom labels
  - Session open/close vertical markers
  - Optional session background boxes (disabled by default)
- ✅ **Kill Zones**:
  - Three kill zone boxes (Asian, London, NY) with customizable times
  - Colored boxes with adjustable transparency
  - Optional borders and text labels
  - Independent toggle controls
- ✅ **Full Customization**:
  - Individual colors for each session and kill zone
  - Custom labels for all elements
  - Line width and style options
  - Complete toggle control for each feature
- ✅ **No Watermark Interference**: Sessions and kill zones render independently

---

## 🚀 Installation

### Method 1: TradingView Pine Editor

1. Open TradingView and navigate to the **Pine Editor** tab
2. Click **"New"** to create a new indicator
3. Copy the contents of `obsidian_v1.pine`
4. Paste into the Pine Editor
5. Click **"Save"** and name it "Obsidian"
6. Click **"Add to Chart"**

### Method 2: Import from File

1. Download `obsidian_v1.pine`
2. Open TradingView Pine Editor
3. Use **File → Import** (if available)
4. Select the downloaded file

---

## 🎨 Configuration

### Watermark Settings

#### Display Toggle

**Show Watermark**
- Toggle watermark visibility on/off
- Default: `ON`

#### Watermark Content (Line 1: Title)

**Title Text**
- Add custom title text for the first line
- Example: "Trading Plan", "Focus Zone", "Analysis"
- Default: `Empty`

**Show Symbol**
- Display current symbol ticker in title (e.g., BTCUSD, AAPL)
- Default: `ON`

**Show Timeframe**
- Display current chart timeframe in title (e.g., 1H, 1D, 4H)
- Default: `ON`

#### Watermark Content (Line 2: Subtitles)

**Subtitle 1, 2, 3**
- Add up to 3 subtitle cells for the second line
- Separated by pipe characters "|"
- Example: "Entry: 45000 | Stop: 44000 | Target: 48000"
- Default: `Empty`

#### Watermark Style

**Text Color**
- Choose watermark text color
- Default: `White`

**Transparency**
- Control text visibility (0 = opaque, 100 = invisible)
- Range: 0-100
- Default: `50`

**Font Size**
- Select text size: Auto, Tiny, Small, Normal, Large, Huge
- Default: `Normal`

**Position**
- Horizontal alignment: Left, Center, Right
- Default: `Center`

---

### Time Zones Settings

**User Timezone**
- Select your reference timezone (UTC-12 to UTC+12)
- All session and kill zone times adjust automatically
- Default: `UTC-5` (New York/EST)

---

### Sessions Settings

#### Sessions - Display Toggles

**Show All Sessions**
- Master toggle for all session displays
- Default: `ON`

**Asian Session / London Session / New York Session**
- Individual toggles for each session
- Default: `ON` for all

#### Session Times

Configure start and end hours for each session in your selected timezone:

**Asian Session**
- Start Hour: `0` (midnight)
- End Hour: `9` (9 AM)

**London Session**
- Start Hour: `2` (2 AM)
- End Hour: `12` (12 PM)

**New York Session**
- Start Hour: `8` (8 AM)
- End Hour: `17` (5 PM)

#### Session Markers

**Session Highs / Session Lows**
- Show horizontal lines at session high/low levels
- Default: `ON` for both

**Session Open / Session Close**
- Show vertical lines marking session boundaries
- Default: `ON` for both

#### Session Labels

**Asian Label / London Label / NY Label**
- Customize text labels for each session
- Default: `"Asian"`, `"London"`, `"New York"`

#### Session Style

**Asian Color / London Color / NY Color**
- Choose colors for each session's lines and markers
- Default: Yellow (Asian), Blue (London), Green (NY)

**Show Session Background**
- Enable optional background boxes for sessions
- Default: `OFF`

**BG Transparency**
- Background box transparency (0-100)
- Default: `90`

**Line Width**
- Session line thickness (1-5)
- Default: `1`

**Line Style**
- Choose line style: Solid, Dashed, Dotted
- Default: `Solid`

---

### Kill Zones Settings

#### Kill Zones - Display Toggles

**Show All Kill Zones**
- Master toggle for all kill zone displays
- Default: `ON`

**Asian Kill Zone / London Kill Zone / NY Kill Zone**
- Individual toggles for each kill zone
- Default: `ON` for all

#### Kill Zone Times

Configure start and end hours for each kill zone in your selected timezone:

**Asian Kill Zone**
- Start Hour: `0`
- End Hour: `3`

**London Kill Zone**
- Start Hour: `2` (2:00 AM EST / 7:00 AM GMT)
- End Hour: `5` (5:00 AM EST / 10:00 AM GMT)

**New York Kill Zone**
- Start Hour: `7` (7:00 AM EST)
- End Hour: `10` (10:00 AM EST)

#### Kill Zone Labels

**Asian KZ Label / London KZ Label / NY KZ Label**
- Customize text labels for each kill zone
- Default: `"Asian KZ"`, `"London KZ"`, `"NY KZ"`

#### Kill Zone Style

**Asian KZ Color / London KZ Color / NY KZ Color**
- Choose colors for each kill zone box
- Default: Yellow, Blue, Green (all with 85% transparency)

**KZ Transparency**
- Kill zone box transparency (0-100)
- Default: `85`

**Show KZ Border**
- Display border on kill zone boxes
- Default: `ON`

**Border Color / Border Width**
- Customize kill zone borders
- Default: White (50% transparency), Width: `1`

**Show KZ Labels**
- Display text labels on kill zones
- Default: `ON`

**Label Size / Label Color**
- Customize kill zone label appearance
- Default: Small, White

---

## 💡 Usage Examples

### Basic Setup

1. Add Obsidian to your chart
2. Watermark displays symbol and timeframe by default
3. Sessions and kill zones display automatically
4. Adjust transparency and colors as needed

### Watermark Only (Minimal)

1. Disable "Show All Sessions" and "Show All Kill Zones"
2. Customize watermark content and style
3. Result: Clean two-line text overlay without session markers

### ICT Trading Setup (Full Features)

1. Set your timezone to match your trading timezone
2. Enable all sessions and kill zones
3. Customize colors:
   - London: Blue for lines and kill zones
   - New York: Green for lines and kill zones
   - Asian: Yellow for lines and kill zones
4. Result: Complete ICT session and kill zone visualization

### Session-Only Display

1. Enable "Show All Sessions"
2. Disable "Show All Kill Zones"
3. Customize session colors and labels
4. Result: Session high/low lines with open/close markers

### Kill Zones Only

1. Disable "Show All Sessions"
2. Enable "Show All Kill Zones"
3. Customize kill zone times and colors
4. Result: Clean kill zone boxes without session lines

### Custom Timezone Example (London Trader)

1. Set timezone to UTC+0 (GMT)
2. Adjust session times:
   - London: 8:00-17:00 (8 AM to 5 PM GMT)
   - New York: 13:00-22:00 (1 PM to 10 PM GMT)
   - Asian: 0:00-9:00 (midnight to 9 AM GMT)
3. Adjust kill zone times accordingly
4. Result: Sessions display in your local time

### Combining Features

**Example 1: Trading Plan with Sessions**
- Line 1 Watermark: "BTCUSD | 1H | Long Bias"
- Line 2: "Entry: 45000 | Target: 50000"
- Enable London and NY sessions with kill zones
- Result: Complete trading setup with visual zones

**Example 2: Multi-Timeframe Analysis**
- Keep watermark for symbol/timeframe info
- Enable session backgrounds for visual separation
- Add custom notes about trend direction
- Result: Clean analysis overlay with session context

---

## 🔧 Technical Details

### Performance

- **Single Table Instance**: Optimized pattern using `var` keyword with fixed screen positioning
- **Last Bar Only**: Updates only on `barstate.islast` for minimal CPU usage
- **Efficient Text Building**: Conditional concatenation without redundant operations
- **Auto-Refresh**: Leverages built-in Pine Script variables (no manual refresh logic)

### Auto-Update Mechanism

- **Symbol Changes**: `syminfo.ticker` automatically updates
- **Timeframe Changes**: `timeframe.period` automatically updates
- **Table Update**: Watermark table cell updates on every relevant change

### Code Structure

- **Modular Design**: Clear separation of inputs, logic, and display
- **Grouped Inputs**: Organized UI with Display/Content/Style sections
- **Expansion Ready**: Structured for future ICT features (Phases 2-5)
- **Well Documented**: Comprehensive inline comments for maintainability

---

## 🗺️ Roadmap

### ✅ Phase 1: Watermark Foundation (Completed)

- Customizable watermark overlay
- Symbol and timeframe display
- Custom subtitle cells
- Full style customization

### ✅ Phase 2: ICT Kill Zones & Sessions (Completed)

- Three major trading sessions (Asian, London, New York)
- Customizable timezone support
- Session high/low lines with labels
- Session open/close markers
- Kill zone boxes with full customization
- Optional session backgrounds

### Phase 3: Market Structure (Planned)

- Fair Value Gaps (FVG) detection
- Liquidity zone identification
- Order blocks
- Market structure breaks
- Swing high/low markers
- Break of structure (BOS) detection

### Phase 4: Alerts & Presets (Planned)

- Custom alert conditions for sessions and kill zones
- Alert on FVG formations
- Preset configurations for different trading styles
- Widget system for quick access
- Export/import settings

### Phase 5: Full Trading Suite (Planned)

- Theme system with color presets
- Advanced customization engine
- Multi-indicator coordination
- Performance optimization
- Educational tooltips and guides

---

## ✅ Acceptance Criteria

### Phase 1 Criteria

| Criterion                    | Status |
| ---------------------------- | ------ |
| Watermark displays correctly | ✅     |
| Custom text updates live     | ✅     |
| Symbol auto-updates          | ✅     |
| Timeframe auto-updates       | ✅     |
| Style controls functional    | ✅     |
| Only one table instance      | ✅     |
| Toggle hides watermark       | ✅     |
| No script errors             | ✅     |
| Works all symbols/timeframes | ✅     |

### Phase 2 Criteria

| Criterion                          | Status |
| ---------------------------------- | ------ |
| Sessions detect correctly          | ✅     |
| Timezone adjustment works          | ✅     |
| Session highs/lows accurate        | ✅     |
| Kill zones render properly         | ✅     |
| All toggles function               | ✅     |
| Custom times adjust kill zones     | ✅     |
| Labels display correctly           | ✅     |
| No interference with watermark     | ✅     |
| Performance optimized              | ✅     |
| Works across all sessions/timeframes | ✅     |

---

## 🐛 Troubleshooting

### Watermark Not Visible

- Check "Show Watermark" is enabled in Display Settings
- Verify transparency is not set to 100 (fully transparent)
- Ensure text color contrasts with chart background
- Confirm at least one content option is enabled (Symbol/Timeframe/Custom Note)

### Text Not Updating

- Watermark auto-updates on symbol/timeframe changes
- If issues persist, remove and re-add indicator to chart
- Check Pine Editor for any script errors

### Style Changes Not Applying

- Position changes require label recreation (may take 1 bar to update)
- Color/transparency changes apply immediately
- Refresh chart if changes don't appear

### Performance Issues

- Obsidian uses optimized single-label pattern
- Should have minimal CPU impact
- If issues occur, check for conflicts with other heavy indicators

---

## 📋 Version History

### v2.0.0 - Phase 2 (2025-11-24)

- ✨ Major feature release: Sessions & Kill Zones
- ✅ Three major trading sessions (Asian, London, New York)
- ✅ Customizable timezone support (UTC-12 to UTC+12)
- ✅ Session high/low horizontal lines with custom labels
- ✅ Session open/close vertical markers
- ✅ Kill zone boxes with full customization
- ✅ Optional session background boxes
- ✅ Individual toggle controls for all features
- ✅ Complete color and style customization
- ✅ Reorganized settings into logical zones
- ✅ No interference with existing watermark functionality

### v1.0.0 - Phase 1 (2025-11-23)

- ✨ Initial release
- ✅ Customizable watermark overlay
- ✅ Symbol and timeframe display
- ✅ Custom subtitle cells
- ✅ Full style customization
- ✅ Auto-refresh functionality
- ✅ Performance optimized

---

## 📄 License

This indicator is provided as-is for personal and educational use on TradingView.

---

## 🤝 Support

For issues, suggestions, or feature requests:

- Review `IMPLEMENTATION_WORKFLOW.md` for technical details
- Check `QUICK_START.md` for development reference
- Consult TradingView Pine Script documentation

---

## 🎯 Quick Start

```
1. Copy obsidian_v1.pine code
2. Paste into TradingView Pine Editor
3. Save as "Obsidian"
4. Add to chart
5. Customize in indicator settings
```

**That's it!** Your watermark is ready. Customize to fit your trading style.

---

**Built with**: Pine Script v6
**Optimized for**: All TradingView charts
**Compatible with**: Stocks, Forex, Crypto, Futures, and more

🖤 **Obsidian** - Clean. Professional. Expandable.
