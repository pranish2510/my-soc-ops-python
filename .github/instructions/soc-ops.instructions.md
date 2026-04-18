---
applyTo: "**"
---

# Soc Ops Agent Instructions

## Development checklist
- `uv run ruff check .` (lint)
- `uv run pytest` (test)
- `uv run uvicorn app.main:app --reload --host 0.0.0.0 --port 8000` (run)

## Repository overview
FastAPI + Jinja2 social bingo app with HTMX and cookie sessions. Keep changes small, preserve existing templates, and avoid heavy frontend frameworks.

## Work rules
- Prefer Jinja2/HTMX components in `app/templates/components/`.
- Keep backend endpoints simple and session-driven in `app/main.py`, `app/game_service.py`, and `app/game_logic.py`.
- Use type hints and small helpers where useful.
- Avoid `open_simple_browser`; provide the URL or use `$BROWSER http://localhost:8000`.

## Validation
- Run tests after meaningful changes.
- Verify UI changes still render correctly and HTMX interactions work.
- Add targeted tests for logic changes in `tests/test_game_logic.py` or `tests/test_api.py`.

## Docs
Update `README.md` or relevant `workshop/` guides only if the change affects setup or usage.
