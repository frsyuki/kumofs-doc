.. _trouble:

Troubleshooting
===============

kumo-servers are down
---------------------

First, confirm that which of kumo-servers are down::

    [       ]$ kumoctl m1 status    # m1 is address kumo-manager
    hash space timestamp:
      Wed Dec 03 22:15:35 +0900 2008 clock 50
    attached node:
      192.168.0.101:19800  (active)
      192.168.0.102:19800  (active)
      192.168.0.103:19800  (active)
      192.168.0.104:19800  (fault)
    not attached node:

*(fault)* nodes are down.

Second, reboot the host and run kumo-server. Before running kumo-server, remove database file. Otherwise deleted keys may be restored.

The status of cluster will be as following::

    [       ]$ kumoctl m1 status
    hash space timestamp:
      Wed Dec 03 22:15:45 +0900 2008 clock 58
    attached node:
      192.168.0.101:19800  (active)
      192.168.0.102:19800  (active)
      192.168.0.103:19800  (active)
      192.168.0.104:19800  (fault)
    not attached node:
      192.168.0.104:19800

Finally, *attach* the kumo-server::

    [       ]$ kumoctl m1 attach
    [       ]$ kumoctl m1 status
    hash space timestamp:
      Wed Dec 03 22:15:55 +0900 2008 clock 62
    attached node:
      192.168.0.101:19800  (active)
      192.168.0.102:19800  (active)
      192.168.0.103:19800  (active)
      192.168.0.104:19800  (active)
    not attached node:

