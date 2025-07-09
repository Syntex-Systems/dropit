# Dropit.js - Custom Dropdown jQuery Plugin

Dropit.js is a lightweight and customizable jQuery plugin that transforms standard HTML `<select>` elements into stylish, accessible, and feature-rich dropdowns. It supports list and grid layouts, light and dark themes, search functionality, and dynamic option management.

## Features

- **Customizable Layouts**: Choose between a list or grid layout (2–5 columns).
- **Theming**: Supports `light` and `dark` themes for seamless integration with your UI.
- **Search Functionality**: Enable a search bar to filter options dynamically.
- **Return/Back Button**: Optional button to close the dropdown.
- **Keyboard Navigation**: Full support for arrow keys, Enter, and Escape for accessibility.
- **Dynamic Option Management**: Add, remove, replace, or enable/disable options programmatically.
- **CSS Customization**: Style the dropdown’s appearance using external CSS files.
- **ARIA Support**: Built with accessibility in mind, including ARIA attributes for screen readers.
- **Lightweight**: Minimal footprint with no external dependencies beyond jQuery.

## Installation

Include the required CSS and JavaScript files in your HTML:

```html
<link rel="stylesheet" href="https://syntex-systems.github.io/dropit/dropit.css">
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
<script src="https://syntex-systems.github.io/dropit/dropit.js"></script>
```

## Usage

### Basic Setup

1. Create a standard HTML `<select>` element:

```html
<select id="myDropdown">
    <option value="">Select an option</option>
    <option value="1">Option 1</option>
    <option value="2">Option 2</option>
    <option value="3" disabled>Option 3 (Disabled)</option>
</select>
```

2. Initialize Dropit.js with jQuery:

```javascript
$(document).ready(function() {
    $('#myDropdown').initDropit();
});
```

### Configuration Options

Customize the dropdown by passing an options object to `initDropit`:

```javascript
$('#myDropdown').initDropit({
    type: 'grid',       // 'list' or 'grid'
    columns: 4,         // Number of columns for grid layout (2–5)
    theme: 'dark',      // 'light' or 'dark'
    search: true,       // Enable search functionality
    return: true        // Show return/back button
});
```

#### Available Options

| Option   | Type    | Default  | Description                                      |
|----------|---------|----------|--------------------------------------------------|
| `type`   | String  | `list`   | Layout type: `list` or `grid`.                   |
| `columns`| Number  | `3`      | Number of columns for grid layout (2–5).          |
| `theme`  | String  | `light`  | Theme: `light` or `dark`.                        |
| `search` | Boolean | `false`  | Enable search input for filtering options.        |
| `return` | Boolean | `false`  | Show a return/back button to close the dropdown.  |

### Methods

Use the `Dropit` global object with a selector (e.g., `#myDropdown`) to interact with the dropdown programmatically.

#### Get Selected Value

```javascript
var value = Dropit.getValue('#myDropdown');
console.log(value); // Outputs the selected option's value
```

#### Set Selected Value

```javascript
Dropit.setValue('#myDropdown', '2'); // Selects option with value "2"
```

#### Replace All Options

```javascript
Dropit.replaceOptions('#myDropdown', [
    { value: 'a', text: 'Apple', selected: true },
    { value: 'b', text: 'Banana' },
    { value: 'c', text: 'Cherry', disabled: true }
]);
```

#### Add a Single Option

```javascript
Dropit.addOption('#myDropdown', { value: '4', text: 'Option 4' }, 1); // Adds at index 1
// or
Dropit.addOption('#myDropdown', 'Option 5'); // Adds at the end
```

#### Remove an Option

```javascript
Dropit.removeOption('#myDropdown', '2'); // Removes option with value "2"
```

#### Enable/Disable an Option

```javascript
Dropit.setOptionDisabled('#myDropdown', '1', true); // Disables option with value "1"
Dropit.setOptionDisabled('#myDropdown', '1', false); // Enables option with value "1"
```

### Styling

Customize the dropdown’s appearance using external CSS files to override the default styles in `dropit.css`. Target the following classes:

- `.dropit-container`: Main container
- `.dropit-header`: Dropdown header
- `.dropit-dropdown`: Dropdown menu
- `.dropit-item`: Individual option
- `.dropit-search`: Search input
- `.dropit-return`: Return button
- `.dropit-grid`: Grid layout modifier
- `.dropit-light` / `.dropit-dark`: Theme modifiers

Example CSS customization:

```css
.dropit-container.dropit-dark {
    background-color: #1a1a1a;
}
.dropit-item:hover {
    background-color: #e0e0e0;
}
```

**Note**: You may customize the visual appearance via external CSS, but modifying the JavaScript code or creating derivative works is prohibited under the license.

### Accessibility

- **ARIA Attributes**: Uses `role="listbox"`, `aria-expanded`, and `aria-label` for screen reader support.
- **Keyboard Navigation**:
  - `Enter`: Selects focused option or toggles dropdown.
  - `Escape`: Closes the dropdown.
  - `Up/Down Arrows`: Navigates options.
- **Focus Management**: Search input is focused automatically when the dropdown opens (if enabled).

### Example: Full Implementation

```html
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="https://syntex-systems.github.io/dropit/dropit.css">
    <style>
        /* Custom CSS */
        .dropit-container.dropit-dark {
            border: 1px solid #555;
        }
        .dropit-item:hover {
            background-color: #007bff;
            color: white;
        }
    </style>
</head>
<body>
    <select id="myDropdown">
        <option value="">Choose an option</option>
        <option value="1">Apple</option>
        <option value="2">Banana</option>
        <option value="3">Cherry</option>
    </select>

    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script src="https://syntex-systems.github.io/dropit/dropit.js"></script>
    <script>
        $(document).ready(function() {
            $('#myDropdown').initDropit({
                type: 'grid',
                columns: 3,
                theme: 'dark',
                search: true,
                return: true
            });

            // Example: Add a new option after 2 seconds
            setTimeout(function() {
                Dropit.addOption('#myDropdown', { value: '4', text: 'Date', selected: true });
            }, 2000);
        });
    </script>
</body>
</html>
```

## Browser Support

- Modern browsers (Chrome, Firefox, Safari, Edge)
- Requires jQuery 3.x or later

## Notes

- The original `<select>` element is hidden but remains functional for form submissions.
- Placeholder options (e.g., "Select an option") are automatically skipped in the visual dropdown.
- Ensure unique values for options to avoid unexpected behavior.
- The plugin does not support multiple selections (`<select multiple>`).
- Modifying the JavaScript code or creating derivative works is prohibited under the license. CSS customizations are permitted.

## License

Dropit.js is licensed under a proprietary license. You may use the library in your projects and customize its appearance via external CSS files. Copying, modifying, or redistributing the JavaScript code, or creating derivative works, is strictly prohibited without prior written permission. See the [LICENSE](LICENSE) file for details.
