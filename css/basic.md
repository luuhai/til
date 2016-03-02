Basic syntax
============

* Leading (pronounced ledding) is a term typographers use for the vertical space between lines of text.
* Kerning is the term typographers use for the space between each letter.
* When pseudo-classes are used, they should appear in this order: :link, :visited, :hover, :focus, :active.
* p[class]
Targets any <p> element with an attribute called class
* p[class="dog"]
Targets any <p> element with an attribute called class whose value is dog
* p[class~="dog"]
Targets any <p> element with an attribute called class whose value is a list of space-separated words, one of which is dog
* p[attr^"d"]
Targets any <p> element with an attribute whose value begins with the letter "d"
* p[attr\*"do"]
Targets any <p> element with an attribute whose value contains the letters "do"
* p[attr$"g"]
Targets any <p> element with an nattribute whose value ends with the letter "g"
* Normal flow
Every block-level element appears on a new line, causing each item to appear lower down the page than the previous one. Even if you specify the width of the boxes and there is space for two elements to sit side-byside, they will not appear next to each other. This is the default behavior (unless you tell the browser to do something else).
* Relative Positioning
This moves an element from the position it would be in normal flow, shifting it to the top, right, bottom, or left of where it would have been placed. This does not affect the position of surrounding elements; they stay in the position they would be in in normal flow.
* Absolute positioning
This positions the element in relation to its containing element. It is taken out of normal flow, meaning that it does not affect the position of any surrounding elements (as they simply ignore the space it would have taken up). Absolutely positioned elements move as users scroll up and down the page.
* Fixed Positioning
This is a form of absolute positioning that positions the element in relation to the browser window, as opposed to the containing element. Elements with fixed positioning do not affect the position of surrounding elements and they do not move when the user scrolls up or down the page.
* Floating Elements
Floating an element allows you to take that element out of normal flow and position it to the far left or right of a containing box. The floated element becomes a block-level element around which other content can flow.
