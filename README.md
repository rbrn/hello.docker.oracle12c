# hello.docker.oracle12c

An experiment trying to get oracle 12c up and running in 5 minutes using vagrant, docker et al.

## Prerequisites

You should have installed

- [VirtualBox](https://www.virtualbox.org/) (v4.3.26)
- [vagrant](https://www.vagrantup.com/) (v1.7.2)

### Oracle 12cR1

- Download [Database Install files (1 and 2)](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/database12c-linux-download-1959253.html)
    - `linuxamd64_12102_database_1of2.zip` (1.5G)
    - `linuxamd64_12102_database_2of2.zip` (967.5M)
- Place the zip archives in the folder where the project resides, eg: `hello.docker.oracle12c/database_installer/`
 
## Connect to Database

After running

    vagrant up

If no errors, you should be able to connect to the database.
- Default password for `sys`, `system` is `vagrant`
- Port 1521
- service `cdb12c` (for container), `pdb` (for pluggable database)

## Problems
If problems occurs:

1) If failing because of unzip missing:

	vagrant ssh
	sudo yum install unzip
	Exit vagrant ssh session and execute:
	vagrant provision
You should be able see oracle installation proceeding
	

## Links

We considered gratefully following links
- [dbehnke/oracle12c-vagrant (GitHub)](https://github.com/dbehnke/oracle12c-vagrant)
- [Starting From Windows with Linux VM as Docker Host (AMIS Technology Blog)](https://technology.amis.nl/2015/03/15/docker-take-two-starting-from-windows-with-linux-vm-as-docker-host/)
- [rhopman/docker-oracle-12c (GitHub)](https://github.com/rhopman/docker-oracle-12c)
- [wscherphof/oracle-12c (GitHub)](https://github.com/wscherphof/oracle-12c)
- [phusion/open-vagrant-boxes (GitHub)](https://github.com/phusion/open-vagrant-boxes)

## Changes
April 13th: Oracle12c (Release 12.1.0.2) installed, snapshot AfterOra12Install created

	we preferred to implement our own scripts: 
	01_setup.sh, 02_checkPreq.sh, 03_install.sh, 04_postinstall.log, 05_postinstall.sh
	TODO_1: change resource, kernel parameters, shared memory config, etc. to run several databases
	TODO_2: create first CDB as of Oracle12
	TODO_3: install Oracle11g (Release 11.2.0.4) 
	TODO_4: create first Non-CDB database

