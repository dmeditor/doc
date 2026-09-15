## Widget style keys

A style key is a named slot on a widget that a [widget style](./styles.md) can target. For example, table has `tr` for a body row:

```javascript
// css classes
{
  cssClasses: {
    tr: 'bg-gray-100',
  }
}

// inline css (nested under the block wrapper)
{
  cssStyle: `
.dme-w-tr {
  height: 15px;
}
`;
}
```

Each style key always gets class `dme-w-{key}` on that element (for example `dme-w-tr`), **in addition to** any `cssClasses` you set. Use `.dme-w-{key}` in `cssStyle`. The block wrapper also has `dme-w-root`.

In a custom widget, apply this with `getWidgetStyleClass`:

```javascript
import { getWidgetStyleClass } from 'dmeditor';

<div className={getWidgetStyleClass(styleClasses, 'tr')}>{...}</div>
```

### Common

| Key    | Description                                      |
| ------ | ------------------------------------------------ |
| `root` | Root element of the widget (the block wrapper). Always available. |

Widgets with no extra keys use `root` only: `code`, `content-view`, `grid`, `iframe`, `list`, `module`, `text`, `video`.

---

### accordion

| Key              | Description                          |
| ---------------- | ------------------------------------ |
| `container`      | Accordion list container             |
| `item`           | One accordion item                   |
| `summary`        | Clickable header row                 |
| `title`          | Item title                           |
| `icon-container` | Expand/collapse icon wrapper         |
| `icon`           | Replaces the default expand icon     |
| `body`           | Expandable content                   |

Open items also get the built-in class `dme-w-open` (not a style key).

### button

| Key           | Description                                      |
| ------------- | ------------------------------------------------ |
| `button`      | Button / link element                            |
| `before-icon` | `<i>` before the label. Rendered only if set.    |
| `after-icon`  | `<i>` after the label. Rendered only if set.     |

### carousel

| Key                  | Description                                      |
| -------------------- | ------------------------------------------------ |
| `carousel-inner`     | Slides wrapper. Fallback class: `dme-carousel-inner` |
| `carousel-item`      | One slide. Fallback class: `dme-carousel-item`   |
| `carousel-image`     | Slide image. Fallback class: `dme-carousel-image` |
| `carousel-title`     | Slide caption. Fallback class: `dme-carousel-title` |
| `carousel-title-link` | Caption link. Fallback class: `dme-carousel-title-link` |
| `arrow-button`       | Previous / next arrow button                     |
| `arrow-previous`     | `<i>` for the previous arrow. Replaces the default icon if set. |
| `arrow-next`         | `<i>` for the next arrow. Replaces the default icon if set. |

### collapsable-text

| Key                | Description              |
| ------------------ | ------------------------ |
| `button-container` | Expand/collapse control  |
| `button`           | Expand/collapse button   |

### form

| Key                   | Description                                      |
| --------------------- | ------------------------------------------------ |
| `success-message`     | Shown after a successful submit                  |
| `error-message`       | Form-level error                                 |
| `action`              | Submit / reset button row                        |
| `submit`              | Submit button                                    |
| `icon-before-submit`  | `<i>` before submit text. Rendered only if set.  |
| `reset`               | Reset button                                     |
| `icon-before-reset`   | `<i>` before reset text. Rendered only if set.   |
| `loading`             | Loading indicator                                |

### form-field

| Key                 | Description                                      |
| ------------------- | ------------------------------------------------ |
| `error`             | Field row when validation feedback is present    |
| `required`          | Required marker (`*`)                            |
| `input-text`        | Text input                                       |
| `input-checkbox`    | Checkbox input                                   |
| `input-radio-label` | Radio option label                               |
| `input-radio`       | Radio input                                      |
| `input-select`      | Select                                           |
| `input-textarea`    | Textarea                                         |
| `input-file`        | File input                                       |
| `error-message`     | Field-level error message                        |

### gallery

| Key                      | Description                         |
| ------------------------ | ----------------------------------- |
| `caption`                | Image caption in the grid           |
| `pagination-container`   | Pagination row                      |
| `pagination-item`        | Pagination page link                |
| `pagination-item-current` | Current page link                   |
| `popup-caption`          | Caption in the lightbox             |
| `gallery-indicator`      | Lightbox image index (`1 / 12`)     |

### heading

| Key  | Description                                      |
| ---- | ------------------------------------------------ |
| `h`  | All heading levels                               |
| `h1` | Level 1                                          |
| `h2` | Level 2                                          |
| `h3` | Level 3                                          |
| `h4` | Level 4                                          |
| `h5` | Level 5                                          |

`h1`–`h5` match the heading level setting (1–5).

### hero-text

| Key    | Description        |
| ------ | ------------------ |
| `hero` | Hero image column  |
| `list` | Text / list column |

### image

| Key           | Description      |
| ------------- | ---------------- |
| `image`       | Image wrapper    |
| `description` | Caption text     |

### layout-2columns

| Key       | Description   |
| --------- | ------------- |
| `column1` | First column  |
| `column2` | Second column |

### layout-3columns

| Key       | Description   |
| --------- | ------------- |
| `column1` | First column  |
| `column2` | Second column |
| `column3` | Third column  |

### line

| Key         | Description |
| ----------- | ----------- |
| `line-item` | The line    |

### menu

| Key            | Description                         |
| -------------- | ----------------------------------- |
| `container`    | Menu list                           |
| `menuitem`     | Menu item                           |
| `menuitem-link` | Item link                           |
| `current`      | Added on the selected item's link   |

### popup

| Key                        | Description                                      |
| -------------------------- | ------------------------------------------------ |
| `button`                   | Trigger button                                   |
| `button-before-icon`       | `<i>` before trigger text. Rendered only if set. |
| `button-after-icon`        | `<i>` after trigger text. Rendered only if set.  |
| `container`                | Modal content                                    |
| `close-icon`               | Top-right close control                          |
| `close-button`             | Close text button                                |
| `close-button-before-icon` | `<i>` before close text. Rendered only if set.   |

### space

| Key          | Description |
| ------------ | ----------- |
| `space-item` | Spacer      |

### table

| Key    | Description        |
| ------ | ------------------ |
| `tr-h` | Header row         |
| `th`   | Header cell        |
| `tr`   | Body row           |
| `td`   | Body cell          |

### tabs

| Key        | Description                         |
| ---------- | ----------------------------------- |
| `nav`      | Tab list                            |
| `nav-item` | One tab button                      |
| `active`   | Added on the selected tab button    |
| `body`     | Tab panel content                   |

The selected tab also gets `dme-w-active` from the `active` key.
