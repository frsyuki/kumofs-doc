.. _intro:

What's kumofs?
===============

kumofs is a scalable and highly available distributed key-value store.

  - Data is replicated over multiple servers.
  - Data is partitioned over multiple servers.
  - Extreme single node performance; comparable with memcached.
  - Both read and write performance got improved as servers added.
  - Servers can be added without stopping the system.
  - Servers can be added without changing the client applications.
  - The system does not stop even if one or two servers crashed.
  - The system does not stop to recover crashed servers.
  - Scalable from 2 to 60 servers. (more than 60 servers has not be tested yet)
  - Optimized for storing a large amount of small data.
  - memcached protocol support.
    - supported commands are get (+get_multi), set, delete, gets and cas.
	- specify -F option to the kumo-gateway to save flags.
	- specify -E option to the kumo-gateway to save expiration time.


Actual cases
------------
:ref:`fixme`

