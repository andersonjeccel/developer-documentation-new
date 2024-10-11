https://chatgpt.com/c/67097d91-2484-8007-85ff-f695390f0aba

# Toggletips

The Toggletip template is a reusable component designed to create interactive toggle buttons with tooltip-like popovers.

It serves to enhance user interfaces by providing contextual information or actions through interactive buttons. These buttons can display additional content in a popover when interacted with, improving the user experience by offering on-demand information without cluttering the interface.

## Technologies Used

- **Twig**: A flexible, fast, and secure templating engine for PHP.
- **Bootstrap (or similar CSS framework)**: For styling buttons and popovers.
- **JavaScript (Optional)**: For enhanced interactivity and dynamic content handling.

## Code Structure

The ToggleTip Twig template is organized into several logical sections, each responsible for a specific aspect of the button's behavior and appearance.

### Base Classes Initialization

```twig
{% set classes = ['btn', 'btn-nospin', 'btn-ghost'] %}
```

- Initializes an array of base CSS classes applied to the button.
- Ensures consistent styling across different instances.

### Size Configuration

```twig
{% set size_class = 'btn-xs' %}
{% if size is defined and size %}
    {% set size_class = 'btn-' ~ size %}
{% endif %}
{% set classes = classes|merge([size_class]) %}
```

- Sets the button size, defaulting to `'btn-xs'` if no size is specified when labels are present, and `'btn-toggletip'` when creating an icon-only toggletip.
- Merges the size class into the existing classes array.

### Icon-Only vs. Labeled Button

```twig
{% set is_icon_only = not (label is defined and label) %}

{% if is_icon_only %}
    {% set classes = classes|merge(['btn-icon']) %}
{% else %}
    {% set classes = classes|merge(['gap-5']) %}
{% endif %}
```

- Determines if the button should display only an icon or include a text label.
- Adds appropriate classes based on the presence of a label.

### Button Attributes and Data Attributes

```twig
<button type="button"
    class="{{ classes|join(' ') }}"
    data-toggle="popover"
    data-container="body"
    data-placement="{{ placement|default('right') }}"
    data-html="{{ html is defined and html ? 'true' : 'false' }}"
    data-trigger="{{ trigger|default('focus') }}"
    {% if selector is defined and selector %}
        data-selector="{{ selector }}"
    {% endif %}
    {% if title is defined and title %}
        title="{{ title|trans }}"
    {% endif %}
    {% if content is defined and content %}
        data-content="{{ content|trans }}"
    {% endif %}
    aria-haspopup="true"
    {% if not is_icon_only and label is defined and label %}
        aria-label="{{ label|trans }}"
    {% elseif is_icon_only %}
        aria-label="{{ 'mautic.core.toggletip'|trans }}"
    {% endif %}
>
```

- Configures various data attributes for the popover behavior, such as placement, HTML content, and trigger events.
- Sets accessibility attributes like `aria-haspopup` and `aria-label` based on the button's content.

### Accessibility Features

```twig
aria-haspopup="true"

{% if not is_icon_only and label is defined and label %}
    aria-label="{{ label|trans }}"
{% elseif is_icon_only %}
    aria-label="{{ 'mautic.core.toggletip'|trans }}"
{% endif %}
```

- Ensures the button is accessible by screen readers.
- Dynamically sets the `aria-label` based on whether the button has a label or is icon-only.

### Icon and Label Inclusion

```twig
<i class="{{ icon|default('ri-information-2-line') }}{% if not is_icon_only and icon is defined and icon %} ri-1x{% elseif is_icon_only and icon is defined and icon %} fs-20{% else %} fs-20{% endif %}"></i>

{% if label is defined and label %}
    {{ label|trans }}
{% endif %}
```

- Includes an icon within the button, defaulting to `'ri-information-2-line'` if none is specified.
- Adjusts the icon's size based on whether the button is icon-only or includes a label.
- Displays the label text if provided.

## Setup Instructions

To integrate the ToggleTip Twig template into your project, follow these steps:

1. **Ensure Dependencies are Installed**:
   - **Twig**: Make sure Twig is installed and properly configured in your project.
   - **CSS Framework**: Include Bootstrap or a similar framework to support the button and popover styling.
   - **JavaScript**: If utilizing dynamic popover features, ensure the necessary JavaScript libraries are included.

2. **Add the ToggleTip Template**:
   - Save the provided Twig template in your project's templates directory, for example, `templates/components/toggletip.twig`.

3. **Include the Template in Your Views**:
   - Use the `include` or `embed` function to incorporate the ToggleTip into your desired view.

   ```twig
   {% include 'components/toggletip.twig' with {
       size: 'sm',
       label: 'Info',
       icon: 'ri-info-line',
       placement: 'bottom',
       html: true,
       trigger: 'click',
       selector: '#myPopover',
       title: 'More Information',
       content: 'This is the popover content.'
   } %}
   ```

4. **Initialize Popovers**:
   - Ensure that popovers are initialized in your JavaScript. For Bootstrap, you might include:

   ```javascript
   $(function () {
       $('[data-toggle="popover"]').popover();
   });
   ```

## Usage Examples

### Basic ToggleTip Button

```twig
{% include 'components/toggletip.twig' with {
    label: 'Help',
    content: 'This button provides assistance.'
} %}
```

**Description**: Creates a small button labeled "Help" with a popover displaying the provided content.

### Custom Size and Placement

```twig
{% include 'components/toggletip.twig' with {
    size: 'lg',
    label: 'Settings',
    icon: 'ri-settings-line',
    placement: 'left',
    content: 'Configure your application settings here.'
} %}
```

**Description**: Generates a large button labeled "Settings" with a settings icon, positioning the popover to the left of the button.

### Icon-Only ToggleTip

```twig
{% include 'components/toggletip.twig' with {
    icon: 'ri-question-line',
    content: 'Frequently Asked Questions.'
} %}
```

**Description**: Produces an icon-only button with a question mark, showing a popover with FAQ content upon interaction.

## Configuration Options

The ToggleTip template accepts several parameters to customize its behavior and appearance:

| Parameter | Type | Description | Default |
|-----------|------|-------------|---------|
| `size` | String | Defines the size of the button. Possible values: `xs`, `sm`, `md`, `lg` | `xs` |
| `label` | String | The text label displayed on the button. If omitted, the button will display only an icon. | `null` |
| `icon` | String | The CSS class for the icon to display within the button. Defaults to `'ri-information-2-line'` if not specified. | `'ri-information-2-line'` |
| `placement` | String | Specifies the placement of the popover relative to the button. Common values: `top`, `bottom`, `left`, `right` | `'right'` |
| `html` | Boolean | Determines whether the popover content should be rendered as HTML. | `false` |
| `trigger` | String | Defines the event that triggers the popover. Common values: `click`, `hover`, `focus` | `'focus'` |
| `selector` | String | A CSS selector for delegating the popover. Useful for dynamic content. | `null` |
| `title` | String | The title text of the popover. | `null` |
| `content` | String | The main content of the popover. | `null` |

**Example Usage with Parameters**:

```twig
{% include 'components/toggletip.twig' with {
    size: 'md',
    label: 'Submit',
    icon: 'ri-send-plane-line',
    placement: 'top',
    html: true,
    trigger: 'click',
    selector: '#submitPopover',
    title: 'Submit Form',
    content: '<strong>Are you sure you want to submit?</strong> Please review your information before submitting.'
} %}
```

## Best Practices

- **Consistent Styling**: Utilize the base classes provided (`btn`, `btn-nospin`, `btn-ghost`) to maintain a consistent look and feel across all ToggleTip buttons.

- **Accessibility**: Always provide an `aria-label` to ensure buttons are accessible to users relying on screen readers. Use descriptive labels when possible.

- **Minimal Jargon**: When setting the `label` or `title`, use clear and concise language to effectively communicate the button's purpose.

- **Responsive Design**: Choose appropriate sizes (`xs`, `sm`, `md`, `lg`) based on the context to ensure buttons are easily interactable across different devices.

- **Fallbacks**: Always define default values for parameters like `size`, `placement`, and `icon` to prevent unexpected behavior when certain parameters are omitted.

## Common Issues and Troubleshooting

1. **Popover Not Displaying**:
   - **Cause**: Popover JavaScript not initialized.
   - **Solution**: Ensure that the necessary JavaScript code to initialize popovers is included and executed after the DOM is ready.

   ```javascript
   $(function () {
       $('[data-toggle="popover"]').popover();
   });
   ```

2. **Incorrect Icon Display**:
   - **Cause**: The specified icon class does not exist or is misspelled.
   - **Solution**: Verify that the icon class corresponds to an available icon in your icon library. Check for typos.

3. **Accessibility Issues**:
   - **Cause**: Missing or incorrect `aria-label`.
   - **Solution**: Ensure that the `label` parameter is provided when necessary and that `aria-label` is set appropriately within the template.

4. **Popover Content Not Rendering as HTML**:
   - **Cause**: The `html` parameter is not set to `true`.
   - **Solution**: When including HTML content in the popover, set the `html` parameter to `true` to allow HTML rendering.

5. **Button Size Not Reflecting Changes**:
   - **Cause**: The CSS framework does not recognize the specified size class.
   - **Solution**: Confirm that the size classes (`btn-xs`, `btn-sm`, etc.) are supported by your CSS framework and correctly implemented.

## Design Decisions

1. **Default Size and Placement**:
   - **Reasoning**: Setting default values (`btn-xs` for size and `'right'` for placement) ensures that the ToggleTip has a consistent appearance and behavior even when specific parameters are not provided. This simplifies usage for developers who do not need to customize these aspects.

2. **Icon-Only vs. Labeled Buttons**:
   - **Reasoning**: Allowing flexibility between icon-only and labeled buttons caters to different UI needs. Icon-only buttons save space and are ideal for compact interfaces, while labeled buttons provide clarity.

3. **Accessibility Focus**:
   - **Reasoning**: Incorporating `aria` attributes enhances the usability of the ToggleTip for users with disabilities, aligning with inclusive design principles.

4. **Merge Classes Approach**:
   - **Reasoning**: Building the `classes` array incrementally and merging additional classes based on conditions promotes modularity and ease of maintenance. It allows for dynamic class assignment without hardcoding multiple class combinations.

5. **Use of `trans` Filter**:
   - **Reasoning**: Applying the `trans` filter to labels and content ensures that the ToggleTip supports internationalization, making it adaptable for multilingual applications.

## Conclusion

The ToggleTip Twig template is a versatile and accessible component designed to enhance user interfaces by providing interactive popovers. By following the guidelines outlined in this documentation, developers can effectively implement and customize ToggleTip buttons to meet various application needs. Emphasizing best practices, accessibility, and flexibility, the ToggleTip serves as a valuable tool for creating intuitive and user-friendly interfaces.

For further assistance or to report issues, please contact the Engineering department or refer to the project's repository documentation.