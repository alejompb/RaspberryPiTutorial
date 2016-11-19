# Raspberry Pi Peer Tutorial.
In this tutorial I will make an introduction and a general overview of what is, and how to set up and run simple applications in the Raspberry Pi. Specifically, I will show how to display your Raspberry Pi screen in your computer, without using any extra hardware such as an extra monitor, HDMI cable, wireless keyboard, wireless mouse, or router. Also, I will explain the main approaches on how to create a project with your Raspberry Pi using examples for each approach.

*Note that I will use the Raspberry Pi model 3B. Some features may change from model to model, however, the main concept will be always the same.*

* [What is a Raspberry Pi](#what-is-a-Raspberry-Pi)
* [How to get started](#How-to-get-started)
* [Different Pi project implementations](#Different-Pi-project-implementations)
   - [Example of project using a Pi OS (Raspbian)](#Example-of-project-using-a-Pi-OS-(Raspbian))
   - [Example of project installing a new image of an adapted OS](#Example-of-project-installing-a-new-image-of-an-adapted-OS)


****
     
# What is a Raspberry Pi

> The Raspberry Pi is a series of credit card-sized single-board computers developed in the United Kingdom by the Raspberry Pi Foundation to promote the teaching of basic computer science in schools and developing countries. 	**Wikipedia**

The Raspberry Pi is a very small and tiny computer, capable of running different operating systems. The main purpose of its use is running simple applications due to its limitations at a hardware level. Normally, a Pi has the following common features:

+ CPU speed: 700 MHz to 1.2 GHz.
+ RAM memory 256 MB to 1 GB RAM. 
+ 1 SD card slot 
+ 1-4 USB slots
+ HDMI port
+ 3.5 mm phone jack audio port

Special features of the lastest models:

+ 8P8C Ethernet port 
+ Wi-Fi 802.11n
+ Bluetooth


****


# How to get started

In order to set up the Raspberry Pi we will need:
* Ethernet cable
* SD card of at least 4 GB
* Power adaptor
* Computer
* Your Raspberry Pi 3-B

Optional components:

- Wireless keyboard 
- Wireless mouse
- HDMI cable
- Monitor

In this section you will learn how to set up the Pi without using any optional components, taking advantage of the features that the Model 3-B provides. 


*NOTE: IF YOU HAVE REACHED THIS SITE BUT YOU DO NOT HAVE THIS MODEL AND YOU HAVE KEPT READING, HERE YOU HAVE A COUPLE OF LINKS BY WHICH YOU WILL BE ABLE TO SET UP THE PI.*

* [SETTING UP RASPBERRY PI USING YOUR LAPTOP SCREEN AS DISPLAY, AS WELL AS LAPTOP KEYBOARD AND MOUSE.](https://www.youtube.com/watch?v=toWBmUsWD6M)

* [SETTING UP RASPBERRY PI USING A MONITOR, HDMI CABLE, WIRELESS KEYBOARD AND WIRELESS MOUSE.]
(https://www.youtube.com/watch?v=L3amYDRlIUs)

*AFTER THE THESE STEPS, YOU CAN GO TO THE NEXT SECTION:* [Different Pi project implementations](#Different-Pi-project-implementations)

There are plenty of ways of how to set up your Pi. I have decided to show you how to do it using the least number of hardware components, if you are a student and you cannot wait to buy everything you need. 
First of all, I will list the software components that you need to download and install.

* [Raspbian OS](https://www.raspberrypi.org/downloads/raspbian/): This is the operating system that will be installed in the Pi, you can install any other, however, I recommend this one due to its facility of use. Another reason is that it comes with just one file, the image file, making the process of installation easier. Click on Download ZIP under RASPBIAN JESSIE WITH PIXEL to start your download. I recommend to start with this one since it is a heavy file and it is going to take a while unless you have a super fast internet connection.

* [Win32DiskImager](https://sourceforge.net/projects/win32diskimager/files/latest/download): We will use this software to burn the Pi OS in the SD card.

* [SDFormatter](https://www.sdcard.org/downloads/formatter_4/): Click on this link that will direct you to the SD Association website. In the left bar click on the download link that that is more appropriate for you (Mac or Windows), after clicking on Accept your download will start. 

* [PuTTy](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html): Will be used to connect the Pi to the computer through SSH connection. For that we will need the Pi to be connected to the Internet, that will be explained later.

* [Xming](http://sourceforge.net/projects/xming/): This program will allow us to see the Pi´s display on our laptop´s screen.

Once we have everything downloaded and installed let´s proceed with the configuration.


1. Format the SD card to avoid troubles when installing the Pi OS.
     - Insert your SD card into your laptop
     - Open SD Formatter
     - Make sure that the Volume label is the one associated with your SD card
     - Click on Option and select:
       + Format Type: FULL (Erase)
       + Format Size Adjustment: ON
     - Click on format
       + Wait until it´s finished
       + Check that your SD card is empty
       + Exit program
2. Now it´s time to burn the image of the OS into the SD card. 
     - Open Win32Disk Manager 
     - Make sure you select the Volume label with the one that correspond to the SD card. You can check it in the tab *Device*
     - Click on the folder symbol and select the image of the Raspbian OS. *NOTE: it is likely that the OS image is within            a compressed file; if you have not done it yet first, unzip it, and then you can select the image file.*
     - Click on the Write button to burn the image in your SD card.
     - Once finished eject your SD card safely from your computer.
3. This part of the configuration is really important, it allows the Pi to get internet signal from your laptop´s connection.
     - Open Network and Sharing Center (Windows users)
     - Select your WiFi connection 
     - ![WiFi connection](https://github.com/alejompb/RaspberryPiTutorial/blob/master/1.PNG?raw=true)
     - Click on properties and then *Sharing* tab 
     - ![Properties](https://github.com/alejompb/RaspberryPiTutorial/blob/master/2.PNG?raw=true)
     - ![Sharing tab] (https://github.com/alejompb/RaspberryPiTutorial/blob/master/3.PNG?raw=true)
     - Select both options in order to *Allow other network users* (your Raspberry Pi) *to connect through this computer´s Internet connection*
     - _**NOTE: AT THIS POINT IT IS IMPORTANT TO TAKE INTO ACCOUNT THAT YOU HAVE TO ALLOW JUST THE ETHERNET CONNECTION! YOU MAY HAVE OTHER KIND OF NETWORK CONNECTIONS (LIKE A VIRTUAL MACHINE HOST), WE DO NOT WANT TO SHARE INTERNET WITH ANYTHING ELSE IN THIS CASE, JUST WITH THE COMPONENT THAT WILL BE CONNECTED TO OUR COMPUTER VIA ETHERNET (THIS IS YOUR RASPBERRY PI). IN CASE YOU HAVE ANY ISSUE OPEN YOUR NETWORK CONNECTIONS AND DISABLE THE OTHER ADAPTERS (SPECIALLY, VIRTUAL MACHINE ADAPTER CONNECTIONS SUCH AS VIRTUALBOX OR VM WARE).**_
4. In this part you have to set the wired configuration. If you did the last part correctly, your computer will assign an IP to your Pi through the Ethernet port, you can check that clicking on the *Ethernet* connection (of course, once you have finished with this step) and then *Details* in the *Network and Sharing Center*
     - Stick your SD card in the Pi´s slot.
     - Ethernet cable connecting the Pi and your laptop.
     - Power supply to the Pi. 
     - After all the Pi should look like this
     - ![Pi set up](https://github.com/alejompb/RaspberryPiTutorial/blob/master/IMG_4718.JPG?raw=true)
     - _**Note: check that there is a red light near to the power supply and another one green and yellow under the Ethernet connection.**_
5. Open Xming, I recommend the *One Window* display setting, otherwise it will get confusing to navigate between the Pi´s windows and your laptop´s windows. Then select the default settings.
![Xming settings](https://github.com/alejompb/RaspberryPiTutorial/blob/master/xming1.PNG?raw=true)
6. Open Putty and set the following configuration:
     - **Host Name:** raspberrypi.mshome.net
     - **Port:** 22
     - **Connection Type:** SSH
     - In the *Connection* category (left side), expand *SSH*, click on *X11* and enable **X11 forwarding**.
     - (Optional) I would recommend to save the settings in order to not repeating the same thing always we want to connect to the Pi via PuTTy.
![PuTTy configuration](https://github.com/alejompb/RaspberryPiTutorial/blob/master/putty.PNG?raw=true)
     - Click on *Open*. That will connect your laptop or computer to your Pi.
     - A PuTTy terminal will appear. Input the following login setup:
       + **Login as:** pi
       + **Password:** raspberry
       + Now you have accessed to your Pi! In order to start the GUI and make the process more intuitive type this command: _**startlxde**_
![PuTTy command](https://github.com/alejompb/RaspberryPiTutorial/blob/master/putty%20command.PNG?raw=true)
     - Now Xming will work as your Pi´s screen
     - Congratulations you can navigate within your Pi, use internet and download your programs directly, and all that using your computer´s keyboard and mouse!

![Pi's screen through Xming](https://github.com/alejompb/RaspberryPiTutorial/blob/master/working.PNG?raw=true)


****


#Different Pi project implementations

With the Raspberry Pi you can do almost anything you want, taking into consideration its hardware limits, all in all it’s a simple computer so the range of possibilities is vast.
In terms of how to start thinking in a Raspberry Pi project here I explain two main approaches:

+ Create or download a program or application from your Pi´s OS
For that we will need everything we have done in the section How to get started and then, starting from that point, download and run the program we want. This is the same concept as having a new computer, but infinitely smaller, simpler and extremely cheap.

+ Install the environment directly into your SD card.
This approach will be based on the same steps as in the section How to get started but instead of burning Raspbian or any other similar OS, we will install an OS that already has the functionality that we want.

In order for you to feel the difference more clearly I will show projects that do the same thing but from different approaches. Special thanks to **PiMyLife**


## Example of project using Raspbian
The details of this simple project can be found [here](https://pimylifeup.com/raspberry-pi-dosbox/). 
In this case all we have to do is following the same steps as before. Once we have the Pi´s display in Xming we will start with the tutorial from **PiMyLife**.

The result should loook like this:
![Outrun-dosbox](https://github.com/alejompb/RaspberryPiTutorial/blob/master/dosbox.PNG?raw=true)

## Example of project using a specialized OS

The details of this project can be found [here](https://pimylifeup.com/raspberry-pi-emulator/).
In this case we will follow the steps mentioned in [How to get started section](#How to get started). The changes are the following:
+ Instead of downloading and installing in the SD card Raspbian we will download [Pi Emulator OS](https://retropie.org.uk/download/).
+ Complete step 1
+ Complete step 2 and install Pi Emulator OS, instead of Raspbian, in your Raspberry Pi.
+ Complete steps 3, 4, 5 and 6.

Now we can start the **PiMyLife** tutorial from *step 3.3*.





****


I hope you have now a better idea about what is a Raspberry Pi, how to connect to the Pi through a SSH connection without using any extra hardware (such as a monitor, keyboard or mouse), not even a router, and the different approaches you may encounter in Raspberry Pi projects.

