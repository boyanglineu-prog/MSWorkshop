# Copilot Workspace Instructions

## ✅ Before Committing

```bash
uv run ruff check .     # Lint
uv run pytest           # Test (25 tests)
uv run uvicorn app.main:app --reload --port 8000  # Dev server
```

**All three must pass.**

---

## Project Overview

**Soc Ops**: Social Bingo game (FastAPI + Jinja2 + HTMX). Players mark squares matching questions, get 5 in a row to win.

## Architecture

- **game_service.py** — GameSession (state machine): START → PLAYING → BINGO
- **game_logic.py** — Board generation (25 squares, center is FREE_SPACE), bingo detection (12 win lines)
- **main.py** — FastAPI routes + session middleware
- **models.py** — GameState enum, frozen Pydantic models
- **templates/** — Jinja2 + HTMX components (partial page updates, no full reloads)
- **data.py** — 24 bingo questions

## State Management

**GameSession** is the single source of truth. All models frozen (use `model_copy(update={...})`):

```python
session.start_game()           # Generate board, set PLAYING
session.handle_square_click(id)  # Toggle square, check bingo
session.dismiss_modal()        # Return to PLAYING
session.reset_game()           # Back to START
```

Sessions stored in `_sessions` dict, persisted via signed cookies.

## HTMX Pattern

Endpoints return **partial HTML components** (not full pages). HTMX swaps them:

```html
<button hx-post="/toggle/5" hx-target="#game-container" hx-swap="outerHTML">
```

**Rule**: Always return `response_class=HTMLResponse` with template response.

## Bingo Detection

Board: 5×5 grid (index 12 always marked). Winning lines: 5 rows + 5 cols + 2 diagonals (12 total, cached).

## Testing

Use `TestClient` + pytest. Sessions persist across requests:

```python
client.get("/")        # Establish session
client.post("/start")  # Use same session
```

Use `response.text` for HTML assertions.

## Key Behaviors

- **Center**: Index 12 always marked, can't toggle
- **No duplicates**: `random.sample(QUESTIONS, 24)`
- **Per-browser**: Each session isolated, in-memory (not persistent)
- **Modal**: Controlled by `session.show_bingo_modal` flag

## Adding Features

- **Question**: Add to `QUESTIONS` in `data.py`
- **Endpoint**: Route → session method → template response
- **State**: Add to `GameState` enum, handle transitions in `game_service.py`
- **Component**: Create in `templates/components/`, include with `{% include %}`
