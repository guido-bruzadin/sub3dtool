#Setting up my Raspberry Pi

# Raspberry Pi #

This is how I set up my Raspberry Pi to view 3D contents.

Raspberry Pi, as you may know, is not very powerful. Most of its value lies on the VideoCore IV GPU. But not much programs can utilise its power.

Known programs who managed to do so are:
  * XBMC
  * Quake
  * omxplayer - a command line media player written especially for Raspberry Pi.

As far as I know, omxplayer's support for subtitles is not very matured while XBMC ASS subtile rendering is very slow.

Fortunately, XBMC have a 3D mode. Some people say adding 3DSBS to your video will make XBMC automatically activate 3D mode but apparently, it didn't work for me. (Example: Avatar.3DSBS.mkv)

The second option is to active 3D mode manually by go to System Settings and change Resolution to 960x1080p. This works great in Raspbmc while OpenELEC only render half the screen.

After further testing, I find out that doing **both** renaming and activating 3D mode manually will make it work.

So my only choice is to use Raspbmc for my Raspbmc.

## Setup Raspbmc ##

Go to [raspbmc.com](http://www.raspbmc.com/download/) and download an image file.
Two images are available:

  * **Network Image** - Requires an Internet connection through the Ethernet port. Somehow, it didn't work for me.
  * **Standalone Image** - Doesn't need an Internet connection.

So I download the **Standalone Image**, write it to my SD card:

```
gzip -d raspbmc-rc5-prebuilt.img.gz
sudo dd if=raspbmc-rc5-prebuilt.img of=/dev/sdb
```

First command decompress the downloaded file.

2nd command write the decompressed file to /dev/sdb which is my SD Card. **Note that all the data in /dev/sdb will be erased. So take some care.**

Next, I use GParted to resize the root partition to fill my SD Card. This is unnecessary since Raspbmc will do this automatically when in the first boot.
However, I think it's kind of slow, much slower than doing it in my laptop so I resize it beforehand. Raspbmc will still try to resize the partition though but it's much faster.

OK, Now I insert the SD Card to my Raspberry Pi, plug in the power: the installation process reboot 2 times. At the third boot, I'm greeted with XBMC screen.

I connect the Ethernet cable and allow XBMC to update itself. After update, There's an option for Wireless that is not there before. You can also connect to Wireless through NetworkManager plugin.

## Tweaking a little ##
### Overclock ###
First of all, Overclock. In Raspbmc there's an UI for you to do so. But unless you know what you're doing, don't adjust the over\_voltage option.


### 3D ###
As mentioned above, 3D settings: set Resolution to 960x1080p will activate 3D mode (SBS), 1920x1080p to normal.


### Shortcuts ###
A few shortcuts. Since going to the System Settings everytime to activate 3D mode is a real hassle. I add a little shortcut to my keyboard to bring up the Settings Screen. I did try to use "Resolution" function to change the resolution, but it didn't work.

To archieve this, edit keymap.xml

### Audio ###
Note that enable Audio passthrough would greatly lessen the burden on the CPU, thus improving playback performance. Check if your TV support this feature.


### Fonts ###
Fix the font problem. XBMC will render subtiles normally without making text thiner to fit SBS, thus the text will be quite fat, well, twice as fat.

To fix this, I use FreeSans as a base, downloaded from [GNU.org](http://www.gnu.org/software/freefont/) and make it slimmer using fontforge.

Then copy it to the SD Card. Located at /home/pi/.xbmc/media/Fonts

Choose the font in the Video Settings.

Edited fonts is available in Download, prefixed with "Hwi-" to prevent confict.