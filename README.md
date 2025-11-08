# 🚀 ML SuperTrend Ultimate: Q-Learning + LSTM + PER

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Pine Script](https://img.shields.io/badge/Pine%20Script-v6-blue.svg)](https://www.tradingview.com/pine-script-docs/)
[![TradingView](https://img.shields.io/badge/TradingView-Published-green.svg)](https://www.tradingview.com/)

**Not just an adaptive SuperTrend.** A self-learning trading system with reinforcement learning agent that learns optimal parameters in real-time.

---

## ⚠️ DISCLAIMER

**This is an experimental research project, NOT a ready-to-use trading system.**

- Provided for **educational purposes only**
- **NOT financial advice**
- **NO profit guarantees**
- Use entirely **at your own risk**
- Author bears **no responsibility** for financial losses

---

## 📖 What Is This?

A **trading system with reinforcement learning agent** that learns to select optimal SuperTrend coefficients in real-time.

Instead of static parameters:
- **Q-Learning (QL) agent** selects the optimal ATR multiplier
- **Learns from experience** through Priority Experience Replay (PER)
- **Uses LSTM** to understand temporal context
- **Adapts to the market** without your intervention

---

## 🧠 Architecture

### Three Levels of Intelligence

#### 1. **Q-Learning (QL) — The Brain**
   - **Task:** Selects optimal SuperTrend coefficient (0.3 - 1.5)
   - **8 possible actions** (Q-values for each coefficient)
   - **ε-greedy exploration** with decay
   - **Reinforcement Learning:** Agent learns from rewards/penalties

#### 2. **Priority Experience Replay (PER) — Smart Memory**
   - **100,000 state buffer**
   - **Prioritized sampling:** Focus on large errors
   - **Importance Sampling:** Bias correction
   - **Mini-batch training:** 8 examples per batch

#### 3. **4-Layer LSTM — Long-Term Memory**
   - **Dynamic timesteps:** 8-20 bars (adapts to volatility)
   - **Backpropagation Through Time (BPTT)**
   - **Multi-gate architecture:** Forget, Input, Cell, Output gates
   - **Adam optimization** for all weights

#### 4. **4-Layer MLP — Feature Processing**
   - **20 input features:** RSI, MACD, ATR, Volume, Entropy, Ichimoku, OBV, VWAP, Hurst proxy, etc.
   - **Hidden layers:** 24 → 16 → 8 → 4 neurons
   - **Leaky ReLU activation**
   - **Dropout + L2 regularization**

#### 5. **SuperTrend Core**
   - **Adaptive ATR multiplier** (controlled by QL agent)
   - **K-Means++ clustering** (volatility regime detection)
   - **Multi-kernel filtering** (noise reduction)

---

## ⚡ Unique Features

### 1. **Real-Time Reinforcement Learning**
   - Agent learns to trade, not just follow rules
   - TD-Error guides learning

### 2. **Priority Experience Replay**
   - Focus on important errors
   - Beta annealing: 0.4 → 1.0

### 3. **Adaptive LSTM**
   - Volatility-based timestep adjustment
   - TD-Error-based adaptation

### 4. **Adam Optimizer**
   - Adaptive learning rate
   - Momentum + RMSprop

### 5. **Adaptive Hinge Loss**
   - Dynamic margin based on volatility
   - L2 penalty for overfitting prevention

### 6. **Dual-Kernel CNN Filter**
   - Short-term spikes + long-term trends
   - Z-score normalization

---

## 🔬 Technical Details

### Reinforcement Learning
- **State Space:** 20-dimensional (4 features × 5 bars)
- **Action Space:** 8 discrete actions (ATR multipliers 0.3-1.5)
- **Reward:** (close - entry) / episode_length
- **Gamma:** 0.99
- **Epsilon:** 0.10 with 0.999 decay

### Priority Experience Replay
- **Buffer Size:** 70,000 states
- **Batch Size:** 8 examples
- **Priority Alpha:** 0.6
- **Priority Beta:** 0.4 → 1.0
- **Training Frequency:** Every 10 bars

### LSTM Architecture
- **Hidden Size:** 8 neurons (configurable)
- **Timesteps:** 8-20 (dynamic)
- **Gates:** Forget, Input, Cell, Output
- **Optimizer:** Adam
- **Training:** BPTT with time unrolling

### MLP Architecture
- **Input:** 20 features
- **Layers:** 24 → 16 → 8 → 4 → Q-values (8)
- **Activation:** Leaky ReLU
- **Dropout:** 0.3
- **L2 Lambda:** 0.0008 (MLP), 0.0003 (LSTM)

---

## 🚀 How to Use

### TradingView

1. Go to TradingView
2. Open Pine Editor
3. Copy code from `supertrend_ql_lstm.pine`
4. Click "Add to Chart"
5. Adjust parameters as needed

### GitHub
# 🚀 6-Model ML Ensemble: Institutional-Grade Forecasting on Pine Script

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Pine Script](https://img.shields.io/badge/Pine%20Script-v6-blue.svg)](https://www.tradingview.com/pine-script-docs/)
[![TradingView](https://img.shields.io/badge/TradingView-Published-green.svg)](https://www.tradingview.com/)

**Not just a forecasting tool.** A self-learning ensemble system that adapts to market conditions in real-time.




