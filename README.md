# tvbox-linux-printer
Using a relatively old TV Box (MXQ Pro 4K) as a 3D Print server with OctoPrint and Klipper

# What do I need?
* An TV Box (I am using a MXQ Pro 4K model)
* Screwdrivers
* Linux or WSL
* SD Card
* SD Card Reader

# Instructions - Installing Linux on my TV Box
* Open your TV Box and search for some board info (In my case, the board ID is 329Q)
* Remove the CPU heatsink and write down the CPU model (In my case, it is a Rockchip RK3228a)
* Search on how to setup a Linux on your board model or on your CPU model
* In my case, I am following this guide: [CSC Armbian for RK322X TV Boxes](https://forum.armbian.com/topic/12656-csc-armbian-for-rk322x-tv-boxes/)
  * My board is using a NAND memory instead of an eMMC memory, according to the MultiTool. You can confirm by selecting the option to burn a image in the MultiTool tool itself and observing the name of the internal memory.
  * So, I just followed the instructions on the **Quick installation instructions on NAND** section.
  * I also choose the Minimal Debian Buster with Legacy Kernel (Legacy Kernel is required for the RK3228a processor)
* After that, you will have a fully functional Linux running on your TV Box!
* Remember to setup WiFi connection. I recommend the **nmtui** utility.

# Instructions - Installing OctoPrint and Klipper
## OctoPrint
* Update and install some needed packages with these commands:
```
sudo apt update
sudo apt install python-pip virtualenv build-essential g++ python-dev git
```
* Install OctoPrint and enable auto running
 * See [Installing manually] (https://octoprint.org/download/) and [Automatic start up](https://community.octoprint.org/t/setting-up-octoprint-on-a-raspberry-pi-running-raspbian/2337)
 * Use "systemctl start octoprint" instead of running "service octoprint start"
* Setup Shutdown and Reboot
  * Restart OctoPrint: sudo systemctl restart octoprint
  * Restart system: sudo systemctl reboot
  * Shutdown system: sudo systemctl poweroff
 
## Klipper
* See [Klipper Installation](https://www.klipper3d.org/Installation.html)
