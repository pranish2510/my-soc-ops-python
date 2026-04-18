🌐 [Português (BR)](README.pt_BR.md) | [Español](README.es.md)

# Soc Ops

A lively social bingo experience designed for networking events, icebreakers, and workshop demos.

Launch the game, trade stories with friends, and mark squares as you discover people who match the prompts. The first player to complete 5 in a row wins.

---

## ✨ Why Soc Ops?

- FastAPI + Jinja2 web app with live HTMX interactions
- Cookie-based session state for easy play across browser refreshes
- Minimal HTML/CSS design optimized for rapid development and real-time updates
- Built as a teaching demo for social app workflows and frontend/backend integration

---

## 🚀 Quick Start

```bash
uv run uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

Then open: http://localhost:8000

---

## 🧪 Development Checklist

- `uv run ruff check .`
- `uv run pytest`
- `uv run uvicorn app.main:app --reload --host 0.0.0.0 --port 8000`

---

## 📚 Lab Guide

| Part | Title |
|------|-------|
| [**00**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=00-overview) | Overview & Checklist |
| [**01**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=01-setup) | Setup & Context Engineering |
| [**02**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=02-design) | Design-First Frontend |
| [**03**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=03-quiz-master) | Custom Quiz Master |
| [**04**](https://copilot-dev-days.github.io/agent-lab-python/docs/step.html?step=04-multi-agent) | Multi-Agent Development |

> 📝 Lab guides are also available in the [`workshop/`](workshop/) folder for offline reading.

---

## 📘 Want to explore?

Check `app/main.py`, `app/game_logic.py`, and `app/templates/` to see how the game flow, UI components, and HTMX interactions are wired together.
