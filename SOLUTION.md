# Solution Steps

1. Define all CSS custom properties (design tokens) at the :root level in styles.css, covering the full color palette for the page background, surfaces, header/footer, status colors (sent/pending/failed), badge colors, table header/row colors, spacing scale, border-radius values, box shadows, and typography variables. This ensures every color reference throughout the stylesheet is centralized and easy to update.

2. Write the base CSS reset and body styles: use box-sizing: border-box on all elements, reset margin and padding to zero, then set the body's font-family, font-size, background-color, and text color using the custom properties defined in :root.

3. Structure the outer dashboard shell in HTML using a <div class='dashboard'> wrapper that contains: a <header> for the page title and subtitle, a <main> for the primary content, and a <footer> for copyright text. In CSS, make .dashboard a flex column occupying full viewport height so the footer sticks to the bottom.

4. Style the dashboard header with the dark navy background-color token, white text, comfortable padding, and a colored bottom border using the sent/green accent token to give the page a branded top stripe. Style the title and subtitle with appropriate font sizes, weights, and letter-spacing.

5. Inside <main>, create a <section class='stats' aria-label='Summary Statistics'> containing three <article> elements, one for each stat card. Each article gets both the base class .stat-card and a modifier class (.stat-card--sent, .stat-card--pending, .stat-card--failed). Inside each article, place a <div class='stat-card__body'> with a <span class='stat-card__value'> for the dollar amount and a <span class='stat-card__label'> for the descriptive text.

6. Style the .stats container as display:flex with flex-direction:row and a gap so the three cards sit side by side in a single horizontal row with equal widths (flex:1 on each card). Style the base .stat-card with white/tinted background, border-radius, box-shadow, overflow:hidden, and border-left with a transparent color as the placeholder. Apply the color-coded left border and tinted background for each modifier variant using the appropriate custom property tokens. Style .stat-card__value with a large font size and the matching status color, and .stat-card__label with small uppercase tracking text.

7. Below the stats section, create a <section class='transactions' aria-label='Transaction History'> with an inner <header> containing an <h2> title, followed by a <div class='transactions__table-wrapper'> that wraps a <table class='transactions__table'>. Give the table a proper <thead> with <tr> and <th scope='col'> elements for each column (Transaction ID, Recipient, Date, Amount, Method, Status), and a <tbody> with <tr> rows for each transaction entry. Use semantic <time datetime='...'> for dates, <code class='txn-id'> for transaction IDs, and <span class='badge badge--[status]'> for status values.

8. Style the transactions section as a card with background, border-radius, and box-shadow. Style the inner header with a bottom border. Style .transactions__table with width:100% and border-collapse:collapse. Target thead tr with the dark navy background and thead th with white uppercase small text and consistent padding. Use :nth-child(odd/even) selectors on tbody tr for alternating row background colors. Add a hover state using the hover token color. Add a bottom border to tbody tr cells except the last. Set consistent cell padding on td elements.

9. Style the .badge base class as display:inline-flex with padding, border-radius:9999px (pill shape), small uppercase bold font, and no text wrapping. Apply the three badge modifier classes (.badge--completed, .badge--pending, .badge--failed) each with their respective background-color and color tokens from :root so badges render as colored rounded pills in green, yellow, and red.

10. Add responsive breakpoints: at max-width 768px, switch .stats from flex-direction:row to flex-direction:column so cards stack vertically on smaller screens, and reduce padding on the main content area and header. At max-width 480px, reduce card body padding and table cell padding further for very small screens. Ensure the table wrapper has overflow-x:auto so the table scrolls horizontally on narrow viewports rather than breaking the layout.

