CIS551 - Homework 3, Phase 1

Team members:
Aditya Deshpande
Aryaa Gautam
Aniruddha Rajashekhar
Di Wu

Tools used: Wireshark, tcptrace, ffmpeg, ffplay

1. Steps to Execute

The packets are captured using Wireshark. 
- Run wireshark, select interface wlan0.
- Apply filter ip.src==192.168.1.1 and tcp.port==5555
- Start Capture
- Save the file as video_capture.pcap after stopping the capture
- Run "make attack" to play the captured video

2.  Implementation Details:

Start the capture on the wireshark using the above mentioned filter and save the captured packets to the file "video_capture.pcap"

The script performs the following actions:

- Runs tcptrace -e on the captured packet to get rid of the tcp headers.
>>>tcptrace -e video_capture.pcap

-  ".dat" files will be generated for every communication from 192.168.1.1:5555.

- Converts the .dat file generated by tcptrace to a file with .avi format using the following command:
>>>ffmpeg -f h264 -i am2an_contents.dat video_capture.avi

-Plays the video using the following command:
>>>ffplay video_capture.avi
