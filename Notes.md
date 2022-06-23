<pre>
Responsive Web Design

*Create a queries.css file to hold all our media queries
*Never use pixels in our queries.css file, use em (rem in the queries does not relate to the html font size, it'll rather be equal to 1em or 16px), the browser may have bugs when using rem in media queries so use em.

* rem = root font size
* em = current font size

We can create responsive web pages by using the media query within CSS
We simply say

@media (max-width: 600px) {
    .<class>{
        <style-property>: <value>;
    }
}

In the above example, when the viewport width becomes less than 600px wide, it will use all the CSS enclosed.

We can have as many media queries as we would like and multiple can be applied at the same time. Conflicting styles will be replaced by the last in the media query

We set break points based on when our screens begin to break and common ranges of size e.g.
    Phone - 300-500px
    Tablet - 600-900px
    Landscape Tablet - 900-1100px
    Laptop + Desktop - >1200px 

To ensure our responsive design will work we must ensure the below tag is in our head.

<meta name="viewport" content="width=device-width, initial-scale=1.0" />

This stops phones from auto zooming out the webpage.

To begin
1) open up dev tools and select alternate screen sizes.
2) start at full size and make smaller until the page breaks or doesn't look good.
</pre>
