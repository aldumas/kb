# Key points of interest

## manifest.js

This file determines which files to output into the public/assets directory. You can specify files, directories, or whole trees (while limiting to file type).

You use directives to specify the files.

## manifest files

These are files which will be used to build the output files. They can be regular css and js files, but can contain special comments which include other files.

## Rails.application.config.assets.path

This is an array of paths to search for assets. It is used for a couple of things:

1. To resolve files used in @import or //= require directives.
2. To resolve files referenced by helpers, e.g. `<%= stylesheet_link_tag 'application' %>`.

Note that `link_tree` and `link_directory` use paths relative to the `manifest.js` file, whereas `link` requires a logical path (relative to one of the entries in `Rails.application.config.assets.path`)

# Types of requires

From the [Sprockets](https://github.com/rails/sprockets) README:

The directive processor understands comment blocks in three formats:

```css
/* Multi-line comment blocks (CSS, SCSS, JavaScript)
 *= require foo
 */
```

```javascript
// Single-line comment blocks (SCSS, JavaScript)
//= require foo
```

```coffeescript
# Single-line comment blocks (CoffeeScript)
#= require foo
```

For me, the CSS require didn't work, though I am using dartsass, so maybe that was part of the issue. Instead, I used @import or @use and the content of the file was added (instead of just putting the @import in the output).