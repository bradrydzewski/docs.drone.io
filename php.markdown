---
layout: default
title: PHP
icon: php01
tagline: Building PHP Projects
---

The virtual machine is pre-installed with PHP 5.4 (Zend Engine) and includes the
following extensions:

* bcmath
* bz2
* calendar
* Core
* curl
* ctype
* date
* dba
* dom
* ereg
* exif
* fileinfo
* filter
* ftp
* gd
* gettext
* hash
* iconv
* intl
* json
* libxml
* mbstring
* mcrypt
* mhash
* mysql
* openssl
* pcntl
* pcre
* pgsql
* Phar 
* posix
* readline
* Reflection
* session
* shmop
* SimpleXML
* soap
* sockets
* SPL
* sqlite
* standard
* sysvmsg
* sysvsem
* sysvshm
* tidy
* tokenizer 
* wddx
* xml
* xmlreader
* xmlwriter
* zip
* zlib

## Dependencies

Example using **pear**:

```
sudo pear channel-discover pear.amazonwebservices.com
sudo pear install aws/sdk
```

Example using **composer**:

```
composer install
```

**TODO:** pyrus is not yet installed. If you would like support for pyrus / pear2
please let us know.

## Unit Test

By default, your PHP project is configured to execute tests with PHP Unit:

```
phpunit --coverage-text .
```
---

## Troubleshooting

### Composer & 403 Errors

At some point you may encounter an error message that looks like this:

```
The 'https://api.github.com/repos/doctrine/lexer/zipball/2f708a85bb3aab5d99dab8be435abd73e0b18acb' URL could not be accessed: HTTP/1.1 403 Forbidden
```

There is a [known issue](https://github.com/composer/composer/issues/1861) 
with running composer on high volume build servers. Composer attempts to
download package tarballs directly from GitHub using the GitHub API, which is
limited to 60 requests per hour per IP address. High volume build servers
(like drone.io) quickly exceed these limits.

The recommended approach is to use the `--prefer-source` command line flag.
This will `git clone` your dependencies as opposed to downloading tarballs
using the GitHub API.

```
composer install --prefer-source
```

