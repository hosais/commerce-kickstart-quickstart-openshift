This quick start based on the Quickstart of Drupal on OpenShift
===================
How to use it:
Create an Drupal application on openshift web site and change the code to point 
to this github repo. The mysql, and php cartriges will be created by openshift. 

This quickstart has scripts to deploy commerce kickstart, following the same 
layout like quickstart of drupal on onpenshift. Since using drush to install 
commerce kickstart is complicated (there are many parameters for setup a shop) 
so after the application is built, the admin needs to install it.  
 
The first time you push changes to OpenShift, the build script
will download the latest version of commerce kickstart. 

To make it scalable, please refer to the quickstart of drupal.

If you want to have full control of the code all under git, then you need to checkout 
php directory to local.


All of the scripts used to deploy and configure Drupal are located in
the [build](.openshift/action_hooks/build) and [deploy](.openshift/action_hooks/deploy) hooks.

Updates
-------
You can update the lastest core code (commerce kickstart) by delete current/ 
symbolic link in your downloads. Then run update by drush. 
Of course, do not forget to backup first.

You can use Drupal's module management UI to download new versions of
modules into your data directory.

Repo layout (same as quickstart of drupal)
-----------

php/ - At deploy time, the build script will symlink this directory to a
directory containing Drupal  
../data - For persistent data  
../data/sites - The data for your Drupal site, including settings.php,
downloaded modules, and uploaded files  
../data/downloads - The most recent version of Drupal.  
.openshift/pear.txt - list of pears to install  
.openshift/action_hooks/build - Script that gets run every push, just prior to starting your app  


Notes about layout
------------------

If you create a php directory in your Git repo, it will be served
instead of Drupal.  The build hook automatically symlinks the installed
version of Drupal from your data directory every time you push.  The
runtime directory in your application is automatically recreated each
push, so anything persistent must be in your Git repo or saved and
retrieved from the data directory.

