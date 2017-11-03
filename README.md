# SnortIPS

SnortIPS is a passive Intrusion Prevention System (IPS) for Snort IDS running on OpenBSD.

## Features

This is the summary of how SnortIPS operates:

- SnortIPS follows Snort alerts file to find in each alert the priority and keywords defined in its configuration file.
- When it finds a matching alert, the IP address in the alert is blocked for a duration of time. SnortIPS adds such hosts to a snortips table in pf.
- SnortIPS relies on pfctl while managing its hosts table, and is able to recover previously blocked hosts when starting.
- The hosts table supports white and black list entries.
- Upon receiving the INFO signal, SnortIPS dumps currently blocked, whitelisted, and blacklisted hosts with the total numbers of each to a dump file.
- Upon receiving the USR1 signal, SnortIPS processes commands in the signal message file.
- Upon receiving the USR2 signal, SnortIPS unblocks all non-blacklisted hosts and zeros all variables.
- SnortIPS reloads its configuration upon receiving the HUP signal.
- SnortIPS handles alert file rotation.
