#Europeana Javascript development guide

See the [general development guide](general.md) for guidance. Here are additional JavaScript-specific guidelines.

##1 Style

* use (2) spaces not tabs
* use semi-colons after statements
* use single-quotes rather than double
* use brackets for single-line functions / conditional statements
* closures preferred to object.prototype for object oriented programming
* use "on" rather than "click" to assign action handlers
* all variables should be declared and listed alphabetically when possible.  Variables should be declared before used in preparation for ECMA6.

##2 Architecture

* we use JS to progressively enhance, never as a core dependency    
* we do not aim to be fully AMD compliant but we do use requirejs for dependency management, and applications using the styleguide should have a single js entrypoint in the styleguide (a "main" file) under "source/js/main"
* global variables are to be avoided where possible.  The globals we do have arise from plugins we use (jquery, the PDF viewer) but we should avoid adding any more.
* we never rely on the user agent string
* we load as little JS up-front as possible - most we load on demand (see /source/js/modules/eu/util/scrollEvents.js)

##3 File System

* All Javascript is saved to /source/js/ within the styleguide
* Compiled Javascript is saved to /source/js/dist
* Source Javascript is saved to /source/js/modules
* 3rd party Javascript is saved to /source/js/modules/lib
* Common functionality developed by Europeana is extracted to utility functions in /source/js/modules/eu/util

##4 Builds

We use grunt to concatenate, copy, package, version and watch the Javascript codebase.  The following functionality is available from the Gruntfile at the root of the styleguide:

* grunt help

        outputs the available commands
* grunt

        default task: concats and copies the source js to the dist folder
* grunt js-component-styles

        compiles the sass bundled with dynamically loaded javascript components.
        Can be used on all components (default) or can target a specific javascript component
        (see the output from "grunt help" for details)
* grunt freeze-version --styleguide-version

        creates a styleguide version based on the supplied parameter


##5 Documentation

Method signatures should have a clarity that negates the need for an explanatory comment - we should avoid this type of thing:

      // returns the page title
      function getPgeTitle(){
         ...
