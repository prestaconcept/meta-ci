meta-ci
=======

presta meta CI package. Proof of concept meta package for continuous integration dependencies

## tools

### setup script for apache in ci

In in order to run behat validations or other stuff, this creates a vhost for current job

~~~
bin/ci_init_vhost {job_name}
~~~

The server name will be `{job_name}.loc`.

_See [behat + jenkins][1] for more details._

[1]: http://stackoverflow.com/a/12074135/536174
