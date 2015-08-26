Convert subtitle to 3D. Use with VLC or MPlayer or any player that properly supports ASS subtitle format.

This tool is made for GNU/Linux but is reportedly working fine with OS X (previously known as Mac OS X).

### Web-based tool ###
Since not everyone is able to compile and make use of the the software with ease, I decided to write a javascript version of the tool with limited functionality.

To use it, download the file `sub3dtool.js-x.x.tar.gz`, extract it and open the file `index.htm` (in your browser). Then follow the directions on the page. Make sure you have javascript enabled.

### Basic Usage ###
To compile from source code. Run in CLI:
```
wget http://sub3dtool.googlecode.com/files/sub3dtool-0.4.2.tar.gz
tar -xf sub3dtool-0.4.2.tar.gz
cd sub3dtool-0.4.2
make
./sub3dtool
```

Note that the above commands may change as later versions of the software are released.

To convert a subtitle to Side-by-Side, first **`cd`** to the folder you put the **sub3dtool** program. Then run:
```
./sub3dtool input.srt --3dsbs -o output.ass
```
Whereas **`input.srt`** is the path to the file you need to convert.

**`output.ass`** is the name of the file you want as the result.

**`--3dsbs`** indicates that you want to convert the subtitle to 3DSBS (Side-by-Side) format.


### Current Features ###
  * OSes: Linux (seem to work with Mac OS X Lion).
  * Input formats: **SRT** and **SSA/ASS**.
  * Output format: **ASS**, **SRT** (without 3D).
  * Side-By-Side.
  * Top-Bottom.
  * Color and font options.
  * Margins.
  * Unicode: UTF-8, UTF-16 and UTF-32 (input only)

### Changelog 0.4.x ###
  * Support for UTF-16 and UTF-32.
  * Partial SSA/ASS input format support.
  * SRT output module.
  * 2 way conversion between SRT and ASS.
  * Reverse 3D-converted subtitles with --no3d option.
  * Bugfixes.

### Changelog 0.3.x ###
  * Command line options are reorganized.
  * New options: --screen, --align-top, --align-middle.
  * SRT: `<font color="#rrggbb">` tags are now supported.
  * Bugfixes.

### Additional informations ###
[Raspberry Pi](http://code.google.com/p/sub3dtool/wiki/RaspberryPi)

