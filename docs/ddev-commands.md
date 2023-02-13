# DDEV Commands
These commands help perform actions, save typing and aid developer memory.

* **Site Builder** commands are useful to someone working on a website built with PrussianBlue. They are prefixed with `pb-`.
* **Developer** commands are useful to someone working on PrussianBlue. These are prefixed wth `pb-dev-`.

## Site Builder Utilities

## pb-uli
Same as running `ddev drush uli | pbcopy`

### pb-site-reinstall
Wipes the database and does a fresh install of the site via `drush site-reinstall`. Does not touch dependencies or code in any way. Does not install prussianblue_builder or its submodules.

### pb-paragraphs-connect
An alias of the Drush command pb-paragraphs-connect. Enables the paragraph types in content type fields. This command depends on the content type builder modules being enabled, since they implement the hook needed to decide what paragraph ids they allow in their fields.

## PrussianBlue Developer Commands

### pb-dev-enable-dev-modules
Enables the modules:

- pb_devel_generate
- mix (disable caches for development)

### pb-dev-config-update-module [module path]
Patches the configuration of the given module to match that of the config/sync directory.
Argument: module path, relative to the project root.

Use example: `ddev pb-config-update-module web/modules/contrib/prussianblue_builder`

**REVIEW CAREFULLY**. This command is of great help, but it's not magic. You still need to review the changes performed on the configuration files, make sure they are what you need and prevent introducing problematic changes.

### pb-dev-config-refresh-reference
Exports the default configuration provided by the current site code, including the PB contrib modules, so it can be used as reference for patching. Note that if there are uncommitted changes to the module being updated, the changes present will still affect the reference configuration generated. If you want the reference to be based on the latest committed config, stash your changes before running this command.

The end result:

- config/sync will contain the current configuration of the site and won't be changed
- config/reference will contain the reference configuration
- The configuration files are prepared to run pb-config-module-update
