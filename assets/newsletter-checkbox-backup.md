# Newsletter Checkbox Backup

Paste these blocks back into `contact/index.html` to restore the "Get the ClipIt newsletter" checkbox.

---

## 1. CSS — after `.error-msg` rule, before `.submit-btn`

```css
.checkbox-row {
  display: flex; align-items: flex-start; gap: 12px;
  padding: 4px 0;
}
.checkbox-row input[type="checkbox"] { margin-top: 2px; flex-shrink: 0; accent-color: var(--navy); width: 16px; height: 16px; cursor: pointer; }
.checkbox-row label { font-size: 14px; color: var(--body); line-height: 1.5; cursor: pointer; }
```

---

## 2. HTML — inside `<form class="form-group">`, between the message field and the submit button

```html
        <div class="checkbox-row">
          <input type="checkbox" id="newsletterCheckbox" name="entry.1802612899" value="Yes">
          <label for="newsletterCheckbox">Get the ClipIt newsletter</label>
        </div>
```

Note: the submit button also had `margin-top: 8px` added for spacing — remove that if restoring the checkbox above it.
