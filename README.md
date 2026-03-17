# 🎉 Soc Ops: Social Bingo Game

[![Python](https://img.shields.io/badge/Python-3.13+-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-green.svg)](https://fastapi.tiangolo.com/)
[![HTMX](https://img.shields.io/badge/HTMX-1.9+-orange.svg)](https://htmx.org/)

**Break the ice at your next mixer!** Find people who match fun questions and get 5 in a row to win. Perfect for team building, networking events, or just having fun with friends.

🎮 **[Play the Game Now](https://madebygps.github.io/vscode-github-copilot-agent-lab/)** • 📚 **[View Lab Guide](https://madebygps.github.io/vscode-github-copilot-agent-lab/docs/)**

---

## 🎯 How to Play

1. **Start the Game**: Click "Start Game" to generate your unique bingo board.
2. **Find Matches**: Talk to people and mark squares when you find someone who matches the question.
3. **Get Bingo**: Get 5 in a row (horizontally, vertically, or diagonally) to win!
4. **Center Square**: The middle square is always marked as "FREE SPACE" - no questions needed!

Questions include fun prompts like "Has traveled to another country" or "Loves coding in Python". Customize them in `app/data.py`!

---

## 🚀 Quick Start

Get up and running in minutes!

### Prerequisites
- [Python 3.13+](https://www.python.org/downloads/)
- [uv](https://docs.astral.sh/uv/) package manager

### Setup & Run
```bash
# Install dependencies
uv sync

# Start the development server
uv run uvicorn app.main:app --reload --port 8000
```

Then open [http://localhost:8000](http://localhost:8000) in your browser and start playing!

### Test & Lint
```bash
# Run tests
uv run pytest

# Check code quality
uv run ruff check .
uv run ruff format .
```

---

## 📚 Workshop Lab Guide

This project is part of a hands-on workshop for building with GitHub Copilot. Follow the guided steps to learn modern web development techniques.

| Part | Title | Description |
|------|-------|-------------|
| [**00**](https://madebygps.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=00-overview) | Overview & Checklist | Get started with the workshop |
| [**01**](https://madebygps.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=01-setup) | Setup & Context Engineering | Set up your environment and understand the codebase |
| [**02**](https://madebygps.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=02-design) | Design-First Frontend | Build beautiful UIs with HTMX and Jinja2 |
| [**03**](https://madebygps.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=03-quiz-master) | Custom Quiz Master | Create engaging questions with AI assistance |
| [**04**](https://madebygps.github.io/vscode-github-copilot-agent-lab/docs/step.html?step=04-multi-agent) | Multi-Agent Development | Collaborate with AI agents for complex features |

> 📝 Lab guides are also available in the [`workshop/`](workshop/) folder for offline reading.

---

## 🛠️ Tech Stack

- **Backend**: FastAPI (Python web framework)
- **Frontend**: HTMX + Jinja2 templates (no JavaScript frameworks needed!)
- **Styling**: Custom CSS with utility classes
- **Testing**: pytest
- **Linting**: Ruff

## 🤝 Contributing

We welcome contributions! Check out our [Contributing Guide](CONTRIBUTING.md) and [Code of Conduct](CODE_OF_CONDUCT.md).

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

*Built with ❤️ using GitHub Copilot and modern Python tools. Deploys automatically to GitHub Pages on push to `main`.*
