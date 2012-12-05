Quiz Application
================

This is a simple quiz application made for a client.  It is intended to be used in multiple released apps, and emphasizes configurability.

Because the configuration and questions are bundled with the app, it needs to be built to change these features.  You will need to install [eclipse](http://www.eclipse.org/downloads/) and the [adt plugin](http://developer.android.com/sdk/installing/installing-adt.html) to do this.

Assets
----------------
Assets live, not suprisingly in the `assets` project directory. When we say *asset file* or *asset path* we mean a path relative to this directory.

Config Resources
----------------
Static configuration is stored in `res/values/config.xml`, using the format specified in the [android documentation](http://developer.android.com/guide/topics/resources/index.html).  See the comments in the file for an explaination of each setting.

Settings
---------------
The app is mainly configured via the standard android settings mechanism.  The idea is that we have two versions of the preferences xml file -- one containing preferences for all of the configurable variables, which lets us play with "live" configuration while developing an app (`res/xml/settings.xml`), and the other containing only those settings we want the user to be able to set (`res/xml/public_settings.xml`).  A config resource (`settingsResource`) tells the app  which to use.  When the app is first installed, it imports a settings file from the assets directory called `defaults.xml`.  *You do not edit this file*.  Instead, touch the "Export Settings" button at the bottom of the settings page and export the xml it generates via email.  Save the exported file to `assets/defaults.xml` and rebuild the app with `config_settingsResource` set to the public settings before release.

Xml Format
----------------
Each released application is bundled with a fixed set of questions, stored as xml in an asset file.  The file name is given by the config resource `config_questionsFile`.  The syntax is documented in the [quiz-example.xml](https://github.com/jjmason/android-quiz/blob/master/assets/quiz-example.xml) file.



