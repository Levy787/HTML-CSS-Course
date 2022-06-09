We have a server which is a computer connected to the internet. Our browser makes a request to the server and the server sends all reuqired files back (response) to the browser requesting. Generally this will be HTML, CSS and JavaScript files. The browser will then look at these and render the website in the browser.

Front-end - HTML, CSS and JavaScript

We also have backend which includes the code running on the web servers, this will allow us to create much larger programs. This is generally done in Node.js, php, python c++ etc. There server will determine what files to provide the browser depending on the state and user requests etc.

HTML is responsible for the content on the web page - text, images, iconsetc. (Noun)
CSS is responsible for the layout and colors and positioning of HTML. (Adjective)
Javascript is used to help manage state and manipulate the info displayed. (Verb)

---

Index is the first page of any website, its the entry point to any website.

---

<h2>--- HTML Fundamentals ---<h2>

<h3>Basics<h3>

HTML - Hyper Text Markup Language

     v content    v closing tag

<p>paragraph tag</p>  <- Element
 ^Opening tag

Some tags dont have content in which case we can ommit the closing tag
v To self close we place a "/" at the end
<img rec="abc.jpeg" />

<h3>HTML structure</h3>
1. We start by setting the document type, in almost all cases this will be a html doc type to set that we say
     <!DOCTYPE html>
2. We must then set a html element which will hold all our html.
     <html></html>
3. There are generally two tags that fall inside the html element the <head> tag and <body> tag.
4. The head tag stores the meta data about the page an doesn't show anything visible on the screen. It holds things like the page title <title> and CSS links etc.
5. The body holds all information which is shown on the page.

So based on the above, the most basic template is below:

<!DOCTYPE html>
<hmtl>
  <head>
    <title>The Basic language of the web: HTML</title>
  </head>
  <body>
    <h1>Heading 1</h1>
  </body>
</hmtl>

Some things to remember are the we always need the <DOCTYPE>, <html>, <head> and <body> tags.

---

Heading - <h1> is a heading 1 tag, there are 6 heading tags, they get smaller as you go down <h1><h2><h3>...<h6>
Paragraph - <p>
Comments - <!--comment here--> This creates a comment tag
Bold - <b> -> <p>Posted by <b>Laura Jones</b> on 1/1/2021</p> <-- Bad practice, this is an old element. We should use strong!
Bold - <p>Posted by <strong>Laura Jones</strong> on 1/1/2021</p>
Italic -> Old <i> new <em> i is the old tag which should not be used, we should instead use em which stands for emphasise.

Lists - There are two main types of lists, ordered lists and unordered lists <ol> - ordered list <ul> - unordered list
Each list needs a list element <li>
So an ordered list would look like

<ol>
  <li>The opening tag</li>
  <li>The closing tag</li>
  <li>The actual element</li>
</ol>

An unordered list would look like

<ul>
  <li>To be able to use the fundamental web dev language</li>
  <li>To build web applications</li>
  <li>To impress friends</li>
  <li>To have fun 😃</li>
</ul>

\*\* The <i> and <b> tags are not semantic where as the <strong> and <em> have semantic meaning and are prefered.
\*\* Each page should only have one h1 tag

---

Images
<img> -> The tag used for displaying images.

When displaying images they dont have any content, rather we pass the element attributes which tells the tag what and how to load the image. We then self close the tag e.g., <img src="./post-img.jpg" />
^tag ^attribute ^img dir ^self closing tag

When using an image tag we should always use the alt attribute, this is the alternate text to be shown for blind people or if the image cannot be loaded for whatever reason, It also tells google what is in the image making search results better.

We also have width and height attributes. The default is in pixels eg., <img src=... alt=... width="500"> <- This would hold the aspect ratio of the image the same but make the width exactly 500 pixels wide. We can do a similar thing with the height. We can distort the image by specifiying different heights and widths to its orgiginal ratios.

We can also get images from the net such as
<img src="https://i.ibb.co/JrWh1d/challenges.jpg">

---

Attributes
We saw that the image tag has attributes, there are also other tags which require attributes such as the html tag. One thing we should always do is specify the language as an attribute in the html tag.

<html lang="en"></hmtl>

Within our template we should also specify the character set being used, this is generally stored in a meta tag which is within the head tag.

<head>
  <meta charset="UTF-8">
</head>

---

Links

There are two fundamental types of links

1. Links pointing to pages within our web page
2. Links pointing to external websites.

These are both created in the same way.

<a> is the tag used to specify a link, the tag stands for anchor. To give it somewhere to link to we set the href attribute. We can also specify content which will be the tag.

Example
vv
<a href="https://developer.mozilla.org/en-US/docs/Web/HTML">MDN Web Docs</a>

This type of tag will load a page into the current tab, we can also specify the target attribute to \_blank which will open the link in a new tab

<a href="https://developer.mozilla.org/en-US/docs/Web/HTML" target="_blank">MDN Web Docs</a>

We can also create links to navigate within our website. First we create a new html doc, set the template up and save it.
We then create our link tag and set the href as the new file name
<a href="./blog.html">Blog</a>

So when we click on the blog link, it will load the blog.html file into the browser.

We can also create links which dont lead anywhere by setting the href to #, this will essentially take you back to the top of the current page you are on.
<a href="#">Challenges</a>

---

Structuring hmtl documents

In our page we have

<body>
    <h1>📘 The Code Magazine</h1>
    <a href="./blog.html">Blog</a>
    <a href="#">Challenges</a>
    <a href="#">FlexBox</a>
    <a href="#">CSS Grid</a>
    <h2>The Basic Language of the Web: HTML</h2>
    ...
</body>

It would be nice to structure this a bit better, a good way to start would be to group the navigation links into a container, there is a special container made for this called a <nav>.

<body>
    <h1>📘 The Code Magazine</h1>
    <nav>
      <a href="./blog.html">Blog</a>
      <a href="#">Challenges</a>
      <a href="#">FlexBox</a>
      <a href="#">CSS Grid</a>
    </nav>
    <h2>The Basic Language of the Web: HTML</h2>
    ...
</body>

This doesnt change the visuals of our web page.

We may also want to group the navigation bar and heading into a header.

<body>
    <header>
      <h1>📘 The Code Magazine</h1>
      <nav>
        <a href="./blog.html">Blog</a>
        <a href="#">Challenges</a>
        <a href="#">FlexBox</a>
        <a href="#">CSS Grid</a>
      </nav>
    </header>
    <h2>The Basic Language of the Web: HTML</h2>
     ...
</body>

Again this doesn't change our layout.

We can then put the blog post into an article element.

<body>
     <header>
          ...
     </header>
     <article>
          <h2>The Basic Language of the Web: HTML</h2>
          ...
     </article>
</body>

Now our body only has two elements, the header and article.
This can keep going deeper, so we can set a header within the article tag.

There is also a <footer> tag which is self explanitory

There is also an <aside> tag which is generally used for a side bar.

---

HTML entites

HTML entites are symbols that are built into html, we can generally search for what we would like on the internet. An example is the copywrite symbol.

We specify it like so &<symbol name>;

For the copywrite symbol its $copy;

So we can set our footer to by

<footer> Copywrite &copy; 2017 by The Code Magazine</footer>

There are many html entites!

---

Semantic HMTL

Semantic elements essentially means that an element has a meaning attached to it rather than just how it looks on the web page.

Not all elements in html are semantic such as the <b> an <i> tags. This means that the text will be bold or italic but no meaning will be attached to it.

When we say <strong> or <em> it means there is now meaning attached to the text not just changed visiuals.

All elements we have used so far are semantic such as <h1>, <header>, <nav> etc. So tags which aren't semantic are <div> this just create a box with no meaning.
The <div> tag used to be used for everything such as <nav>, <header>, <footer> etc, it is now recommened we use <div> only when we must and when we cant to create a box without meaning.

If we wanted to, we could build an entire web page from <div> tags and syle them as we would like with CSS. This is not recomened though, it reduces search engine optimisation it also reduces the readability of the website for blind people.
