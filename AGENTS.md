# Agent Guidelines for cv

This document provides guidelines for AI coding agents working in this repository.

## Project Overview

This is a static personal CV website built with vanilla HTML, CSS, and JavaScript. It features:
- Responsive design with mobile-first approach
- Dark/light theme toggle
- English/Slovenian language support (i18n)
- Print-to-PDF functionality
- Deployed via GitHub Pages at https://maticsuc.github.io/cv/

## Repository Structure

```
cv/
├── index.html           # Main HTML file with embedded JavaScript
├── style.css            # All styles including themes and responsive design
├── profile_picture.JPG  # Profile image
└── README.md            # Basic project documentation
```

## Build and Deployment

### No Build Process
This project has **NO build process** - it's pure static HTML/CSS/JS.

### Testing
- Open `index.html` directly in a browser
- Use Live Server or similar for hot-reload during development
- Test responsiveness using browser DevTools (mobile view at 768px and 480px breakpoints)

### Deployment
- Deployed automatically via GitHub Pages from the `main` branch
- URL: https://maticsuc.github.io/cv/
- Changes pushed to `main` are live within minutes

## Code Style Guidelines

### HTML
- Use semantic HTML5 elements
- Two-space indentation
- Use `data-i18n` attributes for translatable content
- Use `data-lucide` for Lucide icons
- Class naming: lowercase with underscores (e.g., `profile_name_firstName`)
- Maintain accessibility with `aria-label` attributes

### CSS
- Two-space indentation
- Use CSS custom properties for theming (see `:root` and `[data-theme="light"]`)
- Follow existing naming convention: component-based with underscores
  - `.profile_container`, `.exp_item`, `.skills_category`
- Mobile-first responsive design
- Breakpoints: `768px` and `480px`
- Transitions: `0.3s ease` for most animations
- Colors: Use CSS variables (`--primary-color`, `--secondary-color`, etc.)
- Use `rem` units for sizing (base: `10px`)

### JavaScript
- Vanilla JavaScript only (no frameworks)
- Embedded in `<script>` tags in `index.html`
- Two-space indentation
- Use `const` by default, `let` when reassignment needed
- Store user preferences in `localStorage` (theme, language)
- Use event delegation where appropriate
- Initialize external libraries after DOM load (e.g., Lucide icons)

### Color Scheme
**Dark Theme (default):**
- Background: `#1C1C1C`
- Primary: `#349c74` (Emerald Green)
- Secondary: `#4db894` (Light Green)
- Text: `#FFFFFF`
- Card: `#262626`

**Light Theme:**
- Background: `#F5F5F5`
- Primary: `#2d8a65`
- Secondary: `#349c74`
- Text: `#1C1C1C`
- Card: `#FFFFFF`

### Typography
- Font: Inter (Google Fonts)
- Weights: 200, 300, 400, 500, 600, 700
- Base size: `10px` (use `rem` for all font sizes)

## Git Workflow

### Commit Message Format
Follow Conventional Commits style:
- `feat:` - New features
- `fix:` - Bug fixes
- `chore:` - Maintenance tasks
- `perf:` - Performance improvements
- `style:` - Styling changes

Examples from history:
- `feat: Add Projects section`
- `fix: Fix ordering of sections in mobile view`
- `perf: Update skills`
- `chore: add latest experience item`

### Branching
- Main branch: `main`
- No PR workflow required for this personal project
- Commit directly to `main` (changes auto-deploy)

### Important Notes
- **NO force pushes** to `main`
- Test changes locally before pushing (they go live immediately)
- Author: Matic Šuc <matic687@gmail.com>

## Content Management

### Adding New Sections
1. Add HTML structure in `index.html` following existing patterns
2. Add corresponding styles in `style.css`
3. Add translations to both `en` and `sl` objects in the translations dictionary
4. Use consistent card styling (`.exp`, `.edu`, `.skills` classes as reference)

### Internationalization (i18n)
- All user-facing text must have `data-i18n` attributes
- Add translations to both `en` and `sl` objects in the `translations` dictionary (index.html:346-476)
- Translation keys use dot notation: `section.subsection.key`
- HTML content in translations is supported (use `innerHTML`)

### Responsive Design
Mobile order (defined at style.css:136-178):
1. Profile
2. Socials
3. Skills
4. Experience
5. Projects
6. Publications
7. Education
8. Languages
9. Hardware
10. Contact
11. Export CV

Use `order` property in CSS to maintain this sequence.

## External Dependencies

- **Lucide Icons**: Loaded via CDN (`https://unpkg.com/lucide@latest`)
  - Initialize with `lucide.createIcons()` after DOM load
  - Use `data-lucide="icon-name"` attributes
- **Google Fonts**: Inter font family

## Common Tasks

### Update Skills
Edit the skills section in `index.html` (lines 67-141), maintaining the category structure.

### Change Theme Colors
Edit CSS variables in `:root` (dark) and `[data-theme="light"]` (light) in `style.css`.

### Add Experience/Education Items
Follow the existing `.exp_item` or `.edu_item` structure, add translations for both languages.

### Modify Print Styles
Edit `@media print` section in `style.css` (lines 838-950).

## Best Practices

1. **Always test both themes** (dark and light) when making visual changes
2. **Always add translations** for both English and Slovenian
3. **Test mobile responsiveness** at 768px and 480px breakpoints
4. **Maintain accessibility** - include alt text, aria labels, semantic HTML
5. **Keep animations consistent** - use 0.3s ease transitions
6. **Use CSS variables** for colors - never hardcode color values
7. **Test print functionality** after layout changes
8. **Maintain card hover effects** for consistency across sections

## Special Considerations

- Profile picture must be JPG format (or update `profile_picture.JPG` reference)
- Loading overlay displays for 800ms on page load (index.html:314-321)
- Theme preference persists via localStorage
- Language preference persists via localStorage
- Print styles remove all interactive elements and enforce light theme
