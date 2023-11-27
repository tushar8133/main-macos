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
| `shift` + `command` + `g` | Goto folder (~ user folder) |
| `ctrl` + `command` + `space` | emoticons / smiley / icons |
| `command` + `option` + `shift` + `esc` | quit apps one by one |
| `defaults write com.apple.desktopservices DSDontWriteNetworkStores true` | DS_Store |
| hover on maximize button | split screen |
| right click on speaker icon next to search bar | picture in picture |
| startup hidden items location for Users | `/Users/tusharkumar/Library/LaunchAgents/` |
| startup hidden items location for System | `/Library/LaunchDaemons`  |
| copy full path | right click and open context menu, now press OPTION key |
| open pkg file | `pkgutil --expand ./filename ./outputfolder` |


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
- https://github.com/ytdl-org/youtube-dl (HomeBrew)
- https://github.com/section83/MacYTDL
- https://github.com/alb12-la/KBOS
- https://github.com/peazip/PeaZip
- https://github.com/TheTorProject/gettorbrowser
- https://github.com/ganeshrvel/openmtp
- https://github.com/HandBrake/HandBrake

# youtube-dl
### zoom video
- open zoom meeting with passcode.
- open network tab and filter for `mp4`
- something like this will be there `https://ssrweb.zoom.us/cmr/replay/.../Recording_1920x1080.mp4`
- Sometimes there might be 2 streams, one for camera video and other for screen sharing.
- copy full `Request URL` and paste in below code.
- copy whole `Cookie` and paste in below code.

```
youtube-dl --output "FILENAME_HERE" --referer "https://zoom.us/" \
--add-header "cookie: PASTE_COOKIE_HERE" \
"PASTE_REQUEST_URL_HERE"
```

# Finder
- open finder window `option` + `command` + `space` 
- open finder from terminal `open .`
- toggle hidden files `shift` + `command` + `.`
- two finder instances: drag the tab outside
- Set default folder > `Finder` > `Settings` > `General` > `New Finder Window show`
- `Settings` > `Advanced` > `Show all filename extensions`
- `View` > `Show Status Bar`
- `View` > `Show Path Bar`
- `View` > `Show View Options (⌘ + J)`
- `Go` > Shortcuts to jump to specific folders

# Screenshot
- Auto save to _Pictures_ instead of _Desktop_
- Press `command + shift + 5`
- Click `Options`
- Choose `Other Locations...`


# ExifTool

https://exiftool.org

#### To increment/decrement time taken

`exiftool “-DateTimeOriginal+=0:0:0 15:0:0” -r folder_or_putadot`
#### File Rename

`exiftool '-filename<CreateDate' -d %Y%m%d_%H%M%S%%-c.%%ue -ext jpg -r folder_or_putadot`
- `-d` means “Set format for date/time values”.
- `%%-c` if two images have the same file name, then automatically increment. “-” before the “c” puts a dash before the copy number.
- `.%%ue` make existing extension uppercase
- `.%%le` make existing extension lowercase
- `-r` recursive

# NodeJs
- https://nodejs.org/en/about/previous-releases
- `.zprofile` or `.zshrc` paste `export PATH=/Users/tushar/node-v20.10.0-darwin-arm64/bin:$PATH`
- To avoid the error from vscode `"node" can’t be opened because Apple cannot check it for malicious software.`. Open the `bin` folder, right click on `node` executable, and select _Open_ once.

# HomeBrew
- Link https://brew.sh
- `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
- Check terminal instructions OR run these 2 commands
- `(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> ~/.zprofile`
- `eval "$(/opt/homebrew/bin/brew shellenv)"`
- Close all terminal instances.

## Homebrew > NVM
- After installing NVM from homebrew check instructions in the terminal
- OR paste below code in these files `~/.zshrc`, `~/.profile`, `~/.bash_profile`

```
export NVM_DIR="$HOME/.nvm"
[ -s "/opt/homebrew/opt/nvm/nvm.sh" ] && \. "/opt/homebrew/opt/nvm/nvm.sh"  # This loads nvm
[ -s "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm" ] && \. "/opt/homebrew/opt/nvm/etc/bash_completion.d/nvm"  # This loads nvm bash_completion
```

## Homebrew > GIT
- Regular homebrew install

## VSCode
- Preferred download is `silicon` over `universal` bundle.
- `Command + Shift + P` search `install 'code' command in PATH` ___OR___ follow below
- Paste below code to enable `code .` command from `zsh` terminal

For `~/.bash_profile`, `~/.zprofile`
```
# Add Visual Studio Code (code)
export PATH="\$PATH:/Applications/Visual Studio Code.app/Contents/Resources/app/bin"
```

## Different path files (not sure)
```
# for bash
source ~/.bashrc
source ~/.bash_profile

# for zsh
source ~/.zshrc
source ~/.zprofile
```
