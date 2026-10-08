# Level 1 Reflection: Flexbox vs. Grid

For Level 1 I built a simple page with a fixed-height header, a main area that expands to fill the remaining space, and a fixed-height footer, once with Flexbox and once with CSS Grid. Both versions share a `common.css` file for colours and spacing, so the two layout files contain only layout code.

**Which was easier to implement?**
Both were easy at this level, but Flexbox felt slightly quicker because the idea is simple: turn `body` into a column with `display: flex; flex-direction: column;` and give `main` `flex-grow: 1`. The only extra thing I had to remember was `flex-shrink: 0` on the header and footer so they never get squashed when the content is large. Grid needed a little more thinking up front, because I had to define all three rows at once with `grid-template-rows: 80px 1fr 80px`.

**Which required less code?**
They were almost identical in size. Flexbox needed rules on three different selectors (`body`, `header, footer`, and `main`), while Grid defined the entire structure in a single rule on `body`, plus optional `grid-area` lines. Grid kept the layout in one place, so the whole page structure could be read from one declaration.

**Which was more intuitive?**
For a one-dimensional stack like this, Flexbox was more intuitive, since I was only thinking about one direction and "which item should grow". Grid felt more explicit, which I liked, because the numbers `80px 1fr 80px` map directly to what I see on screen: top bar, flexible middle, bottom bar. The `1fr` unit made the "fill the leftover space" idea very clear.

**Responsiveness**
Both layouts are already a single column, so they stack on mobile by default. At 600px and below I reduced the header and footer height to 60px and the padding of `main` to 1rem. I tested both versions in the browser developer tools at mobile, tablet and desktop widths and they looked identical, with the footer staying at the bottom even with little content (thanks to `min-height: 100vh`).

**When would I prefer one over the other?**
I would choose Flexbox for one-dimensional layouts such as navigation bars, rows of buttons, centring content, or a simple column like this one. I would choose Grid when the page has both rows and columns that need to line up, such as a header, sidebars, main content and footer arranged together, because named areas and `fr` units describe the whole page in one place. For this Level 1 layout either works well, and the choice comes down to preference. The main lesson was that Flexbox is content-driven and Grid is layout-driven.