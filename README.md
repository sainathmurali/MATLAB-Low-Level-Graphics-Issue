# MATLAB-Low-Level-Graphics-Issue in Linux

### To run MATLAB with Hardware Renderer

First, disable Wayland if enabled.
Steps to disable Wayland:
* Open Wayland config file from /etc/gdm3/custom.conf (or /etc/gdm/custom.conf) with elevated permissions.
* Uncomment the line #WaylandEnable=false.
* Run the following command to restart gnome display manager

```
sudo systemctl restart gdm3
```

Install a few graphics-related packages. Change the apt-get for your distro's package manager.
For Ubuntu,
```
sudo apt-get install lib64stdc++6:i386
sudo apt-get install mesa-utils
```
Then update some links (replace <matlab_installed_location> with the installation location of matlab; for example: <b>/usr/local/MATLAB/R20xxx</b>):

```
cd <matlab_installed_location>/sys/os/glnxa64/
sudo mv libstdc++.so.6 libstdc++.so.6.bak
sudo ln -s /usr/lib64/libstdc++.so.6  libstdc++.so.6
```

Then try one of the following 2 methods (if either of them not working properly, do both):
1)  Launch MATLAB with the following command in terminal

```
export JAVA_TOOL_OPTIONS="-Djogl.disable.openglarbcontext=1"; matlab
```


3)	Find matlab.desktop file; which can be found under /usr/share/applications/ (OR  /usr/local/share/applications/)
Inside the file, replace the line **Exec=........** with the following.

```
Exec=env JAVA_TOOL_OPTIONS="-Djogl.disable.openglarbcontext=1" matlab -desktop 
```
