## Setting up a dev environment

### Requirements:

* Docker
* DDEV

### Steps

* Clone this repository
* cd into it and run `ddev start`
* Run `ddev composer install`
* Run `ddev pb-reinstall-site` to trigger the site installation and installing all the required modules

If you want to do development at the template level, you're done.

If you want to do development in the freeform, prussianblue_builder or other repo in the prussianblue-cms repository:

* cd into the directory where composer deployed the repo. For example `web/modules/contrib/prussianblue_builder`
* Edit .git/config and switch the HTTPS repo path to SSH
* Checkout the main branch (or the branch you need to work on)

That's it. You can now edit code in that repository, commit it and push it. If you want to try a standard install, simply remove the directory (make sure you're not losing work) and run `composer install` at the root level again.
