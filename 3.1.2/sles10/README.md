# Building Puppet Enterprise on SLES 10

Puppetlabs are providing source RPMs for those part of their Puppet Enterprise stack which is under GPL license terms. This is short guide on how build the GPL packages yourself.

## Building Instructions

* You need a SLES 10 server to build on. A temporary server will work fine, I spun up a Vagrant instance with a minimal SLES 10.4 installation. The build process include installing the new RPMs as they partially require each other to build. This is one more argument for building on a temporary server.

* Download the source RPMs from http://downloads.puppetlabs.com/enterprise/sources/3.1.2/sles/11/SRPMS/ (yes, the SLES 11 files. SLES 10 is not officially supported). Put them all into the "srpms" directory. I have provided md5 checksum from my downloads. Notice that for some RPMs they are several versions on the Puppetlabs download server, so only pick the one you want to build.

* Satisfy all build requirements by executing 'init-vm-sles10'. Depending on your SLES 10 you may have some of the packages installed already. Also your environment might look different so you have to adjust the lines regarding the repositories.

* Build everything by running 'build-pe-sles10'. Its basically a loop over all the listed spec files. If for some reason one RPM should fail to build then fix the problem and re-run the script. If the variable $skip is left on the "true" value then the script will pick up from last error. You wont need to build everything from start again.

If you have problems then please let me know.

/ Thomas Willert

