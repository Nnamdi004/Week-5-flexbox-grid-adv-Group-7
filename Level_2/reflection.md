# Level 2 Reflection: Flexbox vs Grid

# 1. What i built
I built a page with a header, navigation bar, a main content area (70% wide) next to a sidebar (30% wide), and a footer. On small screens everything stacks into one column. I built it with Flexbox once aswell as the CSS grid.

# 2. Which was easier to implement?
Grid was easier for this layout. ## Which was easier to implement?
Grid was easier for this layout. One line, "grid-template-columns: 7fr 3fr", gave me the 70/30 split, and "grid-template-areas" let me write the layout like a map of the page. Flexbox took more steps. I made the body a column, then made a row inside it for the main area and sidebar. My first attempt, "flex: 7" and "flex: 3", was slightly off because padding and borders changed the split. I fixed it with "flex: 0 0 70%" and "flex: 0 0 30%".

# 3. Which required less code?
Grid needed less HTML. Flexbox needed an extra wrapper "<div class="content">" around "main" and "aside", and Grid did not. The CSS was about the same length. On mobile, Flexbox needed two rules (change the direction to column, then reset the flex sizes), while Grid needed one block that redrew the layout map as a single column.

# 4. Which was more intuitive?
For a whole page layout, Grid was more intuitive. I could see the finished layout in "grid-template-areas", and moving things around for mobile just meant rewriting that map. Flexbox felt natural for lining things up in one direction, but nesting a flex row inside a flex column made me stop and think about which container controlled what.

# 5. When would I use each one?
I would use Grid for full page layouts that have both rows and columns, like this one. I would use Flexbox for smaller, one-direction jobs like a row of navigation links, a set of buttons, or centering one item inside a box. In real projects they work well together: Grid for the page structure and Flexbox for the pieces inside it.

## Testing
I tested both versions in the browser developer tools at 375px (mobile), 768px and 1024px (desktop). Both versions looked identical at every size, and the layout stacked correctly below 768px.