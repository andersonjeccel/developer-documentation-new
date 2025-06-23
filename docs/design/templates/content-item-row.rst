Content item row
================

Display a row of content with a heading, copy, and optional image, supporting multiple layout types for media, featured, or default content.

Content item row template variables
==================================

.. list-table:: Content item row template variables
   :header-rows: 1

   * - Variable
     - Description
   * - ``type``
     - Set the layout type: ``media``, ``featured``, or default (optional).
   * - ``eyebrow``
     - Show a label above the heading (optional; accepts translation string only).
   * - ``heading``
     - Set the main heading for the content item row (accepts translation string only).
   * - ``copy``
     - Provide the main text for the row (accepts translation string only).
   * - ``cta``
     - Add a call-to-action button with a link (optional; see subvariables below).
   * - ``cta.label``
     - The button label (accepts translation string only).
   * - ``cta.link``
     - The target URL for the button.
   * - ``image``
     - Display an image (optional; see subvariables below).
   * - ``image.path``
     - The relative path to the image file (string).
   * - ``image.alt``
     - The alternative text for the image (accepts translation string only).

Content item row example
=======================

.. code-block:: twig

   {% include '@MauticCore/Components/content-item-row.html.twig' with {
       type: 'media',
       eyebrow: 'mautic.docs.content_item_row.eyebrow',
       heading: 'mautic.docs.content_item_row.heading',
       copy: 'mautic.docs.content_item_row.copy',
       image: {
           path: '/images/marketing.png',
           alt: 'mautic.docs.content_item_row.image_alt'
       },
       cta: {
           label: 'mautic.docs.content_item_row.cta_label',
           link: '/get-started'
       }
   } %}

.. note::
   Use relative paths for the image path. Clicking to copy a file's relative path in your IDE will commonly result in the ready-to-use format required.