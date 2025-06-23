Content group
=============

Group related content with a heading, copy, and optional call-to-action, typically used to organize sections within a page.

Content group template variables
==============================

.. list-table:: Content group template variables
   :header-rows: 1

   * - Variable
     - Description
   * - ``heading``
     - Set the group heading (optional; accepts translation string only).
   * - ``copy``
     - Provide the main text or a list of text items for the group (optional; accepts translation string(s) only).
   * - ``childContainer``
     - Render additional HTML content inside the group (optional).
   * - ``cta``
     - Add a call-to-action button with a link (optional; see subvariables below).
   * - ``cta.label``
     - The button label (accepts translation string only).
   * - ``cta.link``
     - The target URL for the button.

Content group example
====================

.. code-block:: twig

   {% include '@MauticCore/Components/content-group.html.twig' with {
       heading: 'mautic.docs.content_group.heading',
       copy: [
           'mautic.docs.content_group.copy_1',
           'mautic.docs.content_group.copy_2'
       ],
       cta: {
           label: 'mautic.docs.content_group.cta_label',
           link: '/features'
       }
   } %}

