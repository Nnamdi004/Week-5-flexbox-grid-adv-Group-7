# Level 3 Reflection: Flexbox vs Grid

# 1. What I built
I built a page with a header, a navigation bar, a left sidebar (20% wide), a main content area (60% wide), a right sidebar (20% wide), and a footer. On smaller screens the layout changes depending on the screen size. I built the whole thing twice, once using Flexbox and once using CSS Grid.

# 2. Which was easier to implement?
Grid was easier for this layout. I wrote "grid-template-columns: 20% 1fr 20%" and used "grid-template-areas" to map out the whole page in one place. That gave me the three-column layout straight away. Flexbox needed more steps. I had to make the body a column flex container, then add a "content-wrapper" div inside it and make that a flex row for the three columns. I used "flex: 0 0 20%" on both sidebars and "flex: 1" on the main content to get the 20/60/20 split.

# 3. Which required less code?
Grid needed less code, especially for the responsive part. At tablet size I just rewrote the "grid-template-areas" map to move the sidebars below the main content. With Flexbox I had to add "flex-wrap: wrap" and then use the "order" property on each child to make them reflow in the right order. It worked but it was more lines and harder to read at a glance.

# 4. Which was more intuitive?
Grid was more intuitive for this level because the layout is two-dimensional. I could read "grid-template-areas" and immediately see what the page looked like. Flexbox is great for one direction but managing rows and columns at the same time meant nesting containers inside each other, which made it harder to keep track of what was controlling what.

# 5. When would I use each one?
I would use Grid whenever the layout has both rows and columns at the same time, like this one. I would use Flexbox for smaller one-direction things like a navigation bar, a row of cards, or centering a single item. In a real project I would probably use both together, Grid for the overall page structure and Flexbox for the components inside each section.

## Testing
I tested both versions in Chrome DevTools at 375px (mobile), 768px (tablet), and 1200px (desktop). Both versions looked identical at every breakpoint. The sidebars moved below the main content at tablet width and everything stacked into a single column on mobile.
