Tile Component Documentation
=============================

Overview
--------

The Tile component is a versatile, reusable UI element. It is designed to be flexible and adaptable, capable of serving a variety of functions in a user interface. The Tile component can be used to display content, act as a clickable or selectable element, or even house an icon.

It is designed to group related information in flexible containers and can contain text, images, and/or a block of color. The usage guidance for the Tile component is intentionally high-level, focusing specifically on the tile's structure and responsiveness to the grid. It does not have pre-set styles for the content within them, allowing for a wide variety of content to be displayed. This flexibility makes tiles suitable for various use cases, such as displaying feature highlights, providing navigation options, or presenting data summaries, including information, getting started guides, how-to guides, and more.

CSS class definitions
---------------------

``.tile`` 
    This is the base class for the Tile component. It sets up the basic appearance and layout of the tile, including its size, padding, background color, and border radius. It also sets up some default styles for when the tile is in focus.

``.tile-clickable`` and ``.tile-selectable`` 
    These classes are modifiers for the base ``.tile`` class. They are used to make the tile behave as a clickable or selectable element, respectively. These classes adjust the padding, border, margin, font properties, and cursor style of the tile. They also set up hover and focus styles.

``.tile-icon`` 
    This class is used for an icon within the tile. It positions the icon within the tile and sets its color. It also includes styles for when the icon is disabled.

How to use
----------

To use the Tile component, you need to add the ``.tile`` class to an HTML element. If you want the tile to be clickable or selectable, add the ``.tile-clickable`` or ``.tile-selectable`` class as well. If you want to include an icon in the tile, add an element with the ``.tile-icon`` class inside the tile.

.. code-block:: html

    <div class="tile">
        <p>Basic Tile Content</p>
    </div>

    <a class="tile tile-clickable">
        <p>Clickable Tile Content</p>
    </a>

    <a class="tile tile-selectable">
        <p>Selectable Tile Content</p>
    </a>


Examples
--------

.. image:: design/images/tile.png
   :alt: Base tile used to display import file information

   .. image:: pdesign/images/tile-clickable.png
   :alt: Example of a clickable tile used to create an expressive link


.. note::

    When a tile is not clickable, you must use a ``<div>`` tag. Use a ``<a>`` tag only when turning the tile into a clickable element.
