## Preamble

This is a visual guide on how to compile and debug the latest libwdi/Zadig using the __freely available__ Visual Studio 2013 Community Edition. If you follow this guide through, you should end up with a setup that is extremely close to the one that I, the developer, have been using for all my libwdi and Zadig development, and which should allow you to troubleshoot Zadig crashes for instance.

This visual guide does not assume any familiarity with any of the development tools mentioned below. Even if you don't know anything about development, if you follow these steps through, you should be in a position to compile, run and debug the application as if you were a well-seasoned developer.

Finally, it should be noted that, because libwdi and Zadig and OSI-licensed Open Source projects (LGPL v2.1 and GPL v3 respectively), you are __fully entitled__ to download and install Visual Studio 2013 Community Edition to build and troubleshoot the project, no matter whether you are an individual doing it at home or an enterprise user doing it within your company.

## Before Installing

The installation of Visual Studio and the WDK will require between 3 to 4 GB of disk space for the downloaded files, and about the same for the applications. Thus, if you are not able or willing to spare 8 GB of disk space, you should not proceed.

Since the installation files will be downloaded from the internet, you will need to also consider the time it will take to download about 4 GB worth of data for the installer. If you have a slow connection, it might take a couple hours or more to complete this installation.

Also, this whole installation process will not work on Windows XP, as this version of Windows has been officially retired by Microsoft. If you are still running Windows XP, you should really consider upgrading!

## Installing Visual Studio and the WDK

### Visual Studio 2013 Community Edition

* Go to http://www.visualstudio.com/products/visual-studio-community-vs and click the _Download_ button.
* Save the `vs_community.exe` file in the location of your choice and run it.
* Proceed to the screen where it asks for the installation location:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_install_01.png)](https://github.com/pbatard/libwdi/wiki/images/vs_install_01.png)  
On this screen:
    * Check "_I agree to the License Terms and Privacy Policy_".
    * Uncheck "_Join the Visual Studio Experience Improvement Program_".
    * Click _Next_.
* On the next screen:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_install_02.png)](https://github.com/pbatard/libwdi/wiki/images/vs_install_02.png)  
    * __Unselect__ everything (as this will reduce the amount you need to download and libwdi only needs the base system).
    * Click _INSTALL_.
    * If a prompt asks you for elevated privileges, accept it.
* Depending on your connection and computer speed, the download and installation of the components should take a while:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_install_03.png)](https://github.com/pbatard/libwdi/wiki/images/vs_install_03.png)
* Once completed, you will see the following dialog:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_install_04.png)](https://github.com/pbatard/libwdi/wiki/images/vs_install_04.png)
    * __DO NOT__ select _LAUNCH_, but instead __close the dialog__, as we need to install the WDK before we can proceed.

### Windows Driver Kit (WDK) 8.1

Sadly, the WinUSB redistributable files, which libwdi needs to compile the library, are no longer provided as a standalone download by Microsoft, so we need to download and install the latest Windows Driver Kit, which is about 500 MB in size, to have them available.

* Click on http://go.microsoft.com/fwlink/?LinkID=317353 to download the WDK 8.1.
* Save the `wdksetup.exe` file in the location of your choice and run it.
* Specify the download location of your choice (or keep the default) and click _Next_.
* On the following screen:  
[![](https://github.com/pbatard/libwdi/wiki/images/wdk_install_01.png)](https://github.com/pbatard/libwdi/wiki/images/wdk_install_01.png)  
    * Because the installer detects that Visual Studio has been installed, it should automatically select the proper location, so just click _Next_.
* If asked to join the Customer Experience Improvement Program, select No:  
[![](https://github.com/pbatard/libwdi/wiki/images/wdk_install_02.png)](https://github.com/pbatard/libwdi/wiki/images/wdk_install_02.png)
* On the License Agreement screen:  
[![](https://github.com/pbatard/libwdi/wiki/images/wdk_install_03.png)](https://github.com/pbatard/libwdi/wiki/images/wdk_install_03.png)
    * Click _Accept_.
    * If a prompt asks you for elevated privileges, accept it.
* Let the download and installation process complete:  
[![](https://github.com/pbatard/libwdi/wiki/images/wdk_install_04.png)](https://github.com/pbatard/libwdi/wiki/images/wdk_install_04.png)
* Close the final screen:
[![](https://github.com/pbatard/libwdi/wiki/images/wdk_install_05.png)](https://github.com/pbatard/libwdi/wiki/images/wdk_install_05.png)

## Launching Visual Studio and fetching the latest git sources

### First Visual Studio Startup

* Go to _Start_ &rarr; _All Programs_ &rarr; _Visual Studio 2013_ &rarr; _Visual Studio 2013_ or (Windows 8) go to search and type _Visual Studio_ to launch Visual Studio 2013.
* On the sign in screen:  
[![](https://github.com/pbatard/libwdi/wiki/images/ws_startup_01.png)](https://github.com/pbatard/libwdi/wiki/images/ws_startup_01.png)
    * For the _Development Settings:_ dropdown, select `Visual C++`.
    * Click _Not now, maybe later._
* On the next screen:  
[![](https://github.com/pbatard/libwdi/wiki/images/ws_startup_02.png)](https://github.com/pbatard/libwdi/wiki/images/ws_startup_02.png)
    * Select the colour scheme that you prefer.
    * Click _Start Visual Studio_.
* Wait for Visual Studio to be ready:  
[![](https://github.com/pbatard/libwdi/wiki/images/ws_startup_03.png)](https://github.com/pbatard/libwdi/wiki/images/ws_startup_03.png)

### Cloning the latest libwdi source

Since git is integrated in Visual Studio 2013, there's no need to install a third party client to download the latest sources from github.

* In the main Visual Studio window, on the left handside:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_git_01.png)](https://github.com/pbatard/libwdi/wiki/images/vs_git_01.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<sup>(Click on the image for bigger size)</sup>
    * Select _Local Git Repositories_ and make sure the _Clone_ entry is selected.
    * Enter `https://github.com/pbatard/libwdi.git` for the first field (the libwdi source repository on github).
    * If desired, change the local destination directory.
    * Click _Clone_.
* The libwdi source will be retrieved from the internet:  
[![Git source retrieval](https://github.com/pbatard/libwdi/wiki/images/vs_git_02.png)](https://github.com/pbatard/libwdi/wiki/images/vs_git_02.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<sup>(Click on the image for bigger size)</sup>
* Eventually a new `libwdi` Local Git Repository will be listed:  
[![Git source retrieval](https://github.com/pbatard/libwdi/wiki/images/vs_git_03.png)](https://github.com/pbatard/libwdi/wiki/images/vs_git_03.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<sup>(Click on the image for bigger size)</sup>
    * Double Click on the `libwdi` repository.
* Now the main Visual Studio solution file for this project (`libwdi.sln`) should be listed:  
[![Git source retrieval](https://github.com/pbatard/libwdi/wiki/images/vs_git_04.png)](https://github.com/pbatard/libwdi/wiki/images/vs_git_04.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<sup>(Click on the image for bigger size)</sup>
    * Double Click on `libwdi.sln`.
* Finally, click on the _Solution Explorer_ tab at the bottom left (circled), so that you can navigate the source files:
[![Git source retrieval](https://github.com/pbatard/libwdi/wiki/images/vs_git_05.png)](https://github.com/pbatard/libwdi/wiki/images/vs_git_05.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<sup>(Click on the image for bigger size)</sup>
    * Double Click on `libwdi.sln`.

__Note:__ The above only needs to be done once. On subsequent startups of Visual Studio, you will just need to select `libwdi` from the the list of recent projects.