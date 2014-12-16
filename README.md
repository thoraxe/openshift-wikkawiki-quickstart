#WikkaWiki on OpenShift
WikkaWiki is a flexible, standards-compliant and lightweight wiki engine written
in PHP, which uses MySQL to store pages. Forked from WakkaWiki. Designed for
speed, extensibility, and security. Released under the GPL license.

More information can be found on the official Piwik website at
http://www.wikkawiki.org

#Running on OpenShift

Create an account at http://openshift.redhat.com/

Create a PHP application

	rhc app create -a wikka -t php-5.4 -l $USERNAME

Add mysql support to your application
    
	rhc cartridge add -a wikka -c mysql-5.5 -l $USERNAME

Make a note of the username, password, and host name as you will need to use these to complete the Piwik installation on OpenShift

Add this upstream Piwik quickstart repo

    cd wikka/php
    rm -rf *
    git remote add upstream -m master https://github.com/thoraxe/openshift-wikkawiki-quickstart.git
    git pull -s recursive -X theirs upstream master

Then push the repo upstream to OpenShift

	git push

That's it, you can now checkout your application at:

	http://wikka-$yourlogin.rhcloud.com
