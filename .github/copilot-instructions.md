<!-- .github/copilot-instructions.md: Project-specific guidance for AI coding agents -->
# Copilot instructions — My-Portfolio

Goal: Be productive editing this small static portfolio site. The project is a single-page static site (no build tooling). Target files: `index.html`, `main.js`, `style.css`.

- **Big picture**: This is a simple, static, single-page portfolio. Navigation is anchor-based (`#home`, `#service`, `#about`, `#contact`). Interactivity is implemented with vanilla DOM in `main.js`. Styling is in `style.css`. There are no npm packages, bundlers, or tests in the repo.

- **Key files**:
  - `index.html` — root HTML. Contains the site sections and elements referenced by JS and CSS. Note: some IDs expected by `main.js` (e.g. `menuToggle`, `navMenu`) are not present by default; add them if you implement mobile menu markup.
  - `main.js` — DOM-driven interactions: mobile menu toggle, navbar hide/show on scroll, and scroll-to-top button. Guards are used (`if (element)`) — follow the same defensive pattern when adding DOM code.
  - `style.css` — layout, theme color (`#7cf03d`) and animations. The stylesheet contains a global `zoom: 2;` which scales the UI; don't remove or change without confirming visual intent.

- **Patterns & conventions**:
  - Minimal JS: use plain DOM APIs and early guards (e.g. `const el = document.getElementById('x'); if (el) { ... }`). Prefer that style for new features.
  - Anchor navigation: add new sections with an `id` and a corresponding `<a href="#id">` in the nav.
  - Styling: color/animation choices are centralized in `style.css`; reuse existing class names and the green accent `#7cf03d` for consistency.
  - Accessibility: existing interactive elements use clear labels (e.g. `aria-label` on scroll button). Maintain or add ARIA attributes for new interactive components.

- **Examples (copy-paste friendly)**:
  - Add a mobile menu toggle (HTML snippet to match `main.js` expectations):

```html
<button id="menuToggle" class="menu-toggle" aria-label="Toggle menu">
  <span></span><span></span><span></span>
</button>
<div id="navMenu" class="nav-menu"> <!-- wrap the <ul> or clone links here -->
  <!-- nav links -->
</div>
```

  - Scroll-to-top is implemented by `main.js` with the button `id="scrollToTopBtn"`. If you change this id, update `main.js` accordingly.

- **Developer workflows**:
  - No build step — preview `index.html` directly in a browser. Recommended quick workflows:
    - VS Code Live Server extension (recommended). Or run a local file server:

```powershell
# From project root (Windows PowerShell)
python -m http.server 5500; Start-Process "http://localhost:5500"
```

  - Git: normal `git add` / `git commit` / `git push` workflows apply. There is no CI configuration in the repo.

- **When editing**:
  - Keep changes small and focused. Preserve the single-page structure unless converting to a multi-page app is explicitly requested.
  - Avoid introducing new frameworks or build tooling without coordinating with the repository owner.
  - Update `index.html` nav anchors when adding sections.

- **Safe refactor notes**:
  - `main.js` expects `menuToggle`, `navMenu`, `.navbar`, and `scrollToTopBtn`. If you rename any selector, update the JS accordingly.
  - CSS uses `zoom: 2;` and a bright accent color; visual regressions are likely if those are removed.

- **Limitations / not present**:
  - No linting, tests, package manager files, or CI workflows.
  - No server-side code or APIs to integrate with — it's entirely static.

If anything above is unclear or you want me to include additional examples (e.g., HTML snippets for a responsive nav or a small unit-test scaffold), say which area to expand and I will iterate.
