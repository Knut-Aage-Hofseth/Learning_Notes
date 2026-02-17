# Installing Windos programs in Linux  

Sometimes you need the actual Windows program and substitutes or Linux versions are not enough. One of the primary ways of running Windows applications on Linux is through Wine.  
> Wine (originally an acronym for "Wine Is Not an Emulator") is a compatibility layer capable of running Windows applications on several POSIX-compliant operating systems, such as Linux, macOS, & BSD. Instead of simulating internal Windows logic like a virtual machine or emulator, Wine translates Windows API calls into POSIX calls on-the-fly, eliminating the performance and memory penalties of other methods and allowing you to cleanly integrate Windows applications into your desktop.  

<div style="text-align: right"> 
<a href='https://www.winehq.org/'>"WineHQ"</a>
</div>  
  
  
I spent some time looking at this and is trying to justify it by saying I could perhaps use Visual Studio on Linux, but that is proving more troublesome than I had expected.

### Include 32 bit architecture
Wine has released with 64 bit architecture, and is installed as such if your os is 64-bit. This can, as of writing (May 2025), cause issues with older 32-bit programs installed in wine if the 32-bit extension is not installed.  
Wine claims that wow64 can run 32-bit programs, but I encountered errors with that.  
Because of this I reccomend installing in the command line where it is easier to install additional packages than with an GUI package manager.

## Installation in Fedora
If your distribution comes with a wine repo, the installtion is simple, just do the normal install app command line process. For wine it can cause trouble if you have multiple instances of wine installed through different means, flatpak or compiled version. (If you know how to do the last one you do not need my help). Check if there is wine already installed with
```
wine --version
```
Install wine with
```
sudo dnf install wine
```
Then install the 32-bit addition
```
sudo dnf install wine.i686
```
Check if the installation went well with
```
wine --version
```
It is recommended to also install *winetricks*
```
sudo dnf install winetricks
```

The installation steps are fundamentally the same for other Linux distributions, but you might have to look for repositories from WineHQ if the repositories are not standard.

I used this guide for a successful install: [How to install Wine on Fedora Linux](https://linuxcapable.com/how-to-install-wine-on-fedora-linux/)  

### Further use
Wine is a compatibility layer instead of a full VM. This means that there can be a lot of work to make some programs open and run. Some general steps to start with:
```
winecfg
```
opens a config window where you can fine-tune the wine instance, such as choosing which windows version to emulate.
*Winetricks* also often has a gui interface where you can create new wine instances, select the instance to install fonts, dll's and programs such as Internet Explorer versions that some programs rely on.  

#### Install throug Winetricks
Through winetricks, after selecting the appropriate wine instance, there is an option to run an arbitrary .exe file from anywhere in your system inside the wine instance.  
This allows you to download installers and install them into the wine emulation of windows.

### Final note on Visual Studio 2019
Looking for information online, I did not find any good news about installing Visual Studio in Wine. It seems that VS needs such an integration with windows that the more shallow emulation in Wine does not have all the needed windows parts. No full wine config for Visual Studio seems to exist. The only solution so far seem to be a full VM.
