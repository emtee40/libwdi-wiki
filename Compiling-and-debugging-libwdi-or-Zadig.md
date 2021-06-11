## Preamble

This is a visual guide on how to compile and debug the latest libwdi/Zadig using the __freely available__ Visual Studio 2019 Community Edition. If you follow this guide through, you should end up with a setup that is extremely close to the one that I, the developer, have been using for all my libwdi and Zadig development, and which should allow you to troubleshoot Zadig crashes for instance.

This visual guide does not assume any familiarity with any of the development tools mentioned below. Even if you don't know anything about development, if you follow these steps through, you should be in a position to compile, run and debug the application as if you were a well-seasoned developer.

Finally, it should be noted that, because libwdi and Zadig and OSI-licensed Open Source projects (LGPL v2.1 and GPL v3 respectively), you are __fully entitled__ to download and install Visual Studio 2019 Community Edition to build and troubleshoot the project, no matter whether you are an individual doing it at home or an enterprise user doing it within your company.

## Before Installing

The installation of Visual Studio and the WDK will require between 3 to 4 GB of disk space for the downloaded files, and about the same for the applications. Thus, if you are not able or willing to spare 8 GB of disk space, you should not proceed.

Since the installation files will be downloaded from the internet, you will need to also consider the time it will take to download about 4 GB worth of data for the installer. If you have a slow connection, it might take a couple hours or more to complete this installation.

Also, this whole installation process will not work on Windows XP, as this version of Windows has been officially retired by Microsoft. If you are still running Windows XP, you should really consider upgrading!

## Installing Visual Studio and the WDK

### Visual Studio 2019 Community Edition

* Go to https://www.visualstudio.com/vs/community/ and click the _Download_ button.
* Save the `vs_community_###.exe` file in the location of your choice and run it.
* Proceed to the screen where it asks for the installation location:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_install_01.png)](https://github.com/pbatard/libwdi/wiki/images/vs_install_01.png)  
On this screen:
    * Check "_I agree to the License Terms and Privacy Policy_".
    * Uncheck "_Join the Visual Studio Experience Improvement Program_".
    * Click _Next_.
* On the next screen:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_install_02.png)](https://github.com/pbatard/libwdi/wiki/images/vs_install_02.png)  
    * __Unselect__ everything (as this will reduce the amount you need to download &mdash; libwdi only needs the base system).
    * Click _INSTALL_.
    * If a prompt asks you for elevated privileges, accept it.
* Depending on your connection and computer speed, the download and installation of the components should take a while:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_install_03.png)](https://github.com/pbatard/libwdi/wiki/images/vs_install_03.png)
* Once completed, you will see the following dialog:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_install_04.png)](https://github.com/pbatard/libwdi/wiki/images/vs_install_04.png)
    * __DO NOT__ select _LAUNCH_, but instead __close the dialog__, as we need to install the WDK before we can proceed.

### WDK 8 Redistributables

For its installation on Windows 8 or earlier (this is not needed on Windows 10 or later), WinUSB requires the provision of some redistributable files, that are part of the WDK for Windows 8.

Thankfully, Microsoft now provides those as a standalone MSI packaage, which you can download [here](https://go.microsoft.com/fwlink/p/?LinkID=253170).

You should therefore download the package above and install it to its default location `C:\Program Files (x86)\Windows Kits\8.0\`.

## Launching Visual Studio and fetching the latest libwdi source

### First Visual Studio Startup

* Launch Visual Studio 2019.
* On the sign in screen:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_startup_01.png)](https://github.com/pbatard/libwdi/wiki/images/vs_startup_01.png)
    * For the _Development Settings:_ dropdown, select `Visual C++`.
    * Click _Not now, maybe later._
* On the next screen:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_startup_02.png)](https://github.com/pbatard/libwdi/wiki/images/vs_startup_02.png)
    * Select the colour scheme that you prefer.
    * Click _Start Visual Studio_.
* Wait for Visual Studio to be ready:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_startup_03.png)](https://github.com/pbatard/libwdi/wiki/images/vs_startup_03.png)

### Cloning the latest libwdi source

Since git is integrated in Visual Studio 2019, there's no need to install a third party client to download the latest sources from github.

* In the main Visual Studio window, on the left handside:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_git_01.png)](https://github.com/pbatard/libwdi/wiki/images/vs_git_01.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<sup>(Click on the image for bigger size)</sup>
    * Select _Local Git Repositories_ and make sure the _Clone_ entry is selected.
    * Enter `https://github.com/pbatard/libwdi.git` for the first field (the libwdi source repository on github).
    * If desired, change the local destination directory.
    * Click _Clone_.
* The libwdi source will be retrieved from the internet:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_git_02.png)](https://github.com/pbatard/libwdi/wiki/images/vs_git_02.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<sup>(Click on the image for bigger size)</sup>
* Eventually a new `libwdi` Local Git Repository will be listed:  
[![Git source retrieval](https://github.com/pbatard/libwdi/wiki/images/vs_git_03.png)](https://github.com/pbatard/libwdi/wiki/images/vs_git_03.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<sup>(Click on the image for bigger size)</sup>
    * Double Click on the `libwdi` repository.
* Now the main Visual Studio solution file for this project (`libwdi.sln`) should be listed:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_git_04.png)](https://github.com/pbatard/libwdi/wiki/images/vs_git_04.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<sup>(Click on the image for bigger size)</sup>
    * Double Click on `libwdi.sln`.
* Finally, click on the _Solution Explorer_ tab at the bottom left (circled), so that you can navigate the source files:
[![](https://github.com/pbatard/libwdi/wiki/images/vs_git_05.png)](https://github.com/pbatard/libwdi/wiki/images/vs_git_05.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<sup>(Click on the image for bigger size)</sup>
    * Double Click on `libwdi.sln`.

__Note:__ The above only needs to be done once. On subsequent startups of Visual Studio, you will just need to select `libwdi` from the the list of recent projects.

## Compiling libwdi and debugging Zadig

### Compiling

Now we are finally set to compile and debug libwdi applications. However, we need to modify one of the source files because the only driver we have available (through the WDK 10 installation) is WinUSB, and by default, libwdi also expects the libusb-win32 and libusbK drivers to be available.

Rather than ask you to download and install these drivers, we are just going to tell libwdi to ignore them:

* Expand `embedder` &rarr; `Header Files` and double click on `config.h` to open it in the Visual Studio source editor:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_compile_01.png)](https://github.com/pbatard/libwdi/wiki/images/vs_compile_01.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<sup>(Click on the image for bigger size)</sup>
* Navigate to the following section:  
```
/* embed libusb0 driver files from the following location */
#ifndef LIBUSB0_DIR
#define LIBUSB0_DIR "D:/libusb-win32"
#endif

/* embed libusbK driver files from the following location */
#ifndef LIBUSBK_DIR
#define LIBUSBK_DIR "D:/libusbK/bin"
#endif

/* embed user defined driver files from the following location */
#ifndef USER_DIR
 #define USER_DIR "C:/signed-driver"
#endif
```  
and change it to (add `//` at the beginning of 3 lines):  
```
/* embed libusb0 driver files from the following location */
#ifndef LIBUSB0_DIR
//#define LIBUSB0_DIR "D:/libusb-win32"
#endif

/* embed libusbK driver files from the following location */
#ifndef LIBUSBK_DIR
//#define LIBUSBK_DIR "D:/libusbK/bin"
#endif

/* embed user defined driver files from the following location */
#ifndef USER_DIR
 //#define USER_DIR "C:/signed-driver"
#endif
```  
You should end up with something similar to this:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_compile_02.png)](https://github.com/pbatard/libwdi/wiki/images/vs_compile_02.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<sup>(Click on the image for bigger size)</sup>
* In the menu, select _BUILD_ &rarr; _Build Solution_. The Output window should now fill up with something like this:  
```
1>------ Build started: Project: detect_64build, Configuration: Debug Win32 ------
2>------ Build started: Project: installer_x86, Configuration: Debug Win32 ------
3>------ Build started: Project: installer_x64, Configuration: Debug x64 ------
4>------ Build started: Project: getopt, Configuration: Debug Win32 ------
2>  installer.c
3>  installer.c
4>  getopt1.c
4>  getopt.c
4>  Generating Code...
5>------ Build started: Project: embedder, Configuration: Debug Win32 ------
4>  getopt.vcxproj -> C:\Source\Repos\libwdi\Win32\Debug\lib\getopt.lib
5>  embedder.c
3>  installer_x64.vcxproj -> C:\Source\Repos\libwdi\x64\Debug\helper\installer_x64.exe
2>  installer_x86.vcxproj -> C:\Source\Repos\libwdi\Win32\Debug\helper\installer_x86.exe
5>  embedder.vcxproj -> C:\Source\Repos\libwdi\libwdi\.msvc\\..\embedder.exe
6>------ Build started: Project: libwdi (static), Configuration: Debug Win32 ------
7>------ Skipped Build: Project: libwdi (dll), Configuration: Debug Win32 ------
7>Project not selected to build for this solution configuration 
6>  detected change for 'C:\Source\Repos\libwdi\Win32\Debug\helper\installer_x86.exe'
6>    EMBED  C:\Program Files (x86)\Windows Kits\10\redist\wdf\x86\WdfCoInstaller01011.dll (2015.03.30)
6>    EMBED  C:\Program Files (x86)\Windows Kits\10\redist\wdf\x86\winusbcoinstaller2.dll (2015.03.30)
6>    EMBED  C:\Program Files (x86)\Windows Kits\10\redist\wdf\x64\WdfCoInstaller01011.dll (2015.03.30)
6>    EMBED  C:\Program Files (x86)\Windows Kits\10\redist\wdf\x64\winusbcoinstaller2.dll (2015.03.30)
6>    EMBED  C:\Source\Repos\libwdi\Win32\Debug\helper\installer_x86.exe (2014.11.26)
6>    EMBED  C:\Source\Repos\libwdi\x64\Debug\helper\installer_x64.exe (2014.11.26)
6>    EMBED  C:\Source\Repos\libwdi\libwdi\winusb.inf.in (2014.11.25)
6>    EMBED  C:\Source\Repos\libwdi\libwdi\libusb0.inf.in (2014.11.25)
6>    EMBED  C:\Source\Repos\libwdi\libwdi\libusbk.inf.in (2014.11.25)
6>    EMBED  C:\Source\Repos\libwdi\libwdi\winusb.cat.in (2014.11.25)
6>    EMBED  C:\Source\Repos\libwdi\libwdi\libusb0.cat.in (2014.11.25)
6>    EMBED  C:\Source\Repos\libwdi\libwdi\libusbk.cat.in (2014.11.25)
6>  vid_data.c
6>  tokenizer.c
6>  pki.c
6>  logging.c
6>  libwdi_dlg.c
6>  libwdi.c
6>  Generating Code...
6>  libwdi_static.vcxproj -> C:\Source\Repos\libwdi\Win32\Debug\lib\libwdi.lib
8>------ Build started: Project: wdi-simple, Configuration: Debug Win32 ------
9>------ Build started: Project: zadic, Configuration: Debug Win32 ------
10>------ Build started: Project: zadig, Configuration: Debug Win32 ------
11>------ Build started: Project: inf-wizard, Configuration: Debug Win32 ------
11>  inf_wizard.c
10>  zadig_net.c
9>  zadic.c
8>  wdi-simple.c
10>  profile.c
10>  zadig.c
9>  zadic.vcxproj -> C:\Source\Repos\libwdi\Win32\Debug\examples\zadic.exe
8>  wdi-simple.vcxproj -> C:\Source\Repos\libwdi\Win32\Debug\examples\wdi-simple.exe
10>  zadig_parser.c
10>  zadig_stdlg.c
10>  Generating Code...
10>  zadig.vcxproj -> C:\Source\Repos\libwdi\Win32\Debug\examples\zadig.exe
11>  inf_wizard.vcxproj -> C:\Source\Repos\libwdi\Win32\Debug\examples\inf-wizard.exe
========== Build: 10 succeeded, 0 failed, 0 up-to-date, 1 skipped ==========
```

If you don't get any `failed` projects then __congratulations__: you have just rebuilt libwdi and Zadig from the latest sources!

### Debugging

Let's say you have been running the release version of Zadig, and experienced a crash. With the version that you just recompiled above, you should be able to help pinpoint where exactly in the code the problem might be located, which is of __tremendous__ help for the developers.

To do just that:

* In the solution explorer, expand `examples` and right click on `zadig`:
[![](https://github.com/pbatard/libwdi/wiki/images/vs_debug_01.png)](https://github.com/pbatard/libwdi/wiki/images/vs_debug_01.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<sup>(Click on the image for bigger size)</sup>
    * In the menu that appears, select _Set as StartUp Project_.
    * After that, click on the _Local Windows Debugger_ button at the top (circled).
* Because Zadig is an application that requires elevated privileges, and Visual Studio was not started as administrator, you will get the following prompt:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_debug_02.png)](https://github.com/pbatard/libwdi/wiki/images/vs_debug_02.png)
    * Click on _Restart under different credentials_.
* Once Visual Studio has relaunched, click on click on the _Local Windows Debugger_ button again. This time the application will launch in debug mode:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_debug_03.png)](https://github.com/pbatard/libwdi/wiki/images/vs_debug_03.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<sup>(Click on the image for bigger size)</sup>
* From there you can proceed to testing for problems as you would with the regular application, except that if you encounter a condition where the application is about to crash, you will be presented with the following dialog:  
[![](https://github.com/pbatard/libwdi/wiki/images/vs_debug_04.png)](https://github.com/pbatard/libwdi/wiki/images/vs_debug_04.png)
    * If that happens, select _Break_.
* Once you have issued a break, the debugger allows you to pinpoint the location of the code where the most likely cause is located, as well as explore the value of some of the code variables. To access the relevant section of code then, you should ensure that the _Call Stack_ tab at the bottom is the current one selected and in the list from the _Call Stack_, you would usually select one of the topmost entry. If you double click on it, it should then take you close to the line in the source that is the likely culprit. For instance, in the following screenshot, the line just above the arrow is the cause of the crash:
[![](https://github.com/pbatard/libwdi/wiki/images/vs_debug_05.png)](https://github.com/pbatard/libwdi/wiki/images/vs_debug_05.png)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<sup>(Click on the image for bigger size)</sup>

Of course, if you do get a crash in the debugger, you probably want to contact the developer of the application so that they can guide you to the information that is likely to be most relevant.

