# PrussianBlue Developer Recipes
This file aims to provide "recipes" that can be followed by devs to achieve the same results. Recipes here is not related to Drupal Recipes or any particular code piece; they are just series of steps you can read and follow.

These recipes are useful for someone working on the PrussianBlue distribution — not in a particular site instance.

## Add or update fields to entity types

**Start with a clean state**

- Do `pb-site-reinstall`
- Export configuration `drush cex`
- Refresh the reference configuration `pb-dev-config-refresh-reference`

**Do the changes you need, using the Drupal UI**
For example, add a field to a paragraph type.

**When done, export configuration again**
Once you export the configuration, you'll have the conditions to diff the changes and add the differences to your module.

**Copy and clean new configurations**
Configuration yamls for new fields will not exist yet in the target module and won't be copied by `pb-dev-config-update-module` since that command works on existing files.

So, copy the files reported as _Created_ by `drush cex` to the target module, and remove the UUID from them.

**Patch the module configuration**
Now execute `pb-dev-config-update-module` to apply the configuration changes to the target module.

For example:
`ddev pb-dev-config-update-module web/modules/contrib/prussianblue_builder/modules/pb_base_paragraphs/`

**Do a site reinstall and test**
The code is in your module, so if you execute `ddev pb-site-reinstall` it should have the new or changed fields.

**All good? Commit to your module and move on.**