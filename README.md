# Adapt or Perish — Control Shift Intelligence

A top-down boss-fight game where the boss **learns from your playstyle** and adapts its strategy after every battle. Built with Godot Engine and powered by an AI pipeline using Mira Flows and the ChatGPT API.

> Developed as a team project at IIT (BHU) Varanasi by Shreyas Pol, Akash Kumar, Prabhav Sunia, Divye Nayyar, and Kapish Gupta.

---

## How It Works

The game features a single boss — **Mahoraga** — with five possible actions:

| Action | Description |
|--------|-------------|
| Melee | Close-range attack |
| Ranged | Projectile attack from a distance |
| Block | Deflects incoming player attacks |
| Chase | Aggressively pursues the player |
| Tackle | High-damage charge attack |

Each action has an associated probability weight. Initially all weights are equal:

```gdscript
var actions = { State.MELEE: 25, State.RANGED: 25, State.BLOCKED: 25, State.TACKLE: 25 }
```

After each fight, the AI pipeline analyzes the player's behavior and updates these weights to counter their playstyle. For example, if the player tends to fight up close, Mahoraga will increase its melee and tackle probabilities in the next round.

---

## AI Pipeline

The adaptation system runs through **Mira Flows** as the orchestration layer:

```
Player fight data (attack patterns, positioning)
        ↓
   Mira Flows fetches and structures the data
        ↓
   ChatGPT API analyzes patterns and generates updated probabilities
        ↓
   Mira Flows sends updated boss config back to Godot
```

---

## Tech Stack

- **Godot Engine** — Game engine (GDScript)
- **Mira Flows** — AI workflow orchestration and middleware
- **ChatGPT API (OpenAI)** — Player behavior analysis and boss strategy generation
- **Python** — Glue scripts for data handling between Godot and Mira

---

## Project Structure

```
ControlShiftIntelligence/
├── src/          # Godot game source (GDScript)
├── ai/           # Python scripts for Mira Flows integration and AI pipeline
└── README.md
```

---
