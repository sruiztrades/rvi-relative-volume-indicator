📊 RVI – Relative Volume Indicator (by @sruiztrades)

A custom Pine Script indicator that visualizes short-term volume strength relative to long-term historical volume using a dual-average model. Designed for traders who want to easily spot abnormal accumulation or distribution zones.

---

## 🔧 What It Does

- Uses a **6-bar EMA** of volume as the fast signal
- Compares it against a **200-bar SMA** baseline (adaptive average volume)
- **Color-codes volume bars** based on relative magnitude:
  - 🟤 **Light Taupe** → Volume > 1.5× trailing average (strong accumulation/distribution)
  - 🟡 **Beige-Gold** → Volume > average, but < 1.5× (moderate strength)
  - 🔵 **Deep Blue** → Volume < trailing average (low activity)
- Plots the trailing average as a translucent reference line
- Shown in a subpanel (like RSI or MACD)

---

## 📈 Example Use Case

- **Breakout Confirmation:** Strong light taupe bar → conviction
- **Accumulation Zones:** Series of beige bars in an uptrend → hidden buying
- **Avoid Choppy Entries:** Blue bars → dead zone, wait for volume confirmation

---

## 🧪 How It Works (Code Logic)

```pinescript
// 200-bar SMA as baseline volume
trail_avg_vol = ta.sma(volume, 200)

// 6-bar EMA as fast signal
fast_Average = ta.ema(volume, 6)

// Dynamic bar color logic
dyn_color = if (fast_Average > trail_avg_vol * 1.5)
    color.new(#afaaa0, 12)  // Light taupe, strong pressure
else if (fast_Average > trail_avg_vol)
    color.new(#c2b280, 24)  // Beige-gold, moderate strength
else
    color.new(#395ea1, 31)  // Deep blue, low volume

## 💡 Design Philosophy

This tool was created to solve a real problem I noticed as a young trader: volume is meaningless without context. Over years, I saw stocks shift between high and low liquidity regimes, making raw volume useless. By adapting to long-term baselines and highlighting deviations, this tool brings volume into context.

## 📷 Screenshot

<img width="1835" height="858" alt="GOOG_2025-07-25_16-54-08" src="https://github.com/user-attachments/assets/0f021efd-0fe5-4fb4-96fc-9b095954a1e1" />

