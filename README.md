# vRun
Bash script that compiles, runs, and (optionally) showns waveform for verilog script.   
This repo specifically includes the vRun script and an example config file.

# Installation
Go to whatever repository you want to install this in, and run
```
git clone https://github.com/m-ruiz21/vRun.git
cd vRun
chmod +x vRun
./vRun -u
```
This will:
1) Clone repo into your directory
2) Enter vRun source code directory
3) Give permissions to run vRun
4) Update vRun and add it to PATH (so you can run it anywhere)

# Dependencies
**gtkwave**  - used to display waveforms
```
sudo apt install gtkwave
````
**XServer**  - windows X-Server (only if using wsl/wsl2)
```
To install, check out sourceforge.net/projects/vcxsrv
```
**iverilog** - verilog compiler
 ```
 sudo apt-get install iverilog
 ```
 # Configuration
vRun uses a vRun.conf file for configuration. It needs the configuration file to do anything.    
  
**important!!** make sure a config file is always in the same directory you're calling vRun from.  
  
It reads the file line by line and adds builds to associative array accordingly. To avoid malicious code being injected into the config file and run by run.sh with special permissions, it expects a Specific format. It's easy enough to follow if you want, but why?  
Just use the built in tools...  

# Options
 b {name} - Builds name  
         Notes: requied if you want to display waveform

 v - Display waveform

 p - Prints available builds

 a {name} - Adds build with given name  
         Notes: will add name assuming {name}Test.v and {name}.v exist

 d {name} - Deletes build with given name
 
 c - create default config file

 t - toubleshooting checks health / proper dependencies

 h - prints help screen / documentation
 
 # Troubleshooting
 Health Check
     vRun checks:  
     1) vRun.conf exists / is reachable by the program  
     2) iverilog is installed / can be found  
     3) gtkwave is installed / can be found  
     4) x server is running and the wsl can open up the display  

 X Server connection issues  
     Make sure the following options are selected when setting up XLaunch:  
     - Display number: 0  
     - &#9745; Start no client  
     - &#9745; Disable access control  
