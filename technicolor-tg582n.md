# Technicolor TG582n

## How to log into the modem's web interface

Open a browser and go to `http://192.168.1.254/` (or `http://10.0.0.138`)

Log in using your credentials. If you're on Infinitum (Telmex) the default user is `TELMEX` and the password is the default Wi-Fi password, also written on a sticker on the modem.

Otherwise, the default user is `Administrator` and the password is blank (i.e. no password).

## How to change the Wi-Fi network name and password

[Log into the modem's web interface](#how-to-log-into-the-modems-web-interface).

On the sidebar, click on "Home Network".

On the sidebar, under "Home Network", click on "Interfaces".

Click on "Wireless Interface".

On the top right corner, click on "Configure".

Under "Configuration", enter a new network name/SSID on the form.

Under "Security", enter a new network password on the form.

Click on the "Apply" button

## How to export/backup the modem configuration

[Log into the modem's web interface](#how-to-log-into-the-modems-web-interface).

On the sidebar, click on the "Technicolor Gateway".

On the sidebar, under "Technicolor Gateway", click on "Configuration".

Under "Pick a task...", click on "Save or Restore Configuration".

Under "Backup current configuration", click on the "Backup Configuration Now..." button.

Shortly after, a `user.ini` file will be downloaded. This text file contains all of the (current) modem's configuration and setup.

## How to restore a modem configuration

[Log into the modem's web interface](#how-to-log-into-the-modems-web-interface).

On the sidebar, click on the "Technicolor Gateway".

On the sidebar, under "Technicolor Gateway", click on "Configuration".

Under "Pick a task...", click on "Save or Restore Configuration".

Under "Restore saved configuration", select a configuration file to restore (e.g. `user.ini`) and click on the "Restore Configuration Now..." button.

## How to enable Telnet

Note: You don't need to do this if you _are_ able to connect via Telnet.

[Export/backup the modem configuration](#how-to-exportbackup-the-modem-configuration) and edit the file.

Under `[ servmgr.ini ]`, search for `TELNET state=disabled`, update its state to `enabled`, and save the file.

[Restore the updated modem configuration](#how-to-restore-a-modem-configuration).

## How to change default DNS

[Ensure Telnet is enabled](#how-to-enable-telnet).

Connect via Telnet: `telnet 192.168.1.254` or `10.0.0.138`

Log in using your credentials (same as the web interface's).

To list out the current DNS servers enter: `dns server forward list`

To delete the current DNS servers enter: `dns server forward flush`

List out the DNS servers again to confirm they were correctly removed.

To set the primary DNS server enter (replace `0.0.0.0`):

```bash
dns server forward dnsset add set=0 dns=0.0.0.0 label=None metric=10 intf=Internet owner=PPP
```

To set the secondary DNS server enter the previous command, updating the address.

To save the changes enter: `saveall`

To exit enter: `exit`

To verify the changes, [log into the modem's web interface](#how-to-log-into-the-modems-web-interface).

Under "Broadband Connection", click on "Internet".

Under "TCP/IPv4 Settings", verify the primary and secondary DNS addresses were updated.

Note: This may also be accomplished by editing the modem configuration and importing it.

## How to restrict access to the Wi-Fi network to registered devices only

[Log into the modem's web interface](#how-to-log-into-the-modems-web-interface).

On the sidebar, click on "Home Network".

On the sidebar, under "Home Network", click on "Interfaces".

Click on "Wireless Interface".

On the top right corner, click on "Configure".

Under "Security", for "Allow new devices", select "Allow new devices (via registration)".

Click on the "Apply" button.

## How to manage device access to the Wi-Fi network

[Log into the modem's web interface](#how-to-log-into-the-modems-web-interface).

On the sidebar, click on "Home Network".

On the sidebar, under "Home Network", click on "Interfaces".

Click on "Wireless Interface".

On the top right corner, click on "Configure".

Click on "Advanced WLAN settings".

Under "MAC Address filter" you can add new devices to the list.

Under "List of wireless devices" you can edit the access of the devices in the list.

Click on the "Apply" button to save the changes.

Note: The device name field has a character limit of 12. To work around that you can edit the HTML (via browser tools) or enter a short name, export the modem configuration, edit it with the desired name, and import it.
