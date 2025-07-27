# 🧠 Civilization VII Turn Logger & Machine Learning Trainer

## 🎯 Project Overview

**Goal**: Create a plugin-based system to log detailed Civilization VII gameplay data in order to train machine learning models capable of learning and recommending optimal strategies for beating the game. The long-term vision is to build an AI assistant or self-play engine that can outperform even the most advanced human players in various victory types (science, culture, domination, etc).

This project will:
- **Collect structured turn-by-turn gameplay data**
- **Log metadata, decisions, and results** of Civ 7 games
- **Aggregate data across players** in a standardized format
- **Train predictive and prescriptive AI models**
- Eventually support **autonomous strategy discovery** through self-play and reinforcement learning

---

## 📊 Why This Matters

Civilization is a deep, turn-based strategy game where each decision can ripple across 200+ turns. It’s ideal for research in:
- **Sequential decision-making**
- **Game theory**
- **Long-term strategy optimization**
- **Reinforcement learning**

By logging enough high-quality data from real player games, we can train an AI to:
- Predict likely outcomes from a current game state
- Recommend optimal next actions
- Simulate full-game strategy trees
- Discover new paths to victory across different civilizations and maps

---

## 🕹️ What the System Will Do

### ✅ Phase 1: Human Logging System

- Use a Markdown-based format to log each game and turn.
- Allow players to input their decisions manually for now.
- Collect:
  - Resources: Science, Culture, Faith, Gold
  - Cities and Districts
  - Military Strength
  - Government, Policies
  - Technology/Civics chosen
  - Wonders built
  - War declarations and diplomatic actions
  - Victory path and outcome

### 🧠 Example Metadata for One Game

```yaml
game_id: game-001
player_civ: "Egypt"
difficulty: "Emperor"
map_type: "Continents"
map_size: "Standard"
victory_type_pursued: "Science"
victory_achieved: "TBD"
turns: TBD
notes: "Testing logging system with a classical science rush."
```

### 📅 Example Per-Turn Entry

```yaml
turn: 41
era: "Classical"
science: 28.4
culture: 20.1
gold: 310
faith: 90
military_strength: 330
cities: 3
districts: ["Campus", "Holy Site"]
tech_researched: "Construction"
civic_chosen: "Political Philosophy"
wonders_built: ["Pyramids"]
wars_declared: ["Greece"]
notes: "Preparing for expansion south after stabilizing science production."
```

---

## 🧱 How It Works

### 1. Markdown-Based Turn Logs
- Human-readable `.md` files for each game
- Stored under `/games/` folder with unique IDs
- Each game has full metadata + sequential turn data
- Easy to diff, commit, share, and version

### 2. Optional Future Automation
Once Civ 7 modding or telemetry is available:
- Use **memory reading or APIs** to capture game state
- Implement **OCR overlay tools** to detect screen elements (e.g., Tesseract + OpenCV)
- Hook into **Next Turn** hotkey to auto-log data

### 3. Data Extraction & Storage
- Write a Python parser to convert markdown logs to JSON or CSV
- Store in SQLite locally or Supabase/PostgreSQL for scalability
- Include scripts to validate schema and normalize entries

---

## 🧠 What We'll Use the Data For

### 📈 1. Statistical Analysis
- Win rates per civ / map type / strategy
- Early-game choices correlated with victory
- Analysis of common loss patterns
- Identify dominant player paths

### 🤖 2. ML & AI Models

#### Supervised Learning
- Predict outcome (victory type or loss) based on early game state
- Recommend next actions based on historical performance

**Example Models**:
- Logistic regression to classify game outcome likelihood
- Decision trees to map victory conditions to strategy sequences
- Neural networks to model high-dimensional turn data

#### Reinforcement Learning (Phase 3+)
- Define rewards (e.g., tech progress, unit success, win)
- Train AI agents to make turn-based decisions
- Use player logs as **expert demonstrations** (imitation learning)
- Explore **self-play** and simulation environments

---

## 🧪 Example Training Scenario

```
Input: Game state at Turn 60
- 4 cities
- Campus and Commercial Hub built
- Tech: Education
- Culture: 28.4
- Military: 170
- Pursuing Science Victory

Model Output:
- 76% chance of Science Victory
- Suggested actions: Prioritize Industrial Zones, build Universities
- Avoid war unless defensive
```

---

## 🔌 Optional Plugin Features (Stretch Goals)

If Civ 7 modding tools or APIs become available:
- Build a **UI overlay plugin** that hooks into game events
- Enable **real-time stat logging**
- Support **multiple player telemetry**
- Allow **live game analysis dashboards**

---

## 🧱 Repository Structure

```
civ7-turn-logger/
├── games/
│   ├── game-001.md
│   ├── game-002.md
├── schema/
│   └── turn-schema.json
├── analysis/
│   └── basic_stats.ipynb
├── data/
│   ├── parsed_logs.csv
│   └── ml-ready.json
├── models/
│   └── train_model.py
├── docs/
│   └── vision.md
│   └── how-it-works.md
├── README.md
└── turn-log-template.md
```

---

## 📦 Tools & Libraries

| Function              | Tools / Libraries            |
|-----------------------|------------------------------|
| Logging & Schema      | Markdown, YAML, JSON         |
| Parsing               | Python, Pandas               |
| Visualization         | Plotly, Matplotlib           |
| ML Training           | Scikit-learn, PyTorch        |
| Storage               | SQLite (local), Supabase     |
| OCR (optional)        | Tesseract, OpenCV            |
| Web UI (optional)     | Flask, Next.js, Supabase     |

---

## 🔐 Ethics & Privacy

This project prioritizes privacy and transparency:

- **All logs are user-owned**
- **No personal data** is ever collected
- Multiplayer logs (if ever used) will be **fully anonymized**
- Contributors can opt-in to share logs for open AI research

---

## 🤝 Contributing

We welcome contributions from:
- Civ players logging games
- Python devs writing parsers or scripts
- Data scientists building models
- Strategists helping identify decision patterns

To get started:
1. Copy `turn-log-template.md` and log your next game
2. Submit a PR with your game log in `/games/`
3. Help us build models from the data!

---

## 🚀 The Long-Term Vision

Imagine an AI that:
- Knows how to beat *Civilization VII* on Deity
- Learns not from hardcoded rules, but from thousands of human games
- Adapts to your playstyle and improves your win rate
- Becomes a digital grandmaster in 4X strategy

This is more than a mod. It’s a step toward machine understanding of strategic long-term planning — and a way to make your next game a little smarter.

Let’s build it. One turn at a time.