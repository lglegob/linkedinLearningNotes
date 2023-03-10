# Simplifying Web Development with Accessibility Best Practices

- Morten Rand-Hendrickson

---

## Back to the Basics

- Complexity Obscures Simplicity

  - Many ways of doing things makes things confusing

- Accessibility is the core promise of the web

- Don’t use divs as buttons

![A button that isn’t a button](./2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Chapter01/CH01-Capture01.png)

- use a button instead

![The button](./2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Chapter01/CH01-Capture02.png)

- Many of our habits, examples, and best practices rely on building custom solutions to problems the web platform has already solved with standard-based elements
- When something is not accesible on the web, it is because something has gone wrong in its development. Accessibility problems are designed and built in by us.
- Accessibility is the Job.
- What causes accessibility problems?

  - Lack of awareness
    - Accessibility was long considered an optional feature
    - Historical lack of available education and best practice examples
    - accessibility awareness and education is improving
  - Problems introduced through iteration.

- Accessibility Mindset
  - What is the functionality of the thing I’m trying to build
  - What existing elements serve this functionality

## Accessible Design

### Accessible Color palette

- Designing an accesible color palette for your project centers on two core principles

  - Color Contrast

    - WCAG recommendations
      - background to text color contrast ratios:
        - Small Text (23px or less): 4.5
        - Small bold text (17px or less): 4.5
        - Large text (24px or more): 3
    - [webaim](https://webaim.org) to check contrast
    - [Create accessible palette](https://color.adobe.com)

  - Color Blindness
    - 8% of male global population is red-green color blind
    - don’t rely on color difference only when indicating state

### Accessible typography

- What does it mean? Presenting text that has:

  - Enough contrast to the background
  - It is big enough to read
  - It is using a font that is easily readable.

- Accessible Typography Principles
  - Larger font sizes (Within reason) are preferred.
    - Default size of 16px is OK
    - 18ox or 20ox is better
  - avoid complex fonts for anything but decoration
    - handwriting and decorative fonts look good, but are difficult to read
  - avoid “fancy” fonts with unusual features
    - stylish ligaments are difficult to read
  - keep max sentence length between 70 and 80 characters
    - max-width: 70ch;

---

### Designing accessible content hierarchies and flows

- Websites are communication tools
- Websites often display a lot of information.
- our design should accommodate to visualization patterns (example of the typical patters of people reading from left to right)

![Typical visualization pattern](./2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Chapter02/CH02-Capture01.png)

- Scanning Patters

  - Stop at headings and other “breaking” elements.
  - Scan past blocks of text.
  - Note heading hierarchies.
  - Sidebar blindness.

- People tend to ignore what is in the right sidebar (Usually ads are located that way)
- HTML is built for hierarchical content.

---

## 3. Hiding and Showing

### Is hiding or showing content a good idea?

- Web is a visual medium, that’s why we have Web Design

  - Part of this sometimes includes hiding text content from the visual browser

- Ideal scenario

  - Visual browser shows only buttons
  - Screen reader reads out hidden text
  - Search Engines index hidden text and links

- Social Media Links Accessibility
  - make the social media menu a List
  - Add the social media icons and accompanying text
  - And then use CSS, to hide the text from the Visual Browser

![Social Media Configuration](./2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Chapter03/CH03-Capture01.png)

- Separation between text and Links
  - Add a hidden heading inside the Navigation telling the user they are switching context

![Links Separation](./2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Chapter03/CH03-Capture02.png)

### How to hide visual content

- Content hidden from the visual browser without being hidden from screen readers.
- Screen readers read out what’s visible on the screen. If something is set to display: none; or otherwise hidden, screen reader will not read this content.
- Setting opacity to zero doesn’t work, the elements is still taking space, and if you set the height and width to zero, probably the screen reader will not read it as well
- With the following code, the elements stills exists but it is effectively hidden from the screen and still readable by screen readers.

![Links Separation](./2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Chapter03/CH03-Capture03.png)

### How to hide content from screen readers

- In cases where visually makes sense to have two links to the same address (like title and button of a card), but it doesn’t makes sense to leave two links for screen readers.
- The aíra-hidden=“true’ attribute hides it and any child elements.

![Double Link Example](./2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Chapter03/CH03-Capture04.png)

—--

## 4. Semantics and Interactivity

### The role of semantic elements

- With HTML5, now we have highly semantic elements.
  - HTML semantic elements help describe different types of content.
  - Semantic elements have implicit roles describing their role in the document.

![Roles and Landmarks](./2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Chapter03/CH03-Capture05.png)

- These roles and landmarks also improve the SEO

### Elements with purpose

- <nav> is for navigation
- <table> is for tables
- <form> is for forms
- <ul> and <lo> are for unordered and ordered lists
- <select> is for selecting things
- <input> is for input elements like check box, date picker, color selector, a password, or range selector.
- <button>
- <link>

- For almost any type of data or interaction, there is a dedicated HTML element.
- That includes not-so-commonly used features like sliding range selectors, and so on.
- Modern browsers have built-in date pickers
- First identify the purpose of the thing you are developing and see if there is an existing HTML element that already serves that purpose.
  - What is the functionality of the thing I’m trying to build?
  - What existing elements serve this functionality?

### Links and button basics

- Both links and buttons have various states with corresponding CSS pseudo classes.

  - :hover
    - The user hovers a pointing device (usually a mouse) over the item
  - :active
    - The item is activated by the user clicking or selecting it
  - :focus
    - The element currently has focus (is selected)
  - :ficus-visible
    - The element has focus and should be visibly focused

- Links have some exclusive pseudo classes

  - :link
    - The link target has not yet been visited
  - :visited
    - The link target has been visited
  - :local-link
    - The absolute URL of the current page and link target match

- We often choose between a link and a button based on their looks
- We should choose based on their function (We can be using the wrong tool for the wrong job)
- How do we decide if it should be a link or a button?
  - Is it a Navigation link taking the visitor to a new location in the document or a new document? --> LINK
  - Is it an interactive element triggering some form of behaviour in the existing context like opening a modal, or closing a modal, or sending a form, or toggling a menu or something similar that doesnt involve navigation? --> BUTTON

### Links

- in its most basic configuration a link is an anchor tag with an href attribute containing the target URL
- We can expand its functionality using URL schemes:

  - Phone capabilities

  ```html
  <a href="“tel:+15558675309”">Call our Store</a>
  ```

  - mail to capabilities

  ```html
  <a href="“mailto:store@example.com”">Mail us</a>
  ```

  - download capabilities

  ```html
  <a href=“/cheese-menu.pdf” download>See our Menu</a>
  ```

- Anytime you have a link, the screen reader will try to read out everything that sits inside the link.

### Buttons

- it doesn’t have default behavior
- Button behavior is added by hooking them to browser events or using JavaScript
- Links are often used in place of buttons (wrong)
- The following code removes all default styling of a button except for the focus state

  ```css
  button {
    font-family: inherit;
    font-size: 100%;
    line-height: 1.15;
    margin: 0;
    overflow: visible;
    text-transform: none;
    -webkit-appearance: button;
    border: 0;
    background: none;
  }

  button:hover {
    /* Mouse behavior like link */
    cursor: pointer;
  }

  button:hover,
  button:focus,
  button:active {
    background: none;
    border-color: inherit;
    border-radius: 0;
  }
  ```

- Best practice
  - Create global styles for all buttons to match design
  - Use classes to apply custom styles where necessary
  - Modify and build on default styling rather than full reset

### Screen reader-friendly links and buttons

- Examples of when hide content from visual browsers and provide more context for screen readers

![Examples to hide](./2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Chapter04/CH04-Capture02.png)

- Read more links
- Close modal buttons
- Next and previous buttons
- Blocks of texts with links inside

![read more links effect in screen readers](./2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Chapter04/CH04-Capture03.png)

- To fix it, add hidden text

![Screen Reader-Only CSS rule](./2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Chapter04/CH04-Capture04.png)

![Screen Reader-Only example](./2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Chapter04/CH04-Capture05.png)

### Icon links and buttons with SVG

- when we want to display a link or a button using an icon with or without accompanying text
- Use SVGs for icons. They can be made accesible, and they don’t interfere with assistive technologies the way icon fonts do.

![Example for all escenarios](./2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Chapter04/CH04-Capture06.png)

—--

## 5. Images, graphics and media

## images, graphics and media basics

- two categories

  - Static Assets (images and graphics)
  - Dynamic Assets (Video and Audio)

- Static Assets

  - information
  - link/button
  - decoration

  - defining the purpose of the assets becomes important when choosing how to markup

- Dynamic Assets

  - information
  - decoration (not recommended)

- video and audio are not always accesible
- they require alternative methods for communicating the information within (plain text transcripts)

- advantages for video and audio transcripts
  - make information accesible to anyone through text
  - make information searchable, copyable, and auto-translatable
  - make information indexable for search engines

### the img element

- inline replaced element
- two required attributes
  - src
  - alt
- optional attributes

  - width
  - height
  - loading
  - sizes
  - srcset

- <img> global CSS reset

  ```css
  /* Standard */
  img {
    display: block;
    width: 100%;
    height: auto;
  }

  /* Modern CSS Remedy */
  img {
    display: block;
    vertical-align: middle;
    max-width: 100%;
    height: auto;
  }
  ```

- Don’t use title attribute (pointless information)

- [alt decisión tree from w3c](https://www.w3.org/WAI/tutorials/images/decision-tree/)

- the role of the image can be changed with ARIA roles

### The figure and figcaption elements

- one or more images that include a caption
- <figure> element wraps around one or moire image elements that can contain an optional figcaption element

![figure element with figcaption](./2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Chapter05/CH05-Capture01.png)

- When wrapping an image in a container, use a figure (That's what it's for)
- the only styling a figure introduces is margin, you can easily reset it with:

  ```css
  figure {
    margin: 0;
  }
  ```

### Accesible SVG

- Can be displayed as regular <img>
- Can be incorporated in HTML document
- Can be defined once and used many times
- Can be styled using CSS
- Can be made accessible
- Because an SVG is a standalone web document, which can be embeded into an HTML document, the SVG can contain its own title and description elements.

![Accessible <svg> Example](./2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Chapter05/CH05-Capture02.png)

[Creating Accessible SVGs](https://www.deque.com/blog/creating-accessible-svgs/)

### Making embedded videos more accessible

- Embedding comes with some tricky problems for performance, usability and accessibility
- The embed loads even if the visitor never interacts with it
- The embed slows down rendering of the page
- the embed frame I frame can create a keyboard navigation trap where the user can’t escape the embed to get back to the current page
- SOLUTION:

  - load the embed only when the user interacts with it
  - inside the iframe, loads an image with a button on top of it, then if when that button is clicked, the embedded content is loaded
  - thanks to sir doc attribute
  - We are loading just a picture, not the video

  ```html
  <iframe
    width=“720”
    height=“540”
    src=“https://www.youtube.com/embed/Buw4vOXcr_4”
    srcdoc=“
      <style>*{padding:0;margin:0;overflow:hidden}html,body{height:100%}img,span{position:absolute;width:100%;top:0;bottom:0;margin:auto}span{height:1.5em;text-align:center;font:48px/1.5 sans-serif;color:white;text-shadow:0 0 0.5em black}</style>
      <a href=https://www.youtube.com/embed/Buw4vOXcr_4?autoplay=1>
        <img
          src=https://img.youtube.com/vi/Buw4vOXcr_4/hqdefault.jpg
          alt=‘Video: Variable Fonts Explained’>
        <span>&#x25BA;</span>
      </a>”
    frameborder=“0”
    allow=“accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture”
    allowfullscreen
    title=“Variable Fonts Explained”
    loading=“lazy”
  ></iframe>
  ```

### Adding transcripts

- If a Web Page contains an audio or video file with information, it should contain a full transcript
- Transcripts make information:

  - accessible to anyone through text
  - searchable, copyable, and auto-translatable
  - indexable for search engines

- Two options to show transcript
  - Scrolling
  - expand button (JavaScript)

---

## Practical Examples

- For these examples, check the Screen Reader chrome extension

### Mobile-Friendly navigation menu

- Example combining html, css and js for a friendly navigation menu

[html code](/2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Ex_Files_Simplifying_Web_Development/06_01/index.html)
[css code](/2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices//Ex_Files_Simplifying_Web_Development/06_01/style.css)
[js code](/2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices//Ex_Files_Simplifying_Web_Development/06_01/script.js)

### Multilevel navigation menu

- really straightforward example with a fully accessible dropdown menu using links for links and buttons for buttons, and this work across mouse users, touch screen users, keyboard users, visual users, and screen reader users

[html code](/2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices//Ex_Files_Simplifying_Web_Development/06_02/index.html)
[css code](/2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices//Ex_Files_Simplifying_Web_Development/06_02/style.css)
[js code](/2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices//Ex_Files_Simplifying_Web_Development/06_02/script.js)

### Basic Card

- When we try to make cards that do perfect things for everyone, we will run into issues, where we have to trade a solution for one group for another group
- In the case of the example, is trading to have the whole card clickable, instead of being able to highlight the inside text.
- the key component is the CSS with the “after” configuration where the anchor element is extended.

[html code](/2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Ex_Files_Simplifying_Web_Development/06_03/index.html)
[css code](/2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Ex_Files_Simplifying_Web_Development/06_03/style.css)

### Card with internal links

- What about cards with multiple links, or buttons or other interactive elements

[html code](/2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Ex_Files_Simplifying_Web_Development/06_04/index.html)
[css code](/2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Ex_Files_Simplifying_Web_Development/06_04/style.css)

### Date Picker

- used to be difficult to be accessible
- the input type date field, hooks into whatever dates picker feature is built into the browser and those date picker features have now been migrated into desktop browsers as well
- JavaScript code is just adjusting the format of year, month and day

[html code](/2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Ex_Files_Simplifying_Web_Development/06_05/index.html)
[css code](/2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Ex_Files_Simplifying_Web_Development/06_05/style.css)
[js code](/2023-01-26-SimplifyingWebDevelopmentWithAccessibilityBestPractices/Ex_Files_Simplifying_Web_Development/06_05/script.js)

## Proof and Pudding

### Simplifiying Web Development with Accessibility Best practices

- Accessibility Mindtset

  - What is the functionality of the thing I'm trying to build?
  - What existing elements serve this functionality?

- Component-based JavaScript front-endframeworks encourage us to build custom components to do what existing elements already do.
- It's always a good idea, to check if the Web Platform, already gives what you need out of the box, and all you need to do is style it or add backwards compatibility.

- Three key questions
  - Is there an existing element that does what I need?
  - Can I extend an existing element to do what I need?
  - Can I use existing elements as part of my component?

### Where to find more information

- [MDN Web Docs HTML Elements reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)
- [A list apart](https://alistapart.com/)
- [smashing magazine](https://www.smashingmagazine.com/)
- [CSS Tricks](https://css-tricks.com/)

### Tools for manually testing sites

- Accessibiliy testing is central to successful web development, but it is not something we do naturally.
  - get used to navigate ypour creations using your keyboard only
  - screen reader
  - Accesibility tools (Browsers)

### Lighthouse score and similar

- Use lighthouse accessibility test
