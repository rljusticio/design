Float
-floating an element allows you to take that element out of normal flow and
position it to the far left or far right of a containing box.
-the floated element becomes a block-level element around which other content
can flow
-the float property moves an element to either the left or right. In the process,
content below the floated element moves up and wraps around the float
-Floated elements move to the left or right edge of their containing element. In
some cases, this just means that the element moves to the left or right edge of the
browser window. However if you float an element that’s inside another tag with a
set width or position on a web page, then the float will go to the left or right edge
of that tag—the floated element’s “container.”
-A web browser treats a floated inline element just like a block-level
element, so you don’t run into the problems with padding and margin that normally
trouble inline elements
-CSS rules require setting the width for floated elements for all tags except images
-when specified, the box is positioned vertically as it would be within the  
normal flow, its top aligned with the top of the current line box. But horizontally,
it is shifted as far to the right or left of its containing block as possible,
within that block's padding
-the box being floated should have a width defined for it, either explicitly or implicitly. Otherwise, it will fill its containing block horizontally
-anything else that sits inside the containing element will flow around the
element that is floated
-the vertical margins of a floated box are not collapsed with the margins of
boxes either above or below it
-when you use the float property you should also use the width property to indicate
how wide the floated element should be
-a lot of layouts place boxes next to each other, the float property is commonly
used to achieve this.
-when elements are floated, the height of the boxes can affect where the following
elements sit
-if a containing element only contains floated elements, some browsers will treat
it as if it is zero pixels tall
-add two rules to the containing element to solve this: overflow: auto and width:
100%
-the float property specifies whether or not an element should float.
-the clear property is used to control the behavior of floating elements.
-elements after a floating element will flow around it. To avoid this, use the
clear property.
-if an element is taller than the element containing it, and it is floated,
it will overflow outside of its container.
-then we can add overflow: auto; to the containing element to fix this problem
-floated elements remain a part of the flow of the web page
-there are four valid values for the float property. Left and Right float elements
those directions respectively. None (the default) ensures the element will not
float and Inherit which will assume the float value from that elements parent
element.
-floats can be used to create entire web layouts
-if this parent element contained nothing but floated elements, the height of it would literally collapse to nothing
-collapsing almost always needs to be dealt with to prevent strange layout and
cross-browser problems. We fix it by clearing the float after the floated
elements in the container but before the close of the container.



Clearing Floats
-the clear property allows you to say that no element (within the same containing
element) should touch the left or right-hand sides of a box. It can take the
following values:
  -left: the left hand side of the bx should not touch any other elements
  appearing in the same containing element
  -right: the right-hand side of the box ill not touch elements appearing in the
  same containing element
  -both: neither the left nor right side if the box will touch elements appearing
  in the same containing element
  -none: elements can touch either side
-an element that has the clear property set on it will not move up adjacent to
the float like the float desires, but will move itself down past the float.

Methods for Clearing Floats
-The Empty Div Method
  -literally an empty div. <div style="clear: both;"></div>
  -div is the most common because it has no browser default styling, doesn't
  have any special function, and is unlikely to be generically styled with CSS.
-The Overflow Method
  -relies on setting the overflow CSS property on a parent element
  -If this property is set to auto or hidden on the parent element, the parent
  will expand to contain the floats, effectively clearing it for succeeding elements.
