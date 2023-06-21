--------------------------------------------------------------------------------
== HTML Notes ==
--------------------------------------------------------------------------------
HTML5 inputs types           | The following input types will not work on older
                             | browsers and do not function the same across all
                             | browsers
                             |
  label for                  | What lable for does is allow you to associate
                             | preceding contextual inputs  for a specific label
                             | Example:
                             |   <label for='fname'>Click this label</label>  <-- indicates that this label is
                             |   <input type='text' id='fname'>                   for the input with the "id"
                             |                                                    fname
                             |
  Search                     | Aside from the semantic aspect of the search
                             | input, when typing something into the input field
                             | an "x" will apear on the right side of the input
                             | field allowing you to quickly delete entered text
                             |
  email                      | With regards to HTML, the email input type only
                             | provides semantic benefits, but can be used with
                             | with other programming languages to parse and
                             | check the entered value and some browsers will
                             | perform validation
                             |
  url                        | Provides semantic benefits as well as some
                             | browsers providing validation
                             |
  number                     | The number type allows you to force a "min", "max"
                             | and "step" number attribute as well as double
                             | arrows on the right side of the input field which
                             | allows incrementing and decrementing an entered
                             | value, as well as validation
                             |
  range                      | The range input creates a "slider", "min" and
                             | "max" number range is required
                             |
  date                       | The date input provides an input that provides
                             | a premade input for specific dats "min" and "max"
                             | attributes are also available
                             |
  month                      | Similar to the date input type
                             |
  week                       | Similar to the date input type
                             |
  time                       | Similar to the date input type
                             |
  datetime                   | Similar to the date input type
                             |
  datetime-local             | Similar to the date input type
                             |
  color                      | Provides a color picker
                             |
--------------------------------------------------------------------------------
Custom Data attributes       | Custom data attribures can be used to identify
                             | elements in order to interacte with them
                             | programmatically
                             |
                             | Simply prefix your custom attribute with "data-"
                             | Example:
                             |   <article class="something" *data-account="Chequing"* *data-max="9999"*>
