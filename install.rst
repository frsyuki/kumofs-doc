.. _install:

Installation
============

Using package manager
---------------------

FreeBSD Ports Collection
~~~~~~~~~~~~~~~~~~~~~~~~
FIXME

Gentoo Portage
~~~~~~~~~~~~~~
FIXME

RPM
~~~
FIXME


Requirements
------------

Following environment is required to build kumofs:

  - linux &gt;= 2.6.18
  - g++ &gt;= 4.1
  - ruby &gt;= 1.8.6
  - [Tokyo Cabinet](http://1978th.net/tokyocabinet/) &gt;= 1.4.10
  - [MessagePack for C++](http://msgpack.sourceforge.net/cpp:install) &gt;= 0.3.1
  - [MessagePack for Ruby](http://msgpack.sourceforge.net/ruby:install) &gt;= 0.3.1
  - libcrypto (openssl)
  - zlib

To install Tokyo Cabinet, get the latest source package from [the web site](http://1978th.net/tokyocabinet/) and run ./configure && make && make install.

To install MessagePack, get the latest source package from [the web site](http://msgpack.sourceforge.jp/) and run ./configure && make && make install.

The administration tools are implemented in ruby. Since they requires "msgpack" package, install it using RubyGems.

    $ sudo gem install msgpack


Configure and Build
-------------------

The latest release of the kumofs is available at [Downloads](http://github.com/etolabo/kumofs/downloads). Get it and run ./configure && make && make install.

    $ ./bootstrap  # if needed
    $ ./configure
    $ make
    $ sudo make install

According to the install directory of MessagePack or Tokyo Cabinet, --with-msgpack option or --with-tokyocabinet option might have to be added to ./configure.

    $ ./bootstrap
    $ ./configure --with-msgpack=/usr/local --with-tokyocabinet=/opt/local
    $ make
    $ sudo make install

