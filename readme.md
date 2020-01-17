
Tested with Ubuntu 19.10 run the scripts in this order.

	./box-apts
	./box-format
	./install-snapd
	./install-gamecake


Qemu management scripts
-----------------------

The scripts for handling the qemu image are documented bellow if you
run into any problems or wish to tweak things.

	./box-apts

Install the required dependencies using apt ( eg qemu ) This should be 
run once before doing anything else or you need to source qemu yourself 
for the rest of the scripts to work.

	./box-settings

Tweakable values, you should read and edit this file.

	./box-format

This will download raspbian (first run only) and create a fresh output 
image with some basic system modifications, mostly to get qemu working. 
Take a look at the script for the tweaks it performs.

Run this script again to reset the image back to base, it is quite 
quick as we do not do an apt upgrade which can take a very long time. 
If you want to make sure the image has the latest patches be sure to 
apt upgrade before using.

	./box-mount

Mount the image in boot and root folders, after this you can copy files 
into the image, eg root/home/pi is the home directory for the pi user.

This must not be run while the box is up or bad things may happen.

	./box-umount

Un mount the image, again please allways run this after mounting to 
avoid possible issues.

	./box-up

Start a qemu box, this script will take over the current console so you 
will need to switch to a new one to ./ssh into it.

THis must not be run while the image has been mounted or bad things may 
happen.

	./box-up-wait

Start a qemu box in the background and wait until ssh is working, after 
running this you can use ./ssh to run commands on it.

	./ssh

If you have created an image and it is currentl up (booted in a qemu 
box) then this script will ssh you into it.

	./box-down

Shut down the running qemu box, this must be run for a clean shutdown 
otherwise your image will not boot on a real raspberry pi.
