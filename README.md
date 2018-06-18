# Moodle Plugin Template

[![License](https://img.shields.io/badge/License-GPL--3.0-blue.svg)](https://www.gnu.org/licenses/gpl-3.0.en.html)

## Autofix of all linter Errors

1. Install [Composer](https://getcomposer.org/doc/00-intro.md)
1. `$ composer install --no-dev`
1. `$ composer autofix`

## Moodle Instances

Currently, there is only one generell Moodle instance for this project:
[https://moodle.ganymed.me](https://moodle.ganymed.me)

I am currently working on providing both processes with their own development instance of Moodle, each with their own database to prevent any complications. 
When these instances are available, I will link to them here as well as inform everybody through Slack. Keep in mind that each new instance does not contain data that you entered in the database on the generell instance.

## Official Moodle Docs With Additional Comments

The following steps should get you up and running with this module template code.

For the sake of this tutorial, it is assumed that you have a shell (or cmd on Windows) in the directory of this cloned repository. In all following command lines, it is assumed that you are not in any subdirectory. If `/` is used leading a path, it is assumed that this means the directory of this cloned repository and not your systems root directory. 

* DO NOT PANIC!

* Clone the repository and read this file

* Rename the newmodule/ folder to the name of your module (eg "widget").
  The module folder MUST be lower case and can't contain underscores. You should check the [CVS contrib](http://cvs.moodle.org/contrib/plugins/mod/) to make sure that
  your name is not already used by an other module. Registering the plugin
  name @ [http://moodle.org/plugins](http://moodle.org/plugins) will secure it for you.

* Edit all the files in this directory and its subdirectories and change
  all the instances of the string "newmodule" to your module name
  (eg "widget"). If you are using Linux, you can use the following command:
  `$ find . -type f -exec sed -i 's/newmodule/widget/g' {} \;`
  `$ find . -type f -exec sed -i 's/NEWMODULE/WIDGET/g' {} \;`

  On a mac, use:
  `$ find . -type f -exec sed -i '' 's/newmodule/widget/g' {} \;`
  `$ find . -type f -exec sed -i '' 's/NEWMODULE/WIDGET/g' {} \;`

* Rename the file lang/en/newmodule.php to lang/en/widget.php
  where "widget" is the name of your module

* Rename all files in backup/moodle2/ folder by replacing "newmodule" with
  the name of your module

  On Linux you can perform this and previous steps by calling:
  `$ find . -depth -name '*newmodule*' -execdir bash -c 'mv -i "$1" "${1//newmodule/widget}"' bash {} \;`

* Move the folder `/vendor`, which was created by composer, in the folder `/source`, overwriting any existing files if asked.

* If you encounter any problems while uploading, delete the whole folder `/source/vendor/trahloff/activiti/.git`. Deleting this folder is generally no bad idea.

* Create a ZIP archive of the `/source` folder and name it according to your app (in this tutorial "widget").

* Login in to [our Moodle instance](https://moodle.ganymed.me), navigate to the Management of Moodle and select the Option to install a new plugin.

* Upload your ZIP archive and click the button to proceed. You do not need to edit any other fields in this interface. 

* When asked if you want to update the Moodle database, do so. This is required for your plugin to be recognized by Moodle. The site might freeze for a short moment. DO NOT PANIC. This is normal.

  * If you get a timeout message, then your ZIP Archive is too big. Please run `composer install --no-dev` again, this time with the flag at the end to prevent all unnecessary libs from installing. This should slim down your ZIP archive (that you have to recreate, of course) down a bit, and processing should no longer take longer than 30 seconds.

* Go the main page of Moodle, select the "Test Course" and click "Enable Editing" in the options on the upper right. by clicking the option of "Add a resource ...", you should see a list of available plugins including your new module.

  * If you don't see your module, DO NOT PANIC! Moodle uses a Unix-daemon called `cron` that periodically runs specific tasks. In this case, specific commands are run every 5 minutes. Wait 5 minutes before trying anything else, and refresh the site.

  * If this does not help, then enter the Management section again, manually uninstall your plugin (accepting to update the Moodle database on the way), and upload your module again. Chances are somebody else just uploaded their plugin and there was a race for the database update that you lost.

* Select your module, name it in a way that others may understand what you are trying to test, and click on your new module instance.

* Have fun playing with your Moodle plugin!

* You may now proceed to run your own code in an attempt to develop
  your module. You will probably want to modify mod_form.php and view.php
  as a first step. Check db/access.php to add capabilities.
  Go to Settings > Site Administration > Development > XMLDB editor
  and modify the module's tables.

We encourage you to share your code and experience - visit [http://moodle.org](http://moodle.org)

Good luck, you will need it...