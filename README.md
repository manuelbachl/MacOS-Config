# MacOS-Config

## Disclaimer

**Use at your own risk and when you know what you're doing!**  
**I am not responsible for any weird behaviour or other problems you may run into after using any of those settings.**

## Undo changes

If you want to revert some settings, in most cases (all commands that start with `defaults write`), you can use the `defaults delete` command:

`defaults delete domain key`

Alternatively you can just toggle the flag you defined from `true` to `false` or vice versa.

But now just have a look at the huge list of possible tweaks and settings and pick the stuff you need.

## Terminal commands

### Gatekeeper [(Wikipedia)](https://en.wikipedia.org/wiki/Gatekeeper_(macOS))

#### Download option "Anywhere" in security system settings

| Command | Result |
| --- | --- |
| `$ sudo spctl --master-disable` | Readd "Anywhere" option |
| `$ sudo spctl --master-enable` | Remove "Anywhere" option (default) |

#### Gatekeepers Quarantine

| Command | Result |
| --- | --- |
| `$ sudo xattr -d com.apple.quarantine /Applications/PhpStorm.app` | Disable the “Are you sure you want to open this application?” dialog for specific app<br>(replace `PhpStorm.app` with the app u need) |
| `$ defaults write com.apple.LaunchServices LSQuarantine -bool false` | Disable the “Are you sure you want to open this application?” dialog globally |
| `$ defaults write com.apple.LaunchServices LSQuarantine -bool true` | Renable the “Are you sure you want to open this application?” dialog globally |

### Dock

#### Non-active apps

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.dock static-only -bool true`<br>`$ killall Dock` | Hide non-active apps in your Dock |
| `$ defaults write com.apple.dock static-only -bool false`<br>`$ killall Dock` | Show non-active apps in your Dock (default) |

#### Hidden apps

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.Dock showhidden -bool true`<br>`$ killall Dock` | Dull hidden apps in the Dock |
| `$ defaults write com.apple.Dock showhidden -bool false`<br>`$ killall Dock` | Do not dull hidden apps in the Dock (default) |

#### Highlight hover effect (stack)

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.dock mouse-over-hilite-stack -bool true`<br>`$ killall Dock` | Enable highlight hover effect for the grid view of a stack |
| `$ defaults write com.apple.dock mouse-over-hilite-stack -bool false`<br>`$ killall Dock` | Disable highlight hover effect for the grid view of a stack (default) |

#### Icon size

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.dock tilesize -int 36`<br>`$ killall Dock` | Set the icon size of Dock items to 36 pixels |

#### Minimize/maximize window

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.dock mineffect -string "scale"`<br>`$ killall Dock` | Change minimize/maximize window effect |
| `$ defaults write com.apple.dock minimize-to-application -bool true`<br>`$ killall Dock` | Minimize windows into their application’s icon |
| `$ defaults write com.apple.dock minimize-to-application -bool false`<br>`$ killall Dock` | Reset minimizing to default behaviour |
| `$ defaults write com.apple.dock launchanim -bool false`<br>`$ killall Dock` | Don’t animate opening applications from the Dock |
| `$ defaults write com.apple.dock launchanim -bool true`<br>`$ killall Dock` | Animate opening applications from the Dock (default) |

#### Indicator lights

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.dock show-process-indicators -bool true`<br>`$ killall Dock` | Show indicator lights for open applications in the Dock |
| `$ defaults write com.apple.dock show-process-indicators -bool false`<br>`$ killall Dock` | Show indicator lights for open applications in the Dock (default) |

#### Auto-hiding

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.dock autohide -bool true`<br>`$ killall Dock` | Automatically hide and show the Dock |
| `$ defaults write com.apple.dock autohide -bool false`<br>`$ killall Dock` | Don't automatically hide and show the Dock |
| `$ defaults write com.apple.dock autohide-delay -float 0`<br>`$ killall Dock` | Remove the auto-hiding Dock delay |
| `$ defaults write com.apple.dock autohide-time-modifier -float 0`<br>`$ killall Dock` | Remove the animation when hiding/showing the Dock |

### Mission Control, Dashboard, Launchpad

#### Mission Control

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.dock expose-animation-duration -float 0.1` | Speed up Mission Control animations |
| `$ defaults write com.apple.dock expose-group-by-app -bool false` | Don’t group windows by application in Mission Control |
| `$ defaults write com.apple.dock expose-group-by-app -bool true` | Group windows by application in Mission Control (default) |

#### Dashboard

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.dashboard mcx-disabled -bool true` | Disable Daschboard |
| `$ defaults write com.apple.dashboard mcx-disabled -bool false` | Enable Daschboard |
| `$ defaults write com.apple.dock dashboard-in-overlay -bool true` | Don’t show Dashboard as a Space |
| `$ defaults write com.apple.dock dashboard-in-overlay -bool false` | Show Dashboard as a Space (default) |
| `$ defaults write com.apple.dock mru-spaces -bool false` | Don’t automatically rearrange Spaces based on most recent use |
| `$ defaults write com.apple.dock mru-spaces -bool true` | Automatically rearrange Spaces based on most recent use (default) |
| `$ defaults write com.apple.dashboard devmode -bool true` | Enable Dashboard dev mode (allows keeping widgets on the desktop) |
| `$ defaults write com.apple.dashboard devmode -bool false` | Disable Dashboard dev mode (default) |

#### Launchpad

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.dock showLaunchpadGestureEnabled -int 0` | Disable the Launchpad gesture (pinch with thumb and three fingers) |
| `$ sudo ln -sf "/Applications/Xcode.app/Contents/Developer/Applications/Simulator.app" "/Applications/Simulator.app"` | Add iOS Simulator to Launchpad |
| `$ sudo ln -sf "/Applications/Xcode.app/Contents/Developer/Applications/Simulator (Watch).app" "/Applications/Simulator (Watch).app"` | Add Watch Simulator to Launchpad |

### Finder

#### Close with `⌘ + Q`

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.finder QuitMenuItem -bool true` | Allow quitting via `⌘ + Q`, also hides desktop icons |
| `$ defaults write com.apple.finder QuitMenuItem -bool false` | Disallow quitting via `⌘ + Q` (default) |

#### Window/Get info animations

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.finder DisableAllAnimations -bool true` | Disable window and Get Info animations |
| `$ defaults write com.apple.finder DisableAllAnimations -bool false` | Enable window and Get Info animations (default) |

#### Default location for new Finder windows

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.finder NewWindowTarget -string "PfLo"`<br>`$ defaults write com.apple.finder NewWindowTargetPath -string "file:///full/path/here/"` | Set desired path as the default location |
| `$ defaults write com.apple.finder NewWindowTarget -string "PfDe"`<br>`$ defaults write com.apple.finder NewWindowTargetPath -string "file://${HOME}/Desktop/"` | Set Desktop as the default location |

#### Hidden files

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.finder AppleShowAllFiles -bool TRUE`<br>`$ killall Finder` | Show hidden files |
| `$ defaults write com.apple.finder AppleShowAllFiles -bool FALSE`<br>`$ killall Finder` | Hide hidden files (default) |

#### File extensions

| Command | Result |
| --- | --- |
| `$ defaults write NSGlobalDomain AppleShowAllExtensions -bool true`<br>`$ killall Finder` | Show all filename extensions |
| `$ defaults write NSGlobalDomain AppleShowAllExtensions -bool false`<br>`$ killall Finder` | Hide filename extensions (default) |

#### File extensions change

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.finder FXEnableExtensionChangeWarning -bool false`<br>`$ killall Finder` | Disable the warning when changing a file extension |
| `$ defaults write com.apple.finder FXEnableExtensionChangeWarning -bool true`<br>`$ killall Finder` | Enable the warning when changing a file extension (default) |

#### .DS_Store files

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool true`<br>`$ defaults write com.apple.desktopservices DSDontWriteUSBStores -bool true` | Avoid creating .DS_Store files on network or USB volumes |

#### File Info

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.finder FXInfoPanesExpanded -dict General -bool true` | Expand the "General" File Info panes |
| `$ defaults write com.apple.finder FXInfoPanesExpanded -dict General -bool false` | Collapse the "General" File Info panes (default) |
| `$ defaults write com.apple.finder FXInfoPanesExpanded -dict OpenWith -bool true` | Expand the "OpenWith" File Info panes |
| `$ defaults write com.apple.finder FXInfoPanesExpanded -dict OpenWith -bool false` | Collapse the "OpenWith" File Info panes (default) |
| `$ defaults write com.apple.finder FXInfoPanesExpanded -dict Privileges -bool true` | Expand the "Privileges" File Info panes |
| `$ defaults write com.apple.finder FXInfoPanesExpanded -dict Privileges -bool false` | Collapse the "Privileges" File Info panes (default) |

#### Default view in Finder

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.finder FXPreferredViewStyle -string "Nlsv"` | Use list view in all Finder windows by default |
| `$ defaults write com.apple.finder FXPreferredViewStyle -string "icnv"` | Use icon view in all Finder windows by default |
| `$ defaults write com.apple.finder FXPreferredViewStyle -string "clmv"` | Use column view in all Finder windows by default |
| `$ defaults write com.apple.finder FXPreferredViewStyle -string "Flwv"` | Use Cover Flow view in all Finder windows by default |

#### Status bar

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.finder ShowStatusBar -bool true`<br>`$ killall Finder` | Show status bar |
| `$ defaults write com.apple.finder ShowStatusBar -bool false`<br>`$ killall Finder` | Hide status bar (default) |

#### Path bar

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.finder ShowPathBar -bool true`<br>`$ killall Finder` | Show path bar |
| `$ defaults write com.apple.finder ShowPathBar -bool false`<br>`$ killall Finder` | Hide path bar (default) |

#### Window title

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.finder _FXShowPosixPathInTitle -bool true`<br>`$ killall Finder` | Display full POSIX path as Finder window title |
| `$ defaults write com.apple.finder _FXShowPosixPathInTitle -bool false`<br>`$ killall Finder` | Display only current directory name as Finder window title (default) |

#### Sorting

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.finder _FXSortFoldersFirst -bool true`<br>`$ killall Finder` | Keep directories on top when sorting by name |
| `$ defaults write com.apple.finder _FXSortFoldersFirst -bool false`<br>`$ killall Finder` | Mix files and riectories when sorting by name (default) |

#### Search

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.finder FXDefaultSearchScope -string "SCcf"`<br>`$ killall Finder` | When performing a search, search the current directory by default |

#### Volumes

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.frameworks.diskimages auto-open-ro-root -bool true`<br>`$ defaults write com.apple.frameworks.diskimages auto-open-rw-root -bool true`<br>`$ defaults write com.apple.finder OpenWindowForNewRemovableDisk -bool true` | Automatically open a new Finder window when a volume is mounted |
| `$ sudo chflags nohidden /Volumes` | Show the `/Volumes` directory |
| `$ sudo chflags hidden /Volumes` | Hide the `/Volumes` directory (default) |

#### Library

| Command | Result |
| --- | --- |
| `$ chflags nohidden ~/Library` | Show the `~/Library` directory |
| `$ chflags hidden ~/Library` | Hide the `~/Library` directory (default) |

#### Trash

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.finder WarnOnEmptyTrash -bool false`<br>`$ killall Finder` | Disable the warning before emptying the trash |
| `$ defaults write com.apple.finder WarnOnEmptyTrash -bool true`<br>`$ killall Finder` | Enable the warning before emptying the trash (default) |

#### Desktop

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.finder CreateDesktop -bool false`<br>`$ killall Finder` | Hide all icons on desktop |
| `$ defaults write com.apple.finder CreateDesktop -bool true`<br>`$ killall Finder` | Show all icons on desktop (default) |

#### Quick Look

| Command | Result |
| --- | --- |
| `$ defaults write -g QLPanelAnimationDuration -float 0`<br>`$ killall Finder` | Disable animations when opening a Quick Look window |
| `$ defaults write com.apple.finder QLEnableTextSelection -bool true`<br>`$ killall Finder` | Enable text selection in Quick Look windows |
| `$ defaults write com.apple.finder QLEnableTextSelection -bool false`<br>`$ killall Finder` | Disable text selection in Quick Look windows (default) |

### Icons

#### Item info

| Command | Result |
| --- | --- |
| `$ /usr/libexec/PlistBuddy -c "Set :DesktopViewSettings:IconViewSettings:showItemInfo true" ~/Library/Preferences/com.apple.finder.plist`<br>`$ /usr/libexec/PlistBuddy -c "Set :FK_StandardViewSettings:IconViewSettings:showItemInfo true" ~/Library/Preferences/com.apple.finder.plist`<br>`$ /usr/libexec/PlistBuddy -c "Set :StandardViewSettings:IconViewSettings:showItemInfo true" ~/Library/Preferences/com.apple.finder.plist` | Show item info near icons on the desktop and in other icon views |
| `$ /usr/libexec/PlistBuddy -c "Set DesktopViewSettings:IconViewSettings:labelOnBottom false" ~/Library/Preferences/com.apple.finder.plist` | Show item info to the right of the icons on the desktop |

#### Grid

| Command | Result |
| --- | --- |
| `/usr/libexec/PlistBuddy -c "Set :DesktopViewSettings:IconViewSettings:arrangeBy grid" ~/Library/Preferences/com.apple.finder.plist`<br>`/usr/libexec/PlistBuddy -c "Set :FK_StandardViewSettings:IconViewSettings:arrangeBy grid" ~/Library/Preferences/com.apple.finder.plist`<br>`/usr/libexec/PlistBuddy -c "Set :StandardViewSettings:IconViewSettings:arrangeBy grid" ~/Library/Preferences/com.apple.finder.plist` | Enable snap-to-grid for icons on the desktop and in other icon views |
| `/usr/libexec/PlistBuddy -c "Set :DesktopViewSettings:IconViewSettings:gridSpacing 100" ~/Library/Preferences/com.apple.finder.plist`<br>`/usr/libexec/PlistBuddy -c "Set :FK_StandardViewSettings:IconViewSettings:gridSpacing 100" ~/Library/Preferences/com.apple.finder.plist`<br>`/usr/libexec/PlistBuddy -c "Set :StandardViewSettings:IconViewSettings:gridSpacing 100" ~/Library/Preferences/com.apple.finder.plist` | Increase grid spacing for icons on the desktop and in other icon views |
| `/usr/libexec/PlistBuddy -c "Set :DesktopViewSettings:IconViewSettings:iconSize 80" ~/Library/Preferences/com.apple.finder.plist`<br>`/usr/libexec/PlistBuddy -c "Set :FK_StandardViewSettings:IconViewSettings:iconSize 80" ~/Library/Preferences/com.apple.finder.plist`<br>`/usr/libexec/PlistBuddy -c "Set :StandardViewSettings:IconViewSettings:iconSize 80" ~/Library/Preferences/com.apple.finder.plist` | Increase the size of icons on the desktop and in other icon views |

### Airdrop

#### Ethernet and unsupprted Macs

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.NetworkBrowser BrowseAllInterfaces -bool true` | Enable AirDrop over Ethernet and on unsupported Macs running Lion and higher |
| `$ defaults write com.apple.NetworkBrowser BrowseAllInterfaces -bool false` | Disable AirDrop over Ethernet and on unsupported Macs running Lion and higher (default) |

### Spring loading

What is spring loading? Check this - very old but still up to date - video: (Spring-loaded Folders (Youtube)[https://www.youtube.com/watch?v=F9kdAxGe9SE]

#### Finder

| Command | Result |
| --- | --- |
| `$ defaults write NSGlobalDomain com.apple.springing.enabled -bool true` | Enable spring loading for directories |
| `$ defaults write NSGlobalDomain com.apple.springing.enabled -bool false` | Disable spring loading for directories (default) |
| `$ defaults write NSGlobalDomain com.apple.springing.delay -float 0` | Remove the spring loading delay for directories |

#### Dock

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.dock enable-spring-load-actions-on-all-items -bool true` | Enable spring loading for all Dock items |
| `$ defaults write com.apple.dock enable-spring-load-actions-on-all-items -bool false` | Disable spring loading for all Dock items (default) |

### Screenshots

#### Default file name

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.screencapture name "newscreenshotname"` | Change cefault name of screenshots |


#### Drop shadow on Screenshots

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.screencapture disable-shadow -bool TRUE` | Disable drop shadows |
| `$ defaults write com.apple.screencapture disable-shadow -bool FALSE` | Enable drop shadows (default) |

#### Screenshot location

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.screencapture location [path]`<br>`$ killall SystemUIServer` | Set desired path (replace `[path]`) |
| `$ defaults write com.apple.screencapture location -string "${HOME}/Desktop"`<br>`$ killall SystemUIServer` | Save screenshots on users desktop (default) |

#### Screenshot format

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.screencapture type -string "bmp"` | Save screenshots as BMP |
| `$ defaults write com.apple.screencapture type -string "gif"` | Save screenshots as GIF |
| `$ defaults write com.apple.screencapture type -string "jpg"` | Save screenshots as JPG |
| `$ defaults write com.apple.screencapture type -string "pdf"` | Save screenshots as PDF |
| `$ defaults write com.apple.screencapture type -string "tiff"` | Save screenshots as TIFF |
| `$ defaults write com.apple.screencapture type -string "png"` | Save screenshots as PNG (default) |

### General UI/UX

#### Scrollbar visibility

| Command | Result |
| --- | --- |
| `$ defaults write NSGlobalDomain AppleShowScrollBars -string "Always"` | Always show scrollbars |
| `$ defaults write NSGlobalDomain AppleShowScrollBars -string "WhenScrolling"` | Show scrollbars on scroll |
| `$ defaults write NSGlobalDomain AppleShowScrollBars -string "Automatic"` | Automatic mode |

#### Smooth scrolling

| Command | Result |
| --- | --- |
| `$ defaults write NSGlobalDomain NSScrollAnimationEnabled -bool false` | Disable smooth scrolling (e.g. on older Macs) |
| `$ defaults write NSGlobalDomain NSScrollAnimationEnabled -bool true` | Enable smooth scrolling (default) |

#### Windows

| Command | Result |
| --- | --- |
| `$ defaults write NSGlobalDomain NSAutomaticWindowAnimationsEnabled -bool false` | Disable animations when opening and closing windows |
| `$ defaults write NSGlobalDomain NSAutomaticWindowAnimationsEnabled -bool true` | Enable animations when opening and closing windows (default) |
| `$ defaults write NSGlobalDomain NSWindowResizeTime -float 0.001` | Accelerated playback when adjusting the window size (Cocoa applications) |

#### Save panel

| Command | Result |
| --- | --- |
| `$ defaults write NSGlobalDomain NSNavPanelExpandedStateForSaveMode -bool true`<br>`$ defaults write NSGlobalDomain NSNavPanelExpandedStateForSaveMode2 -bool true` | Expand save panel by default |
| `$ defaults write NSGlobalDomain NSNavPanelExpandedStateForSaveMode -bool false`<br>`$ defaults write NSGlobalDomain NSNavPanelExpandedStateForSaveMode2 -bool false` | Collapse save panel by default |

#### Notifications

| Command | Result |
| --- | --- |
| `$ sudo launchctl unload -w /System/Library/LaunchAgents/com.apple.notificationcenterui.plist 2> /dev/null` | Disable Notification Center and remove the menu bar icon |

### OS related

#### User password

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.screensaver askForPassword -int 1`<br>`$ defaults write com.apple.screensaver askForPasswordDelay -int 0` | Require password immediately after sleep or screen saver begins |

#### Login screen

| Command | Result |
| --- | --- |
| `$ sudo defaults write /Library/Preferences/com.apple.loginwindow AdminHostInfo HostName` | Show basic system info on login screen |
| `$ sudo defaults write /Library/Preferences/com.apple.loginwindow LoginwindowText "Live Long & Prosper"` | Add a message to login screen |

#### Restart Mac after crash

| Command | Result |
| --- | --- |
| `$ sudo systemsetup -setrestartfreeze on` | Make your Mac automatically restart after a crash |
| `$ sudo systemsetup -setrestartfreeze off` | Deactivate automatic restart (default) |

#### Sound effects on boot

| Command | Result |
| --- | --- |
| `$ sudo nvram SystemAudioVolume=" "` | Disable the sound effects |

#### Sleep mode

| Command | Result |
| --- | --- |
| `$ sudo systemsetup -setcomputersleep Off > /dev/null` | Never go into computer sleep mode |

### Printer

#### Print panel

| Command | Result |
| --- | --- |
| `$ defaults write NSGlobalDomain PMPrintingExpandedStateForPrint -bool true`<br>`$ defaults write NSGlobalDomain PMPrintingExpandedStateForPrint2 -bool true` | Expand print panel by default |
| `$ defaults write NSGlobalDomain PMPrintingExpandedStateForPrint -bool false`<br>`$ defaults write NSGlobalDomain PMPrintingExpandedStateForPrint2 -bool false` | Collapse print panel by default |

#### Printer app

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.print.PrintingPrefs "Quit When Finished" -bool true` | Automatically quit printer app once the print jobs complete |
| `$ defaults write com.apple.print.PrintingPrefs "Quit When Finished" -bool false` | Do not automatically quit printer app once the print jobs complete (default) |

### iCloud

#### Stop apps from saving to iCloud by default

| Command | Result |
| --- | --- |
| `$ defaults write NSGlobalDomain NSDocumentSaveNewDocumentsToCloud -bool false` | Make your Mac automatically restart after a crash |
| `$ defaults write NSGlobalDomain NSDocumentSaveNewDocumentsToCloud -bool false` | Deactivate automatic restart (default) |

### Typing/Keyboard

#### All controls

| Command | Result |
| --- | --- |
| `$ defaults write NSGlobalDomain AppleKeyboardUIMode -int 3` | Enable full keyboard access for all controls (e.g. enable Tab in modal dialogs) |

#### Make holding down a key repeat characters

| Command | Result |
| --- | --- |
| `$ defaults write -g ApplePressAndHoldEnabled -bool FALSE` | Enable character repeat |
| `$ defaults write -g ApplePressAndHoldEnabled -bool TRUE` | Disable character repeat (default) |

#### Automatic capitalization

| Command | Result |
| --- | --- |
| `$ defaults write NSGlobalDomain NSAutomaticCapitalizationEnabled -bool false` | Disable automatic capitalization |
| `$ defaults write NSGlobalDomain NSAutomaticCapitalizationEnabled -bool true` | Enable automatic capitalization (default) |

#### Smart dashes

| Command | Result |
| --- | --- |
| `$ defaults write NSGlobalDomain NSAutomaticDashSubstitutionEnabled -bool false` | Disable smart dashes |
| `$ defaults write NSGlobalDomain NSAutomaticDashSubstitutionEnabled -bool true` | Enable smart dashes (default) |

#### Automatic period

| Command | Result |
| --- | --- |
| `$ defaults write NSGlobalDomain NSAutomaticPeriodSubstitutionEnabled -bool false` | Disable automatic period substitution |
| `$ defaults write NSGlobalDomain NSAutomaticPeriodSubstitutionEnabled -bool true` | Enable automatic period substitution (default) |

#### Smart quotes

| Command | Result |
| --- | --- |
| `$ defaults write NSGlobalDomain NSAutomaticQuoteSubstitutionEnabled -bool false` | Disable smart quotes |
| `$ defaults write NSGlobalDomain NSAutomaticQuoteSubstitutionEnabled -bool true` | Enable smart quotes (default) |

#### Auto-correct

| Command | Result |
| --- | --- |
| `$ defaults write NSGlobalDomain NSAutomaticSpellingCorrectionEnabled -bool false` | Disable auto-correct |
| `$ defaults write NSGlobalDomain NSAutomaticSpellingCorrectionEnabled -bool true` | Enable auto-correct (default) |

### Trackpad

#### Tap to click

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad Clicking -bool true`<br>`$ defaults -currentHost write NSGlobalDomain com.apple.mouse.tapBehavior -int 1`<br>`$ defaults write NSGlobalDomain com.apple.mouse.tapBehavior -int 1` | Enable tap to click for this user and for the login screen |

#### Right-click

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad TrackpadCornerSecondaryClick -int 2`<br>`$ defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad TrackpadRightClick -bool true`<br>`$ defaults -currentHost write NSGlobalDomain com.apple.trackpad.trackpadCornerClickBehavior -int 1`<br>`$ defaults -currentHost write NSGlobalDomain com.apple.trackpad.enableSecondaryClick -bool true` | Map bottom right corner of trackpad to right-click |

### Bluetooth

#### Sound Quality

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.BluetoothAudioAgent "Apple Bitpool Min (editable)" -int 40` | Increase sound quality for Bluetooth headphones/headsets |

### Apps

#### Safari

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.Safari UniversalSearchEnabled -bool false`<br>`& defaults write com.apple.Safari SuppressSearchSuggestions -bool true` | Privacy: don’t send search queries to Apple |
| `$ defaults write com.apple.Safari WebKitTabToLinksPreferenceKey -bool true`<br>`$ defaults write com.apple.Safari com.apple.Safari.ContentPageGroupIdentifier.WebKit2TabsToLinks -bool true` | Press Tab to highlight each item on a web page |
| `$ defaults write com.apple.Safari ShowFullURLInSmartSearchField -bool true` | Show the full URL in the address bar |
| `$ defaults write com.apple.Safari HomePage -string "about:blank"` | Set home page to `about:blank` for faster loading |
| `$ defaults write com.apple.Safari AutoOpenSafeDownloads -bool false` | Prevent Safari from opening ‘safe’ files automatically after downloading |
| `$ defaults write com.apple.Safari com.apple.Safari.ContentPageGroupIdentifier.WebKit2BackspaceKeyNavigationEnabled -bool true` | Allow using Backspace key to go to the previous page in history |
| `$ defaults write com.apple.Safari ShowFavoritesBar -bool false` | Hide bookmarks bar by default |
| `$ defaults write com.apple.Safari ProxiesInBookmarksBar "()"` | Remove useless icons from bookmarks bar |
| `$ defaults write com.apple.Safari ShowSidebarInTopSites -bool false` | Hide sidebar in Top Sites |
| `$ defaults write com.apple.Safari DebugSnapshotsUpdatePolicy -int 2` | Disable thumbnail cache for History and Top Sites |
| `$ defaults write com.apple.Safari FindOnPageMatchesWordStartsOnly -bool false` | Make Safari’s search banners default to Contains instead of Starts With |
| `$ defaults write com.apple.Safari IncludeInternalDebugMenu -bool true` | Enable debug menu |
| `$ defaults write com.apple.Safari IncludeDevelopMenu -bool true`<br>`$ defaults write com.apple.Safari WebKitDeveloperExtrasEnabledPreferenceKey -bool true`<br>`$ defaults write com.apple.Safari com.apple.Safari.ContentPageGroupIdentifier.WebKit2DeveloperExtrasEnabled -bool true` | Enable the Develop menu and the Web Inspector |
| `$ defaults write NSGlobalDomain WebKitDeveloperExtras -bool true` | Add a context menu item for showing the Web Inspector in web views |
| `$ defaults write com.apple.Safari WebContinuousSpellCheckingEnabled -bool true` | Enable continuous spellchecking |
| `$ defaults write com.apple.Safari WebAutomaticSpellingCorrectionEnabled -bool false` | Disable auto-correct |
| `$ defaults write com.apple.Safari AutoFillFromAddressBook -bool false` | Disable autofill from Adress Book |
| `$ defaults write com.apple.Safari AutoFillPasswords -bool false` | Disable autofill of passwords |
| `$ defaults write com.apple.Safari AutoFillCreditCardData -bool false` | Disable autofill of credit card data |
| `$ defaults write com.apple.Safari AutoFillMiscellaneousForms -bool false` | Disable autofill of miscellaneous forms |
| `$ defaults write com.apple.Safari WarnAboutFraudulentWebsites -bool true` | Warn about fraudulent websites |
| `$ defaults write com.apple.Safari WebKitJavaScriptCanOpenWindowsAutomatically -bool false`<br>`$ defaults write com.apple.Safari com.apple.Safari.ContentPageGroupIdentifier.WebKit2JavaScriptCanOpenWindowsAutomatically -bool false` | Block pop-up windows |
| `$ defaults write com.apple.Safari SendDoNotTrackHTTPHeader -bool true` | Enable “Do Not Track” |
| `$ defaults write com.apple.Safari InstallExtensionUpdatesAutomatically -bool true` | Update extensions automatically |
| `$ defaults write com.apple.Safari WebKitInitialTimedLayoutDelay 0.25` | Disable the standard delay in rendering a Web page |

#### Mail

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.mail DisableReplyAnimations -bool true`<br>`$ defaults write com.apple.mail DisableSendAnimations -bool true` | Disable send and reply animations |
| `$ defaults write com.apple.mail AddressesIncludeNameOnPasteboard -bool false` | Copy email addresses as `foo@bar.com` instead of `Foo Bar <foo@bar.com>` |
| `$ defaults write com.apple.mail NSUserKeyEquivalents -dict-add "Send" "@\U21a9"` | Activate shortcut `⌘ + Enter` to send email |
| `$ defaults write com.apple.mail DraftsViewerAttributes -dict-add "DisplayInThreadedMode" -string "yes"`<br>`$ defaults write com.apple.mail DraftsViewerAttributes -dict-add "SortedDescending" -string "yes"`<br>`$ defaults write com.apple.mail DraftsViewerAttributes -dict-add "SortOrder" -string "received-date"` |  Display emails in threaded mode, sorted by date (oldest at the top) |
| `$ defaults write com.apple.mail DisableInlineAttachmentViewing -bool true` | Disable inline attachments (just show the icons) |
| `$ defaults write com.apple.mail SpellCheckingBehavior -string "NoSpellCheckingEnabled"` | Disable automatic spell checking |

#### iTerm 2

| Command | Result |
| --- | --- |
| `$ defaults write com.googlecode.iterm2 PromptOnQuit -bool false` | Disable the annoying prompt when quitting iTerm |

#### Time Machine

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.TimeMachine DoNotOfferNewDisksForBackup -bool true` | Prevent Time Machine from prompting to use new hard drives as backup volume |
| `$ hash tmutil &> /dev/null && sudo tmutil disablelocal` | Disable local Time Machine backups |

#### Activity Monitor

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.ActivityMonitor OpenMainWindow -bool true` | Show the main window when launching Activity Monitor |
| `$ defaults write com.apple.ActivityMonitor IconType -int 5` | Visualize CPU usage in the Activity Monitor Dock icon |
| `$ defaults write com.apple.ActivityMonitor ShowCategory -int 0` | Show all processes in Activity Monitor |
| `$ defaults write com.apple.ActivityMonitor SortColumn -string "CPUUsage"`<br>`$ defaults write com.apple.ActivityMonitor SortDirection -int 0` | Sort Activity Monitor results by CPU usage |

#### Address Book

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.addressbook ABShowDebugMenu -bool true` | Enable the debug menu in Address Book |
| `$ defaults write com.apple.addressbook ABShowDebugMenu -bool false` | Disable the debug menu in Address Book (default) |

#### TextEdit

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.TextEdit RichText -int 0` | Use plain text mode for new TextEdit documents |
| `$ defaults write com.apple.TextEdit PlainTextEncoding -int 4`<br>`$ defaults write com.apple.TextEdit PlainTextEncodingForWrite -int 4` | Open and save files as UTF-8 in TextEdit |

#### Disk Utility

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.DiskUtility DUDebugMenuEnabled -bool true`<br>`$ defaults write com.apple.DiskUtility advanced-image-options -bool true` | Enable the debug menu in Disk Utility |
| `$ defaults write com.apple.DiskUtility DUDebugMenuEnabled -bool false`<br>`$ defaults write com.apple.DiskUtility advanced-image-options -bool false` | Disable the debug menu in Disk Utility (default) |

#### Mac App Store

| Command | Result |
| --- | --- |
| `$ defaults write com.apple.appstore WebKitDeveloperExtras -bool true` | Enable the WebKit Developer Tools in the Mac App Store |
| `$ defaults write com.apple.appstore WebKitDeveloperExtras -bool false` | Disable the WebKit Developer Tools in the Mac App Store (default) |
| `$ defaults write com.apple.appstore ShowDebugMenu -bool true` | Enable Debug Menu in the Mac App Store |
| `$ defaults write com.apple.appstore ShowDebugMenu -bool false` | Disable Debug Menu in the Mac App Store (default) |
| `$ defaults write com.apple.SoftwareUpdate AutomaticCheckEnabled -bool true` | Enable the automatic update check |
| `$ defaults write com.apple.SoftwareUpdate AutomaticCheckEnabled -bool false` | Disable the automatic update check |
| `$ defaults write com.apple.SoftwareUpdate ScheduleFrequency -int 1` | Check for software updates daily instead of weekly |
| `$ defaults write com.apple.SoftwareUpdate AutomaticDownload -int 1` | Download newly available updates in background |
| `$ defaults write com.apple.SoftwareUpdate CriticalUpdateInstall -int 1` | Install System data files & security updates |
| `$ defaults write com.apple.SoftwareUpdate ConfigDataInstall -int 1` | Automatically download apps purchased on other Macs |
| `$ defaults write com.apple.commerce AutoUpdate -bool true` | Turn on app auto-update |
| `$ defaults write com.apple.commerce AutoUpdateRestartRequired -bool true` | Allow the App Store to reboot machine on macOS updates |

#### Photos

| Command | Result |
| --- | --- |
| `$ defaults -currentHost write com.apple.ImageCapture disableHotPlug -bool true` | Prevent Photos from opening automatically when devices are plugged in |

#### Google Chrome & Google Chrome Canary

| Command | Result |
| --- | --- |
| `$ defaults write com.google.Chrome AppleEnableSwipeNavigateWithScrolls -bool false`<br>`$ defaults write com.google.Chrome.canary AppleEnableSwipeNavigateWithScrolls -bool false` | Disable backswipe on trackpads |
| `$ defaults write com.google.Chrome AppleEnableSwipeNavigateWithScrolls -bool true`<br>`$ defaults write com.google.Chrome.canary AppleEnableSwipeNavigateWithScrolls -bool true` | Enable backswipe on trackpads (default) |
| `$ defaults write com.google.Chrome AppleEnableMouseSwipeNavigateWithScrolls -bool false`<br>`$ defaults write com.google.Chrome.canary AppleEnableMouseSwipeNavigateWithScrolls -bool false` | Disable backswipe on Magic Mouse |
| `$ defaults write com.google.Chrome AppleEnableMouseSwipeNavigateWithScrolls -bool true`<br>`$ defaults write com.google.Chrome.canary AppleEnableMouseSwipeNavigateWithScrolls -bool true` | Enable backswipe on Magic Mouse (default) |
| `$ defaults write com.google.Chrome DisablePrintPreview -bool true`<br>`$ defaults write com.google.Chrome.canary DisablePrintPreview -bool true` | Use the system-native print preview dialog |
| `$ defaults write com.google.Chrome DisablePrintPreview -bool false`<br>`$ defaults write com.google.Chrome.canary DisablePrintPreview -bool false` | Use the Chrome print preview dialog (default) |
| `$ defaults write com.google.Chrome PMPrintingExpandedStateForPrint2 -bool true`<br>`$ defaults write com.google.Chrome.canary PMPrintingExpandedStateForPrint2 -bool true` | Expand the print dialog by default |
| `$ defaults write com.google.Chrome PMPrintingExpandedStateForPrint2 -bool false`<br>`$ defaults write com.google.Chrome.canary PMPrintingExpandedStateForPrint2 -bool false` | Collapse the print dialog by default (default) |
