
### Hardening Asustor NAS

1. Create new administrator user account
2. Disable default `admin` user
3. Disable vulnerable services:
	- FTP
	- WebDAV
	- SFTP
	- TFTP
4. Disable EZConnect under settings
5. Change HTTP/HTTPS ports to something nonstandard.
6. (Optional: Create a new SSL cert using `openssl`, import the cert and keyfile, and set as default)
7. ADM updates - Update ADM immediately, and set it to daily automated security updates
8. Harden SSH:
	1. Change SSH port to something nonstandard.
	2. Log in via SSH and password with your new user to ensure you have console access:
	   `ssh someuser@192.168.[whatever-ip] -p [your SSH port]` 
	2. Create an ~/.ssh directory in your new admin user's root
	3. Create a ~/.ssh/authorized_keys file and set permissions to 600
	4. Copy your ssh pubkey into the `authorized_keys` file.
	5. Log out of SSH, and try logging in again using your keyfile.
	   `ssh someuser@192.168.[whatever-ip] -p [your SSH port] -i ~/.ssh/id_rsa`  (use the path to your SSH private key, if it's not `~/.ssh/id_rsa`)
	6. After confirming ability to log in with the private key, edit the SSHD config to disable password-based login and root login:
		1. Edit the sshd_config: `vi /usr/etc/ssh/sshd_config`
		2. Find the following config lines, uncomment, and change each to `no`
		   `PasswordAuthentication yes`
		   `PermitRootLogin yes`.
		 3. Save and exit.
	7. Restart the SSHD service: `/etc/init.d/S41ssh restart`
9.  Confirm you can SSH in now, using passwordless login