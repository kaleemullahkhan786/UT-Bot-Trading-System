# UT Bot Trading System - Professional MT4 EA & Indicator Suite

<div align="center">

![Version](https://img.shields.io/badge/version-5.0-blue.svg)
![Platform](https://img.shields.io/badge/platform-MetaTrader%204-green.svg)
![License](https://img.shields.io/badge/license-Commercial-red.svg)
![Status](https://img.shields.io/badge/status-Active-success.svg)

**A Professional Automated Trading System for MetaTrader 4**

*Advanced Algorithm with Smart Signal Generation & Risk Management*

[Features](#-features) • [Installation](#-installation) • [Usage](#-usage) • [Screenshots](#-screenshots) • [Contact](#-contact)

</div>

---

## 📋 Overview

**UT Bot Trading System** is a sophisticated, fully automated trading solution for MetaTrader 4 that combines advanced technical analysis with intelligent trade management. The system consists of two powerful components:

- **UT Bot Alerts Indicator** - Smart signal generator with multiple confirmation filters
- **UT Bot Phase EA** - Intelligent Expert Advisor that executes trades based on indicator signals

This professional-grade trading system is designed for serious traders who demand precision, reliability, and consistent performance across various market conditions.

---

## ✨ Features

### 🎯 Indicator Features

- **Smart Signal Generation**
  - Real-time signal detection using live Bid/Ask prices
  - Multiple confirmation filters (Volume, Momentum, ADX, Multi-Timeframe)
  - Trend consistency validation
  - Breakout detection with customizable thresholds

- **Advanced Filtering System**
  - Volume confirmation (configurable multiplier)
  - Momentum indicators for trend strength
  - ADX filter for trend confirmation
  - Higher timeframe trend alignment
  - Volatility floor requirements

- **Customizable Settings**
  - Adjustable sensitivity (Key Value)
  - ATR period customization
  - Heikin Ashi candle support
  - Strict/Relaxed trend filter modes
  - Breakout threshold configuration

### 🤖 EA Features

- **Signal-Based Trading**
  - Purely signal-driven (no discretionary trading)
  - Automatic trade opening on indicator signals
  - Automatic trade closing on opposite signals
  - No trailing stops or manual interference

- **Risk Management**
  - Configurable lot sizing (Fixed or Risk-Based)
  - Risk percentage per trade
  - Initial stop loss (virtual calculation)
  - Slippage protection

- **Smart Trade Management**
  - Phase-based trading system (BUY/SELL phases)
  - Prevents duplicate trades
  - Session time filtering (optional)
  - Magic number isolation

- **Professional Features**
  - Real-time info panel display
  - Trade statistics tracking
  - Detailed logging for debugging
  - Sound alerts for signal detection

---

## 🚀 Installation

### Requirements

- **MetaTrader 4** (Build 600+ recommended)
- Windows 7/8/10/11 or compatible Windows Server
- Active internet connection for live trading
- Trading account with a MetaTrader 4 broker

### Installation Steps

1. **Download the Files**
   ```bash
   # Clone or download the repository
   git clone https://github.com/yourusername/ut-bot-trading-system.git
   ```

2. **Install Indicator**
   - Copy `OriginalIndicator.mq4` to: `MT4_Folder/MQL4/Indicators/`
   - Restart MetaTrader 4 or compile from MetaEditor (F7)

3. **Install Expert Advisor**
   - Copy `UT_Bot_Phase_EA.mq4` to: `MT4_Folder/MQL4/Experts/`
   - Restart MetaTrader 4 or compile from MetaEditor (F7)

4. **Enable AutoTrading**
   - In MT4, ensure "AutoTrading" button is enabled (green)
   - Allow DLL imports if prompted (not required by default)

5. **Attach to Chart**
   - Open your desired chart (recommended: H1 or H4 timeframe)
   - Drag `OriginalIndicator` from Navigator → Indicators → Custom
   - Drag `UT_Bot_Phase_EA` from Navigator → Expert Advisors → Custom

---

## 📖 Usage

### Indicator Setup

1. **Initial Configuration**
   ```
   Key Value: 1.0 (adjust for sensitivity)
   ATR Period: 10
   Use Heikin Ashi: false (recommended)
   ```

2. **Advanced Filters** (Optional but Recommended)
   ```
   Use Strict Filter: true
   Trend Strength: 2 (Medium)
   Detect Breakouts: true
   Breakout Threshold: 1.5
   ```

3. **Signal Settings**
   ```
   Min Bars Between Signals: 5
   Use Volume Filter: true
   Use Momentum Filter: true
   Use ADX Filter: true
   ```

### EA Setup

1. **Trade Settings**
   ```
   Main Trade Lot Size: 0.01 (default for Gold/XAUUSD)
   Main Initial Stop Loss: 40 (pips - virtual only)
   Use Risk Based Lot Sizing: true (recommended)
   Risk Per Trade: 1.0 (%)
   ```

2. **Session Filter** (Optional)
   ```
   Use Session Filter: false (or enable for specific hours)
   Session Start Hour: 7
   Session End Hour: 20
   ```

3. **Display Settings**
   ```
   Show Info Panel: true
   Panel Colors: Customize as per preference
   ```

### Recommended Settings for XAUUSD (Gold)

- **Timeframe**: H1 (1 Hour)
- **Lot Size**: 0.01 (start small, scale gradually)
- **Risk Per Trade**: 1-2%
- **ATR Period**: 10-14
- **Key Value**: 1.0-1.5

---

## 📊 Screenshots

### Indicator Signals on Chart
*[Screenshot showing BUY/SELL signals on XAUUSD H1 chart]*

### EA Info Panel
*[Screenshot showing EA panel with trade statistics]*

### Trade Execution
*[Screenshot showing open trades and profit tracking]*

> **Note**: Actual screenshots will be added based on live trading results.

---

## ⚙️ Technical Details

### Indicator Architecture

- **Language**: MQL4
- **Type**: Custom Indicator (Chart Window)
- **Buffers**: 3 (ATR Line, Buy Signals, Sell Signals)
- **Calculation**: OnCalculate() - optimized for real-time updates

### EA Architecture

- **Language**: MQL4
- **Type**: Expert Advisor
- **Execution**: OnTick() - every price tick
- **Signal Detection**: Global Variables (fast, reliable)
- **Trade Management**: OrderSend(), OrderClose()

### Signal Communication

The system uses **Global Variables** for fast, reliable communication between Indicator and EA:

- `UTBOT_SIGNAL_SYMBOL_TIMEFRAME` - Signal type (1.0 = BUY, -1.0 = SELL)
- `UTBOT_SIGNAL_TIME_SYMBOL_TIMEFRAME` - Signal timestamp

This method ensures:
- ✅ Zero lag between signal generation and trade execution
- ✅ Works across multiple charts/symbols
- ✅ No file I/O overhead
- ✅ Thread-safe communication

---

## 🎓 Trading Strategy

### Entry Conditions

**BUY Signal Generated When:**
- Price crosses above ATR Trailing Stop line
- Volume confirmation (above average)
- Momentum indicators align bullish
- Higher timeframe trend supports
- ADX indicates trending market

**SELL Signal Generated When:**
- Price crosses below ATR Trailing Stop line
- Volume confirmation (above average)
- Momentum indicators align bearish
- Higher timeframe trend supports
- ADX indicates trending market

### Exit Conditions

- **Automatic**: Opposite signal triggers trade close
- **Manual**: User can manually close trades anytime
- **No SL/TP**: Trades managed purely by signal logic (no hard stop loss/take profit)

---

## 🔒 Risk Disclaimer

**⚠️ IMPORTANT RISK WARNING**

- Trading forex, CFDs, and other financial instruments carries substantial risk
- Past performance does not guarantee future results
- This system is a tool, not a guarantee of profits
- Always trade with money you can afford to lose
- Test thoroughly on demo accounts before live trading
- Market conditions can change, affecting system performance
- No trading system can guarantee profits or eliminate risk

**The developer assumes no responsibility for trading losses or damages resulting from the use of this software.**

---

## 📝 Changelog

### Version 5.0 (Latest)
- ✨ Complete rewrite with advanced filtering system
- 🚀 Real-time signal detection (no candle-close wait)
- 🎯 Pure signal-based trading (EA trades only on indicator signals)
- 📊 Enhanced risk management features
- 🐛 Fixed multiple signal generation issues
- ⚡ Optimized performance and memory usage

### Version 4.x
- Initial release with basic signal generation
- ATR-based trailing stop implementation

---

## 🤝 Support & Contact

For questions, support, or commercial inquiries:

### 📞 Contact Information

- **WhatsApp**: [+92 314 712 1270](https://wa.me/923147121270)
- **Email**: [kaleemullahkhan.contact@gmail.com](mailto:kaleemullahkhan.contact@gmail.com)

### 📧 Support Channels

- **Technical Issues**: Email with subject "UT Bot - Technical Issue"
- **Purchase Inquiries**: Email with subject "UT Bot - Purchase Inquiry"
- **Custom Development**: WhatsApp or Email for quotes

### ⏰ Response Time

- **WhatsApp**: Usually within 24 hours
- **Email**: Within 48 hours (business days)

---

## 📄 License

This software is **commercial** and **proprietary**. 

**Usage Rights:**
- ✅ Personal use (single account)
- ✅ Commercial use (with appropriate license)
- ❌ Redistribution or resale without permission
- ❌ Reverse engineering or decompilation
- ❌ Sharing source code or compiled files

**For licensing inquiries, please contact via email or WhatsApp.**

---

## 🌟 Reviews & Testimonials

*Coming soon - Add your testimonials here!*

---

## 🗺️ Roadmap

### Future Enhancements

- [ ] Multi-currency portfolio management
- [ ] Advanced backtesting suite
- [ ] Cloud-based signal synchronization
- [ ] Mobile app for monitoring
- [ ] Web dashboard for analytics
- [ ] Telegram/Discord signal notifications
- [ ] Multi-account management
- [ ] Advanced risk calculators

---

## 🙏 Acknowledgments

Special thanks to all beta testers and early adopters who provided valuable feedback for improving this trading system.

---

<div align="center">

**Built with ❤️ for Serious Traders**

*Trade Smart. Trade Safe. Trade with Confidence.*

[⬆ Back to Top](#ut-bot-trading-system---professional-mt4-ea--indicator-suite)

</div>
