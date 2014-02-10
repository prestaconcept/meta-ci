meta-ci
=======

#Overview #

presta meta CI package. Proof of concept meta package for Manage your vhost for Behat on continuous integration

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
Defaults:jenkins !requiretty
jenkins ALL=(ALL) NOPASSWD: /usr/sbin/apachectl graceful
jenkins ALL=(ALL) NOPASSWD: /usr/sbin/apachectl -t
~~~


## tools

### setup script for apache in ci

In in order to run behat validations or other stuff, this creates a vhost for current job

~~~
bin/ci_init_vhost [<subdir_for_documentroot>]
~~~

The server name will be `{JOB_NAME}.loc`.

_See [behat + jenkins][1] for more details._

[1]: http://stackoverflow.com/a/12074135/536174

## Ask for help ##

:speech_balloon: If you need help about this project you can [post a message on our google group][3]

## Contributing

Pull requests are welcome.


Thanks to
[everyone who has contributed](https://github.com/prestaconcept/PrestaSonataNavigationBundle/graphs/contributors) already.

---

*This project is supported by [PrestaConcept](http://www.prestaconcept.net)*

**Lead Developer** : [@nicolas-bastien](https://github.com/nicolas-bastien)

Released under the MIT License

[3]: https://groups.google.com/forum/?hl=fr&fromgroups#!forum/prestacms-devs



[2]: https://github.com/prestaconcept/prestacms-sandbox
[3]: https://groups.google.com/forum/?hl=fr&fromgroups#!forum/prestacms-devs
[4]: http://prestaconcept.github.io/presta-sonata-navigation/
[5]: http://sandbox.prestacms.com/
[6]: http://sandbox.prestacms.com/admin

[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/prestaconcept/meta-ci/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

