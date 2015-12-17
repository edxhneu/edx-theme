Overview
========
This directory stores a default theme for an Open edX instance.

We've organized the tree to mimic the directory structure of the edX
codebase so that it's easy to tell where the files will end up upon
deploy. We'll use a special settings file to set the template and
staticfiles paths properly to point to these files.

![Alt text](/default_theme_screenshot.jpg?raw=true "Open edX Default Theme Screenshot")

Theme Authoring
===============
To customize your theme:
- Fork this repository.
- Clone it into the theme directory next to your edx-platform directory and rename the theme directory to your new theme's name.
- Upload your own image assets.
- Edit the .scss file in static/sass/ and rename the file with your theme's name.
- Edit the lms.envs.json file in edx-platform and set 'USE_CUSTOM_THEME' to true, and 'THEME_NAME' to your theme's name.

Provisioning method
===============

To enable Stanford theming in a sandbox instance:

1) Add the following lines to /edx/app/edx_ansible/server-vars.yml

```
edxapp_use_custom_theme: true
edxapp_theme_name: 'default_hneu'
edxapp_theme_source_repo: 'https://github.com/edxhneu/edx-theme.git'
edxapp_theme_version: 'HEAD'
```

2) Re-run the provisioning scripts:

```
sudo /edx/bin/update edx-platform master
```
or
```
sudo /edx/bin/update edx-platform named-release/cypress
```

Please note: the stanford theme has some customized code implemented in the latest `edx-platform` and it would only be activated when `edx_theme_name` is set to `stanford`. Also another hack should be applied for successful compiling: `./static/sass/_stanford.scss` should be renamed to `stanford.scss`

License
=======

The code in this repo is licensed under the Apache 2.0 License.
See [LICENSE.txt](LICENSE.txt) for more info.