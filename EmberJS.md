--------------------------------------------------------------------------------
= Ember JS Notes =
--------------------------------------------------------------------------------
  Generate ember project     | ember init -> creates emberjs files structure in current dir.
                             |
                             | ember new nameofnewproject --lang en
                             |
--------------------------------------------------------------------------------
  jsconfig.json              | used to indicate the current workspace
                             | and has useful features for the the Javascrip LSP
                             | for example:
                             |
                             | "compilerOptions": {
                             |   "target": "es2015",
                             |   "experimentalDecorators": true
                             | },
                             | "exclude": {
                             |   "node_modules",
                             |   "dist"
                             |
--------------------------------------------------------------------------------
Important Files              |
  app/templ../application.hbs|  Entrypoint into the application - it is imported into
                             |  app/index.html which hold header, footer and site
                             |  wide meta-data (site wide dependencies like bootstrap
                             |  / font-awesome
                             |
--------------------------------------------------------------------------------
Ember addons                 | ember install ember-cli-sass
                             | add support for addons in /ember-cli-buid.js
--------------------------------------------------------------------------------
Routing system               |
  Add a basic route          | ember g route clothes
--------------------------------------------------------------------------------
Testing                      |
  GENERATORS                 |
  Generating Acceptance test | ember generate acceptance-test super-rentals
                             | (file location: tests/acceptance)
                             |
  Generating Component test  | ember generate component-test jumbo
                             | (file location: tests/integration/componets)
                             |
  HELPERS                    |  -> imported from @ember/test-helpers
                             | import { click, visit, currentURL } from '@ember/test-helpers';
  test current url           |  currentURL
  visit links (LinkTo)       |  visit -> await visit('/testRoute')
  test clickables            |  click -> await click('.firstClass a.nestedElementClass') -> similar to css
  render compoenents         |  render -> await render(hbs`<Jumbo>Hello World</Jumbo>`); -> hbs (with backticks)
                             |
  Test (test case function)  | the test() -- Assumtion test is for a searies
                             |               of test cases.
                             | The test() function takes two arguments
                             | a string that represents the title/name for
                             | the test case series and an async call back
                             | function for the asertions
                             |
  ASSERTIONS                 |
  assert.strictEqual         | takes two arguments, retures boolean (AND)
  assert.dom()               | checks DOM elements -> asser.dom('h2').hasText('text for test case')
  assert.dom().hasText()     |
  assert.dom().exists()      |
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
                             |
                             |
                             |
                             |
                             |
