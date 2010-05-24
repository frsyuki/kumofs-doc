.. _howto:

HowTo
=====


Run on localhost
----------------

    [localhost]$ kumo-manager -v -l localhost
    [localhost]$ kumo-server  -v -m localhost -l localhost:19801 -L 19901 -s ./database1.tch
    [localhost]$ kumo-server  -v -m localhost -l localhost:19802 -L 19902 -s ./database2.tch
    [localhost]$ kumo-server  -v -m localhost -l localhost:19803 -L 19902 -s ./database3.tch
    [localhost]$ kumo-gateway -v -m localhost -t 11211


Configuring 6-node cluster
--------------------------

Run kumo-manager
~~~~~~~~~~~~~~~~

First, run kumo-manager on *svr1* and *svr2*.
kumo-manager requires IP address of its host and IP address of the another kumo-manager.

    [on svr1]$ kumo-manager -v -l svr1 -p svr2
    [on svr2]$ kumo-manager -v -l svr2 -p svr1

kumo-manager listens on 19700/tcp by default.


Run kumo-server
~~~~~~~~~~~~~~~

Second, run kumo-server on *svr1,svr2,svr3*.
kumo-server requires IP address of its host, IP address of the kumo-managers and path to the database file:

    [on svr1]$ kumo-server -v -l svr1 -m svr1 -p svr2 -s /var/kumodb.tch
    [on svr2]$ kumo-server -v -l svr2 -m svr1 -p svr2 -s /var/kumodb.tch
    [on svr3]$ kumo-server -v -l svr3 -m svr1 -p svr2 -s /var/kumodb.tch


Attach kumo-server
~~~~~~~~~~~~~~~~~~

Third, attach kumo-servers into the cluster using **kumoctl** command.
Confirm that the kumo-servers are recognized by the kumo-manager first:

    [       ]$ kumoctl svr1 status
    hash space timestamp:
      Wed Dec 03 22:15:55 +0900 2008 clock 62
    attached node:
    not attached node:
      192.168.0.101:19800
      192.168.0.102:19800
      192.168.0.103:19800

Recognized kumo-servers are listed at **not attached node**. Then, attach them as follows:

    [       ]$ kumoctl svr1 attach

Attached kumo-servers are listed at **attached node**. Confirm it as follows:

    [       ]$ kumoctl svr1 status
    hash space timestamp:
      Wed Dec 03 22:16:00 +0900 2008 clock 72
    attached node:
      192.168.0.101:19800  (active)
      192.168.0.102:19800  (active)
      192.168.0.103:19800  (active)
    not attached node:


Run kumo-gateway
~~~~~~~~~~~~~~~~

Finally, run kumo-gateway on the hosts that runs applications that uses kumofs.
kumo-gateway requires IP address of the kumo-managers and port number that accepts memcached protocol client.

    [on cli1]$ kumo-gateway -v -m svr1 -p svr2 -t 11211

It is ready to use kumofs cluster.  Connect **localhost:11211** using memcached client on *cli1*.


Adding new servers
------------------

To add a server into the system that is built in the tutorial, run kumo-server on another host, and then attach it using **kumoctl** command.

    [on svr4]$ kumo-server -v -l svr4 -m svr1 -p svr2 -s /var/kumodb.tch
    [       ]$ kumoctl svr1 attach


Removing fault servers
----------------------

    [       ]$ kumoctl svr1 remove


Show status of cluster
----------------------

You can get status of the cluster from from kumo-manager.
Use **kumoctl** command to get the status. Specify IP address of the kumo-manager for first argument and 'status' for second argument.

    [       ]$ kumoctl svr1 status
    hash space timestamp:
      Wed Dec 03 22:15:45 +0900 2008 clock 58
    attached node:
      192.168.0.101:19800  (active)
      192.168.0.102:19800  (active)
      192.168.0.103:19800  (active)
      192.168.0.104:19800  (fault)
    not attached node:
      192.168.0.104:19800

**hash space timestamp** The time that the list of attached kumo-servers is updated. It is updated when new kumo-server is added or existing kumo-server is down.

**attached node** The list of attached kumo-servers. **(active)** is normal node and **(fault)** is fault node or recovered but not re-attached node.

**not attached node** The list of recognized but not-attached nodes.


Show status of the node
-----------------------

kumo-server is the node that stores data. You can get load information such as the number of items that is stored on the node using **kumostat** command.

    $ kumostat svr3 items
    $ kumostat svr3 cmd_get

**uptime** uptime of the kumo-server

**version** version of the kumo-server

**cmd_get** total number of processed get requests

**cmd_set** total number of processed set requests

**cmd_delete** total number of processed delete requests

**items** number of stored items


**kumotop** command shows status of the servers like *top* command.

    $ kumotop -m svr1


Where the key?
--------------

kumofs distributes key-value pairs into the multiple servers. **kumohash** command look up which node stores the key.

    $ kumohash -m svr1 assign "the-key"


