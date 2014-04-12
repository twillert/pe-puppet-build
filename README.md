# Building the pe-puppet stack on SLES 11

Puppetlabs are providing source RPMs for those part of their Puppet Enterprise stack which is under GPL license terms. This is short guide on how build the GPL packages yourself.

Building Instructions

* You need a SLES 11.2 server to build on. A temporary server will work fine, I spun up a Vagrant instance. You need 2GB or more of RAM. Else pe-java might have problems building.

* Download the source RPMs from http://downloads.puppetlabs.com/enterprise/sources/3.1.2/sles/11/SRPMS/ . Put them all into the "srpms" directory. I have provided md5 checksum from my downloads.

* Satisfy all build requirements by executing 'init-vm'. Depending on your SLES 11.2 you may have some of the packages installed already. Also your environment might look different so you have to adjust the lines regarding the repositories.

* Build everything by running 'build-pe'. Its basically a loop over all the listed spec files. If for some reason one RPM should fail to build then fix the problem and re-run the script. If the variable $skip is left on the "true" value the the script will pick up from last error. You wont need to build evrything from start again.

If you have problems then let me know.

/ Thomas Willert

