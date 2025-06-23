Content section
==============

Content template relationships
-----------------------------

Content templates are designed to be nested for flexible layouts:

- A **section** wraps one or more blocks.
- A **block** wraps one or more groups.
- A **group** wraps one or more items and item rows.
- **Item** and **item row** are the leaf-level content templates.

Organize content into a section with a heading and a container for additional content or components.

Content section template variables
===============================

.. list-table:: Content section template variables
   :header-rows: 1

   * - Variable
     - Description
   * - ``heading``
     - Set the section heading (accepts translation string only).
   * - ``childContainer``
     - Render additional HTML content inside the section.

Content section example
======================

.. code-block:: twig

   {% set feature1 = 'mautic.docs.content_section.feature_1' %}
   {% set feature2 = 'mautic.docs.content_section.feature_2' %}

   {% include '@MauticCore/Components/content-section.html.twig' with {
       heading: 'mautic.docs.content_section.heading',
       childContainer: '<ul><li>{{ feature1|trans }}</li><li>{{ feature2|trans }}</li></ul>'
   } %}

.. note::
   Use a separate set block to define the content of the childContainer variable. This approach avoids common syntax issues.