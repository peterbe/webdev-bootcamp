.. index:: arecibo


================================
Error Notification in Production
================================

When a traceback occurs in production sites, you need to send it somewhere.
Normally Django sends emails which can work fine until you get a few thousand
error emails in a minute.

To mitigate this, you can use `Arecibo`_ to track your errors.  There are
currently three servers:

https://arecibo-phx.mozilla.org/ (behind LDAP)
   The *preferred* PHX instance.

   To use it place the following in your Django settings::

      ARECIBO_SERVER_URL = 'http://arecibo1.dmz.phx1.mozilla.com/'

https://arecibo-sjc.mozilla.org/ (behind LDAP)
   The SJC instance.

   To use it place the following in your Django settings::

      ARECIBO_SERVER_URL = 'http://arecibo1.dmz.sjc1.mozilla.com/'

http://amckay-arecibo.khan.mozilla.org/
   Test server for local development.

   To use it place the following in your Django settings::

      ARECIBO_SERVER_URL = 'http://amckay-arecibo.khan.mozilla.org/'

To send errors from playdoh, see the `playdoh`_ docs.

.. warning::
   IT needs to update the ``ARECIBO_SERVER_URL`` in Django's local settings.
   They will need to verify via curl, that the webheads can reach Arecibo::

       curl -I http://arecibo1.dmz.phx1.mozilla.com/

.. note::
   The PHX data centre server is on a dedicated box, where as SJC is in a VM.
   Please use the PHX one if possible.

.. _playdoh: http://playdoh.readthedocs.org/en/latest/userguide/errors.html#arecibo
.. _Arecibo: http://areciboapp.com
