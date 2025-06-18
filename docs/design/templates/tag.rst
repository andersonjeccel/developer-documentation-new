Template: Tag (@MauticCore/Components/tag.html.twig)
####################################################

Overview
********

The ``tag`` template iterates over an array of tag definitions (``tags``) and generates HTML elements (``<div>`` or ``<a>``) for each tag based on the provided configuration. Each tag supports custom styles, icons, tooltips, and unique IDs. You can pass a top-level ``className`` variable to add a custom class to each tag's wrapper.

Tag properties
**************

Each tag object in the ``tags`` array can have the following properties:

- **type** (enum: ``read-only``, ``dismissible``, ``selectable``)  
  Determines the behavior and layout of the tag. Defaults to ``read-only``.  
  - ``read-only``: Displays a static tag.  
  - ``dismissible``: Includes a close button to remove the tag. Button behavior can be set via ``attributes.onclick``.  
  - ``selectable``: Renders the tag as a selectable button with ``aria-pressed="false"``.
- **color** (string)  
  Sets the tag's background color. Supported values: ``gray``, ``cool-gray``, ``warm-gray``, ``red``, ``magenta``, ``purple``, ``blue``, ``cyan``, ``teal``, ``green``, ``primary``, ``brand``, ``outline``, ``high-contrast``, ``default``, ``success``, ``info``, ``warning``, ``danger``. Defaults to ``gray``.
- **label** (string)  
  The text displayed inside the tag, or as the ``aria-label`` and tooltip if ``iconOnly`` is true. All labels are translated using the ``|trans`` filter.
- **renderIcon** (string)  
  CSS class for an icon (e.g., ``ri-price-tag-3-line``). If provided, the icon is displayed before the label.
- **iconOnly** (bool)  
  If ``true``, only the icon is displayed. The ``label`` is used for ``aria-label`` and as a tooltip. Defaults to ``false``.
- **size** (string)  
  Sets the tag size. Example: ``md`` (default).
- **attributes** (object)  
  Custom HTML attributes for the tag's wrapper element (e.g., ``class``, ``href``, ``data-*``, ``onclick``). Example:  
  ``attributes: { 'href': '/example', 'data-toggle': 'tooltip' }``

Customization and generated attributes
*************************************

- **id** (string): Automatically generated if not defined in ``attributes``.  
  - If the label contains periods (e.g., ``mautic.core.item``), the ID is formed from the last two parts (``core-item``).  
  - Otherwise, it is derived from the label slug (e.g., ``tag-my-tag``).  
  - If no label exists, a random ID is created.
- **aria-label** (string): Set to the full, translated label for accessibility.
- **Tooltips**: Added automatically in these cases:  
  - On a truncated label (shows full text).  
  - On an ``iconOnly`` tag (shows label).  
  - On the close button of a ``dismissible`` tag.  
  Tooltips use ``data-toggle="tooltip"`` and ``tooltip-placement="top"``.
- **href** (string, in ``attributes``): If present, the tag is rendered as an ``<a>`` element; otherwise, defaults to ``<div>``.
- **truncated_label** (string): If the translated label exceeds 27 characters, it is truncated to 24 characters with ``...``, and the full label appears as a tooltip.

Examples
********

.. code-block:: twig

    {% include '@MauticCore/Helper/_tag.html.twig' with {
        tags: [
            {
                color: 'warm-gray',
                label: 'mautic.email.type.list.header'
            },
            {
                type: 'dismissible',
                color: 'blue',
                label: 'mautic.core.alert',
                renderIcon: 'ri-alert-line',
                attributes: { 'data-dismiss': 'tag', 'class': 'alert-tag' }
            },
            {
                type: 'selectable',
                color: 'green',
                label: 'mautic.email.type.selectable',
                renderIcon: 'ri-check-line',
                attributes: { 'onclick': 'handleSelect()' }
            }
        ]
    } %}
