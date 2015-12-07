Graphite-Cassandrisper
================

.. image:: https://travis-ci.org/gitinsky/graphite-cassandrisper.svg?branch=master
   :alt: Build Status
   :target: https://travis-ci.org/gitinsky/graphite-cassandrisper

A plugin for using graphite with the cassandra-based Cassandrisper storage
backend.

Requires `Graphite-API`_ **(preferred)** or Graphite-web 0.10.X.

Graphite-API is available on PyPI. Read the `documentation`_ for more
information.

Graphite-web 0.10.X is currently unreleased. You'll need to install from
source.

.. _Graphite-API: https://github.com/brutasse/graphite-api
.. _documentation: http://graphite-api.readthedocs.org/en/latest/

Installation
------------

::

    pip install cassandrisper

Using with graphite-api
-----------------------

In your graphite-api config file::

    cassandrisper:
      urls:
        - http://cassandrisper-host:port
    finders:
      - cassandrisper.CassandrisperFinder

Using with graphite-web
-----------------------

In your graphite's ``local_settings.py``::

    STORAGE_FINDERS = (
        'cassandrisper.CassandrisperFinder',
    )

    CASSANDRISPER_URLS = (
        'http://host:port',
    )

Where ``host:port`` is the location of the Cassandrisper HTTP API. If you run
Cassandrisper on multiple hosts, specify all of them to load-balance traffic::

    # Graphite-API
    cassandrisper:
      urls:
        - http://host1:port
        - http://host2:port

    # Graphite-web
    CASSANDRISPER_URLS = (
        'http://host1:port',
        'http://host2:port',
    )

See `gitinsky/cassandrisper`_ for running the Cassandrisper carbon daemon.

.. _gitinsky/cassandrisper: https://github.com/gitinsky/cassandrisper

Changelog
---------

* **0.0.1** (8-12-2015): Initial version.
