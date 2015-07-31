---
layout: post
categories: design css box-sizing
---

The box-sizing property was introduced in CSS3. It provides an alternative method for calculating an element's size. Box-sizing can accept one of two values: content-box or border-box. These values allow us to decide whether content or borders determine the width and height of an element.  

##content-box
If we leave the value for box-sizing undeclared, it will default to content-box. This is the standard box-model, where width and height values apply to only the element's content. The default behavior calculates dimensions by adding the content's width (or height) to padding and borders. With default box-sizing, the width and height we set for an element are increased when padding and borders are added.

We can give an element 400px of width and watch it grow to 450px if given 20px of padding and a 5px border.


    #content-box-example {
      width: 400px;
      padding: 20px;
      border: 5px #000 solid;
      height: 100px;
      margin: 2em auto;
    }


<div id="content-box-example">
  <p>
    This element is 450px wide.
  </p>
</div>

##border-box
The border-box option is often used to easily keep track of element dimensions. This property makes the browser include padding and borders in the width and height values. Essentially, width and height are unaffected by padding and borders. We could set an elements width to 50% and the element will take up 50% of the space, even with padding and borders applied. This means that our content must grow smaller to accommodate padding and borders.

With this property we can give an element a width of 400px, 20px of padding, and a 5px border without our element growing any larger. However, our content will shrink to 350px to make room for padding and borders.

    #border-box-example {
      box-sizing: border-box;
      width: 400px;
      padding: 20px;
      border: 5px #000 solid;
      height: 100px;
      margin: 2em auto;
    }

<div id="border-box-example">
  <p>
    This element is 400px wide.
  </p>
</div>

Most web designers find the border-box setting quite useful, so they create a universal selector style to apply it to every element on a page.

    *, *:before, *:after{
      box-sizing: border-box
    }

Ultimately, border-box is superior to content-box because elements will remain the size you declare. This makes your life as a developer or designer just a bit easier.
