

# Building Puppet Enterprise on CentOS 6

Puppetlabs are providing source RPMs for those part of their Puppet Enterprise stack which is under GPL license terms. This is short guide on how build the GPL packages yourself.

## Agent only

The build chain stop with an error when compiling java. At that point all the RPMs required for full agent operations have already been build. So unless you plan to run a Puppet Master on CentOS you should be able proceed with the agent packages just fine.
If you find out what causes the java to not build then please let me know!

## Building Instructions

* You need a CentOS 6 server to build on. A temporary server will work fine, I spun up a Vagrant instance. You need 2GB or more of RAM. The build process include installing the new RPMs as they partially require each other to build. This is one more argument for building on a temporary server.

* Download the source RPMs from http://downloads.puppetlabs.com/enterprise/sources/3.1.2/el/6/SRPMS/ . Put them all into the "srpms" directory. I have provided md5 checksum from my downloads. Notice that for some RPMs they are several versions on the Puppetlabs download server, so only pick the one you want to build.

* Satisfy all build requirements by executing 'init-vm-centos6'. Depending on your OS installation you may have some of the packages installed already.

* Build everything by running 'build-pe-centos6'. Its basically a loop over all the listed spec files. If for some reason one RPM should fail to build then fix the problem and re-run the script. If the variable $skip is left on the "true" value then the script will pick up from last error. You wont need to build everything from start again.

* The Ruby RPM will be patched for the openssl EC problems (https://bugs.ruby-lang.org/issues/8384):

If you have problems then please let me know.

/ Thomas Willert

