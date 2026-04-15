HNG Stage 1a: Advanced Todo Card

Built on top of Stage 0. 
 
1. What changed from Stage 0

- Edit mode: clicking Edit reveals an inline form with fields for title, description, priority, and due date. Save commits changes; Cancel restores the previous values. 
- Status control: a dropdown lets the user switch between Pending, In Progress, and Done. The checkbox, status badge, and dropdown stay in sync at all times.
- Priority indicator: a colored dot and left border accent on the card change color depending on priority (red = High, amber = Medium, green = Low).
- Expand/collapse: descriptions longer than 100 characters are truncated with a Show more/Show less toggle. Uses aria-expanded and aria-controls correctly.
- Overdue indicator: if the due date has passed and the task is not Done, a red Overdue badge appears and the time remaining shows in red.
- Time updates every 30 seconds and shows granular text (minutes, hours, days, weeks). Stops and shows "Completed" when status is Done.

2. Design decisions

- Single state object with a renderView() function; all DOM updates go through one path, no scattered mutation.
- Native HTML elements for all controls (select, input, textarea, checkbox) for maximum accessibility.
- The edit form is hidden with the hidden attribute (not display:none in CSS) so assistive technology correctly ignores it when not in use.

3. Accessibility notes

- All form fields have label elements with for attributes matching input ids.
- Focus trap keeps keyboard users inside the edit form while it is open.
- aria-live="polite" on the time remaining element so screen readers announce updates.
- aria-expanded and aria-controls on the expand toggle per WCAG pattern.
- Visible focus rings on all interactive elements.
