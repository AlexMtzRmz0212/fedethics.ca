# fedethics.ca
## [Version 1](Old/indexV1.html) was using tones of blue and golden, incluiding:

- ![#1a2f5e](https://placehold.co/15x15/1a2f5e/1a2f5e.png) `navy:       #1a2f5e;`
- ![#0f1e3d](https://placehold.co/15x15/0f1e3d/0f1e3d.png) `navy-deep:  #0f1e3d;`
- ![#1f4a9c](https://placehold.co/15x15/1f4a9c/1f4a9c.png) `royal:      #1f4a9c;`
- ![#c9a84c](https://placehold.co/15x15/c9a84c/c9a84c.png) `gold:       #c9a84c;`
- ![#e8d08a](https://placehold.co/15x15/e8d08a/e8d08a.png) `gold-lt:    #e8d08a;`
- ![#f9f6f0](https://placehold.co/15x15/f9f6f0/f9f6f0.png) `cream:      #f9f6f0;`
- ![#4a5568](https://placehold.co/15x15/4a5568/4a5568.png) `slate:      #4a5568;`
- ![#ffffff](https://placehold.co/15x15/ffffff/ffffff.png) `white:      #ffffff;`
- ![#dde3ef](https://placehold.co/15x15/dde3ef/dde3ef.png) `border:     #dde3ef;`
- ![#eef2fb](https://placehold.co/15x15/eef2fb/eef2fb.png) `tag-bg:     #eef2fb;`

## [Version 2](Old/indexV2.html) changed so the colors followed the book theme:

- ![#0a1a3a](https://placehold.co/15x15/0a1a3a/0a1a3a.png) `navy-deep: #0a1a3a;`
- ![#05122b](https://placehold.co/15x15/05122b/05122b.png) `navy-richer: #05122b;`
- ![#b22234](https://placehold.co/15x15/b22234/b22234.png) `crimson: #b22234;`
- ![#dc143c](https://placehold.co/15x15/dc143c/dc143c.png) `crimson-bright: #dc143c;`
- ![#ffffff](https://placehold.co/15x15/ffffff/ffffff.png) `white: #ffffff;`
- ![#ffffff](https://placehold.co/15x15/ffffff/ffffff.png) `white-soft: rgba(255,255,255,0.9);`
- ![#ffffff](https://placehold.co/15x15/ffffff/ffffff.png) `white-muted: rgba(255,255,255,0.7);`
- ![#ffffff](https://placehold.co/15x15/ffffff/ffffff.png) `border-light: rgba(255,255,255,0.15);`
- ![#ffffff](https://placehold.co/15x15/ffffff/ffffff.png) `grid-line: rgba(255,255,255,0.03);`

## [Version 3](Old/indexV3.html) follows the Web Content Accessibility Guidelines (WCAG):

1. The Contrast Ratio Standard
The goal is to ensure that users with visual impairments, including color blindness or low vision, can distinguish text from the background. Contrast is measured on a scale from 1:1 (white text on a white background) to 21:1 (black text on a white background).

Level AA (Standard): Requires a contrast ratio of at least 4.5:1 for normal text and 3:1 for large text (18pt or 14pt bold).

Level AAA (Enhanced): Requires a contrast ratio of at least 7:1 for normal text and 4.5:1 for large text.

2. Tools to Check Accessibility

WebAIM Contrast Checker: A popular browser-based tool where you enter Hex codes to see if they pass AA or AAA levels.

Adobe Color: Includes an "Accessibility Tools" tab that simulates different types of color blindness and checks contrast.

Browser DevTools: In Chrome or Firefox, right-click an element, select "Inspect," and click on the color square in the Styles pane. It will often show the contrast ratio and a pass/fail mark.

3. Beyond Contrast: Color Blindness

Accessibility isn't just about contrast; it’s also about not relying on color alone to convey meaning. For example, if an error message is only indicated by red text, a user with protanopia (red-blindness) might not notice the change.

Always pair color with a secondary indicator, such as an icon, a bold font weight, or an underline (e.g., "Error: [Icon] Please enter a valid email").

4. The "Greyscale Test"

A quick "lo-fi" way to test a design is to view it in greyscale. If you can still read the text and understand the hierarchy of the page without any color, your contrast is likely in a good spot.


### According to this, the webpage would have to be edited as follows:

1. Color Contrast (The Most Critical Issue)
Several elements likely fail the 4.5:1 contrast ratio requirement for normal text:

White Muted on Navy: Your --white-muted variable (rgba(255,255,255,0.7)) over --navy-deep is often borderline or failing for small body text (like the "sec-lead" or "card-desc").

Crimson on Navy: Red-on-dark-blue is notoriously difficult to read for many users. The "sec-label" and "card-link" using --crimson (#b22234) on a navy background may not reach the required contrast for small, bold text.

Placeholder Text: The email placeholder (rgba(255,255,255,0.4)) is almost certainly too faint to be legible.

2. Interactive Elements & Screen Readers
Non-Descriptive Links: You have multiple links that just say "Order your copy," "Get template," or "Get the four assets free." To a screen reader user navigating by links, "Get template" lacks context.

Fix: Use aria-label="Get the 90-Day Constitutional Launchpad template".

The Scorecard (JavaScript Logic): The "dots" used for scoring are <div> elements with onclick events.

Problem: They are not keyboard reachable (you can't Tab to them) and screen readers won't recognize them as buttons or sliders.

Fix: Use `<button>` elements or `<input type="radio">` buttons for the scores.

SVG Icons: Your icons (like the ones in the cards) don't have `<title>` tags or aria-hidden="true". Screen readers might try to read the code of the SVG or skip them awkwardly.

3. Structural & Semantic Issues
Skipped Heading Levels: You jump from `<h1>` in the hero to `<h2>` in sections, which is good. However, ensure that the content within cards (`<h3>`) follows the logical flow.

Form Labels: The email input uses a placeholder but lacks a <label> element. Placeholders disappear when the user starts typing, which is a major hurdle for users with cognitive disabilities.

Fix: Add a `<label for="nlEmail" class="sr-only">Email Address</label>`.

4. Visual Navigation
Focus States: You have styles for :hover, but no visible :focus styles for keyboard users. If I press "Tab" to navigate your site, I won't know which button or link I am currently on.

Fix: Add a:focus, button:focus { outline: 3px solid var(--crimson-bright); }.

- ![#0a1a3a](https://placehold.co/15x15/0a1a3a/0a1a3a.png) `navy-deep: #0a1a3a;`
- ![#05122b](https://placehold.co/15x15/05122b/05122b.png) `navy-richer: #05122b;`
- ![#ae1f2c](https://placehold.co/15x15/ae1f2c/ae1f2c.png) `crimson: #ae1f2c;`
- ![#c62837](https://placehold.co/15x15/c62837/c62837.png) `crimson-bright: #c62837;`
- ![#ffffff](https://placehold.co/15x15/ffffff/ffffff.png) `white: #ffffff;`
- ![#f0f0f0](https://placehold.co/15x15/f0f0f0/f0f0f0.png) `white-soft: #f0f0f0;`
- ![#d0d0d0](https://placehold.co/15x15/d0d0d0/d0d0d0.png) `white-muted: #d0d0d0;`
- ![#ffffff](https://placehold.co/15x15/ffffff/ffffff.png) `border-light: rgba(255,255,255,0.2);`
- ![#ffffff](https://placehold.co/15x15/ffffff/ffffff.png) `grid-line: rgba(255,255,255,0.03);`
- ![#ffb347](https://placehold.co/15x15/ffb347/ffb347.png) `focus-outline: 4px solid #ffb347;`


## [Version 4](Old/indexV4.html) includes Author Backgrounder


## [Version 5 (Current)](index.html) has a newsletter subscription button.