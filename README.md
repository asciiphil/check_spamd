check_spamd
===========

This is a simple Python script that checks whether SpamAssassin's
spamd process is running.  It's intended for use as a Nagios plugin.

The script makes use of `spamc`'s "keep-alive" check and basically
just serves as a wrapper to translate the result of that check into
Nagios-speak.

You need to have Python 2.4 or later installed, as well as
SpamAssassin's `spamc` script.


Usage
-----

For a local spamd communicating via UNIX socket, use:

    check_spamd -U /path/to/socket

For a spamd listening on a TCP/IP socket, use:

    check_spamd -H hostname -p port

`hostname` defaults to "localhost", and `port` defaults to 783, so a
local spamd with a default configuration can be checked with just:

    check_spamd

You can also use `-S` if you're using SSL communications and the
`--spamc` parameter if `spamc` is not in the script's default `$PATH`.
