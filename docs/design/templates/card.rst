Card
====

Display a card component with flexible layouts, supporting images, headings, copy, tags, pictograms, and call-to-action buttons.

Card template variables
======================

.. list-table:: Card template variables
   :header-rows: 1

   * - Variable
     - Description
   * - ``type``
     - The card type: ``default``, ``static``, ``logo``, ``link``, ``pictogram``, ``feature``, or ``feature--large`` (optional; default is ``default``).
   * - ``aspectRatio``
     - The aspect ratio for the card image: ``1:1``, ``2:1``, ``3:2``, ``4:3``, or ``16:9`` (optional; default depends on type).
   * - ``ctaType``
     - The call-to-action type: ``local``, ``jump``, ``external``, ``new tab``, ``download``, ``video``, ``pdf``, ``blog``, ``modal``, ``email``, ``schedule``, ``chat``, or ``call`` (optional; default is ``local``).
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
   * - ``copy``
     - The main text content for the card (accepts translation string only).
   * - ``tags``
     - List of tag objects to render (optional; see tag template for details).
   * - ``pictogram``
     - The pictogram icon name (optional).
   * - ``cta``
     - Call-to-action button object (optional; see subvariables below).
   * - ``cta.label``
     - The button label (accepts translation string only).
   * - ``cta.link``
     - The target URL for the button.
   * - ``href``
     - The link URL for the card (optional).
   * - ``disabled``
     - If true, disables the card interaction (optional).

Card example
============

.. code-block:: twig

   {% include '@MauticCore/Components/card.html.twig' with {
       type: 'feature',
       image: { src: '/images/feature.jpg', alt: 'mautic.docs.card.img.alt' },
       eyebrow: 'mautic.docs.card.eyebrow',
       heading: 'mautic.docs.card.heading',
       copy: 'mautic.docs.card.copy',
       tags: [ { label: 'mautic.docs.card.tag1' }, { label: 'mautic.docs.card.tag2' } ],
       pictogram: 'automation',
       cta: { label: 'mautic.docs.card.cta.label', link: '/learn-more' },
       href: '/feature',
       disabled: false
   } %}

.. note::
   All text variables (e.g., ``heading``, ``copy``, ``cta.label``, ``image.alt``) should use translation string keys.
