.. _design:

Design
======

Data Model
----------

kumofs supports following 4 operations:

*Set(key, value)*
    Store the key-value pair. One key-value pair is copied on three servers.
    If the Set operation is failed (because of network trouble, etc.), the associated value of the key becomes indefinite. Retry to set the value, delete the key or not to get the key.

*value = Get(key)*
     Retrieve the associated value of the key.

*Delete(key)*
    Delete the key and its associated value.

*CAS(key, value, compare)*
    Compare-and-Swap the key and its associated value.
    The semantics of the CAS operation is that "the swapping always fails if the comparison fails". This means that the swapping may not succeed if the comparison succeeds. This restriction is caused when some servers are detached or attached. You are required to retry the operation if the swapping is failed.


Network Topology
----------------
:ref:`fixme`


Roles of the node
-----------------
:ref:`fixme`

Server
~~~~~~
:ref:`fixme`

Gateway
~~~~~~~
:ref:`fixme`

Manager
~~~~~~~
:ref:`fixme`


Partitioning and Replication
----------------------------
:ref:`fixme`

Dynamic rebalancing
-------------------

http://github.com/etolabo/kumofs/issues/closed#issue/1

:ref:`fixme`

