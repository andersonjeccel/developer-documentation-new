Tag
===

Display a tag label with optional icon, color, size, and interactive features such as dismiss or select.

Tag template variables
=====================

.. list-table:: Tag template variables
   :header-rows: 1

   * - Variable
     - Description
   * - ``tags``
     - List of tag objects to render (array; see subvariables below).
   * - ``tags.type``
     - The tag type: ``read-only``, ``dismissible``, or ``selectable`` (optional; default is ``read-only``).
   * - ``tags.label``
     - The label text for the tag (accepts translation string only).
   * - ``tags.renderIcon``
     - The icon class to display (optional).
   * - ``tags.iconOnly``
     - If true, show only the icon without label (optional).
   * - ``tags.color``
     - The color for the tag (optional; default is ``gray``).
   * - ``tags.size``
     - The tag size: ``sm``, ``md``, or ``lg`` (optional; default is ``md``).
   * - ``tags.attributes``
     - Additional HTML attributes for the tag element (object; see subvariables below).
   * - ``tags.attributes.id``
     - The HTML ID for the tag element (optional).
   * - ``tags.attributes.href``
     - If set, tag is rendered as a link (optional).
   * - ``tags.attributes.onclick``
     - JavaScript for the dismiss button (only for ``dismissible`` type; optional).
   * - ``className``
     - Additional CSS classes to add to the tag element (optional).

Tag example
===========

.. code-block:: twig

   {% include '@MauticCore/Components/tag.html.twig' with {
       tags: [
           {
               type: 'dismissible',
               label: 'mautic.docs.tag.label',
               renderIcon: 'ri-price-tag-3-line',
               color: 'blue',
               size: 'md',
               attributes: {
                   id: 'main-tag',
                   href: '/features',
                   onclick: 'handleTagDismiss()'
               }
           },
           {
               type: 'read-only',
               label: 'mautic.docs.tag.readonly',
               renderIcon: 'ri-bookmark-line',
               color: 'gray'
           }
       ],
       className: 'my-tag-list'
   } %}

.. note::
   The ``label`` variable should always use a translation string key. The tag component supports rendering as a link, button, or div depending on the presence of ``href`` and ``type``.
