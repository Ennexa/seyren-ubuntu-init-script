seyren-ubuntu-init-script
=========================

Ubuntu Init script for Seyren


Installation
============

Clone the repository

    git clone git@github.com:Ennexa/seyren-ubuntu-init-script.git
	cd seyren-ubuntu-init-script

Create a system user for running the daemon

    sudo useradd -r -s /bin/false seyren
	
Download seyren

    sudo mkdir /usr/share/seyren
    wget https://github.com/scobal/seyren/releases/download/1.2.0/seyren-1.2.0.jar
	sudo mv seyren-*.jar /usr/share/seyren/
    sudo chown -R seyren:seyren /usr/share/seyren/

Create the log directory

    mkdir /var/log/seyren
    chown seyren:seyren /var/log/seyren

Configure the init script

	sudo cp init.d/seyren /etc/init.d/seyren
	sudo chmod +x /etc/init.d/seyren
	sudo cp defaults/seyren /etc/defaults/seyren

edit `/etc/defaults/seyren` to configure `GRAPHITE_URL` and other options.

Run the service

    service seyren start