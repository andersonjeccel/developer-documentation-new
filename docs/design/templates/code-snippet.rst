Code snippet
===========

Display code in inline, multi-line, or single-line formats and let users easily copy the content if needed.

Code snippet template variables
==============================

.. list-table:: Code snippet template variables
   :header-rows: 1

   * - Variable
     - Description
   * - ``type``
     - Set the variant of the code snippet: ``inline``, ``multi``, or ``single``.
   * - ``innerText``
     - Provide the code or text content to display.
   * - ``className``
     - Add custom CSS classes to the code element (optional).
   * - ``ariaLabel``
     - Set an accessible label for the code element (optional).
   * - ``copyButtonDescription``
     - Set an accessible label or tooltip for the copy button (optional).
   * - ``copyText``
     - Set the text to be copied to the clipboard when using the copy button (optional; defaults to ``innerText``).
   * - ``disabled``
     - Disable the code snippet and copy functionality if true (optional).
   * - ``hideCopyButton``
     - Hide the copy button if true (optional; only for ``multi`` and ``single`` variants).

Example:

.. code-block:: twig

   {% include '@MauticCore/Helper/code_snippet.html.twig' with {
       'type': 'inline',
       'innerText': 'hello.world.text',
       'className': 'my-class',
       'ariaLabel': 'code.snippet.aria.label',
       'copyButtonDescription': 'copy.code.button.description',
       'copyText': '<iframe src="https://www.youtube.com/embed/VIDEO_ID"></iframe>',
       'disabled': false,
       'hideCopyButton': false,
   } %}
       