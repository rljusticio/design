---
layout: post
title: CSS Positioning
categories: css design
---

The [CSS position](https://developer.mozilla.org/en-US/docs/Web/CSS/position 'Position on MDN') property grants us control over how and where a web browser displays elements. CSS treats each html element as either a block-level box or an inline box. Block-level boxes act as the main building blocks of any layout, while inline boxes live inside block-level boxes as flowing text and images.


##Static
All elements default to static positioning if we don't declare a position value.

    .box{
      position: static; // We can omit this declaration
      height: 100px;
      width: 100px;
    }

In normal flow, [block-level](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements 'Block-level on MDN') boxes flow vertically starting at the top of their parent container. Each box is placed directly below the preceding one, because block-level elements consume the entire width of their parent container. If we were to specify the widths of the boxes and there was adequate space for two elements to sit side by side, two block level elements would not sit next to each other in normal flow.

    .box-red{
      height: 100px;
      width: 100px;
      background-color: red;
    }
    .box-green{
      height: 100px;
      width: 100px;
      background-color: green;
    }
    .box-blue{
      height: 100px;
      width: 100px;
      background-color: blue;
    }
<div class='demo'>
  <div class='box-red'></div>
  <div class='box-green'></div>
  <div class='box-blue'></div>
</div>

Note how these boxes stack vertically, even with widths as small as 100px.

<div class='demo'>
  <p>
    Note how this text wraps as it reaches the edge of it's container. Inline elements wrap as they get too wide for their container, while block-level elements stack vertically.
  </p>
</div>
[Inline](https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elemente 'Inline on MDN') boxes flow horizontally from left to right. When there isn't enough space to fit all the inline elements on one line, they wrap to the next line.


##Relative
Relatively positioned elements behave similarly to static elements, except they are subject to the values of four other CSS properties. Setting the top, right, bottom, and left properties allows us to move an element from its position in normal flow, shifting it away from where it would have been placed. Other content is not adjusted to fit into any gaps left by the relatively positioned elements, they stay in the position they would be in normal flow.

The offset values are specified using a combination of the top, right, left and bottom properties. These properties adjust an element's position relative to where it appears in normal flow. The value of each offset property is understood as the distance the box should be moved from it's original position.

    .box-red{
      position: relative;
      height: 100px;
      width: 100px;
      background-color: red;
      left: 300px;
      top: 100px;
    }
    .box-green{
      position: relative;
      height: 100px;
      width: 100px;
      background-color: green;
    }
    .box-blue{
      position: relative;
      height: 100px;
      width: 100px;
      background-color: blue;
      left: 150px;
      bottom: 50px;
    }
<div class='demo'>
  <div class='box-red offset-relative'></div>
  <div class='box-green'></div>
  <div class='box-blue offset-relative'></div>
</div>

The red box is relatively positioned 300px right and 100px down from it's origin, while the blue box is 150px right and 50px down from it's origin. Moving an element with offset properties creates space on the specified side of the element. Left: 300px creates 300px of space on the left side of the red box, leaving it 300px to the right of it's origin.

Note that the green box has not moved, despite the absence of it's sibling elements. Remember, content will not adjusted to fit into gaps left by relatively positioned elements.

Although offsetting an element's position can be useful, the main benefit of relative positioning is to set a new point of reference for absolutely positioned elements that are nested inside it.


##Absolute
Absolute positioning lets you determine an element’s location by specifying a left, right, top, or bottom position. The box offset properties specify where the element should appear in relation to its containing element.

These absolutely positioned elements are positioned relative to the boundaries of the nearest positioned parent element. A positioned element is one whose position is anything except static, meaning relative, absolute, or fixed. If there are no positioned parent elements, the point of reference is set to the document body and the element moves along with the page as it scrolls.

    .box-red{
      position: absolute;
      height: 100px;
      width: 100px;
      background-color: red;
      left: 60px;
    }
    .box-green{
      height: 100px;
      width: 100px;
      background-color: green;
    }
    .box-blue{
      height: 100px;
      width: 100px;
      background-color: blue;
    }

Absolutely positioned elements are taken out of normal flow, meaning that they do not affect the position of surrounding elements. The space originally occupied by the element will not be honored by surrounding elements, which behave as if the absolutely positioned element is not there. This means that you can put it anywhere, and it won’t affect or be affected by any other element.

<div class='demo relative'>
  <div class='box-red absolute-offset'></div>
  <div class='box-green'></div>
  <div class='box-blue'></div>
</div>

In this case the red box is positioned absolutely, so it is taken out of normal flow. The other boxes then ignore the red box, as it exists on its own layer now, and shift upward to fill the empty space. The red box has been shifted to the right with a 60px offset to demonstrate how it exists on a separate layer, obscuring the green box.

The box with the thin black outline has been positioned relatively to create a new positioning context for the elements inside. Had we not positioned the container, our boxes would be positioned relative to the browser window rather than our container.


##Fixed
Fixed positioning is a form of absolute positioning that positions the element in relation to the browser window instead of a parent container. This allows us to position elements relative to the viewport, which means that these elements will stay in the same place as the page is scrolled. As with relative and absolute positioning, top, right, bottom, and left properties are used to position the element.

Fixed elements do not leave a gap in the page as they are removed from normal flow.  We can think of absolute and fixed positioned elements as existing on a layer above the page. Elements on this layer do not interrupt normal flow.


##Overlapping Elements
When elements are positioned, they can overlap each other. These elements stack on the z-index. The [z-index](https://developer.mozilla.org/en-US/docs/Web/CSS/z-index 'z-index on MDN') property specifies the stack order of the elements and allows us to control which box appears on top.

Normally, the stacking order of positioned elements follows their order in the page’s HTML code. The elements that appear later in the html code sit on top of those that are earlier in the page. We can give positioned elements positive or negative z-index values to determine their stacking order. An element with a higher z-index appears in front of an element with a lower z-index. When two elements have the same value (or if neither has been assigned a value) the source order is used. The element that is defined earlier in the source is displayed behind the one defined later.

    .box-red{
      position: absolute;
      height: 100px;
      width: 100px;
      background-color: red;
    }
    .box-green{
      position: absolute;
      height: 100px;
      width: 100px;
      background-color: green;
    }
    .box-blue{
      height: 100px;
      width: 100px;
      background-color: blue;
    }

<div class='demo relative'>
<div class='box-red absolute'></div>
<div class='box-green absolute'></div>
<div class='box-blue'></div>
</div>

In the example above, the red and green boxes have been positioned absolutely, placing them on a layer of their own and overlapping the blue box entirely.

    .box-red{
      z-index: 1;
    }

<div class='demo relative'>
<div class='box-red absolute zindex'></div>
<div class='box-green absolute'></div>
<div class='box-blue'></div>
</div>

Note how the red box is now at the top of the stacking order. The z-index property overrides the natural stacking order and forces an element to the foreground.
