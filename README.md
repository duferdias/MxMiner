# Minexcoin Mining App (MxMiner v0.20.1) by Racquemis

Minexcoin CPU & CUDA Miner

Binaries are available for Windows And Linux. 64 bit only.

Windows: CPU (SSE2,AVX,AVX2) & CUDA (Nvidia GPU) & OpenCL (AMD + Nvidia GPU)

Linux: (SSE2,AVX,AVX2) & CUDA (Nivida GPU)
```
Pools: eu.minexpool.nl
       asia.minexpool.nl
```       

Instructions for Windows
=========================

Make sure you installed the latest version of 'Visual C++ 2013 Redistributable x64'. 
You can download it from the microsoft website.

Next, Edit the start_mining.bat file. The example below is for cpu minin

EU:       mxminer -l eu -u <Wallet Address> -p <Anything> -t <Number of Threads>
ASIA:     mxminer -l asia -u <Wallet Address> -p <Anything> -t <Number of Threads>

Example:
mxminer -l eu -u x123d56789A4C7c7F34k3 -t 6
mxminer -l eu -u x123d56789A4C7c7F34k3

Miner works best at 75% CPU utilization. Use Number of CPU Threads Minus 1. 
You also remove -t parameter for the miner to select the number of Threads automatically

CUDA (Nvidia GPU):
If you want to add cuda mining on top of CPU mining add the -cd parameter followed by your device id e.g.
mxminer -l eu -u x123d56789A4C7c7F34k3 -t 6 -cd 0
For a second GPU:
mxminer -l eu -u x123d56789A4C7c7F34k3 -t 6 -cd 0 1

OPENCL (Nvidia & AMD GPU):
add the -oi parameter to the bat file to get info about all the available opencl devices on your system
Write down the platform number and the device numbers of each device you want to mine with
You can only mine with devices from a single platform. if you want to mine devices of multiple platforms you must start
a seperate instance for each platform.

set the -op parameter to the platform number
next set the -od parameter with the device numbers.
If you want to mine with device #0 and device #1 you type: -od 0 1
Optionally you can  set the number of threads for each device with the -ot command
-ot 1 1 sets the threads for both devices to one. This means at a single instance of the solver will run on the card.
If you see that your GPU isn't loaded fully set -ot 2 2 and try again.

Example for two devices one platform number 0 with two threads
mxminer -l eu -u x123d56789A4C7c7F34k3 -t 6 -op 0 -od 0 1 -ot 2 2

The miner supports the AVX and AVX2 instruction for faster mining. These are selected automatically to the capabilities of your CPU.
Use parameter -e to force SSE2 or AVX mode
SSE2:    -e 1
AVX:     -e 2
AVX2:    -e 3

Instructions for Linux (tested with Ubuntu 16.04)
================================================
- Right click the binary and click properties
- Navigate to the Permissions menu
- Under Execute, check the box "Allow executing file as program" if it isn't checked
- Do the same or start_mining.sh
- Edit the .sh file in gpedit, change the address and the number of threads

 ./mxminer -l eu -u <Wallet Address> -p <Anything> -t <Number of Threads>

- Run the miner by starting the start_mining.sh file (from terminal)

Notes
=====
Standard port is 9999 
To use the alternative port 3333 start the miner with the -z parameter

If you have problems reconnecting on connection loss. consider using a bat file to automatically restarts the miner when it exits
Use the respawnMiner.bat file for this. Don't forget to change the mining parameters in this file first. Also do not remove the -ed parameter.
This parameter makes sure the process is terminated when connection is lost, making sure the bat file can do it's work.

There is also an API which can be used to restart the miner externally.




