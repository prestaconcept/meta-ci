# meta-ci

presta meta CI package. Proof of concept meta package for continuous integration dependencies

## Requirement for ci_init_vhost

### httpd configuration

### create a directory to store your CI vhosts

~~~
mkdir -m775 /etc/httpd/conf.d/jenkins_vhosts
chgrp jenkins /etc/httpd/conf.d/jenkins_vhosts
~~~

### auto include vhosts

include jenkins vhosts in an Apache configuration file
(after your default vhost)

~~~
Include conf.d/jenkins_vhosts/*.conf
~~~

### Allow jenkins to write in /etc/hosts

~~~
chmod g+w /etc/hosts
chgrp jenkins /etc/hosts
~~~

### Allow jenkins and reload Apache


for visudo syntax check
~~~
visudo -f /etc/sudoers.d/jenkins 
~~~

file content to allow HTTPD configuration test + reload

~~~

jenkins ALL=(ALL) NOPASSWD: /usr/sbin/apachectl graceful
jenkins ALL=(ALL) NOPASSWD: /usr/sbin/apachectl -t
~~~


## tools

### setup script for apache in ci

In in order to run behat validations or other stuff, this creates a vhost for current job

~~~
bin/ci_init_vhost
~~~

The server name will be `{JOB_NAME}.loc`.

_See [behat + jenkins][1] for more details._

[1]: http://stackoverflow.com/a/12074135/536174
