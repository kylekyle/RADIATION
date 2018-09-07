# Irradiating Raspberry Pis

This setup was created by Kyle King (D/EECS) and CDT Haley Duke to support a D/PANE project.  

First, make sure your Pi has the correct time:

```bash
sudo timedatectl set-ntp false
sudo timedatectl set-timezone EST
sudo timedatectl set-time "2018-04-18 14:10:00"
```

To make the software run automatically at boot, you'll need copy `rc.local` to the `/etc/` directory:

```bash
$ sudo cp /media/noobs/RADIATION/rc.local /etc/
```

When the Pi boots, it will check for `/boot/RADIATION/COLLECTDATA`. If that file exists, then it will do a few things:

1. It will wait for 1 minute to give you time to set up. The green LED will be dark for that minute.
2. It will start collecting data after a minute. The green LED will heartbeat while it is collecting. 
3. It will record the Pi temperature every 10 seconds to `/media/noobs/RADIATION/results/TIME-temp.log`
4. It will run a memory test against 500 MBs of RAM and save the results to `/media/noobs/data/TIME-mem.log`
5. The green LED will turn off when it it done.

The temp and mem scripts that collect data are in `/media/noobs/RADIATION/`

