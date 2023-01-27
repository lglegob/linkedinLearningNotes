# Simplifying Web Development with Accessibility Best Practices

- Morten Rand-Hendrickson

## Back to the Basics

- Complexity Obscures Simplicity
  - Many way of doing things makes things confusing
 
 
- Accessibility is the core promise of the web
 
- Don’t use divs as buttons

![A button that isn’t a button](./Chapter01/CH01-Capture01.png)

- use a button instead

![The button](./Chapter01/CH01-Capture02.png)

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
   