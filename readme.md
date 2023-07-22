# MACOS
|   |   |
|---|---|
| dock icon `control` + `click` | show extra options |
| dock icon `option` + `click` | show hide window |
| dock icon `command` + `click` | open app location in finder |
| Download's dock icon `command` + `click` | show downloads folder in finder |
| xyz.app `control` + `click` + `open` | allows to run without malicious warning |
| `control` + `click` | open context menu |
| context menu + `option` | extra context menu |
| `shift` + `option` + `brightness/volume` | very small shifts |
| `command` + `option` + `esc` | Force quit running apps |
| `command` + `shift` + `3/4/5` | screenshot or recording |
| `file` + `spacebar` | quick preview jpg/pdf |
| `command` + `tab, Q` | quit application |
| `command` + `spacebar` | spotlight (screensharing, currency/temerature conversion, calc, flights) |
| `command` + `shift` + `.` | show hidden files |
| `shift` + `command` + `g` | Goto folder (~ user folder) |
| `ctrl` + `command` + `space` | emoticons |
| `command` + `option` + `shift` + `esc` | quit apps one by one |
| `defaults write com.apple.desktopservices DSDontWriteNetworkStores true` | DS_Store |
| hover on maximize button | split screen |
| right click on speaker icon next to search bar | picture in picture |
| startup hidden items location for Users | `/Users/tusharkumar/Library/LaunchAgents/` |
| startup hidden items location for System | `/Library/LaunchDaemons`  |
| copy full path | right click and open context menu, now press OPTION key |
| open pkg file | `pkgutil --expand ./filename ./outputfolder` |
| open finder from terminal | `cd yourpath` then `open .`|

## Remove Leftover "Context Menu" of Uninstalled Apps
* Keyboard > Shortcuts > Services
* ~/Library/Services
* Open that app > In the dock select Show in Finder > Delete that app >  Related context Items will be removed


## Remove hidden attribute from file or app

```
xattr -d com.apple.FinderInfo <filename>
xattr -px com.apple.FinderInfo
xattr -c
xattr -cr <folder>

getfileinfo <file/folder>
setfile -a V
aVbstclinmEdz

chflags -R nohidden <foldername>
chflags nohidden <filename>

Finder >> go back and forward to refresh

man chflags
man xattr
```

## Create FTP for file transfer

```
sudo -s launchctl load -w /System/Library/LaunchDaemons/ftp.plist

Enter password

Press 'option' + click 'Wifi' icon - to check IP address
```

## Hosts File Permission
```
sudo chflags uchg /etc/hosts
sudo chflags schg /etc/hosts

sudo chflags nouchg /etc/hosts
sudo chflags noschg /etc/hosts
```

# Caffeinate
`caffeinate -dimsu`

# Extract
`gunzip archive.xz` Unzips .xz extension file (will take some time in the background) and deletes the original file afterwards.

# Softwares
- https://github.com/MacPass/MacPass
- https://github.com/p0deje/Maccy
- https://github.com/exelban/stats
- https://github.com/section83/MacYTDL
- https://github.com/alb12-la/KBOS
- https://github.com/peazip/PeaZip
- https://github.com/TheTorProject/gettorbrowser
- https://github.com/ganeshrvel/openmtp
- https://github.com/HandBrake/HandBrake

