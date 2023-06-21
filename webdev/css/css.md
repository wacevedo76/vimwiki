--------------------------------------------------------------------------------
General CSS
--------------------------------------------------------------------------------
Commonly used                |
                             |
  Format for external css    | <link rel="stylesheet" type="text/css" href="style.css">
  links                      |       *rel*(ationship)   type            hyper reference
                             |
--------------------------------------------------------------------------------
Most common measurements     |
                             |
  px                         | pixels
                             |
  %                          | percentage
                             |
  em                         | Relative to the font size of the paretn element.
                             | If the parent element has a font size of 14px,
                             | then 1em = 14px
                             |
  rem                        | Relative to the font size of the root elemet
                             | (html element). If the html element is 18px,
                             | then 1rem = 18px
                             |
--------------------------------------------------------------------------------
CSS Combinators              |
                             |
  Desendent Selectors        |
                             |
  *Selector*                   | *Example*      *Example Description*
  element element            | div p        Selects all <p> elements inside <div> elements
                             |
  element > element          | div > p      Selects all <p> elements where the parent is a <div> element
                             |
  element + element          | div + p      Selects the first <p> element that are place immediately after the <div> elements
                             |
  element ~ element          | p ~ ul       Selects every <ul> element that are preceded by a <p> element
                             |
--------------------------------------------------------------------------------
Grouping Elements            |
  .selector1, .selector2     | The defined styles will apply to both selector1 and selector2
                             |
--------------------------------------------------------------------------------
Form Selectors               |
  fieldset                   |
                             |
  fieldset legend            |
                             |
  legend                     |
                             |
  input[type="text"]         |
  input[type="tel"]          |
  input[type="emai"]         |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
                             |

