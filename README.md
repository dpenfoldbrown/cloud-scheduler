Cloud Scheduler 0.3
====================

Introduction
--------------
The cloud scheduler: a cloud-enabled distributed resource manager.

The cloud scheduler manages virtual machines on clouds configured with Nimbus, 
OpenNebula, Eucalyptus or EC2 interfaces to create an environment for batch 
job execution. Users submit their jobs to a batch job queue like Condor, Sun 
Grid Engine, or Platform LSF, and Cloud Scheduler boots VMs to suit those jobs,
creating a malleable, virtual environment for efficient job execution.

For more documentation on the cloud scheduler, please refer to the following pages:

* [http://wiki.github.com/hep-gc/cloud-scheduler](http://wiki.github.com/hep-gc/cloud-scheduler)
* [http://cloudscheduler.org](http://cloudscheduler.org)

Configuration
-------------

There are two configuration files that define the function of the cloud scheduler. 
These are:

### The general cloud scheduler configuration file

The general (or central) cloud scheduler configuration file contains fields for
defining cloud scheduler program functionality, including Condor job pool con-
figuration information, logging information, and default cloud resource config-
uration options. 

The cloud scheduler config file can be manually specified on the command line 
when the cloud scheduler is run via the `[-f FILE | --config-file=FILE]` option, 
or can be stored in  the following locations:
    ~/.cloudscheduler/cloud_scheduler.conf
    /etc/cloudscheduler/cloud_scheduler.conf

Note: the cloud scheduler will attempt first to get the general configuration
file from the command-line, then from the `~/.cloudscheduler` directory, and finally from the
`/etc/cloudscheduler directory`.

### The cloud resource configuration file

The cloud resource configuration file contains information on the cloud-enabled
clusters that the cloud scheduler will use as resources. Clusters in this con-
figuration file will be used by the cloud scheduler to create and manage VMs.
See the cloud_resources.conf file for an explanation of cluster configuration parameters.

The cloud resource config file can be specified on the command-line with the
[-c | --cloud-config=FILE] option. If the cloud resource config file is not
specified on the command line, it will be taken from the location given in the
cloud_resource_config field of the cloud_scheduler.conf file.


Prerequisites
----------------
* pyXML
* suds (https://fedorahosted.org/suds/)
* boto (For EC2 support: http://code.google.com/p/boto/)

You can install these on RHEL5 (and clones) with the following:

    $ yum install PyXML
    $ wget 'https://fedorahosted.org/suds/attachment/wiki/WikiStart/python-suds-0.3.6-1.el5.noarch.rpm?format=raw'\
    $ -O python-suds.el5.noarch.rpm
    $ yum localinstall python-suds.el5.noarch.rpm

    $ wget http://boto.googlecode.com/files/boto-1.8d.tar.gz
    $ tar xvf boto-1.8d.tar.gz
    $ cd boto-1.8d
    $ python setup.py install

On Mac OS X, using Macports, you can install these with the following
(say you're using python 2.6):

    $ sudo port install py26-xml py26-suds py26-boto


Install
-----------

To install cloud scheduler, as root, run:

    $ python setup.py install


License
---------

This program is free software; you can redistribute it and/or modify
it under the terms of either:

a) the GNU General Public License as published by the Free
Software Foundation; either version 3, or (at your option) any
later version, or

b) the Apache v2 License.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See either
the GNU General Public License or the Artistic License for more details.

You should have received a copy of the Apache v2 License with this
software, in the file named "LICENSE".

You should also have received a copy of the GNU General Public License
along with this program in the file named "COPYING". If not, write to the
Free Software Foundation, Inc., 51 Franklin Street, Fifth Floor, 
Boston, MA 02110-1301, USA or visit their web page on the internet at
http://www.gnu.org/copyleft/gpl.html.


