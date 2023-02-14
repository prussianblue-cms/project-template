# PrussianBlue CLI
These commands help perform actions, save typing and aid developer memory.

Commands are defined in two different ways:
- As DDEV commands, found in .ddev/commands/host/
- As Drush commands provided by submodules of prussianblue_builder

## DDEV Site Builder Utilities
These are useful to someone working on a website built with PrussianBlue. They are prefixed with `pb-`.

### pb-uli
Same as running `ddev drush uli | pbcopy`

### pb-site-reinstall
Wipes the database and does a fresh install of the site via `drush site-reinstall`. Does not touch dependencies or code in any way. Does not install prussianblue_builder or its submodules.

## Drush Site Builder Utilities
Drush commands help site builders interact with content and configuration in a Drupal instance. They are prefixed with `pb:` and can be found by running `ddev drush | grep pb:`.

### pb:populate-menus
Creates dummy elements in the main and secondary-navigation menus.

### pb:paragraphs-connect
Enables the paragraph types in the fields that allow them in nodes. The command and the paragraph discovery API are defined in the `pb_paragraphs_connector` module.

## DDEV PrussianBlue Developer Commands
These are useful to someone working on the PrussianBlue software. They are prefixed wth `pb-dev-`.

### pb-dev-site-reinstall
Runs:
- pb-site-reinstall
- pb-dev-enable-dev-modules
- pb-dev-starterkit
- pb-uli

### pb-dev-enable-dev-modules
Enables the modules:

- pb_devel_generate
- mix (disable caches for development)

### pb-dev-starterkit
Enables the starterkit theme and sets it as default.

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
