# Copilot Workspace Instructions

## Development Checklist

Before committing any changes, ensure:

- [ ] `uv run ruff check .` passes with no errors
- [ ] `uv run pytest` passes all 25 tests
- [ ] Code follows Python conventions (snake_case, type hints)
- [ ] No unused variables or imports

## Project Overview

**Soc Ops** is a Social Bingo game built with Python (FastAPI + Jinja2 + HTMX). Players find people who match questions to mark squares and get 5 in a row. The app is styled with a **neon black-and-white aesthetic** featuring cyan, pink, and green accents.

## Architecture

```
app/
├── templates/       # Jinja2 HTML templates
│   ├── base.html
│   ├── home.html
│   └── components/  # bingo_board, bingo_modal, game_screen, start_screen
├── static/          # CSS & JS assets
├── models.py        # Pydantic models (GameState, BingoSquare)
├── game_logic.py    # Board generation & bingo detection
├── game_service.py  # Session management (GameSession)
├── data.py          # Question bank
└── main.py          # FastAPI routes & HTMX endpoints
tests/
├── test_api.py      # API endpoint tests (httpx + TestClient)
└── test_game_logic.py  # Game logic unit tests
```

## Key Commands

```bash
uv run uvicorn app.main:app --reload --port 8000  # Run dev server
uv run pytest                                       # Run tests
uv run ruff check .                                 # Lint
```

## Design Guide: Neon Black & White Theme

### Color Palette

All colors are defined as CSS variables in `app/static/css/app.css`:

- `--bg`: `#050505` (near-black background)
- `--surface`: `#111111` (surface cards)
- `--text`: `#f7f7f7` (white text)
- `--accent-cyan`: `#00f2ff` (primary neon accent)
- `--accent-pink`: `#ff2ae6` (secondary neon accent)
- `--accent-green`: `#7dff2b` (tertiary neon accent)

### Key Classes & Effects

**Typography & Glow**
- `.text-hero`: Large, uppercase display text (2.5rem–5rem responsive)
- `.glow-cyan`, `.glow-pink`, `.glow-green`: Text shadow glows matching accent colors
- `.animate-glow`: Pulsing effect for hero text (3s cycle)

**Animations**
- `.animate-fade-in`: Fade in with upward translate (0.8s ease-out)
- `.delay-100` through `.delay-500`: Stagger reveal animations (100ms increments)
- `@keyframes glow-pulse`: Breathing glow cycle for glowing text

**Backgrounds & Effects**
- `.grid-bg`: Subtle cyan grid overlay pattern (40px grid)
- `.accent-line`: Gradient line (cyan → pink → green)
- `.shadow-neon`: Multi-layer glow shadow (cyan + pink)
- `.hover:shadow-neon`: Hover state enhancement

**Interactive Elements**
- Buttons use solid neon colors with rounded-full corners
- Marked bingo squares: cyan or pink with neon glow
- Free space: solid green with black text
- Unmarked squares: dark surface with white/10 border

### Typography & Font

- Font family: `'Courier New', 'IBM Plex Mono', monospace`
- Monospace aesthetic for tech/retro vibe
- Use `.tracking-wider` and `.tracking-widest` for letter-spacing emphasis
- Uppercase for headings and accents

### Animation Strategy

Follow the "staggered reveal" pattern:
- Hero title: ~200ms delay
- Subtitle: ~300ms delay
- Content box: ~400ms delay
- Button: ~500ms delay

This creates a cohesive, high-impact entrance sequence rather than scattered micro-interactions.

### Dark Mode Convention

- Dark backgrounds are non-negotiable (black/near-black)
- Light text on dark surfaces
- Neon accents add vibrancy and are the only saturated colors
- Avoid whites and grays except for muted text
- Use opacity variants (e.g., `rgba(255, 255, 255, 0.1)`) for subtle borders and overlays

### When Adding New Features

1. **Use the CSS utility system in `app/static/css/app.css`**
2. **Respect the neon color palette** — don't introduce new colors
3. **Apply glow effects to interactive or emphasized elements**
4. **Animate entrances and state changes** for visual feedback
5. **Test dark theme rendering** across browsers/devices

## State Management

- `GameSession` manages game state server-side
- State persisted via signed cookies (itsdangerous)
- HTMX handles partial page updates without full reloads

## Frontend Conventions

- Use Jinja2 template composition in `app/templates/components/`
- Prefer HTMX attributes (`hx-post`, `hx-target`, `hx-swap`) over custom JavaScript
- Keep CSS classes composable and utility-based
- Avoid inline styles; use utility classes exclusively
