Notifications
=============

Notifications are a critical component of user experience (UX) in digital products, serving as a bridge between the system and the user. They should enhance, not detract from, the user experience, assisting users in achieving their goals and providing immediate, relevant feedback. This guide synthesizes best practices from the Carbon Design System and industry standards to help developers create effective and user-friendly notifications.

Notification types and their use
================================

Understanding notification variants
-----------------------------------

Notifications come in various forms, each serving a specific purpose within an app:

- **Inline notifications**: these are integrated into task flows to inform users about the status of an action or system changes. They are typically placed at the top of the content area or near the relevant item.

- **Toast notifications**: these are time-based messages that appear at the top of the screen and disappear after a short duration. They are used for brief messages that do not require user interaction.

- **Actionable notifications**: these include interactive elements and require user interaction. They are styled similarly to inline or toast notifications but are more disruptive due to their interactive nature.

Design
------

- Carefully examine the context in which notifications appear. Use them sparingly and only when they add value to the user experience.
- Maintain consistency in the design and behavior of notifications across the app.
- Be sure to use high-contrast notifications for critical messaging, as low-contrast notifications are less visually disruptive.

Content
-------

- Notifications should be concise and to the point, with a short and descriptive title. The body content should be limited to one or two sentences.

Actions
-------

- Limit actionable notifications to one action per notification to avoid overwhelming the user.
- Inline notifications should persist until dismissed by the user or resolved through an action. Toast notifications can time out but should also include a close button.

Accessibility
-------------

- Notifications should be accessible and not rely solely on color to convey status, as this can be problematic for users with color blindness, so use additional HTML attributes according to the notification type.
- Toast notifications with interactive content should not automatically disappear to remain WCAG 2.1 compliant.

Using notification components
=============================

Standard notifications with icons
---------------------------------

For standard notifications that include an icon, developers should use a ``<div>`` element with the class ``alert`` and an additional class to specify the type of notification:

- ``.alert-success`` for success messages
- ``.alert-info`` for informational messages
- ``.alert-warning`` for warnings
- ``.alert-danger`` for errors

Each class corresponds to a specific icon and color that is automatically applied using CSS logic.

Example:

.. code-block:: html

    <div class="alert alert-warning" role="alert">
      No emails are scheduled to be sent.
    </div>

This displays a warning notification with an appropriate icon and color styling.

Larger notification blocks without icons
----------------------------------------

When a larger notification block is needed, for instance, to include headings or additional content, developers should use the ``alert`` class along with a column class that starts with the ``col-`` prefix. These notifications do not display an icon but have only a colored left border indicative of the notification type.

Example:

.. code-block:: html

    <div class="alert alert-warning col-md-6">
      <h4>No Results Found</h4>
      <p>Seems there are none! Try changing a filter (if applicable) or how about creating a new one?</p>
    </div>

This creates a more substantial notification block with a heading and paragraph, distinguished by a yellow left border for a warning but without an accompanying icon.