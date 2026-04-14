# Agent Instructions (AGENTS.md)

Welcome, agent. This file contains the rules, conventions, and operational guidelines for contributing to this repository. You must adhere to these guidelines to ensure consistency, quality, and maintainability.

## 1. Project Overview and Architecture

This is a static site built using **Hugo** and **Tailwind CSS**. It relies on Hugo's built-in asset pipeline (via PostCSS) to process Tailwind styles.
- **Content:** Markdown files reside in the `content/` directory.
- **Layouts:** Go html/template files reside in the `layouts/` directory.
- **Assets:** CSS and JS are kept in `assets/`.
- **Static files:** Images and static resources go in `static/` or `assets/` depending on whether they need processing.

## 2. Build, Test, and Lint Commands

### 2.1 Building and Running
- **Local Development Server:** Run the dev server with drafts enabled.
  ```bash
  hugo server -D
  ```
- **Production Build:** Build the static site into the `public/` directory with minification.
  ```bash
  hugo --gc --minify
  ```

### 2.2 Testing
As this is primarily a static site generator project, formal unit testing frameworks (like Jest) might not be fully configured by default.
- **Testing the Build:** To verify that the site builds without template errors:
  ```bash
  hugo --buildDrafts --gc --minify
  ```
- **Single Test / Debugging:** If you are debugging a specific page or shortcode, use `hugo server -D` and navigate to the relevant route. Check the terminal output for Go template rendering errors.

### 2.3 Linting
- **HTML/Templates:** Ensure Go templates are properly formatted. Avoid deep nesting and keep logic out of templates where possible (use partials).
- **CSS:** Tailwind CSS is used via PostCSS. Stick to utility classes in HTML. Do not write custom CSS unless absolutely necessary (in which case, place it in the main Tailwind input CSS file in `assets/`).

## 3. Code Style Guidelines

### 3.1 Hugo Templates (`layouts/`)
- **Naming Conventions:**
  - Partials: Use `kebab-case.html` (e.g., `layouts/partials/site-header.html`).
  - Shortcodes: Use descriptive names (e.g., `layouts/shortcodes/image-gallery.html`).
- **Formatting:**
  - Indent Go template tags `{{ ... }}` to match the HTML structure.
  - Use `{{-` and `-}}` selectively to strip unnecessary whitespace and keep the generated HTML clean.
- **Structure:**
  - Break complex layouts into smaller, reusable `partials`.
  - Use block templates (`baseof.html`) for common page structure (head, header, footer).

### 3.2 Markdown Content (`content/`)
- **Front Matter:** Always use YAML (or TOML) front matter consistently. Include at least `title`, `date`, and `draft` status.
- **Formatting:** Follow standard Markdown conventions. Use Hugo shortcodes for complex components (like responsive images or complex grids).
- **Paths:** When referencing images or internal links, prefer page bundles or use Hugo's relref/ref functions or appropriate shortcodes.

### 3.3 CSS and Styling
- **Tailwind Utility-First:** Strictly use Tailwind CSS utility classes directly in the HTML templates.
- **Custom CSS:** If you must use custom CSS (e.g., for complex animations or pseudo-elements not easily handled by utilities), add them to the main CSS file in `assets/css/` using `@layer components` or `@layer utilities` to maintain proper specificity.
- **Naming:** If you extract components using `@apply` (discouraged unless highly reused), use `kebab-case` for class names.

### 3.4 JavaScript (If applicable)
- **Imports:** Use standard ES6 modules. If utilizing Hugo's js.Build, ensure entry points are in `assets/js/`.
- **Formatting:** Use 2 spaces for indentation. Use single quotes for strings and trailing commas in multiline objects.
- **Error Handling:** Use `try...catch` blocks for asynchronous operations or DOM manipulation that might fail. Favour early returns and defensive programming.

## 4. Operational Directives for Agents

### 4.1 Modifying Code
- **Understand the Context:** Before editing any `layout` or `content` file, use `grep` or `read` to understand how the file is connected to `baseof.html` or other partials.
- **Idiomatic Changes:** Ensure new components use existing Tailwind utility patterns. Do not introduce raw CSS or inline styles (`style="..."`).
- **Incremental Steps:** When creating a new feature (e.g., a new shortcode or page type), first create the minimal working structure, test it (conceptually or via build), and then refine the styling.

### 4.2 Handling Ambiguity
- If a request lacks specific design details, default to clean, minimalist Tailwind classes (e.g., sensible padding, muted text colors for secondary information, accessible contrast).
- If asked to create new content types (taxonomies), ensure both the configuration (`hugo.yaml`) and the required layout files (list, single) are created or considered.

### 4.3 Agent Workflows
- **Discovery:** Always use `glob` to find existing partials or shortcodes before creating new ones to avoid duplication.
- **Execution:** When implementing a fix or feature, ensure the corresponding Tailwind classes are valid for the configured Tailwind version.
- **Review:** After generating template code, visually inspect the HTML structure and Go template logic for missing closing tags (`{{ end }}`).

## 5. Security and Safety
- Never expose sensitive environment variables or API keys in public layout files or client-side JS.
- Do not add untested third-party scripts to the `<head>` or before `</body>` without explicit instruction.
- Ensure any user-provided content rendered in templates uses safe HTML functions if necessary, though Hugo handles most escaping by default.

---
*End of AGENTS.md*
