#How to set up a Raspberry Pi Wixel receiver#

>Based on using the Raspbian distribution.

First login to your Pi and set it up with a .local name, see: [assigning a .local address](http://www.howtogeek.com/167190/how-and-why-to-assign-the-.local-domain-to-your-raspberry-pi/)

Make sure packages are installed:

`sudo apt-get update && sudo apt-get -y install git screen python python-pycurl wget sdcc python-serial libusb-1.0-0`

Download the usb wixel python code:

`git clone https://github.com/jamorham/python-usb-wixel-xdrip.git`

`cd python-usb-wixel-xdrip`

On Debian based linux distro's if you wish to run as non-root, add your user to the "dialout" group to grant rights to the USB serial device.

Run the auto-installer as the user you with to run as "non-root":

`sh forusb.sh`

This will compile the wixel firmware and install the python script

If all is good you should see "Waiting for connections" on the screen 
and a flashing yellow light on the Wixel until it gets the first dex signal.

Within [xDrip+](https://jamorham.github.io/#xdrip-plus) select `WiFi Wixel` in `Data source` settings section and add `raspberry.local:50005` in to `List of Receivers` or whatever your Raspberry Pi hostname is.

After reboot you can check the script is running with:
`sudo screen -r wixel`
