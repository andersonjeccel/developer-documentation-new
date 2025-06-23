Content item
============

Show a single content item with flexible layouts for images, logos, pictograms, statistics, or text.

Content item template variables
=============================

.. list-table:: Content item template variables
   :header-rows: 1

   * - Variable
     - Description
   * - ``type``
     - Set the layout type: ``image``, ``logo``, ``pictogram``, ``statistic``, or ``text`` (optional).
   * - ``heading``
     - Set the main heading for the content item (accepts translation string only).
   * - ``copy``
     - Provide the main text for the item (accepts translation string only).
   * - ``cta``
     - Add a call-to-action button with a link (optional; see subvariables below).
   * - ``cta.label``
     - The button label (accepts translation string only).
   * - ``cta.link``
     - The target URL for the button.
   * - ``image``
     - Display an image (optional; for ``image`` type; see subvariables below).
   * - ``image.path``
     - The relative path to the image file (string).
   * - ``image.alt``
     - The alternative text for the image (accepts translation string only).
   * - ``logo``
     - Display a logo (optional; for ``logo`` type; see subvariables below).
   * - ``logo.path``
     - The relative path to the logo file (string).
   * - ``logo.alt``
     - The alternative text for the logo (accepts translation string only).
   * - ``pictogram``
     - Show a pictogram icon (optional; for ``pictogram`` type).
   * - ``orientation``
     - Arrange pictogram horizontally if set to ``horizontal`` (optional; for ``pictogram`` type).
   * - ``statistic``
     - Show a statistic value (optional; for ``statistic`` type).

Content item example
===================

.. code-block:: twig

   {% include '@MauticCore/Components/content-item.html.twig' with {
       type: 'pictogram',
       heading: 'mautic.docs.content_item.heading',
       copy: 'mautic.docs.content_item.copy',
       pictogram: 'shield',
       orientation: 'horizontal'
   } %}

