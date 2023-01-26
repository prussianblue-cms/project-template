# Patching Drupal
The composer template includes support for patching via [cweagans/composer-patches](https://github.com/cweagans/composer-patches).

composer.json is configured so Composer will expect to find the patches file in `patches/composer.patches.json`. The file exists and contains the patches needed by PrussianBlue (if any).