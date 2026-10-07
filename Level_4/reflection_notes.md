# Level 4 Reflection: Flexbox vs. Grid

I built the same "Holy Grail" page twice (header, nav, two collapsible sidebars, a card grid and a three-column footer). Each CSS file has two parts: a theme section for colours and component styling that is identical in both files, and a layout section that is different. That way the two layouts can be compared fairly. I also checked both in a browser at four widths and with the sidebars collapsed, and the pages measured identically.

**Which was easier to implement?** Grid was easier for the page skeleton. Drawing the layout with `grid-template-areas` ("left main right", then "main main / left right" on tablet) took a few lines. In Flexbox we had to get the same result with `flex-wrap`, `order: -1` on main, and a mix of `flex-basis` values that change at each breakpoint. Flexbox felt easier for small, one-dimensional pieces: the header, nav toggles, card meta bar, and centring the card label with `margin: auto`.

**Which required less code?** It was close. Counting only the layout section, Flexbox has 98 non-blank lines and Grid has 111. Grid needed extra lines for the subgrid fallback and for placing overlapping items. Per layout task, though, Grid was shorter: three-column footer, page columns and card columns were each one declaration.

**Which was more intuitive?** Grid, once we thought in rows and columns. The cards show why. With subgrid, every card shares its row's three tracks, so titles and "min read" bars line up even when the text lengths differ. In Flexbox we only get a similar result by making the card body grow, and that only works inside each card, not across a row.

**Surprises I experienced:**
- `position: sticky` did not work on a grid item, because it can't leave its own grid area. We used `position: fixed` plus padding on the body in the Grid version.
- A collapsed sidebar still leaves its gap behind, so we pulled `main` into it with a negative margin in both versions.
- In Flexbox, `flex-grow` stretches an orphan card on the last row. We avoided it by setting card widths with container queries.

**When would we choose each?** You should use Grid for the overall page structure and any two-dimensional arrangement: dashboards, card galleries, and anything that needs alignment across rows and columns. You should use Flexbox for components that flow in one direction: navigation bars, toolbars, button groups, and content that should wrap naturally at its own size. In practice they work best together, with Grid for the page and Flexbox inside the components, which is what the header, nav and card components do.