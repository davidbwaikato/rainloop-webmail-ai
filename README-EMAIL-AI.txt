#
# One Time Setup
#

Optional:
  The following are useful if you want to run some NodeJS associated
  command-line tools

sudo npm install -g gulp
sudo npm install -g yarn

Get the supporting dependencies installed:

    npm install

Build the first version of the files:

    npm run build

At this point, the 'minified' version of rainloop is the active version
of the code that is setup to run.  Test this is functioning first:


Access the rainloop admin login panel in your web browser:

    echo  http://email-ai.interactwith.us/interactwith.us/rainloop-$USER/?admin

and paste into your web browser

At this stage, default password to log in, as noted in rainloop website.

Change the default password.  As a side-effect of this, the rainloop
configuration file:

  data/_data_/_default_/configs/application.ini

is generated.  This is an important file that we make use of below
when running the code in development mode.


Through the rainloop admin console, add in the email domain:

    email-ai.interactwith.us

And set the servers to:

    imap server is localhost, port is 2143
    smtp server is localhost, port is 2525

Click on the 'test' button to confirm things are working


You should now be able to access the email accounts that have been
created in James via:

    echo  http://email-ai.interactwith.us/interactwith.us/rainloop-$USER/

and paste into your web browser



#
# Working as a developer on the code base
#

To be on the safe side, rebuild the project, using the 'standard way'
NodeJS projects indicate they are being operated in developer mode:

    export NODE_ENV=development

    npm run build


The real key to editing rainloop files in development is to make some
key changes to application.ini.

Cribbed on details in CONTRIBUTOR.md


    **Debugging JavaScript**

    1. Edit data/_data_/_default_/configs/application.ini
    2. Set 'use_app_debug_js' (and optionally 'use_app_debug_css') to 'On'

    ---

   **Editing HTML Template Files**

    1. Edit data/_data_/_default_/configs/application.ini
    2. Set 'cache_system_data' to Off


Now you can type, for example:

    npm run watch-js


And edit the JavaScript files in:

  dev/

And when you reload the page in the web browser, the new JS code is used.

Similarly, having set cache_sysetm_data to Off, you can change the HTML content in:

  v/0.0.0.0/templates

And those changes come through when you reload the page.


The git forked version of the repository currently has two examples of customization.

For an HTML change see:

    rainloop/v/0.0.0/app/templates/Views/User/MailMessageList.html

Search within the file for Email-AI

For a JavaScript change see:

    dev/Remote/User/Ajax.js
 
Again, search for Email-AI in this file


========

