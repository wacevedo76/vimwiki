--------------------------------------------------------------------------------
= React notes =
--------------------------------------------------------------------------------
  Initialize and new node    | npm init
  project                    |
                             |
  adding dependencies in     | "dependencies": {
  package.json               |   "express": "^4.16.1"
                             | }
                             |
  adding npm start command   | "start": "node server.js"
  (package.json)             |  running: > npm start -- will tringer node to run "server.js"
                             |
  install dependencies via   | npm install express --save
  command line               | npm install express --save-dev
  (automatically adds to     |
    package.json)            |
                             |
  install packages           | npm install
  (defined in package.json)  |
--------------------------------------------------------------------------------
NPM - package.json
available keys
  name                    author
  bin                     browser
  bugs                    bundledDependencies
  config                  contributors
  cpu                     dependencies
  description             devDependencies
  directories             engines
  files                   homepage
  keywords                license
  man                     main
  optionalDependencies    os
  peerDependencies        private
  publishConfig           repository
  scripts

--------------------------------------------------------------------------------
NPM commands:
  Auditng Package Security   | npm audit
                             | npm audit --fix
                             | npm audit --json
                             | npm audit --readable
                             | npm audit --dry-run
                             |
  Deduplication and Pruning  | npm dedup
                             | npm prune
                             |
  Updating Packages          | npm update
                             |
  Publishing / Unpublishing  | npm login
                             | npm publish
                             | npm unpublish [<@scope>/]<package-name>[@<version>]
--------------------------------------------------------------------------------
Node: Standard Moudles
  File System (fs)           | const fs = require("fs");
                             |   The fs mouule provides an API for working with the
                             |   local files system in a pattern tha closely matches
                             |   standard POSIX functions
                             |
    Common fs functions      | fs.copyFile()
                             | fs.copyFileSync()
                             | fs.readFile()
                             | fs.unlink()
                             | fs.mkdir()
                             | fs.stat()
                             | fs.readdir()
                             |
  HTTP and HTTPS             |
                             |
  OS                         | os.EOL - provides you the end-of-line character the OS uses
                             | os.cpus() - Returns an object array where each object give
                             |   you information about the CPU(s) in the system (model, sped
                             | os.freemem() - returns an int value which represents free system memory
                             | os.homedir() returns path to the current home dir of the user running process
                             | os.hostname()
                             | os.tempdir()
                             |
  Path                       | path.basename()
                             | path.dirname()
                             | path.extname() - file extension
                             |
  Process (global)           |
                             |
  Query Strings (querysting) |
                             |
  URL                        |
                             |
                             |
                             |
                             |
--------------------------------------------------------------------------------
create-react-app basic file structure
  src                        | The dir where all written source code is put
                             |
  public                     | The dir where all static files are placed
                             |
  node_modules               | The dir that contains the project dependencies
                             |
  package.json               | Records of project dependencies and configures the project
                             |
  package-lock.json or       | Records the exact version of the packages that we installed
  yarn.lock                  |
--------------------------------------------------------------------------------
Import statements
  anatomy of the import      | import <variable> from <name of the file>
                             | import React from 'react';
                             | import ReactDOM from 'react-dom';
                             |
                             | (the variable can be named anything, but conventions
                             |  are usually followed)
--------------------------------------------------------------------------------
Components
  A component is a           | function or a class that produces html to show users (using jsx)
                             | and handles feedback from the user (using event handlers)
  JSX inline styles
                             | `<div style={{ backgroundColor: 'red', color: 'white' }}></div>`
                             | the two curly braces represents:
                             |   * the outer curly braces is a reference to a JavaScript variable with JSX
                             |   * the inner curly braces is a frefrence ot a JavaScript object
                             | for css properties that contain a hyphen, remove
                             |   the hypen and capitalize the next word
                             | the value for the css property is wrapped in
                             |   single-quotes
                             | CSS Property definitions are separated with a comma
                             | not a semi-colon
 Giving tags a class
                             | <lable for="name" className="label">enter e-mail</lable>
                             | "Class" is a keyword in JSX, therefore, to give a tag a
                             | class, give it the "className" attribute
 Referencing variables in jsx
                             | { predefinedVariable }
--------------------------------------------------------------------------------
Tenents of React
  Component Nesting          | A component can be shown inside another component
                             |
  Component Reusability      | We want to make components resued throughout the application
                             |
  Component Configuration    | We should be configuring components when they are created
--------------------------------------------------------------------------------
Creating Resusable Components
  * Identify the JSX that appears to be duplicated
  * Think of a descriptive name for the resuable component
  - Create a new file for the resuable component
  - Create a new component in the new file
  - Make the new component configurable by using the 'props' system
--------------------------------------------------------------------------------
Props
  - Props is a system for passing data from a parent component to a child component
  - Its purpose is to customize or configure a child component
--------------------------------------------------------------------------------
Timeline of application inside the browser
  JS file loaded up by browser
  App components gets created
  We call geolocation service
  App gets rendered to page as HTML
    We get result of geolocation!
    - Since the geolocation results take some time to complete (asyncronis)
      a class based component must be used.
--------------------------------------------------------------------------------
Rules of Class Based Components
  - When defining a costructor, you must pass 'props' in the constructor
    definition statesment, and pass 'props' in super, -> constructor(props) { super(props)
  - Must be a Javascript Class
  - Must extend React.Component
  - Must define a 'render' method
--------------------------------------------------------------------------------
State Rules
  - Only usable with class components
  - 'State' is a JS object that contain data relevant to a component
  - Updating state on a component causes the component to re-render
  - State must be initialized when a component is created
  - Stat can only be updated using the function 'setState'
--------------------------------------------------------------------------------
Lifecycle methods
  constructor                | Good place to one time setup
  render                     | Just return JSX
  componentDidMount          | Gets called when component is rendered for the first time - just place to data loading
  componentDidUpdate         | Gets called when component state changes - Good place to do more data loading when state/props change
  componentWillUmount        | Good place to do clean up
  ( rarely used )            |
  shouldComponentUpdate      |
  getDerivedStateFromProps   |
  getSnapshotBeforeUpdate    |
                             |
                             |
                             |
                             |
                             |
                             |
                             |
