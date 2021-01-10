# [Termux](https://termux.com/)

## How to setup an SSH server on an Android device

This does not require root access.

Install and open [Termux](https://wiki.termux.com/wiki/Installation) on your phone.

You'll see a terminal, a welcome message and a command prompt.

Install [OpenSSH](https://www.openssh.com/):

```bash
pkg install openssh
```

If needed, or the package wasn't found, try updating the registry and upgrading existing packages first:

```bash
pkg upgrade
```

Note: You may be prompted to confirm the operation. Enter `y` to confirm. You may also be prompted to decide to update configurations files (`y`) or keep as is (`n`, the default). Either is fine. This may happen several times.

Install [Nmap](https://nmap.org/):

```bash
pkg install nmap
```

Run Nmap to verify an SSH server is not running:

```bash
nmap localhost
```

Note: There shouldn't be any ports opened listed.

Start an SSH server in your phone:

```bash
sshd
```

Verify it's running:

```bash
nmap localhost
```

Note: You should now see the port `8022` opened.

Get the IP address of the device. We'll use this address to connect to the SSH server from an external machine on the same network:

```bash
ifconfig wlan0
```

Note: You can also try with `ifconfig` and look for it there if the above doesn't yield anything. Local IP addresses usually start with `192.168`, e.g. `192.168.100.10`

To securely log into the SSH server we'll setup public key authentication.

On your machine (where you'll connect to your device), open a terminal and enter:

```bash
cd ~/.ssh
ssh-keygen -t rsa -b 4096 -f termux
```

Enter a passphrase for your new key when prompted.

This will generate an RSA key with 4096 bits named `termux`.

Note: The above assumes you have OpenSSH installed on your machine, i.e. `ssh-keygen` binary and `~/.ssh` folder exist

Copy the new key from your machine to your device:

```bash
ssh-copy-id -p 8022 -i termux IP_ADDRESS
```

Where `IP_ADDRESS` should be the local IP address of the device.

Note: If the command failed, try copying and pasting the contents of `termux.pub` (from your machine) into `~/.ssh/authorized_keys` (in your device)

On your device, restart the SSH server for the changes to take effect:

```bash
pkill sshd
sshd
```

On your machine, connect to the SSH server:

```bash
ssh -i ~/.ssh/termux -p 8022 IP_ADDRESS
```

You should have successfully logged into your Android device from your machine using SSH.

To log out of your session enter:

```
exit
```

## Further security

In addition to the above, and to avoid risks, you should disable password authentication (enabled by default).

To do this edit the SSHD configuration file on your device located at `$PREFIX/etc/ssh/sshd_config`:

```
nano $PREFIX/etc/ssh/sshd_config
```

And change `yes` to `no`:

```diff
-PasswordAuthentication yes
+PasswordAuthentication no
```

Save the file, and restart the SSH server.

## How to simplify the connection

Remembering the exact `ssh` command with its parameters and options may be cumbersome.

You can leverage the SSH configuration file to help with that

On your machine, edit your configuration file at `~/.ssh/config` and add something like:

```diff
+Host android
+	HostName 192.168.100.10
+	IdentityFile ~/.ssh/termux
+	Port 8022
```

Where:

* `android` is an alias for the hostname
* `192.168.100.10` is the local IP address of the device
* `~/.ssh/termux` is the path to your (Termux SSH) public key
* `8022` is the port of the SSH server

You can then log into your device by entering:

```bash
ssh android
```

## Links

* [Termux – Android terminal emulator and Linux environment app](https://termux.com/)
* [How to set up SSH Server in Termux (video)](https://www.youtube.com/watch?v=TNZW0LvEUKM)
* [Termux Package Management](https://wiki.termux.com/wiki/Package_Management)
* [Termux – Remote Access (wiki)](https://wiki.termux.com/wiki/Remote_Access)
* [Official (package) repositories](https://wiki.termux.com/wiki/Package_Management#Official_repositories)
