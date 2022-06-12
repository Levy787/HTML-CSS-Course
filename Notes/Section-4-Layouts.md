<pre>
Section 4 Notes - Layouts

The original way to build layouts was using the CSS float property. These are somtimes used but have generally been replaced with flex box and grid.

Flex box uses a row layout, it gives us a single row with many columns and allows us to place things side by side.

The grid allows us to build 2-D layouts, e.g., many rows and mnany columns.

---
Float Layouts

The most basic example is to take something and set it's float property to say left...

.author-img {
  float: left;
}

This will then push the element to the left similar to absolute positioning and then make all other elements float around it as normal.

The float property makes things take up the minimum space possible.

Floats are not a positioning thing but act like absolute positioning. They do have some impact on surrounding elements.

Container elemetns do not adjust their height to floated elements.

When we make all child elements float, the parent thinks it holds nothing and hence whill often lose it's height. The padding will stay however. This is called collapsing elements. We can fix this however. 

To get around this we add a div element as a child and give it a class, we then style that class giving it a property of clear, this will then clear on the left floats or right floats. e.g.,

<div>
    <div class="c1">abc</div>
    <div class="c2">def</div>
    <div class="clear"></div>
</div>

.c1 {
    float: left;
}
.c2 {
    float: right;
}
.clear {
    clear: both;
}

This is quite bad practice as it leaves us with a lot of empty divs throughout out code. A better method is to use clear fixed tag. Here we essentially give a class name to the parent of clearfix, we then create a pseudo element to essentially add that div to the end and set the clear property. e.g.,

<div class="clearfix">
    <div class="c1">abc</div>
    <div class="c2">def</div>
    <div class="clear"></div>
</div>

.clearfix::after {
    content: "";
    clear: both;
    display: block;
}


</pre>
