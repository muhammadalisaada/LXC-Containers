# LXC-Containers
how to install lxc containers on ubuntu 22.4 server with plesk?

LXC can easily be installed on Ubuntu from upstream repositories using the following commands:

    sudo apt update && sudo apt install lxc
    
The above command will install lxc package and all dependencies required then configure a default container network. The name of the bridge is  **lxcbr0**:

```
$ ip ad | grep lxc
3: lxcbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
inet 10.0.3.1/24 scope global lxcbr0
```
## Install LXC Web UI on Ubuntu

There are a number of tools that you can use to manage your LXC containers. On this article, we’ll install and use LXC Web Panel. Run this command to install it:

```
wget https://lxc-webpanel.github.io/tools/install.sh -O - | sudo bash
```

This will automatically install and configure LXC Web UI for you. You’ll get an output similar to below after installation.

```

 _     __   _______  __          __  _       _____                 _
| |    \ \ / / ____| \ \        / / | |     |  __ \               | |
| |     \ V / |       \ \  /\  / /__| |__   | |__) |_ _ _ __   ___| |
| |      > <| |        \ \/  \/ / _ \ '_ \  |  ___/ _` | '_ \ / _ \ |
| |____ / . \ |____     \  /\  /  __/ |_) | | |  | (_| | | | |  __/ |
|______/_/ \_\_____|     \/  \/ \___|_.__/  |_|   \__,_|_| |_|\___|_|


Automatic installer

Installing requirement...
+ Installing Python
+ Installing Python pip
E: Package 'python-pip' has no installation candidate
| + Flask Python...
Cloning LXC Web Panel...
Cloning into '/srv/lwp'...
remote: Enumerating objects: 243, done.
remote: Total 243 (delta 0), reused 0 (delta 0), pack-reused 243
Receiving objects: 100% (243/243), 198.33 KiB | 9.92 MiB/s, done.
Resolving deltas: 100% (108/108), done.

Installation complete!


Adding /etc/init.d/lwp...
Done
Starting server...done.
Connect you on http://your-ip-address:5000/
```

As you can see, the service is listening on port **5000.** If you have a firewall, open the port so that you can access it from a remote device.

```
sudo ufw allow 5000
```

You can now open the URL _http://your-ip-address:5000/_  on your browser to access the dashboard.

Login with user **admin** and password **admin**. Don’t forget to change the password after logging in.
