# Software Installation

## Write your SD Card {pagestep}
You must install an operating system first to set up and use the Raspberry Pi board. Raspbian or Raspberry Pi OS is a Debian-based computer operating system for Raspberry Pi board. There are several OS versions for the workstation. Raspberry Pi OS 32-bit must be installed.
>i **Coming soon:** a pre-built SD card image that contains a full operating system with all the necessary software pre-installed. 

**Before you start, please get:**

* A computer with Internet
* A MicroSD card
* A SD card reader (OPTIONAL) 
* A SD card adapter (OPTIONAL)

**To write your MicroSD card:**

* Download the latest .img file from [Raspberry Pi website](https://www.raspberrypi.com/software/operating-systems/).
* Use an adapter to connect your MicroSD card to your computer.
* Use a program such as [Etcher](https://www.balena.io/etcher) or [Raspberry Pi imager](https://www.raspberrypi.com/software/) to flash the .img file onto your MicroSD card.

More detailed information on installing a Raspberry Pi operating system image onto an SD card can be found [here on the Raspberry Pi website](https://www.raspberrypi.com/documentation/computers/getting-started.html#installing-the-operating-system).

**First boot:**

Connect your Pi to a display, mouse, keyboard, and power. When the Pi first boots, you will be asked to complete a quick setup before rebooting.

Once you have installed and configured the Raspberry Pi OS, you can install the User Interface App.

## Enable SSH, SPI, and Camera {pagestep}

**Method 1:** Use the graphical tool "Raspberry Pi Configuration". This is found under Menu > Preferences > Raspberry Pi Configuration. Then you must select the "Interfaces" tab and set SSH, SPI, and Camera to "Enabled".

**Method 2:** From the command line or Terminal window, start by running `sudo raspi-config`. This will launch the raspi-config utility:

- Select “Interfacing Options”.
- Highlight the "SSH" option and activate **Select**.
- Select and activate **Yes**.
- Highlight and activate **Ok**.
- When prompted to reboot highlight and activate **Yes**.
- Repeat the previous steps to enable "SPI" and "Camera".

## Edit config.txt {pagestep}

We need to edit the config file `sudo nano /boot/config.txt`

Add `disable_camera_led=2` at the end of the file  

Then, save it with `CTL+O` > `Enter` > `CTL+X` and reboot the system `sudo reboot`.

## Plug in Camera {pagestep}

How to connect properly a Raspberry Pi camera and more information about the sensor can be found [here on the Raspberry Pi website](https://www.raspberrypi.com/documentation/accessories/camera.html). Use `vcgencmd get_camera` to verify if your camera was detected and `raspistill -o test.jpg` if it works.

>! Cameras are sensitive to static. Earth yourself before handling the PCB. A sink tap or similar should suffice if you don’t have an earthing strap.

## Install Libraries {pagestep}

The Python libraries that allow the Webb App to work on your Pi are the followings:

```
Flask 1.0.2
Flask-socketio 4.3.2
Werkzeug 0.14.1
Jinja2 2.10
Markupsafe 1.1.0
itsdangerous 0.24
eventlet 0.33.3
spidev 3.6
RPi.GPIO 0.7.1
picamera 1.13
Pillow 9.4.0
```
**Method 1:** Use the terminal window and install each of the above libraries with `pip install`. Example: `pip install Flask==1.0.2`

**Method 2:** Download [requirements.txt](https://github.com/wenzel-lab/modular-microfluidics-workstation-controller/blob/master/user-interface-software/src/requirements.txt) file and copy it into your Home folder on your Pi. Use the terminal window and install all the libraries with `pip install -r requirements.txt` 

>i Use `pip list` to verify which modules are installed and their versions. 

## Set up the GPIO pin states {pagestep}

GPIO pins states must be modified during the bootup sequence to use them with the peripherals of the workstation. Our own custom `dt-blob.bin` file specifies which pin states should change:

* Download the [dts file](https://github.com/wenzel-lab/modular-microfluidics-workstation-controller/blob/master/TEMP/module-pi/pi_config/dt-blob.dts) and copy it into your Home folder.
* Install the Device Tree compiler by running `sudo apt install device-tree-compiler`
* Run the `dtc` command `sudo dtc -I dts -O dtb -o /boot/dt-blob.bin dt-blob.dts`

>i It is very useful to use the command `raspi-gpio get` to look at the setup of the GPIO pins to check that they are as you expect.

## Run the UI App {pagestep}

Download the [folder](https://github.com/wenzel-lab/modular-microfluidics-workstation-controller/tree/master/user-interface-software/src/webapp) and copy it into your Home folder.

**Method 1:** Go to the web app folder and double click on `pi_webapp.py`. A programming editor will open the Python file, then run the code.

**Method 2:** Use the terminal window, then `cd webapp` and `python pi_webapp.py`

Use a browser and go to `https://0.0.0.0:5000` to use the Web App

## Run the UI App on startup {pagestep}

Once the folder and Python files are in your Home folder, configure the Raspberry Pi to run the web app on startup.

We must edit the `rc.local` file `sudo nano /etc/rc.local`

Add `sudo -H -u pi python3 /home/pi/webapp/pi_webapp.py &` before `exit 0` on the file

Then, save it with `CTL+O` > `Enter` > `CTL+X`, and reboot the system `sudo reboot`.

When the Raspberry Pi boot again, use a browser and go to `https://0.0.0.0:5000` to open the Web App.

>i **Note:** While the program is running in the background, you will not be able to use the camera. First, you must kill the process related to the program. To identify the process (number of PID), use `ps aux`. Then, use `sudo kill -9 PID` where `PID` is the process. If you want to run the program again, repeat **STEP 6** or reboot the system. 
