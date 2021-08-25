# Connecting to a remote headless miner

To connect to a miner and not having to turn off the browsers SSL/TLS you can:
- issue a Certificate with a Domain you own and setup a proxy (comlicated)
- port worward the miner to your localhost

## Port forward with ssh

SSH is a way to access remote machines and allows port forwarding.
To set this up there are a few simple steps:

### 1. Installing ssh

SSH is already installed on GNU/Linux.
For Windows install your favorite application.  

### 2. Editing `~/.ssh/config`

This step is done so that you can ssh into machines without typing commandflags each time.

Here is an example entry:
    
    Host miner
        Hostname 192.168.178.132
        User user
        Port 22
        Localforward 8001 localhost:8000

> If you have multiple miner copy/paste the entry and then increment the first port number by one

### Connecting

    ssh miner

Once you drop into the shell start `mimc-fast`
> Notice how `miner` stands for the entry in the `~/.ssh/config`

### Plugin use

The Plugin is called Remote Explorer and is in the official client.
Run it and then add your entries:

    http://localhost:8001/mine

> Don't forget the `/mine` or it won't work
        
### Using key based authentication

Do this because typing the user password sucks.
On the client generate a key.

    ssh-keygen

Then copy it over to your miner and type your user password.

    ssh-copy-id miner
