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

---
Changing the default behaviour of the box model

In the standard box model the width of an element is calculated as left border + left padding + content width + right padding + right border. In some cases, this may be latger than the space it has to be in and hence will get pushed down (using floats). We can alter this by using the box-sizing property, we often set this to border-box. What border box does is takes the padding and border widths out of the calculation so we are just left with the content width value. It essentially make the elements contnent shrink to size so it will fit in a width we give it. e.g., when we set border-box, it will keep all padding and change content area to fit the given width of the parent element.

It is often standard to set this property in the universal selector so it applies to all out elements.

---
Flex box

A set of related CSS properties for building 1-dimentional layouts.

Child elements are automatically divided to fit within the parent element.

Flex box makes it easy to align items vertically and horizontally.

They essentially help replace the need for using floats.

The elements of a flex box are 
1. Flex container
2. Flex items
3. Main Axis
4. Cross Axis

To create a flex container, we set the parent display property to flex.
Flex items are the items which sit inside the flex partent.
The main axis is the hotizontal axis.
The cross axis is the vertical axis.

There are different properties we can apply to the container vs the items.

Some of the main properties:

    Flex Container
        gap -> the gap between child items
        justify-content -> Align items along the main axis (hotizontal)
        align-items -> Align items along the cross axis (vertical)
        flex-direction -> Define the main axis
        flex-wrap -> Allow items to wrap to a new line if they are too large
        align-content -> Align content when there are multiple lines due to flex-wrap being turned on.

    Flex Items
        align-self -> Overwrite align-items for individual elements
        flex-grow -> Allow an element to grow
        flex-shrink -> Allow an element to shrink
        flex-basis -> Define an items width opposed to the width property
        flex -> Shorthand for glex grow, shrink, basis.

Flex boxes align things into columns in a single row.

<div class="container">
      <div class="el el--1">HTML</div>
      <div class="el el--2">and</div>
      <div class="el el--3">CSS</div>
      <div class="el el--4">are</div>
      <div class="el el--5">amazing</div>
      <div class="el el--6">languages</div>
      <div class="el el--7">to</div>
      <div class="el el--8">learn</div>
</div>

If we look at the above, the div container has 8 elements with some simple text. As a div is a block element, when we display this, each text will be ordered one over the other. We can display this in a flex box by setting the display property on the container to flex. This will cause all children to be places side by side in a single row. All elements will take up as little horizontal space as possible and the height of the row will be equal to the element with the largest height.

With the flex box, we can now easily vertically align elements usign the align-items css property. We can also horizontally align elements using the justify-content property.

Using a flex box we can also order items using properties on the child elements. By default they are all given an order value of 0, so if we would like to place an element at teh start we could give it an order value of say -1, this would place it before all elements with the default value of 0. Vice-versa, we could also give them or order value of  >0 which would place them at the end.

Spacing between elements is always set using the gap property to the parent container, this is much better practice than placing a margin on all child elements.

---
Horizontal sizing child elements

Flex box makes the width of each element only as large as it has to be. We can alter this by usign the flex-basis property and set it to the width we would like. Then the actual width of the container will be the maximum out of width content and flex-basis.

Id all the items are to large to fit in the parent container, be default they will all be shunk to fit. We can alter this by setting the flex-shrink to say 0 rather than 1, this will allow them to be full size. flex-shrink essentially says whether flex box is allowed to shrink an element or not.

There is also a property called flex-grow, if set to 1 it will essetnitally make all elements grow until they fit the parent container. We can apply flex-grow to all child elements and set it to 1, we could then apply flex grow to a single element to 2, this will make that element take up twice as much as all other respective elements.

---
CSS GRID

CSS Grid is used to build 2-D layouts, we divide a container into rows and columns. It allows us to write much less HTML and CSS to get good layouts.

CSS Grid does not replace flex box, rather they work together.

CSS GRID is the most modern way to build web layouts, its also the most complete and probably the easiest.

To get started we set the display property to grid, we then set the grid template.

display: grid;
grid-template-columns: 250px 150px;

We give the grid-template-columns as many values as we would like, each value will be the exact width of that column. In the above example, we will get two columns the first will be 250px wide and the second will be 150px wide.

Similar to flex box, all elements will stretch to the max element height by default, we can obviously change this.

grid-template-rows: 300px 200px;

The above will make the height of the first row be equal to 300px and the second row 200px. If there is an element with an already defined height, it will keep its defined height, otherwise it'll be stretched.

If we want a gap between items we use the gap property. There is also a row-gap and column-gap.

column-gap: 30px;
row-gap: 60px;

Generally when using gird we use the fr unit which allows us to create flexible rows and columns. fr stands for fraction. If we have set widths for our columns and would like one column to take up the remaining space, we can jst give it a value of 1fr.

grid-template-columns: 200px 200px 1fr 100px;

If we would like 4 columns all the exact same width, we could give a property of:

grid-template-columns: 1fr 1fr 1fr 1fr;

If we would like to have three columns and the last out to only take up as much space as it needs we can give it a width of auto.

grid-template-columns: 1fr 1fr 1fr auto;

Notice how we have 1fr many times in the above examples? There is a much better way of getting around this by using the repeat CSS function.

grid-template-columns: 1fr 1fr 1fr 1fr; == grid-template-columns: repeat(4, 1fr);
^Explicit                                  ^Implicit

grid-template-columns: 1fr 1fr 1fr auto; == grid-template-columns: repeat(3, 1fr) auto;

We can get a similar effect on rows and row height:

grid-template-rows: 1fr 1fr;

This will find the element with the largest height and set it to 1fr, hence all elements will stretch to be the same height as the largest item, irrespective of what row it is on.

we could create a height for the container and all elements will stretch to take up the free space.

We can place children where would would like by setting their grid-column and grid-row.

.el--8 {
    grid-column: 2 / 3;
    grid-row: 1 / 2;
}

As this is only taking up one space, we can change this to 

.el--8 {
    grid-column: 2;
    grid-row: 1;
}

In the above, the child with class el--8 will be placed in column 2, row 1. It will take up 1 grid space. Alternatively, we could make it take up two columns..

.el--8 {
    grid-column: 2 / 4;
    grid-row: 1 / 2;
}

We can also shorten this by saying how many cells we would like to span.

.el--8 {
    grid-column: 2 / span 2;
    grid-row: 1 / 2;
}

If we would like an element to span the rest of the row or column there is a nice trick we can use.

.el--2 {
    grid-column: 1 /-1;
    grid-row: 2;
}

This will place the second element on the second row and span from column 1 to the end of the grid container, that what the -1 does.

We could also use -2 to go to the second last column or row.

We can also overlap items if we would like by using some of the above methods and setting things to sit in the same area.

ALIGNING ITEMS


</pre>
