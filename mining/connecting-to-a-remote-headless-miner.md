# Connecting to a remote headless miner

Connecting to a remote explorer should be as simple as putting your miners url in the built in Remote Miner plugin. However if that remote explorer isnt running on your localhost machine, your browser security will reject the connection. The explorer guide gives 2 options to fix this browser limitation. 1) you can put an ssl cert on your remote server (difficult, costly) or 2) disable insecure content for the zkga.me domain (not good security practice in crypto where we really need good security practices). But those aren't the only solution!. Instead we can make a remote server look like a local server with a few command lines.

## Port forward with ssh

SSH is a way to access remote machines and allows port forwarding.
To set this up there are a few simple steps:

### 1. Installing ssh

SSH is already installed on GNU/Linux.
For Windows install your favorite application.  

### 2. Editing `~/.ssh/config`

This step is done so that you can ssh into machines without typing commandflags each time. Replace the 192 ip and user with your server.

Here is an example entry:
    
    Host miner
        Hostname 192.168.178.132
        User user
        Port 22
        Localforward 8001 localhost:8000

> If you have multiple miner copy/paste the entry and then increment the first port number by one

### Connecting

    ssh miner

Once you drop into the shell start `mimc-fast` or whatever remote miner client you're using
> Notice how `miner` stands for the entry in the `~/.ssh/config`

### Plugin use

The Plugin is called Remote Explorer and is in the official client, but does need one change from the default```
Run it and then add your entries:

    http://localhost:8001/mine

> Don't forget the `/mine` or it won't work
        
### Using key based authentication

Do this because typing the user password sucks.
On the client generate a key.

    ssh-keygen

Then copy it over to your miner and type your user password.

    ssh-copy-id miner
