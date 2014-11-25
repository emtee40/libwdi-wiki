## Preamble

This is a visual guide on how to compile and debug the latest libwdi/Zadig using the __freely available__ Visual Studio 2013 Community Edition. If you follow this guide through, you should end up with a setup that is extremely close to the one that I, the developer, have been using for all my libwdi and Zadig development, and which should allow you to troubleshoot Zadig crashes for instance.

This visual guide does not assume any familiarity with any of the development tools mentioned below. Even if you don't know anything about development, if you follow these steps through, you should be in a position to compile, run and debug the application as if you were a well-seasoned developer.

Finally, it should be noted that, because libwdi and Zadig and OSI-licensed Open Source projects (LGPL v2.1 and GPL v3 respectively), you are __fully entitled__ to download and install Visual Studio 2013 Community Edition to build and troubleshoot the project, no matter whether you are an individual doing it at home or an enterprise user doing it within your company.

## Before Installing

The installation of Visual Studio and the WDK will require between 3 to 4 GB of disk space for the downloaded files, and about the same for the applications. Thus, if you are not able or willing to spare 8 GB of disk space, you should not proceed.

And since the installation files will be downloaded from the internet, you will need to also consider the time it will take to download about 4 GB worth of data for the installer. If you have a slow connection, it might take a couple hours or more to complete this installation.

## Installation Process

### Visual Studio 2013 Community Edition

* Go to http://www.visualstudio.com/products/visual-studio-community-vs and click the _Download_ button.
* Save the `vs_community.exe` file in the location of your choice.
* Run `vs_community.exe`
* Proceed to the screen where it asks for the installation location:  
![](https://github.com/pbatard/libwdi/wiki/images/vs_install_01.png)  
On this screen:
    * Check "_I agree to the License Terms and Privacy Policy_"
    * Uncheck "_Join the Visual Studio Experience Improvement Program_"

### Windows Driver Kit (WDK) 8.1 installation

