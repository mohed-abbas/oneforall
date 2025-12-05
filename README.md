# 📊 One for All - TradingView All-in-One Indicator

**Version**: 3.4.0
**Author**: theCodeman
**Platform**: TradingView
**Language**: Pine Script v6

---

## 🎯 Overview

**One for All** is a comprehensive ICT (Inner Circle Trader) focused indicator for TradingView that combines essential trading tools into a single, powerful, and highly customizable indicator. Perfect for traders who want professional-grade analysis without cluttering their charts with multiple indicators.

### Why "One for All"?

This indicator eliminates the need for multiple separate indicators by combining:
- ✅ **Quick Toggles** - Instant feature control at top of settings panel (NEW in v3.4.0)
- ✅ **Status Dashboard** - Quick visual reference for enabled features
- ✅ **Customizable Watermark** - Track your setups and trading plans
- ✅ **Session & Kill Zone Visualization** - Asian, London, and NY sessions with kill zones
- ✅ **Previous Period Levels** - Daily, Weekly, and Monthly highs/lows
- ✅ **Higher Timeframe Candles** - Up to 5 HTF candle displays with FVG/VI detection
- ✅ **Professional Styling** - Complete control over colors, styles, and visibility

---

## ✨ Complete Feature List

### ⚡ Quick Toggles (NEW in v3.4.0)
- **Instant Feature Control**: All 5 master toggles grouped at top of settings panel
  - Enable/Disable Watermark
  - Enable/Disable Sessions
  - Enable/Disable Kill Zones
  - Enable/Disable Previous Period H/L
  - Enable/Disable HTF Candles
- **No Scrolling Required**: Quick Toggles appear first when settings panel opens
- **Faster Workflow**: 2 clicks instead of 3+ clicks to toggle any feature
- **Streamlined Organization**: Clean separation between "enable/disable" vs "configure"
- **Perfect for Active Traders**: Quickly adapt indicator to different market conditions

### 📝 Watermark System
- **Dual-Line Display**: Title line + subtitle line for trading notes
- **Auto-Updating**: Automatically displays current symbol and timeframe
- **Custom Text**: Add trading plan, bias, key levels, or any notes
- **Full Style Control**: Color, transparency, size, and position
- **Performance Optimized**: Single table instance, minimal CPU usage

### 🎯 Status Dashboard (NEW in v3.3.1)
- **Quick Visual Reference**: See at-a-glance which features are enabled/disabled
- **Real-Time Indicators**: Color-coded checkmarks (✓/✗) for all 5 main features
  - Watermark
  - Sessions
  - Kill Zones
  - Previous Period
  - HTF Candles
- **9 Position Options**: Top/Middle/Bottom × Left/Center/Right
- **Customizable Appearance**: Adjustable background transparency (0-100)
- **Zero Performance Cost**: Updates only once per bar, uses only 1 drawing object
- **Optional Display**: Disabled by default - enable via settings when needed

### 🌏 Session & Kill Zone Visualization
- **Three Major Sessions**: Asian, London, and New York
- **Universal Timezone Support**: GMT-12 to GMT+14 (manual DST adjustment)
- **Session Markers**:
  - High/Low horizontal lines with custom labels
  - Open/Close vertical markers
  - Optional background boxes
- **Kill Zones**:
  - Customizable time ranges for each session
  - Colored boxes with borders and labels
  - Multi-day history tracking
- **Full Customization**: Individual colors, labels, and toggles for each element

### 📊 Previous Period High/Low Levels
- **Three Periods**: Daily (PDH/PDL), Weekly (PWH/PWL), Monthly (PMH/PML)
- **Customizable Styles**: Choose line style (Solid/Dashed/Dotted) for each period
- **Line Width Control**: Set width from 1-5 for each period
- **Lookback Control**: Display last N periods (1-10)
- **Gradient Effect**: Optional fade for older periods
- **Custom Labels**: Customize label text and position (Left/Right)
- **Smart Display**: Auto-adjusts based on current timeframe

### 🕯️ Higher Timeframe (HTF) Candles
- **5 HTF Slots**: Configure up to 5 different higher timeframes
- **Default Presets**: 5m, 15m, 1H, 4H, Daily (fully customizable)
- **OHLC Display**: Open, High, Low, Close levels for each HTF
- **Fair Value Gaps (FVG)**: Automatic FVG detection and visualization
- **Volume Imbalance (VI)**: VI detection and shading
- **Trace Lines**: Connect HTF levels to their formation bars
- **HTF Timer**: Real-time countdown to next candle close
- **Interval Labels**: Day of week, time, or custom labels
- **Flexible Layout**: Control offset, buffer, and spacing
- **Custom Daily Open**: Choose Midnight, 8:30, or 9:30 daily open
- **Independent Toggles**: Enable/disable each HTF slot individually

---

## 🚀 Installation

### Quick Install (TradingView Pine Editor)

1. **Copy the Code**
   - Open the `oneforall.pine` file
   - Copy all contents (Ctrl+A, Ctrl+C)

2. **Open Pine Editor**
   - Go to TradingView chart
   - Click "Pine Editor" tab at bottom

3. **Create New Indicator**
   - Click "New" button
   - Paste the copied code
   - Click "Save"

4. **Add to Chart**
   - Click "Add to Chart"
   - Configure settings as desired

### Alternative: Import from File

1. Download `oneforall.pine` from the repository
2. In TradingView Pine Editor: File → Import
3. Select downloaded file
4. Click "Add to Chart"

---

## ⚙️ Configuration Guide

### General Settings

**Drawing Limit (Days)**
- Controls how many days of sessions/kill zones to display
- Range: 1-10 days
- Default: 3 days
- Impact: Lower = better performance, higher = more history

**Timezone**
- Your local timezone (GMT-12 to GMT+14)
- All session times adjust to your selected timezone
- Note: Does NOT auto-adjust for Daylight Saving Time
- Default: GMT-5 (New York/EST)

---

### Watermark Configuration

#### Display Control
- **Show Watermark**: Master toggle (ON/OFF)

#### Content Settings - Line 1 (Title)
- **Title Text**: Custom text (e.g., "Long Bias", "Scalping Setup")
- **Show Symbol**: Display current symbol (e.g., BTCUSD)
- **Show Timeframe**: Display current timeframe (e.g., 1H, 15m)

#### Content Settings - Line 2 (Subtitles)
- **Subtitle 1**: First custom field
- **Subtitle 2**: Second custom field
- **Subtitle 3**: Third custom field
- *Separated by pipe "|" symbol*

#### Style Settings
- **Text Color**: Any color
- **Transparency**: 0-100 (0 = solid, 100 = invisible)
- **Font Size**: Auto, Tiny, Small, Normal, Large, Huge
- **Position**: Left, Center, Right

**Example Watermark**:
```
BTCUSD | 1H | Long Bias
Entry: 45000 | Stop: 44000 | Target: 48000
```

---

### Session & Kill Zone Configuration

#### Session Display Toggles
- **Show All Sessions**: Master toggle for all sessions
- **Individual Session Toggles**: Asian, London, New York

#### Session Configuration (for each session)
Each session has:
- **Checkbox**: Enable/disable this session
- **Label Text**: Custom name (e.g., "Asian", "Tokyo")
- **Time Range**: HHMM-HHMM format (e.g., "0000-0900")
- **Color**: Session color for lines and markers

**Default Session Times (GMT-5)**:
- Asian: 0000-0900 (Midnight to 9 AM)
- London: 0800-1600 (8 AM to 4 PM)
- New York: 1300-2200 (1 PM to 10 PM)

#### Session Markers
- **Show Session High/Low**: Horizontal lines at session extremes
- **Show Session Open/Close**: Vertical markers at session boundaries
- **Show Session Background**: Optional colored boxes

#### Session Styling
- **Line Width**: 1-5
- **Line Style**: Solid, Dashed, Dotted
- **Background Transparency**: 0-100 (default: 90)

#### Kill Zone Configuration
Each kill zone has:
- **Checkbox**: Enable/disable
- **Label**: Custom name
- **Time Range**: HHMM-HHMM format
- **Color**: Box color

**Default Kill Zone Times (GMT-5)**:
- Asian KZ: 0000-0300
- London KZ: 0200-0500
- NY KZ: 0700-1000

#### Kill Zone Styling
- **Transparency**: 0-100 (default: 85)
- **Show Border**: ON/OFF
- **Border Color**: Any color (default: White)
- **Border Width**: 1-5
- **Show Labels**: ON/OFF
- **Label Size**: Tiny, Small, Normal, Large
- **Label Color**: Any color

---

### Previous Period H/L Configuration

#### Display Toggles
- **Show Previous Period H/L**: Master toggle
- **Show Daily**: Previous Day High/Low
- **Show Weekly**: Previous Week High/Low
- **Show Monthly**: Previous Month High/Low

#### Style Settings (for each period)
- **Color**: Line color
- **Line Style**: Solid, Dashed, Dotted
- **Line Width**: 1-5
- **Lookback**: How many periods to display (1-10)

#### Label Configuration
- **Enable Labels**: Show/hide labels
- **Label Text**: Custom text (e.g., "PDH", "PWH", "PMH")
- **Label Position**: Left or Right
- **Gradient Effect**: Fade older periods

**Default Labels**:
- Daily: PDH, PDL
- Weekly: PWH, PWL
- Monthly: PMH, PML

---

### Higher Timeframe Candles Configuration

#### HTF Slot Configuration
**5 Independent Slots** - Each with:
- **Enable**: ON/OFF toggle
- **Timeframe**: Select any timeframe (e.g., "5", "15", "60", "240", "D")
- **Label**: Custom name for this HTF

**Default HTF Slots**:
1. 5m (5-minute candles)
2. 15m (15-minute candles)
3. 1H (1-hour candles)
4. 4H (4-hour candles)
5. Daily (Daily candles)

#### HTF Display Elements
- **Show HTF Candles**: Master toggle for all HTF
- **Show OHLC Lines**: Display Open/High/Low/Close levels
- **Show Trace Lines**: Connect HTF levels to formation bars
- **Show HTF Timer**: Countdown to next candle close
- **Show Interval Labels**: Day/time labels on candles

#### HTF Candle Styling
- **Bullish Color**: Color for up candles
- **Bearish Color**: Color for down candles
- **Line Width**: 1-5
- **Border Width**: Border thickness
- **Border Style**: Solid, Dashed, Dotted

#### HTF Imbalance Detection
- **Show FVG (Fair Value Gaps)**: Detect and display FVGs
- **FVG Color**: Color for FVG boxes
- **FVG Transparency**: 0-100
- **Show VI (Volume Imbalance)**: Detect and display VIs
- **VI Color**: Color for VI boxes
- **VI Transparency**: 0-100

#### HTF Layout Control
- **Candle Offset**: Horizontal spacing from current bar
- **Candle Buffer**: Vertical spacing between HTF candles
- **Candle Spacing**: Gap between individual candles
- **Daily Open**: Choose Midnight, 8:30, or 9:30 for daily open

#### HTF Label Settings
- **Show HTF Name**: Display HTF label (e.g., "5m", "1H")
- **Show HTF Timer**: Display countdown timer
- **Label Size**: Font size
- **Label Color**: Text color
- **Label Position**: Top, Middle, Bottom

---

## 💡 Usage Examples

### Example 1: Day Trading Setup
**Goal**: Track intraday sessions with HTF context

**Configuration**:
- Enable all 3 sessions (Asian, London, NY)
- Enable all kill zones
- Show Daily high/low (PDH/PDL)
- Enable 5m and 15m HTF candles
- Watermark: "EURUSD | 5m | Scalping"

**Result**: Full session visualization with immediate HTF context

---

### Example 2: Swing Trading Setup
**Goal**: Multi-day perspective with key levels

**Configuration**:
- Disable sessions and kill zones
- Enable Weekly and Monthly H/L
- Enable 4H and Daily HTF candles
- Watermark: Custom trading plan
- Lookback: 5 periods for W/M levels

**Result**: Clean chart focused on major levels and HTF structure

---

### Example 3: ICT Kill Zone Focus
**Goal**: Trade only during specific kill zones

**Configuration**:
- Disable sessions background (keep lines)
- Enable all kill zones with high visibility
- Enable session high/low lines
- Enable 1H and 4H HTF for context
- FVG detection ON

**Result**: Highlighted kill zones with HTF context and FVG opportunities

---

### Example 4: Multi-Timeframe Analysis
**Goal**: Complete HTF structure analysis

**Configuration**:
- Enable all 5 HTF slots
- Enable FVG and VI detection for all
- Enable trace lines
- Show HTF timers
- Custom HTF: 5m, 15m, 1H, 4H, D

**Result**: Complete view of market structure across 5 timeframes

---

### Example 5: Clean Minimal Setup
**Goal**: Just watermark and key levels

**Configuration**:
- Disable all sessions and kill zones
- Enable only Daily H/L
- Disable all HTF candles
- Watermark with trading plan

**Result**: Ultra-clean chart with just key reference levels

---

## 🎨 Customization Tips

### Color Schemes

**Professional Dark Theme**:
- Sessions: Subtle blues/grays
- Kill Zones: High transparency (90%)
- HTF: Contrasting colors (green/red)
- Watermark: Low transparency (30%)

**High Visibility Theme**:
- Sessions: Bright colors (yellow/blue/green)
- Kill Zones: Medium transparency (70%)
- HTF: Bold colors
- Watermark: High transparency (60%)

### Performance Tips

1. **Reduce Drawing Limit**: Set to 1-2 days if chart is slow
2. **Disable Unused Features**: Turn off HTF slots you don't use
3. **Limit HTF Candles**: Enable only 2-3 HTF slots
4. **Reduce Lookback**: Set to 1-3 periods for previous levels
5. **Disable Trace Lines**: Turn off if not needed

### Layout Tips

1. **HTF Offset**: Increase to move HTF candles right for clarity
2. **HTF Buffer**: Increase for more vertical spacing
3. **HTF Spacing**: Adjust gap between individual candles
4. **Label Position**: Use "Left" to keep right side clean

---

## 🔧 Technical Details

### Performance Optimizations
- **Single Table Instance**: Watermark uses one table for minimal overhead
- **Array-Based Tracking**: Efficient multi-day session/period management
- **Drawing Limits**: Prevents chart overload with configurable limits
- **Last Bar Updates**: Most calculations only on `barstate.islast`
- **Optimized Loops**: Minimal iteration for HTF candle rendering

### Compatibility
- **Pine Script**: v6
- **TradingView**: All chart types
- **Symbols**: Stocks, Forex, Crypto, Futures, Indices
- **Timeframes**: Works on all timeframes (HTF validates automatically)

### Limitations
- **Drawing Limits**: Max 500 lines/boxes/labels per indicator (TradingView limit)
- **HTF Slots**: Maximum 5 HTF timeframes
- **Session History**: Limited by "Drawing Limit" setting (1-10 days)
- **Timezone**: Manual DST adjustment required

---

## 🐛 Troubleshooting

### Watermark Not Showing
- ✅ Check "Show Watermark" is enabled
- ✅ Verify transparency is not 100%
- ✅ Ensure at least one content option is enabled
- ✅ Check text color contrasts with chart background

### Sessions Not Displaying
- ✅ Check "Show All Sessions" is enabled
- ✅ Verify individual session toggles are ON
- ✅ Confirm session times are correct for your timezone
- ✅ Check if chart timeframe is appropriate

### HTF Candles Not Showing
- ✅ Ensure "Show HTF Candles" master toggle is ON
- ✅ Verify individual HTF slot is enabled
- ✅ Check HTF timeframe is HIGHER than chart timeframe
- ✅ Confirm HTF timeframe is valid (e.g., "5", "15", "60", "D")

### Previous Period Levels Missing
- ✅ Check "Show Previous Period H/L" is enabled
- ✅ Verify individual period (D/W/M) is enabled
- ✅ Ensure lookback is set to 1 or higher
- ✅ Confirm chart timeframe is appropriate (lower than period)

### Performance Issues
- ✅ Reduce "Drawing Limit" to 1-2 days
- ✅ Disable unused HTF slots
- ✅ Turn off FVG/VI detection if not needed
- ✅ Reduce lookback for previous periods
- ✅ Disable trace lines

---

## 📋 Version History

### v3.2.1 (2025-11-30) - Bug Fix
- **Fixed**: HTF visibility on non-divisible timeframes
  - M5 HTF now shows on M3, M2, M1 charts
  - Simplified `ValidTimeframe()` function
  - All higher timeframes now display correctly

### v3.2.0 (2025-11-30) - Phase 3B Complete
- **Added**: 5 configurable HTF candle slots
- **Added**: Fair Value Gap (FVG) detection
- **Added**: Volume Imbalance (VI) detection
- **Added**: Trace lines for HTF OHLC
- **Added**: HTF timer with countdown
- **Added**: Interval value labels
- **Added**: Custom daily open options
- **Added**: Flexible layout system

### v3.1.1 (2025-11-29) - Bug Fix
- **Fixed**: Array size management off-by-one error
- Now correctly displays N periods when lookback = N

### v3.1.0 (2025-11-29) - Period Labels
- **Added**: Customizable label text for period H/L
- **Added**: Label position control (Left/Right)
- **Added**: Gradient effect for labels
- **Added**: Independent label array management

### v3.0.0 (2025-11-28) - Phase 3 Complete
- **Added**: Daily/Weekly/Monthly H/L lines
- **Added**: Line style selection per period
- **Added**: Line width control per period
- **Added**: Lookback controls
- **Added**: Gradient effect for older periods
- **Added**: Array-based period tracking

### v2.3.0 (2025-11-27) - Phase 2 Complete
- **Added**: Session visualization (Asian, London, NY)
- **Added**: Kill zone boxes
- **Added**: Universal timezone support
- **Added**: Multi-day history tracking

### v1.0.0 (2025-11-23) - Phase 1 Complete
- **Added**: Customizable watermark
- **Added**: Symbol and timeframe display
- **Added**: Subtitle cells
- **Added**: Full style customization

---

## 📖 Development

### Project Structure
```
obsidian/
├── oneforall.pine          # Main indicator file
├── README.md               # This file
├── CHANGELOG.md            # Detailed version history
├── CLAUDE.md               # Developer guidance
└── docs/                   # Additional documentation
    ├── INSTALLATION.md
    ├── INDEX.md
    └── development/        # Developer resources
```

### Contributing
This project is maintained by theCodeman. For suggestions or issues, please refer to the project repository.

### Development Tools
- **Language**: Pine Script v6
- **Platform**: TradingView
- **Testing**: Manual testing in TradingView required
- **Version Control**: Git

---

## 📄 License

This indicator is provided as-is for personal and educational use on TradingView.

---

## 🙏 Acknowledgments

Built with modern Pine Script v6 features and best practices. Incorporates ICT (Inner Circle Trader) concepts and methodologies.

---

## 🎯 Quick Start Checklist

1. ✅ Install indicator in TradingView
2. ✅ Set your timezone in Settings
3. ✅ Configure watermark with your trading plan
4. ✅ Enable sessions/kill zones you trade
5. ✅ Add HTF candles for your timeframe
6. ✅ Customize colors and styles
7. ✅ Start trading with One for All!

---

**One for All** - Everything you need, all in one indicator.

Author: theCodeman
Version: 3.2.1
Built with: Pine Script v6
