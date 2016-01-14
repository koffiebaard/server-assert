# Server asserts

Asserts for the actual linux servers.

- Low level framework-ish

- Asserts to check if everything in the system is as it should be

- Easily bundle some asserts in a script and run as a cronjob.

- Can send a mail if anything fails.


Examples:

	sassert --exists /var/www
	sassert --ownership /var/www/index.php www-data
	sassert --permissions, /var/www/index.php 770
	sassert --verify-symlink /var/www/public /mnt/nfs01/public/

	sassert --daemon-running nginx
	sassert --daemon-running mysqld

	sassert --host-resolves vm02
	sassert --port-open-locally 3306	
	sassert --port-open-remote 192.168.1.100 80


	sassert --verify-crontab-scripts




Aimed process of usage:
----------------------

verify on interval

	$ apt-get install sassert
	# create bash script w/
	sassert --exists /var/www -q --mailonfail bloop@bleep.com
	sassert --ownership /var/www www-data -q --mailonfail bloop@bleep.com
	# put in crontab

manual checks

	$ apt-get install sassert
	$ sassert --ownership /var/www/index.php www-data
	ownership "/var/www/index.php" OK

