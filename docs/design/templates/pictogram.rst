Pictogram
=========

Display a pictogram SVG icon with customizable size and color.

Pictogram template variables
===========================

.. list-table:: Pictogram template variables
   :header-rows: 1

   * - Variable
     - Description
   * - ``pictogram``
     - Set the pictogram name (SVG file name without extension).
   * - ``size``
     - Set the size of the pictogram icon (optional; default is 48). Available sizes: 48, 64, 80, 96, and 128.
   * - ``color``
     - Set the color of the pictogram icon (optional; defaults to the primary icon color).

Pictogram example
=================

.. code-block:: twig

   {% include '@MauticCore/Components/pictogram.html.twig' with {
       pictogram: 'automation',
       size: 64,
       color: '#007AFF'
   } %}

.. note::
   Check the pictogram names in the pictograms folder. Use CSS variables for color.