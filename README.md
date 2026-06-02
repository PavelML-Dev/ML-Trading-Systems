# 🤖 ML SuperTrend Ultimate: Deep Q-Learning + (Novier-Stokes xortex + mp4 expls)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Pine Script](https://img.shields.io/badge/Pine%20Script-v6-blue.svg)](https://www.tradingview.com/pine-script-docs/)
[![TradingView](https://img.shields.io/badge/TradingView-Compatible-green.svg)](https://www.tradingview.com/)
[![Made in Russia](https://img.shields.io/badge/Made%20in-Russia%20🇷🇺-blue.svg)](https://en.wikipedia.org/wiki/Russia)

> **First fully-working LSTM + Deep Q-Network trading system implemented in Pine Script!**

A self-learning trading agent that uses cutting-edge machine learning techniques to adapt to market conditions in real-time — no external libraries, no Python, just pure Pine Script.

---

## 🔥 What Makes This Unique?

This is **NOT just another indicator**. This is a complete **reinforcement learning system** that:

- ✅ **Learns from experience** using Deep Q-Learning
- ✅ **Remembers patterns** with LSTM neural networks
- ✅ **Adapts in real-time** without retraining
- ✅ **Prioritizes important data** with PER (Prioritized Experience Replay)
- ✅ **Works in your browser** — no GPU, no Python, no servers

### Why It's Special

| Traditional Indicators | ML SuperTrend Ultimate |
|----------------------|------------------------|
| Static parameters | **Learns optimal parameters** |
| Same for all markets | **Adapts to each market** |
| Looks at 1-2 bars | **Analyzes 8-20 bars history** |
| Simple rules | **Deep neural networks** |
| No learning | **Continuous learning** |

---

## ⚠️ DISCLAIMER

**This is an experimental research project for educational purposes.**

- **NOT financial advice**
- **NO profit guarantees** 
- Use at **your own risk**
- Author bears **NO responsibility** for any losses

This is a learning tool, not a production trading system. Always backtest thoroughly and use proper risk management.

---

## 📖 What's Inside?

### 🧠 Deep Q-Network (DQN)
The "brain" that makes trading decisions.

- **8 possible actions** (ATR multipliers: 0.3 → 1.5)
- **4-layer MLP** (Multi-Layer Perceptron): 24 → 16 → 8 → 4 neurons
- **Q-values** predict expected reward for each action
- **Epsilon-greedy** exploration (10% → 2% decay)

### 🔮 LSTM Neural Network
Understands temporal patterns and market context.

- **24 hidden units** (configurable)
- **Dynamic timesteps** (8-20 bars, adapts to volatility)
- **4 gates**: Forget, Input, Cell, Output
- **Backpropagation Through Time (BPTT)**

### 💾 Prioritized Experience Replay (PER)
Smart memory that focuses on important lessons.

- **70,000 state buffer** (replay memory)
- **Prioritized sampling** based on TD-error
- **Importance sampling** for bias correction
- **Beta annealing** (0.4 → 1.0)

### 🎯 Adam Optimizer
State-of-the-art optimization for neural networks.

- **Adaptive learning rate** (starts at 0.01)
- **Momentum** + **RMSprop** combined
- **Gradient clipping** for stability
- **Per-parameter learning rates**

### 📊 Rich Feature Set
20+ features extracted from market data:

- Technical: RSI, MACD, ATR, Stochastic
- Volume: OBV, Volume Rate of Change
- Advanced: Ichimoku, VWAP, Hurst proxy
- Volatility: Heidelberg index, ATR ratios
- Custom: NN confidence, entropy

---

## 🏗 Architecture Overview

```
Market Data
    ↓
[Feature Extraction] → 20 features
    ↓
[LSTM Layer] → Temporal patterns (8-20 timesteps)
    ↓
[MLP Network] → 24→16→8→4 neurons
    ↓
[Q-Values] → 8 actions (ATR multipliers)
    ↓
[Action Selection] → Epsilon-greedy
    ↓
[SuperTrend] → Adaptive coefficient
    ↓
Trading Signals
    ↓
[Reward] → (close - entry) / episode_length
    ↓
[Experience Replay] → Store in buffer (70k states)
    ↓
[PER Sampling] → Prioritize high TD-error
    ↓
[Backpropagation] → Update Q-network
    ↓
[LSTM BPTT] → Update LSTM weights
```

---

## ⚡ Key Features

### 1. **Real-Time Learning**
- No pre-training needed
- Learns continuously as market evolves
- TD-Error-driven updates

### 2. **Adaptive Parameters**
- ATR multiplier: 0.3 - 1.5 (agent selects)
- LSTM timesteps: 8-20 (volatility-based)
- Learning rate: adaptive (0.001 - 0.05)

### 3. **Advanced Techniques**
- Priority Experience Replay (PER)
- Backpropagation Through Time (BPTT)
- Gradient clipping
- Adaptive Hinge Loss with L2 penalty
- Dual-kernel CNN filter

### 4. **Robust Design**
- Dropout (0.3) prevents overfitting
- L2 regularization (0.0008 MLP, 0.0003 LSTM)
- Leaky ReLU activation (no vanishing gradients)
- Epsilon decay (0.10 → 0.02)

---

## 🔬 Technical Specifications

### Reinforcement Learning Parameters

```yaml
State Space: 20-dimensional vector (5 features × 4 timesteps)
Action Space: 8 discrete actions [0.3, 0.4, 0.5, 0.7, 0.9, 1.0, 1.2, 1.5]
Reward Function: (close - entry_price) / episode_length
Discount Factor (γ): 0.99
Epsilon: 0.10 → 0.02 (decay: 0.999)
Training Frequency: Every 10 bars
```

### Network Architecture

```yaml
LSTM:
  Hidden Size: 8 (default, configurable)
  Timesteps: 8-20 (dynamic)
  Gates: Forget, Input, Cell, Output
  Activation: tanh (gates), sigmoid (cell)

MLP (DQN):
  Input: 20 features
  Layer 1: 24 neurons (Leaky ReLU)
  Layer 2: 16 neurons (Leaky ReLU)
  Layer 3: 8 neurons (Leaky ReLU)
  Layer 4: 4 neurons (Leaky ReLU)
  Output: 8 Q-values (linear)

Dropout: 0.3
L2 Lambda: 0.0008 (MLP), 0.0003 (LSTM)
```

### Experience Replay

```yaml
Buffer Size: 70,000 transitions
Batch Size: 6 samples
Priority Alpha (α): 0.6
Priority Beta (β): 0.4 → 1.0 (annealing)
Priority Epsilon: 1e-5
```

### Optimizer

```yaml
Type: Adam
Learning Rate: 0.01 (adaptive: 0.001 - 0.05)
Beta1: 0.9 (momentum)
Beta2: 0.999 (RMSprop)
Epsilon: 1e-8
Gradient Clip: 1.0
```

---

## 🚀 Quick Start

### Installation (TradingView)

1. Open [TradingView](https://www.tradingview.com)
2. Navigate to Pine Editor (bottom panel)
3. Create new indicator
4. Copy-paste code from `ml_supertrend_ultimate.pine`
5. Click "Add to Chart"

### First Run

1. **Initial training**: Wait for 200-500 updates
2. **Monitor EMA Error**: Should decrease over time
3. **Watch TD-Error**: Convergence indicator
4. **Enable debug panel**: See learning metrics

### Recommended Settings

```yaml
Timeframe: H1 (1 hour) or H4 (4 hours)
Asset: BTC, ETH, major forex pairs
History: At least 1000 bars for initial training
Auto Optimize: Enabled
Show Debug Panel: Enabled (while learning)
```

---

## 📊 Performance Metrics

The system tracks several metrics to show learning progress:

### Training Metrics

- **TD-Error**: Should decrease from ~0.5 to <0.1
- **EMA Error**: Smoothed error, should converge
- **Update Count**: Number of gradient updates
- **Epsilon**: Exploration rate (10% → 2%)

### Q-Value Metrics

- **Avg Max Q**: Average of maximum Q-values
- **Avg Old Q**: Average of current Q-predictions
- **Avg Target Q**: Average of target Q-values
- **Zero TD Count**: How many samples have TD-error ≈ 0

### Example Learning Curve

```
Updates 0-500:
  TD-Error: 0.5 → 0.3 (high, exploring)
  EMA Error: 0.7 → 0.5 (decreasing)
  Epsilon: 0.10 → 0.08 (still exploring)

Updates 500-2000:
  TD-Error: 0.3 → 0.15 (converging)
  EMA Error: 0.5 → 0.2 (good convergence)
  Epsilon: 0.08 → 0.04 (exploitation phase)

Updates 2000+:
  TD-Error: 0.15 → 0.05 (converged!)
  EMA Error: 0.2 → 0.1 (stable)
  Epsilon: 0.04 → 0.02 (minimal exploration)
```

---

## 🎓 Educational Value

Perfect for learning:

- How **LSTM** networks work
- **Deep Q-Learning** implementation from scratch
- **Reinforcement Learning** for trading
- **Neural network training** (Adam, BPTT)
- **Experience Replay** and prioritization
- Advanced ML techniques in constrained environment

### Code Structure

```
📁 Project Root
├── 📄 ml_supertrend_ultimate.pine  (Main indicator)
├── 📄 README.md                     (This file)
├── 📄 LICENSE                       (MIT)
├── 📄 CHANGELOG.md                  (Version history)
├── 📁 docs/
│   ├── 📄 ARCHITECTURE.md          (Detailed architecture)
│   ├── 📄 TRAINING.md              (Training guide)
│   ├── 📄 FAQ.md                   (Common questions)
│   └── 📄 RESEARCH.md              (Research notes)
└── 📁 images/
    ├── 🖼️ screenshot_1.png         (Trading signals)
    ├── 🖼️ screenshot_2.png         (Debug panel)
    └── 🖼️ architecture.png         (System diagram)
```

---

## 🤝 Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### Ways to Contribute

- 🐛 **Bug reports** - Found an issue? Open an issue!
- 💡 **Feature requests** - Have an idea? Share it!
- 📝 **Documentation** - Improve README, add examples
- 🔧 **Code** - Submit pull requests
- ⭐ **Star the repo** - Show your support!

### Development

```bash
git clone https://github.com/YOUR_USERNAME/ml-supertrend-ultimate.git
cd ml-supertrend-ultimate
# Edit ml_supertrend_ultimate.pine
# Test on TradingView
# Submit pull request
```

---

## 📚 References

This project implements techniques from cutting-edge research:

1. **Deep Q-Learning**
   - [Playing Atari with Deep Reinforcement Learning](https://arxiv.org/abs/1312.5602) (Mnih et al., 2013)

2. **Prioritized Experience Replay**
   - [Prioritized Experience Replay](https://arxiv.org/abs/1511.05952) (Schaul et al., 2015)

3. **LSTM Networks**
   - [Long Short-Term Memory](https://www.bioinf.jku.at/publications/older/2604.pdf) (Hochreiter & Schmidhuber, 1997)

4. **Adam Optimizer**
   - [Adam: A Method for Stochastic Optimization](https://arxiv.org/abs/1412.6980) (Kingma & Ba, 2014)

---

## 📞 Contact & Support

- **GitHub Issues**: [Report bugs or request features](https://github.com/YOUR_USERNAME/ml-supertrend-ultimate/issues)
- **GitHub Discussions**: [Ask questions, share ideas](https://github.com/YOUR_USERNAME/ml-supertrend-ultimate/discussions)
- **Email**: sail-com@mail.ru

---

## ⭐ Show Your Support

If you find this project useful:

- ⭐ **Star the repository**
- 🔄 **Share with others**
- 📝 **Write about it**
- 🤝 **Contribute**

---

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2025 [Diogenov Pavel]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

[Full MIT License text in LICENSE file]
```

---

## 🙏 Acknowledgments

- **Created with**: Claude Sonnet 4.5 by Anthropic 🤖
- **Inspired by**: DeepMind's DQN research
- **Built in**: Altai Krai, Barnaul, Russia 🇷🇺
- **For**: The trading & ML community 🌍

---

## 📈 Roadmap

### v1.0 (Current)
- ✅ LSTM + DQN implementation
- ✅ Prioritized Experience Replay
- ✅ Adam optimizer
- ✅ Real-time training

### v1.1 (Planned)
- [ ] Multi-asset support
- [ ] Improved reward shaping
- [ ] Advanced visualization
- [ ] Performance analytics

### v2.0 (Future)
- [ ] Dueling DQN architecture
- [ ] Double Q-Learning
- [ ] Rainbow DQN
- [ ] Attention mechanisms

---

<div align="center">

**Made with ❤️ in Russia 🇷🇺**

**Star ⭐ this repo if you found it useful!**

[![Star History Chart](https://api.star-history.com/svg?repos=YOUR_USERNAME/ml-supertrend-ultimate&type=Date)](https://star-history.com/#YOUR_USERNAME/ml-supertrend-ultimate&Date)

</div>
