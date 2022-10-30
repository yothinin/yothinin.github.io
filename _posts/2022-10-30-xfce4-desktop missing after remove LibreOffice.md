Hello, guy!

This morning I use the command in Linux to remove LibreOffice, after that, all xfce4-desktop was missing.

First, I reboot my Orange Pi device, and the system allows me to login into text mode only, no GUI.

after I log in to the terminal I use this command to install the xfce4-desktop:

```
sudo apt install xfce4-desktop
```

It cannot, the device cannot install anything because the network's config is missing too.

I go to /etc/network and edit the interfaces file to add commands to enable and open it up when rebooting the system.

interfaces:

```
auto eth0
  allow-hotplug eth0
  iface eth0 inet dhcp
```

Then reboot the device again, install the missing application, and the GUI comes back after reboot.

Don't forget to install xfce4-screenshooter to capture the screen when you press the PrintScrt button.

Now the GUI seems like the usual but the web browser application is missing too.

I use Firefox-ESR to run as the default web browser because I encounter errors when running after installing chromium.

The first error is:

```
Failed to load module "xapp-gtk3-module"
-- fixed it by using --
sudo apt install xapp-gtk3-module

```

The Chromium web browser still can not open, I called it on the terminal, and see the message about GPU, I google and found somewhere to run chromium with the option --disable-gpu, and it is work. I can open the web browser with chromium, but cannot download the extensions for chrome, it said "disk is full".

I google for disk full in Linux, especially the Debian platform, and I found /run/user/1000 is used 100%, I think this is the reason for the error.

I go to /run/user/1000 and browse the files, I see the Mozilla Firefox directory and it uses more storage, I remove it, then I can download and install the extension for Chrome.

Now, I can use the GUI in Debian, the Orange Pi 3 LTS device.

The problem still annoys me is the synchronization with the google account is not working and some guy told me that is the policy from Google, I hate that, I hate Google when they upgrade the application the problem will come together.
