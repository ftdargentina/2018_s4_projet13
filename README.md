# 2018_s4_projet13
Hand for Poppy in IMT Atlantique

USER GUIDE

1. Prepare the Raspberry

In order to control the robot and the electromagnet you will need a RaspberryPi 3, a GrovePi+
and a Grove Magnet module.

First you need to burn the Raspbian Image in a SD card, download the Raspbian Strech Lite from
https://www.raspberrypi.org/downloads/raspbian/
To burn the image we recommend to use the Etcher opensource software (https://etcher.io/)

2. Connect via SSH to the raspberry, for that:

Connect raspberry pi to laptop with Ethernet.
Go the edit connection setting.
Navigate to ipv4 option. Select method : shared to other computer.
Open a Terminal and type the following command to get the <RaspberryPi IP>:
	cat /var/lib/misc/dnsmasq.leases
To connect to the raspberry Open command prompt and type
	ssh pi@<RaspberryPi IP>

3. Install the Poppy Image

Once you are connected you have to install the image to control poppy, for that use the following commands
in a terminal

	curl -L https://raw.githubusercontent.com/poppy-project/raspoppy/master/raspoppyfication.sh | bash -s "poppy-torso"

It takes a while to install the image, once done you will have to restart the RaspberryPi and now, to connect via ssh
you will have to use the following command

	ssh poppy@<RaspberryPi IP>
	Password: poppy

Also, if you want to connect a keyboard and a screen to the Raspberry you can connect with:

	Login: poppy
	Password: poppy

4. Modify the image to use the GrovePi+

Now you need to install the GrovePi software to control the electromagnet, for that you need to use the following commands:

	cd /home/pi
	sudo git clone https://github.com/DexterInd/GrovePi
	cd /home/pi/Desktop/GrovePi/Script
	sudo chmod +x install.sh
	sudo ./install.sh
	cd
	sudo pip install smbus

Once everything is installed, there are some example codes in the repository

5. Execute reacTIVision and configure it.

If you are using the laptop from the laboratory, all the packages should be installed, if not install them with pip.
You have to connect the USB camera and the projector to the laptop, if the laptop does not recognize the projector, try restarting the laptop with the projector connected.

To lauch the reacTIVision software you have to use the following commands in the laboratory laptop.

	cd /usr/local/src/reacTIVision/linux
	sudo ./reacTIVision

Press h to show the help of the reacTIVision application and configure it with these values:
	finger sensitivity = 0
	finger size = 0
	finger blobs = 0
	blob size = 66
	gradient gate = 8-15
	tile size = 2-4
	shutter = 62

This values depend on the amount of light that strikes the board, try changing them until the reacTIVision application detects the ID of the pieces.

7. Execute the code to show the board

Use the following commands to get our repository and execute the code in the laptop

	cd /home/user/Documents/
	git clone https://github.com/ftdargentina/2018_s4_projet13.git
	cd /home/user/Documents/2018_s4_projet13/game_code/
	sudo python board.py

If everything is working you should see the board in the Reactable

8. Execute the code to control the robot

Connect to the RaspberryPi

	ssh poppy@<RaspberryPi IP>
	Password: poppy

Make sure that the raspberry is connected to the internet with an ethernet cable (it should have internet from the laptop if the laptop as the WiFi enabled).

Clone the repository and execute the file gestion.py to command the robot
	cd /home/pi
	git clone https://github.com/ftdargentina/2018_s4_projet13.git
	cd /home/pi/2018_s4_projet13/game_code/
	sudo python gestion.py

Troubleshooting: 

	Maybe you will need to use sudo to clone the repository, if that's the case, the board.py code will not be able to write the "data" file via ssh
	in every turn, this is indicated by an Access Denied error in the reactable code when you put a piece in the board. If that's the case, you can try:

		cd /home/pi/2018_s4_projet13/game_code/
		ls -l

	This will show if the file is only modifiable by root user, in that case you can remove it

		cd /home/pi/2018_s4_projet13/game_code/
		sudo rm data

	Make sure that you put a piece in the board to generate a new file, before running the code gestion.py that needs the file.

If everything works you should see an "Start!" text printed in the Terminal, followed by the virtual "Board" showing everything empty

9. Enjoy the game

To play you need to prepare something for poppy first, in the lab there is a table to hold Poppy, the metallic part should be right above the board, and it's pieces
to his right, in a particular position. After he tries to play and grab one of them you can perfectly tell where they should be (Below the electromagnet!)

Now you need to grab one of you pieces (The ones without metallic rings), you can select if you want to play first or if you want Poppy to do so with the two Buttons
labeled J1 and J2, just put one of your pieces in the buttons and should be ready to go.

If you selected J1, you can grab the pion that you used and play in a spot.
If you selected J2, lift the pion so you stop reseting the robot, and he will begin to play.

After the robot plays, and takes its time to return to the initial position, you can play again, until someones wins or there is a Tie.

After Poppy's Dab (When you win) or Poppy's handshake (in a Tie or Lose), you can reset the game and play again

10. Questions

If you have questions you can send us an email:

	federicodadam@gmail.com
	juanf.abt@gmail.com
	sola.francisco@hotmail.com
	louis.chauvet@imt-atlantique.net
	hang.zhang@imt-atlantique.net

Keep in mind that the addresses of imt-atlantique.net have a limited time of life.

Good Luck, and thank you for reading this guide.

2018, June 22.

