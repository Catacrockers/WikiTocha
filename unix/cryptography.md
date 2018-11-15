# Key management

## SSH

To create a SSH key:

```
ssh-keygen -t rsa -C "your_email@example.com"
```

This command will place a ssh key (public and private) at ```~/.ssh``` folder. Never share private key, and use public key to set up connections to remote terminals. In this folder you will have the following files:

* authorized_keys: Holds a list of authorized public keys for servers. When the client connects to a server, the server authenticates the client by checking its signed public key stored within this file.
* id_rsa: Contains your PRIVATE key. Never share!
* id_rsa.pub: Contains your PUBLIC key. You can share it.
* known_hosts: Contains DSA host keys of SSH servers accessed by the user. This file is very important for ensuring that the SSH client is connecting the correct SSH server.

## Passwords

Never share your passwords. Never reuse your passwords if is possible. Using a Password manager is a good strategy to improve your security.

### pass

pass is a utility to manage your passwords across several devices. It is the standard unix password manager. It require to create a gpg key. It can be managed though several computers using git directly though the command.

To generate a new key:

```
pass generate $(key_name) $(number_of_character)
```

* Note: key name support ```/```, so you can store in a folder system several keys. In example: ```$(key_group)/$(my_key)``` is a valid ```$(key_name)```
* Note II: Use ```[--no-symbols,-n]``` to avoid symbols and ```[-c]``` option to avoid printing and store it in the clipboard.

To get a key stored:

```
pass $(key_name)
```

* Note: Use ```[-c]``` option to avoid printing and store it in the clipboard.

To save key created:

```
pass git push
```

To get new keys:

```
pass git pull
```
