sysadmin-scripts
================

This is a public repository with some useful scripts I've developed. You're free to fork the repository, modify and use it for your personal use. I'll keep updated the repository adding and modifying scripts under my needs, but improvements and proposals are welcome as well.

Thanks for visit the repository and hope the scripts will be useful for you.

Author: Ivan Mora Perez - ivan@opentodo.net

List of Scripts
================
*   [__distributed-cmd__][1]

	Runs a command by ssh on a list of servers given. Before run the command on the remote server a check command is executed, if returns 0 then the command will be run on the server. Example:

	./distributed-cmd.pl --hosts srv1 srv2 --check "pidof apache2" --command "sudo /usr/sbin/service apache2 restart" --user ivan

*   [__check_http_requests__][2]

	Script to count the number of requests per minute for a given time and shows the next reports for the time period

	./check_requests.pl --log /var/log/apache2/access_log --time 07/Oct/2013:22:09 --minutes 2

*   [__blockips-nginx__][3]

	Script to generate an IP blacklist for nginx from the url: http://www.badips.com/get/list/wordpress/ The script use etckeeper to commit the changes for the configuration file or revert changes.

*   [__rloggerd__][4]
	
	rloggerd is a simple script which sends a log file to remote rsyslog server. Example

	./rloggerd.pl --server 192.168.1.136 --file /var/log/mysqld.log --facility local0 --priority warning --socket tcp --tag "hello world" --daemon

*   [__nagios-status-mklivestatus__][5]

	Script to get all the nagios alarms via mk-livestatus for services and hosts in status of Warning, Critical or Uknown Where the notifications are enabled and the check is not acknowledged. Use the --string or --html to choose the output you want. If html is enabled then will generate an output in html with a table of two columns for each alarm, one with the check command and the output with a background color of red, yellow or orange depending of the check status, and the second one the hostname affected with a url to the nagios page for the host. Edit the html to put your own stuff like styles and nagios url, this is only a simple template to show the alerts with a basic styles.

	./nagios-status-mklivestatus.pl --html > out.html

[1]: distributed-cmd.pl
[2]: https://github.com/opentodonet/check_http_requests
[3]: https://github.com/opentodonet/blockips-nginx
[4]: https://github.com/opentodonet/rloggerd
[5]: nagios-status-mklivestatus.pl
