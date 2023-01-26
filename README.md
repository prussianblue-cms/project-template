# About this repo

It's a template to get started with PrussianBlue using the `composer create-project` command. This template is based on the 10.0.x branch of drupal/recommended-project.

In addition to what the drupal/recommended-project offers, this template includes:

* PrussianBlue module (dev and runtime) and theme dependencies
* Composer patches support
* DDEV configuration
* DDEV commands to help developers create new sites based on the template

## About PrussianBlue
PrussianBlue is not exactly a Drupal distribution but it aims to provide similar benefits. It's a set of tools that helps developers create sites quickly and keep code organized and easy to work with.

It's composed of several tools, each of them with a specific role:

* This template, explained above.
* [The developer module](https://github.com/prussianblue-cms/prussianblue-dev-module). Role: provide configuration for editor tools, fields, paragraph and content types, and any other PrussianBlue configurations. Provide commands for developers to ease configuration and site building (ie: configure SearchAPI, enable paragraph types in fields).
* [The theme](https://github.com/prussianblue-cms/prussianblue-theme). Role: preprocess fields, paragraphs, layouts and content types. Render the site.
* [Testbed](https://github.com/prussianblue-cms/testbed). Role: allow automated testing of the process of instancing a PB website.
* [Freeform module](https://github.com/prussianblue-cms/freeform). A Drupal module to make it easier for front-end developers and content editors to collaborate.