Modal template
==============

Use modals to display focused content that requires user attention or interaction without navigating away from the current page.

Modal template variables
========================

.. list-table:: Modal template variables
   :header-rows: 1

   * - Variable
     - Description
   * - ``id``
     - Unique identifier for the modal instance.
   * - ``size``
     - Sets the modal size; options are ``sm``, ``md``, ``lg``, ``xl``, or ``full-width`` (optional).
   * - ``type``
     - Defines the modal style, either ``productive`` or ``expressive`` (optional).
   * - ``preventCloseOnClickOutside``
     - Prevents the modal from closing when clicking outside of it if set to true (optional).
   * - ``modalHeading``
     - The main heading text displayed in the modal (optional, but recommended for accessibility).
   * - ``modalLabel``
     - Label text shown above the modal heading (optional).
   * - ``modalAriaLabel``
     - Accessible label for the modal for screen readers (optional; used if ``modalLabel`` or ``modalHeading`` are not set).
   * - ``closeButtonLabel``
     - Accessible label for the close button (optional; defaults to a translated close string).
   * - ``modalContent``
     - The main content displayed inside the modal.
   * - ``hasScrollingContent``
     - Enables scrolling within the modal content area if true (optional).
   * - ``isFullWidth``
     - Expands the modal to full width if true (optional).
   * - ``buttons``
     - List of button objects to display in the modal footer (optional). Follows the buttons template array format.
