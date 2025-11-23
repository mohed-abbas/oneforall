# 🖤 Obsidian - TradingView All-in-One Indicator

**Version**: 1.0.0 (Phase 1)
**Platform**: TradingView
**Language**: Pine Script v6

---

## 📖 Overview

Obsidian is a multi-purpose TradingView indicator designed as a clean foundation for future advanced trading tools. Phase 1 provides a simple, elegant watermark-style chart overlay with full customization capabilities.

### ✨ Phase 1 Features

- ✅ **Two-Line Watermark**: Clean overlay fixed at top center of chart with dual-line display
- ✅ **Title Line**: Display symbol, timeframe, and/or custom title text
- ✅ **Subtitle Cells**: Up to 3 customizable subtitle fields with pipe separators
- ✅ **Auto-Refresh**: Automatically updates when switching symbols or timeframes
- ✅ **Full Style Control**: Customize color, transparency, size, and position
- ✅ **Performance Optimized**: Single table instance for minimal CPU usage
- ✅ **Clean UI**: Organized grouped inputs for intuitive configuration

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

### Display Settings

**Show Watermark**
- Toggle watermark visibility on/off
- Default: `ON`

### Content Settings

**Line 1 (Title)**

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

**Line 2 (Subtitles)**

**Subtitle 1, 2, 3**
- Add up to 3 subtitle cells for the second line
- Separated by pipe characters "|"
- Example: "Entry: 45000 | Stop: 44000 | Target: 48000"
- Default: `Empty`

### Style Settings

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

## 💡 Usage Examples

### Basic Setup
1. Add Obsidian to your chart
2. Watermark displays symbol and timeframe by default
3. Adjust transparency for optimal visibility on your chart background

### Two-Line Trading Display
1. Line 1 (Title): Shows "BTCUSD | 1H | Trade Setup A"
2. Line 2 (Subtitles): Enter "Entry: 45000", "Stop: 44000", "Target: 48000"
3. Result:
   - Line 1: `BTCUSD | 1H | Trade Setup A`
   - Line 2: `Entry: 45000 | Stop: 44000 | Target: 48000`
4. Change symbol/timeframe → line 1 auto-updates

### Minimal Display
1. Disable "Show Symbol"
2. Disable "Show Timeframe"
3. Enter title text and subtitles only
4. Result: Clean custom two-line text overlay

### Style Customization
1. Choose your preferred text color
2. Adjust transparency for chart background compatibility
3. Select font size based on chart resolution
4. Choose position (left for annotations, right for status displays)

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

### Phase 2: ICT Kill Zones & Sessions (Future)
- London/New York/Asia session boxes
- Kill zone highlighting
- Session high/low markers

### Phase 3: Market Structure (Future)
- Fair Value Gaps (FVG) detection
- Liquidity zone identification
- Order blocks
- Market structure breaks

### Phase 4: Alerts & Presets (Future)
- Custom alert conditions
- Preset configurations
- Widget system

### Phase 5: Full Trading Suite (Future)
- Theme system
- Advanced customization
- Multi-indicator coordination

---

## ✅ Acceptance Criteria (Phase 1)

| Criterion | Status |
|-----------|--------|
| Watermark displays correctly | ✅ |
| Custom text updates live | ✅ |
| Symbol auto-updates | ✅ |
| Timeframe auto-updates | ✅ |
| Style controls functional | ✅ |
| Only one label instance | ✅ |
| Toggle hides label | ✅ |
| No script errors | ✅ |
| Works all symbols/timeframes | ✅ |

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

### v1.0.0 - Phase 1 (2025-11-23)
- ✨ Initial release
- ✅ Customizable watermark overlay
- ✅ Symbol and timeframe display
- ✅ Custom notes support
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
