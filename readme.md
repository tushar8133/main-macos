# MACOS
|   |   |
|---|---|
| `^` + `↓` | Show Current App's All Windows |
| `^` + `F3` | Show Current App's All Windows |
| dock icon `control` + `click` | show extra options |
| dock icon `option` + `click` | show hide window |
| dock icon `command` + `click` | open app location in finder |
| Download's dock icon `command` + `click` | show downloads folder in finder |
| xyz.app `control` + `click` + `open` | allows to run without malicious warning |
| `control` + `click` | open context menu |
| context menu + `option` | extra context menu |
| `shift` + `option` + `brightness/volume` | very small shifts |
| `command` + `tab, Q` | quit application |
| `command` + `option` + `esc` | Force quit running apps |
| `command` + `option` + `shift` + `esc` | quit apps one by one |
| `command` + `shift` + `3/4/5` | screenshot or recording |
| `file` + `spacebar` | quick preview jpg/pdf |
| `command` + `spacebar` | spotlight (screensharing, currency/temerature conversion, calc, flights) |
| `shift` + `command` + `g` | Goto folder (~ user folder) |
| `ctrl` + `command` + `space` | emoticons / smiley / icons |
| `defaults write com.apple.desktopservices DSDontWriteNetworkStores true` | DS_Store |
| hover on maximize button | split screen |
| right click on speaker icon next to search bar | picture in picture |
| startup hidden items location for Users | `/Users/tusharkumar/Library/LaunchAgents/` |
| startup hidden items location for System | `/Library/LaunchDaemons`  |
| copy full path | right click and open context menu, now press OPTION key |
| open pkg file | `pkgutil --expand ./filename ./outputfolder` |
| restart `finder` | `option` + `right click` + `relaunch` |
| laptop start sound | seach in `settings` for `startup sound` |


# `.zprofile` file contents
```
export PATH="$PATH:/Users/tushar/Setups/node-v20.11.0-darwin-arm64/bin"

export PATH="$PATH:/Users/tushar/Setups/mongo"

export PATH="$PATH:/Users/tushar/Setups/CMake.app/Contents/bin"

export PATH="$PATH:/Applications/Docker.app/Contents/Resources/bin"

alias 7z="/Users/tushar/Setups/7z2407-mac/7zz"

alias nginx="/Users/tushar/Setups/nginx/nginx-1.26.3-arm64-darwin"

alias code="/Users/tushar/Setups/vscode.app/Contents/Resources/app/bin/code"

alias heimdall="/Users/tushar/Setups/heimdall-frontend.app/Contents/MacOS/heimdall"

alias adb="/Users/tushar/Setups/adb/adb"

alias Ninja="/Users/tushar/Setups/ninja"

alias mysql="/Users/tushar/Setups/mysql-8.4.4-macos15-arm64/bin/mysql"

eval "$(/opt/homebrew/bin/brew shellenv)"
```


## Remove Leftover "Context Menu" of Uninstalled Apps
* Keyboard > Shortcuts > Services
* ~/Library/Services
* Open that app > In the dock select Show in Finder > Delete that app >  Related context Items will be removed

## xattr

```sh
ls -la // check @ symbol after file permissions (extended attribute)
xattr myfile // prints info
xattr -l myfile // prints more info
xattr -c myfile // remove all extended attributes
```

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
- https://github.com/ytdl-org/youtube-dl
- https://github.com/alb12-la/KBOS
- https://github.com/peazip/PeaZip
- https://github.com/TheTorProject/gettorbrowser
- https://github.com/ganeshrvel/openmtp
- https://github.com/HandBrake/HandBrake
- https://github.com/alienator88/Pearcleaner


# youtube-dl
```
curl -LO https://github.com/yt-dlp/yt-dlp/releases/download/2025.07.21/yt-dlp_macos
xattr -c yt-dlp_macos
sudo chmod a+rx yt-dlp_macos
sudo mv ./yt-dlp_macos /usr/local/bin/yt-dlp
yt-dlp --help
```

- `yt-dlp "https://www.youtube.com/watch?v=7E-cwdnsiow"` simply download
- `yt-dlp --list-formats "https://www.youtube.com/watch?v=7E-cwdnsiow"` to check available formats
- `yt-dlp --format 222 "https://www.youtube.com/watch?v=7E-cwdnsiow"` download with format code shared using --list-formats
- `yt-dlp --format 137+141 "https://www.youtube.com/watch?v=7E-cwdnsiow"` combine multiple formats
- `yt-dlp --format 22/17/18 <playlist_url>` in case of playlist, pass mutliple formats, so it picks whatever available for each video
- `yt-dlp -x "https://www.youtube.com/watch?v=7E-cwdnsiow"` just audio
- `yt-dlp -x --audio--formatormat mp3 "https://www.youtube.com/watch?v=7E-cwdnsiow"` just audio with format
- `yt-dlp --format best "https://www.youtube.com/watch?v=7E-cwdnsiow"` best quality format (both audio and video)
- `yt-dlp --format 'bestvideo[height<=1080]+bestaudio/best' "https://www.youtube.com/watch?v=7E-cwdnsiow"` to download highest quality
- `yt-dlp --format bestaudio "https://www.youtube.com/watch?v=7E-cwdnsiow"` audio-only with best quality
- `yt-dlp --format bestvideo+bestaudio "https://www.youtube.com/watch?v=7E-cwdnsiow"` merge different format
- `yt-dlp --format 'bestvideo,bestaudio' "https://www.youtube.com/watch?v=7E-cwdnsiow" -o '%(title)s.f%(format_id)s.%(ext)s'` download separate formats
- `yt-dlp --format mp4 "https://www.youtube.com/watch?v=7E-cwdnsiow"` download by extension
- `yt-dlp --min--formatilesize 100M <playlist_url>` download by file size
- `yt-dlp --max--formatilesize 100M <playlist_url>` download by file size
- `yt-dlp --write-description --write-info-json --write-annotations --write-sub --write-thumbnail "https://www.youtube.com/watch?v=7E-cwdnsiow"` download misc

##### zoom video
	# open zoom meeting with passcode.
	# open network tab and filter for `mp4`
	# something like this will be there `https://ssrweb.zoom.us/cmr/replay/.../Recording_1920x1080.mp4`
	# Sometimes there might be 2 streams, one for camera video and other for screen sharing.
	# copy full `Request URL` and paste in below code.
	# copy whole `Cookie` and paste in below code.
	
	yt-dlp \
	--output "FILENAME_HERE" \
	--referer "https://zoom.us/" \
	--add-header "cookie: PASTE_COOKIE_HERE" \
	"PASTE_REQUEST_URL_HERE"

##### vimeo video
	# either use --cookies-from-browser or --cookies
	# --referer is optional (it the page url which holds the video player)
	# --user-agent is optional (use whatever your browser is showing)
	# video url format could be "https://vimeo.com/123456789" or "https://player.vimeo.com/video/123456"
	
	# example 1
	yt-dlp "https://player.vimeo.com/video/123456"

	# example 2
	yt-dlp \
	--cookies-from-browser chrome \
	"https://player.vimeo.com/video/123456"

	# example 3
	yt-dlp \
	--cookies-from-browser chrome \
	--cookies "path/to/cookies.txt" \
	--referer "https://example.com/page" \
	--user-agent "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/108.0.0.0 Safari/537.36" \
	"https://vimeo.com/123456789"


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
- https://nodejs.org/download/release/v20.11.0/node-v20.11.0-darwin-arm64.tar.gz
- double click and extract
- write into `.zprofile` - `export PATH="$PATH:/Users/tushar/Downloads/node-v20.11.0-darwin-arm64/bin"`
- To avoid the error from vscode `"node" can’t be opened because Apple cannot check it for malicious software.`. Open the `bin` folder, right click on `node` executable, and select _Open_ once.

# HomeBrew
- Link https://brew.sh
- `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
- Check terminal instructions OR run these 2 commands
  - `(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> ~/.zprofile`
  - `eval "$(/opt/homebrew/bin/brew shellenv)"`
- Above commands will write below code inside `~/.zprofile`
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
- `brew install git`

## VSCode
- https://code.visualstudio.com/download
- Preferred download is `silicon` over `universal` bundle.
- write in `.zprofile` - `alias code="/Users/tushar/Setups/vscode.app/Contents/Resources/app/bin/code"`
- OR `Command + Shift + P` search `install 'code' command in PATH`
- Context Menu (Automator)
  - Open `Automator`
  - Select `Quick Action`
  - Search `Open Finder Items`
  - Drag it to the right column
  - Select Dropdown `Workflow receives current` > `"Automatic (files or folders)"`
  - Select Dropdown `in` > `"Finder.app"`
  - `Open with` Browse your application
  - `Save`
- Context Menu (Shortcuts)
  - Open `Shortcuts`
  - Select `Quick Actions`
  - Receive `Files and Folders` input from `Quick Actions`
  - Goto `Action Library`
  - Search `Run Shell Script`
  - Paste `open -n -b "com.microsoft.VSCodeInsiders" --args "$*"`
  - Shell: `zsh`
  - Input: Leave Blank
  - Pass Input: `as arguments`
  - Give this Shortcut a name on top
## Different path files (not sure)
```
# for bash
source ~/.bashrc
source ~/.bash_profile

# for zsh
source ~/.zshrc
source ~/.zprofile
```

# Localhost server between MacOs and iPhone
- Start a local server in nodejs to serve static content
- Place your file inside public folder and serve from there
- Lets say it is serving at `http://localhost:4000`
- Copy `IP address` from `MacOs` > `Wifi-Settings`
- On iPhone, open browser, and paste url as `http://YOUR_MAC_IP_ADDRESS:4000`


# Debug page on iPhone
- `iPhone` > `Settings` > `Safari` > `Advanced` > `Web Inspector` turn on
- `Mac` > `Safari` > `Preferences` > `Advanced` > `Show Develop menu in menu bar` check on
- Connect both through USB cable
- `iPhone` > Open website that you want to debug
- `Mac` > `Develop menu` > Select your iOS device
- Debug page will get open

# OS update
- Open Terminal
- `softwareupdate --list-full-installers`
- `softwareupdate --fetch-full-installer --full-installer-version 14.1.1`
- Open `Disk Utility` Format USB as `Format: "Mac OS Extended (Journaled)"` and `Scheme: "GUID Partition Map"`
- `sudo /Applications/Install\ macOS\ Sonoma.app/Contents/Resources/createinstallmedia --volume /Volumes/SanDisk`

# Before Installation
- Backup Browser bookmarks
- Backup Chrome Snippets
- Backup Notes
- Backup Sublime Notes
- Backup .zprofile, zsh

# While Installation
- Select "My computer is not connected to internet"

# After Installation
- Turn on Night Shift
- Battery show percentage
- Off "Slightly dim the display on battery"
- On "Prevent automatic sleeping on power adapter"
- Screenshot default location
- Finder settings
- Finder settings from top menu bar > Show Toolbar, Show Path Bar, Show Status Bar
- Login into app store
- Install whatsapp
- Login google without system wide login
- Safari > Settings > Advance > show full path
- Safari > Settings > Advance > show developer options
- Safari > Settings > General > Uncheck open safe files after downloading
- Keyboard > Autocorrect off
- Off Startup sound
- textEdit.app > Settings > plain text
- Keyboard > Keyboard Shortcuts > App Shortcuts > `+` > Menu Title `Paste and Match Style` > Shortcut > `ctrl + v`
- Trackpad > More Gestures > App Expose > Swipe Down with Three Fingers
- Keyboard > Key Shortcuts… > Mission Control > Mission Control > Switch to Desktop 1… (must have multiple blank workspace before implementing)


# remove .DS_Store from zip files
Replace Archive.zip name at two places.
```sh
zip -d Archive.zip __MACOSX/\* && zip -d Archive.zip \*/.DS_Store
```

# Check app's identifier name
```
codesign -dv "/Users/Downloads/Visual Studio Code.app"
# Identifier=com.microsoft.VSCode
```

# Safari Cache
- `System Settings` > `Privacy & Security` > `Full Disk Access` > `Terminal` turn on
- `sudo rm -rf ~/Library/Caches/com.apple.Safari`
- `sudo rm -rf ~/Library/Preferences/com.apple.Safari.plist`
- `sudo rm -rf ~/Library/Safari`

# PARALLES
- https://gist.github.com/gdurastanti/e79b1fae40a4eff14f5636b8994a89fc?permalink_comment_id=4083430
- https://github.com/utsanjan/PD-Runner
- https://github.com/LuYee6813/PD_Cracker
- https://www.reddit.com/r/MacCrack/comments/xqsg55/parallels_desktop_business_edition_v1801_crack/
- https://www.reddit.com/r/MacCrack/comments/10ada30/parallels_desktop_18_full_crack_activation_for/

# Chris Titus Finder Fixes

save as `fix-finder.sh` file and do `chmod +x fix-finder.sh`

```sh
#!/bin/sh -e

# Dated 2025-07-23 https://github.com/ChrisTitusTech/macutil/blob/main/scripts/system-setup/fix-finder.sh

printf "%b\n" "Applying global theme settings for Finder..."

# Set the default Finder view to list view
printf "%b\n" "Setting default Finder view to list view..."
defaults write com.apple.finder FXPreferredViewStyle -string "Nlsv"

# Configure list view settings for all folders
printf "%b\n" "Configuring list view settings for all folders..."
# Set default list view settings for new folders
defaults write com.apple.finder FK_StandardViewSettings -dict-add ListViewSettings '{ "columns" = ( { "ascending" = 1; "identifier" = "name"; "visible" = 1; "width" = 300; }, { "ascending" = 0; "identifier" = "dateModified"; "visible" = 1; "width" = 181; }, { "ascending" = 0; "identifier" = "size"; "visible" = 1; "width" = 97; } ); "iconSize" = 16; "showIconPreview" = 0; "sortColumn" = "name"; "textSize" = 12; "useRelativeDates" = 1; }'

# Clear existing folder view settings to force use of default settings
printf "%b\n" "Clearing existing folder view settings..."
defaults delete com.apple.finder FXInfoPanesExpanded 2>/dev/null || true
defaults delete com.apple.finder FXDesktopVolumePositions 2>/dev/null || true

# Set list view for all view types
printf "%b\n" "Setting list view for all folder types..."
defaults write com.apple.finder FK_StandardViewSettings -dict-add ExtendedListViewSettings '{ "columns" = ( { "ascending" = 1; "identifier" = "name"; "visible" = 1; "width" = 300; }, { "ascending" = 0; "identifier" = "dateModified"; "visible" = 1; "width" = 181; }, { "ascending" = 0; "identifier" = "size"; "visible" = 1; "width" = 97; } ); "iconSize" = 16; "showIconPreview" = 0; "sortColumn" = "name"; "textSize" = 12; "useRelativeDates" = 1; }'

# Sets default search scope to the current folder
printf "%b\n" "Setting default search scope to the current folder..."
defaults write com.apple.finder FXDefaultSearchScope -string "SCcf"

# Remove trash items older than 30 days
printf "%b\n" "Removing trash items older than 30 days..."
defaults write com.apple.finder "FXRemoveOldTrashItems" -bool "true"

# Remove .DS_Store files to reset folder view settings
printf "%b\n" "Removing .DS_Store files to reset folder view settings..."
# find ~ -name ".DS_Store" -type f -delete 2>/dev/null || true

# Show all filename extensions
printf "%b\n" "Showing all filename extensions in Finder..."
defaults write NSGlobalDomain AppleShowAllExtensions -bool true

# Set the sidebar icon size to small
printf "%b\n" "Setting sidebar icon size to small..."
# defaults write NSGlobalDomain NSTableViewDefaultSizeMode -int 1

# Show status bar in Finder
printf "%b\n" "Showing status bar in Finder..."
defaults write com.apple.finder ShowStatusBar -bool true

# Show path bar in Finder
printf "%b\n" "Showing path bar in Finder..."
defaults write com.apple.finder ShowPathbar -bool true

# Clean up Finder's sidebar
printf "%b\n" "Cleaning up Finder's sidebar..."
defaults write com.apple.finder SidebarDevicesSectionDisclosedState -bool true
defaults write com.apple.finder SidebarPlacesSectionDisclosedState -bool true
defaults write com.apple.finder SidebarShowingiCloudDesktop -bool false

# Restart Finder to apply changes
printf "%b\n" "Finder has been restarted and settings have been applied."
killall Finder
```

# check hash 
```sh
md5 /path/to/your/file
shasum -a 256 /path/to/your/file
shasum -a 512 /path/to/your/file
openssl dgst -sha3-256 /path/to/your/file
openssl dgst -sha3-512 /path/to/your/file
```

# IP Address
- Wifi `ipconfig getifaddr en0`
- Ethernet `ipconfig getifaddr en1`
- Local Address `hostname`
- External Address `curl ifconfig.me`
- Username `whoami`


# 7zip context menu
- Download 7zz
- xattr -c 7zz
- rename to 7z
- copy to /usr/local/bin/
- Automator > Quick Action > Files and Folders > Run Shell Script > as arguments
- 7z
  ```
  /usr/local/bin/7z a "$(dirname "$1")/7z-$(date -u "+%Y%m%d%H%M%S").7z" "$@" "-x!*.DS_Store" "-x!__MACOSX"
  ```
- zip
  ```
  /usr/local/bin/7z a --tzip "$(dirname "$1")/7z-$(date -u "+%Y%m%d%H%M%S").zip" "$@" "-x!*.DS_Store" "-x!__MACOSX"
  ```
