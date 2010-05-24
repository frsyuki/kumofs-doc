.. _install:

Installation
============

Using package manager
---------------------

FreeBSD Ports Collection
~~~~~~~~~~~~~~~~~~~~~~~~
You can install kumofs using Portage Collection on FreeBSD (`databases/kumofs <http://www.freshports.org/databases/kumofs/>`_).

Gentoo Portage
~~~~~~~~~~~~~~
You can install kumofs using Portage on Gentoo (`net-misc/kumofs <http://gp.wolf-u.li/net-misc/kumofs/>`_).

RPM
~~~
FIXME


Requirements
------------

Following environment is required to build kumofs:

  - linux >= 2.6.18
  - g++ >= 4.1
  - `ruby <http://www.ruby-lang.org/>`_ >= 1.8.6
  - `Tokyo Cabinet <http://1978th.net/tokyocabinet/>`_ >= 1.4.10
  - `MessagePack for C++ <http://msgpack.sourceforge.net/cpp:install>`_ >= 0.3.1
  - `MessagePack for Ruby <http://msgpack.sourceforge.net/ruby:install>`_ >= 0.3.1
  - libcrypto (openssl)
  - zlib

To install Tokyo Cabinet, get the latest source package from `the web site <http://1978th.net/tokyocabinet/>`_ and run ./configure && make && make install.

To install MessagePack, get the latest source package from `the web site <http://msgpack.sourceforge.jp/>`_ and run ./configure && make && make install.

The administration tools are implemented in ruby. Since they requires *msgpack* package, install it using RubyGems.

    $ sudo gem install msgpack

:ref:`fixme`


Configure and Build
-------------------

The latest release of the kumofs is available at `Downloads <http://github.com/etolabo/kumofs/downloads`_. Get it and run *./configure && make && make install*.

    $ ./bootstrap  # if needed
    $ ./configure
    $ make
    $ sudo make install

According to the install directory of MessagePack or Tokyo Cabinet, *--with-msgpack* option or *--with-tokyocabinet* options might be needed.

    $ ./bootstrap
    $ ./configure --with-msgpack=/usr/local --with-tokyocabinet=/opt/local
    $ make
    $ sudo make install

