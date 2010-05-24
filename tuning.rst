.. _tuning:

Performance Tuning
==================

Tuning Tokyo Cabinet
--------------------
To get best performance, create database file using *tchmgr* command before starting kumo-server. See [documents of Tokyo Cabinet](http://1978th.net/tokyocabinet/spex-en.html) for details.

Example:

    [on svr1]$ tchmgr create /var/kumodb.tch 1310710
    [on svr1]$ kumo-server -v -l svr1 -m mgr1 -p mgr2 -s /var/kumodb.tch

