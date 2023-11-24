# MATLAB-Low-Level-Graphics-Issue in Linux

### To run MATLAB with Hardware Renderer
First, check if your graphics card is properly recognised by the OS.

Then try one of the following 2 methods:
1)  Launch MATLAB with the following command in terminal	
export JAVA_TOOL_OPTIONS="-Djogl.disable.openglarbcontext=1"; matlab

2)	Find matlab.desktop file; which can be found under /usr/share/applications/ (OR  /usr/local/share/applications/)
Inside the file, replace the line **Exec=........** with the following.

```
Exec=env JAVA_TOOL_OPTIONS="-Djogl.disable.openglarbcontext=1" matlab -desktop 
```
