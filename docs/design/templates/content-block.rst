Content block
============

Present a section with a heading, subheading, copy, and optional call-to-action, visually separated from other content.

Content block template variables
==============================

.. list-table:: Content block template variables
   :header-rows: 1

   * - Variable
     - Description
   * - ``heading``
     - Set the main heading for the content block (optional; accepts translation string only).
   * - ``subheading``
     - Set a subheading below the main heading (optional; accepts translation string only).
   * - ``copy``
     - Provide the main text or a list of text items for the content block (optional; accepts translation string(s) only).
   * - ``childContainer``
     - Render additional HTML content inside the block (optional).
   * - ``cta``
     - Add a call-to-action button with a link (optional; see subvariables below).
   * - ``cta.label``
     - The button label (accepts translation string only).
   * - ``cta.link``
     - The target URL for the button.
   * - ``hasBorder``
     - Show a border at the bottom of the block if true (optional).

Content block example
====================

.. code-block:: twig

   {% include '@MauticCore/Components/content-block.html.twig' with {
       heading: 'mautic.docs.content_block.heading',
       subheading: 'mautic.docs.content_block.subheading',
       copy: [
           'mautic.docs.content_block.copy_1',
           'mautic.docs.content_block.copy_2'
       ],
       cta: {
           label: 'mautic.docs.content_block.cta_label',
           link: '/learn-more'
       },
       hasBorder: true
   } %}
