Card in card
============

Display a card with an image, eyebrow, heading, and icon, typically used as a featured or linked card.

Card in card template variables
==============================

.. list-table:: Card in card template variables
   :header-rows: 1

   * - Variable
     - Description
   * - ``image``
     - The image object for the card (see subvariables below).
   * - ``image.src``
     - The image source path (string).
   * - ``image.alt``
     - The image alternative text (accepts translation string only).
   * - ``eyebrow``
     - Optional eyebrow label above the heading (accepts translation string only).
   * - ``heading``
     - The main heading for the card (accepts translation string only).
   * - ``icon``
     - The icon class for the card's action (optional; defaults to an arrow icon).

Card in card example
====================

.. code-block:: twig

   {% include '@MauticCore/Components/card-in-card.html.twig' with {
       image: { src: '/images/feature.jpg', alt: 'mautic.docs.card_in_card.img.alt' },
       eyebrow: 'mautic.docs.card_in_card.eyebrow',
       heading: 'mautic.docs.card_in_card.heading',
       icon: 'ri-arrow-right-line'
   } %}

.. note::
   The ``image.alt``, ``eyebrow``, and ``heading`` variables should use translation string keys.
