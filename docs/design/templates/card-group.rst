Card group
=========

Display a group of cards arranged in a grid layout, supporting various card types and row configurations.

Card group template variables
============================

.. list-table:: Card group template variables
   :header-rows: 1

   * - Variable
     - Description
   * - ``type``
     - The card group type: ``default``, ``static``, ``logo``, ``link``, ``pictogram``, or ``card-in-card`` (optional; default is ``default``).
   * - ``gridMode``
     - The grid layout mode: ``default``, ``narrow``, or ``condensed`` (optional; default is ``default``).
   * - ``cardsPerRow``
     - Number of cards per row (optional; default is 3).
   * - ``cardSectionOffset``
     - If true, adds an offset to the first card (optional).
   * - ``cards``
     - List of card objects to render (array; see card or card-in-card template for details).

Card group example
==================

.. code-block:: twig

   {% include '@MauticCore/Components/card-group.html.twig' with {
       type: 'default',
       cardsPerRow: 3,
       cards: [
           { heading: 'mautic.docs.card.heading1', copy: 'mautic.docs.card.copy1', image: {src: '/img1.jpg', alt: 'mautic.docs.card.img1.alt'} },
           { heading: 'mautic.docs.card.heading2', copy: 'mautic.docs.card.copy2', image: {src: '/img2.jpg', alt: 'mautic.docs.card.img2.alt'} }
       ]
   } %}

.. note::
   The ``cards`` variable accepts both regular cards and card-in-card objects depending on the ``type``. When using the type card-in-card, only the first card is displayed as card-in-card and the rest are displayed as regular cards.
