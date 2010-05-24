.. _intro:

What's kumofs?
===============


Kumofs is a simple and fast distributed key-value store.
You can use a memcached client library to set, get, CAS or delete values from/into kumofs.
Backend storage is Tokyo Cabinet and it will give you great performance.

  * Data is replicated over multiple servers.
  * Data is partitioned over multiple servers.
  * Extreme single node performance; comparable with memcached.
  * Both read and write performance got improved as servers added.
  * Servers can be added without stopping the system.
  * Servers can be added without modifying any configuration files.
  * The system does not stop even if one or two servers crashed.
  * The system does not stop to recover crashed servers.
  * Automatic rebalancing support with a consistency control algorithm.
  * Safe CAS operation support.
  * memcached protocol support.

    * supported commands are get (+get_multi), set, delete, gets and cas.
    * specify -F option to the kumo-gateway to save flags.
    * specify -E option to the kumo-gateway to save expiration time.


Actual cases
------------
:ref:`fixme`

