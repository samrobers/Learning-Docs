# JSDOC Cheat Sheet

**LINK TO JSDOC - https://jsdoc.app/**

**LINK TO OTHER RESOURCES - https://devhints.io/jsdoc**

## `Start Here`

- State the file
- State the module/directory of the file
- state the required/imported modules
- state the author of the file

**`Example`**

```
/**
 *@file App.js, Manages the main API routes
 *@module src/app.js
 *@requires express
 *@author DabbleLab
 */
```

**`Giving a specific name to a function or comment different from its current value**`

```
/** description - the description must come before the name for the name tag to work
 * @name thisIsTheName - The name must come after the description
 * @function myFunction
 * the above is the same as:
 * @function
 * @name myFunction
 */
```

**example**

- if you have a function with a non descriptive name and need to give it more context, use the name tag to change this. To be able to see what different parts need the name tag generate the md file to get a preview.

```
/** Run this command in the terminal to install the needed dependencies and to be able to test the * output of your documentation. The root directory in the package json might need to be changed to * the directory of your current working doc for the command to work.

run npx documentation build -f md -o ~/docs.md

```

- **The @file tag provides a description for a file. Use the tag in a JSDoc comment at the beginning of the file.**

` Note, could find a way to get rid of the meta heading generated with the author tag`

- synonyms @fileoverview
  @overview

## `Documenting vars`

```
example:
/**
 * express module instance
 * @const
 */
const app = express();
```

## `Imports from Project files`

- https://jsdoc.app/howto-commonjs-modules.html
- https://jsdoc.app/howto-amd-modules.html

- A module. Its name is module:foo/bar.

- @module foo/bar
  The built in string object. Its name is external:String.
- @external String
  An event. Its name is module:foo/bar.event:MyEvent.
- @event module:foo/bar.event:MyEvent

## `Documenting Examples/Tutorials`

- Including Tutorial @tutorial block tag

  - will link to a tutorial specified
    - example: @tutorial socket-tutorial
  - inline tag is { @tutorial socket-tutorial}

## `Tags to describe the code`

- Instance is a new instance of a function, such as a new constructor
- inner is just the local scope of a function inside a function
- static is just a function by itself
- Person#say // the instance method named "say."
- Person.say // the static method named "say."
- Person~say // the inner method named "say."

## `Documentation for Functions`

```
/**
 * @function myFunction
 * the above is the same as:
 * @function
 * @name myFunction
 */
```

## Quick Options for everything else

```
/**
 * @kind <kindName>
 */
```

**`where <kindName> is one of:`**

```
class
constant
event
external
file
function
member
mixin
module
namespace
typedef
```

**`Extra Information`**

- run

```
 npx documentation build -f md -o ./{choose a md file name}
 Example:
 npx documentation build -f md -o ./docs.md
```

- this will generate a docs.md file from the jsdocs read from the root directory within the package.json to test the end result

Extra tips

- installing the JSDoc Generator by kimlimjustin was helpful in generating a template above each function needed. The gif on the extension shows how to use it.
