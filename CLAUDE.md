# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
# Start development server (runs on http://localhost:5001)
python app.py

# Run tests
pytest

# Install dependencies (use a virtual environment)
pip install -r requirements.txt
```

## Architecture

**Spendly** is a Flask-based expense tracking web app targeting the Indian market (₹). It uses server-side rendering with Jinja2 templates and SQLite for persistence.

### Stack
- **Backend**: Flask 3.1.3, Python, SQLite
- **Frontend**: Jinja2 templates + vanilla HTML/CSS/JS (no JS framework)
- **Testing**: pytest + pytest-flask

### Structure
- `app.py` — all route definitions in one file; placeholder routes (marked with step numbers) indicate features not yet implemented
- `database/db.py` — expected to export `get_db()`, `init_db()`, and `seed_db()`; the SQLite file (`expense_tracker.db`) is gitignored
- `templates/base.html` — shared layout all pages extend; includes nav, font imports, and JS
- `static/css/style.css` — global design tokens (CSS variables) and shared component styles
- `static/css/landing.css` — landing-page-only styles

### Routing pattern
Routes follow Flask decorator style. Several routes are stubbed with `# Step N:` comments marking the implementation sequence (Steps 3–9 remain incomplete):

```python
# Step 3: Logout
# Step 4: Profile page
# Step 7: Add expense
# Step 8: Edit expense
# Step 9: Delete expense
```

### Design system
CSS variables defined in `style.css`:
- Colors: `--ink` (dark), `--paper` (light), `--accent` (#1a472a green), `--accent-2` (#c17f24 gold), `--danger`
- Typography: DM Serif Display (display), DM Sans (body) via Google Fonts
- Layout: max content width 1200px, auth form width 440px

### Template conventions
- Error display: `{% if error %}<div class="auth-error">{{ error }}</div>{% endif %}`
- Forms use `method="POST"` with Flask route handling both GET and POST
- Landing page uses a `#open-demo-modal` button to trigger a YouTube demo modal (implemented in `landing.html` inline JS)
