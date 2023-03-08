# IoT-Temperature-Log
An IoT project connecting Arduino, Raspberry Pi, and AWS EC2 (cloud) to monitor and record temperatures. For this project the devices were placed inside a fridge with an LED that activates if the temperature is outside of set parameters. 

This project I designed three teensy boards to monitor and log the temperature of fridges. The idea is that they would be implemented into a healthcare setting to monitor drugs kept inside fridges. 
Drugs such as Box jellyfish anti venom are an example of a perishable drug that requires storage between 2 to 8 degrees. Any storage outside of these parameters the efficacy of the medication decreases. 
A key requirement for this project is to remain low cost and maximise automation. 
The temperature logs are stored locally on the raspyberry pi and are also accessible state wide via AWS. To try to avoid unnecessary waste the board also has an LED that activates as a visual warning that the fridge is outside of the set parameters. 

The hardware used in this project is listed. 
The raspberry Pi, 3x teensy boards with sensors. A windows computer for remote desktop access. And the network layer of WIFI and AWS. 

![image](https://user-images.githubusercontent.com/100078071/223633045-ecd76b9a-c68d-4e5b-ab0f-1de661f4b97f.png)

The Raspberry Pi drives the majority of automation and has python scripts for device 1, 2, and 3. Bluetooth.py prints the temperature on the terminal, in the Arduino serial log, and records it a text file called log.txt with a timestamp. 
Graph.py then takes that data and plots a graph using temperature and time on the axis. 
SCP graph and LOG sends a copy of the text and graph data to the AWS server for remote access. 
Mvbackup and backup graph then moves the file to a different backup directory with a timestamped name of time day month and year. 


The automation of this project is completed via cron jobs. The cron job activates a script at specific times to create the data and move the graph and files to their intended location.


