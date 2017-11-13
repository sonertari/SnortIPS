# SnortIPS

SnortIPS is a passive Intrusion Prevention System (IPS) for Snort IDS running on OpenBSD.

## Features

As a summary of its operation, SnortIPS:

- Follows new lines appended to Snort alerts file to find priority and keywords defined in its configuration file.
- Blocks source IP addresses in matching alerts for a duration of time.
- Adds such hosts to snortips table defined in pf.conf, which supports white and black list entries as well.
- Relies on pfctl while managing this hosts table, and is able to recover previously blocked hosts when starting.
- Upon receiving the INFO signal, dumps currently blocked, whitelisted, and blacklisted hosts with the total numbers of each to a dump file.
- Upon receiving the USR1 signal, processes commands in the signal message file.
- Upon receiving the USR2 signal, unblocks all non-blacklisted hosts and zeros all variables.
- Upon receiving the HUP signal, reloads its configuration.
- Handles alert file rotation.
