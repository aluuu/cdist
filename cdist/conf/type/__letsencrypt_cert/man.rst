cdist-type__letsencrypt_cert(7)
===============================

NAME
----

cdist-type__letsencrypt_cert - Get an SSL certificate from Let's Encrypt

DESCRIPTION
-----------

Automatically obtain a Let's Encrypt SSL certificate using Certbot.

REQUIRED PARAMETERS
-------------------

admin-email
    Where to send Let's Encrypt emails like "certificate needs renewal".

REQUIRED MULTIPLE PARAMETERS
----------------------------

domain
    A domain to be included in the certificate.

OPTIONAL PARAMETERS
-------------------

state
    'present' or 'absent', defaults to 'present' where:

    present
        if the certificate does not exist, it will be obtained
    absent
        the certificate will be removed

webroot
    The path to your webroot, as set up in your webserver config. If this
    parameter is not present, Certbot will be run in standalone mode.

OPTIONAL MULTIPLE PARAMETERS
----------------------------

renew-hook
    Renew hook command directly passed to Certbot in cron job.

BOOLEAN PARAMETERS
------------------

automatic-renewal
    Install a cron job, which attempts to renew certificates daily.

staging
    Obtain a test certificate from a staging server.

MESSAGES
--------

change
    Certificte was changed.

create
    Certificte was created.

remove
    Certificte was removed.

EXAMPLES
--------

.. code-block:: sh

    __letsencrypt_cert example.com \
        --admin-email root@example.com \
        --automatic-renewal \
        --domain example.com \
        --domain foo.example.com \
        --domain bar.example.com \
        --renew-hook "service nginx reload" \
        --webroot /data/letsencrypt/root


AUTHORS
-------

| Nico Schottelius <nico-cdist--@--schottelius.org>
| Kamila Součková <kamila--@--ksp.sk>
| Darko Poljak <darko.poljak--@--gmail.com>
| Ľubomír Kučera <lubomir.kucera.jr at gmail.com>

COPYING
-------

Copyright \(C) 2017-2018 Nico Schottelius, Kamila Součková, Darko Poljak and
Ľubomír Kučera. You can redistribute it and/or modify it under the terms of
the GNU General Public License as published by the Free Software Foundation,
either version 3 of the License, or (at your option) any later version.
