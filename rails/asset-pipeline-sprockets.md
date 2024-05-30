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