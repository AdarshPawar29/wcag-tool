# WCAG Accessibility Checker

This tool checks HTML code for accessibility issues based on WCAG guidelines.

GitHub Page: https://adarshpawar29.github.io/wcag-tool/

## Adding New Rules

To add a new rule, follow the format below and add it to the `accessibilityRules` array in `index.html`:

```javascript
{
    category: 'category-name', // The category of the rule (e.g., 'forms', 'headings')
    selector: 'CSS selector', // The CSS selector to target elements (e.g., 'input[type="text"]')
    test: (el) => {
        // The test function that returns true if the element fails the rule
        // Example: return !el.id || !document.querySelector(`label[for="${el.id}"]`);
    },
    guideline: 'WCAG guideline', // The WCAG guideline reference (e.g., '1.3.1 Info and Relationships')
    severity: 'error' | 'warning', // The severity of the issue ('error' or 'warning')
    suggestion: 'Suggestion text', // The suggestion text to fix the issue
    fix: `Example fix code`, // The example fix code (optional)
    resources: ['Resource URLs'] // An array of resource URLs (optional)
}
```

### Example

```javascript
{
    category: 'forms',
    selector: 'input[type="text"], input[type="email"], input[type="password"]',
    test: (el) => !el.id || !document.querySelector(`label[for="${el.id}"]`),
    guideline: '1.3.1 Info and Relationships',
    severity: 'error',
    suggestion: 'Form inputs must have associated labels',
    fix: `Bad: <input type="text">
Good: <label for="name">Name</label><input type="text" id="name">`,
    resources: ['https://www.w3.org/WAI/WCAG21/Understanding/labels-or-instructions.html']
}
```

## Running the Accessibility Check

1. Paste your HTML code into the textarea.
2. Click the "Run Accessibility Check" button.
3. Review the results in the "Results" section.
