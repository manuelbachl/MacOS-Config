# MacOS-Config

## Disclaimer

**Use at your own risk and when you know what you're doing!**  
**I am not responsible for any weird behaviour or other problems you may run into after using any of those settings.**

## Undo changes

If you want to revert some settings, in most cases (all commands that start with `defaults write`), you can use the `defaults delete` command:

```bash
defaults delete domain key
```

Alternatively you can just toggle the flag you defined from `true` to `false` or vice versa.

But now just have a look at the huge list of possible tweaks and settings and pick the stuff you need.

## Terminal commands

### Gatekeeper

#### Readd download option "Anywhere" in security system settings:

```bash
sudo spctl --master-disable
```
---

#### Disable the “Are you sure you want to open this application?” dialog for specified app:

Replace `/Applications/PhpStorm.app` with the app u need.
```bash
sudo xattr -d com.apple.quarantine /Applications/PhpStorm.app
```  
---

#### Disable the “Are you sure you want to open this application?” dialog globally:

```bash
defaults write com.apple.LaunchServices LSQuarantine -bool false
```
---

### Dock

#### Hide non-active apps in your Dock:

```bash
defaults write com.apple.dock static-only -bool true
killall Dock
```
---

#### Dull hidden apps in the Dock:

```bash
defaults write com.apple.Dock showhidden -bool true
killall Dock
```
---

#### Enable highlight hover effect for the grid view of a stack:

```bash
defaults write com.apple.dock mouse-over-hilite-stack -bool true
killall Dock
```
---

#### Set the icon size of Dock items to 36 pixels:

```bash
defaults write com.apple.dock tilesize -int 36
killall Dock
```
---

#### Change minimize/maximize window effect:

```bash
defaults write com.apple.dock mineffect -string "scale"
killall Dock
```
---

#### Minimize windows into their application’s icon:

```bash
defaults write com.apple.dock minimize-to-application -bool true
killall Dock
```
---

#### Don’t animate opening applications from the Dock:

```bash
defaults write com.apple.dock launchanim -bool false
killall Dock
```
---

#### Show indicator lights for open applications in the Dock:

```bash
defaults write com.apple.dock show-process-indicators -bool true
killall Dock
```
---

#### Automatically hide and show the Dock:

```bash
defaults write com.apple.dock autohide -bool true
killall Dock
```
---

#### Remove the auto-hiding Dock delay:

```bash
defaults write com.apple.dock autohide-delay -float 0
killall Dock
```
---

#### Remove the animation when hiding/showing the Dock:

```bash
defaults write com.apple.dock autohide-time-modifier -float 0
killall Dock
```
---

### Mission Control

#### Speed up Mission Control animations:

```bash
defaults write com.apple.dock expose-animation-duration -float 0.1
```
---

#### Don’t group windows by application in Mission Control:

```bash
defaults write com.apple.dock expose-group-by-app -bool false
```
---

### Dashboard

#### Disable Dashboard:

```bash
defaults write com.apple.dashboard mcx-disabled -bool true
```
---

#### Don’t show Dashboard as a Space:

```bash
defaults write com.apple.dock dashboard-in-overlay -bool true
```
---

#### Don’t automatically rearrange Spaces based on most recent use:

```bash
defaults write com.apple.dock mru-spaces -bool false
```
---

#### Enable Dashboard dev mode (allows keeping widgets on the desktop):

```bash
defaults write com.apple.dashboard devmode -bool true
```
---

### Launchpad

#### Disable the Launchpad gesture (pinch with thumb and three fingers):

```bash
defaults write com.apple.dock showLaunchpadGestureEnabled -int 0
```
---

#### Add iOS & Watch Simulator to Launchpad:

```bash
sudo ln -sf "/Applications/Xcode.app/Contents/Developer/Applications/Simulator.app" "/Applications/Simulator.app"
sudo ln -sf "/Applications/Xcode.app/Contents/Developer/Applications/Simulator (Watch).app" "/Applications/Simulator (Watch).app
```
---

### Finder

#### Allow quitting via `⌘ + Q`, also hides desktop icons:

```bash
defaults write com.apple.finder QuitMenuItem -bool true
```
---

#### Disable window and Get Info animations

```bash
defaults write com.apple.finder DisableAllAnimations -bool true
```
---

#### Set desired path as the default location for new Finder windows:

```bash
defaults write com.apple.finder NewWindowTarget -string "PfLo"
defaults write com.apple.finder NewWindowTargetPath -string "file:///full/path/here/"
```
---

#### Set Desktop as the default location for new Finder windows:

```bash
defaults write com.apple.finder NewWindowTarget -string "PfDe"
defaults write com.apple.finder NewWindowTargetPath -string "file://${HOME}/Desktop/"
```

#### Show hidden files:

```bash
defaults write com.apple.finder AppleShowAllFiles -bool TRUE
killall Finder
```
---

#### Show all file extensions:

```bash
defaults write NSGlobalDomain AppleShowAllExtensions -bool true
killall Finder
```
---

#### Disable the warning when changing a file extension:

```bash
defaults write com.apple.finder FXEnableExtensionChangeWarning -bool false
killall Finder
```
---

#### Avoid creating .DS_Store files on network or USB volumes:

```bash
defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool true
defaults write com.apple.desktopservices DSDontWriteUSBStores -bool true
killall Finder
```
---

#### Expand File Info panes:

Expand "General":

```bash
defaults write com.apple.finder FXInfoPanesExpanded -dict General -bool true
killall Finder
```

Expand "Open with":

```bash
defaults write com.apple.finder FXInfoPanesExpanded -dict OpenWith -bool true
killall Finder
```

Expand "Privileges":

```bash
defaults write com.apple.finder FXInfoPanesExpanded -dict Privileges -bool true
killall Finder
```
---

#### Set default view in all Finder windows by default:

Set list view:

```bash
defaults write com.apple.finder FXPreferredViewStyle -string "Nlsv"
killall Finder
```

Set icon view:

```bash
defaults write com.apple.finder FXPreferredViewStyle -string "icnv"
killall Finder
```

Set column view:

```bash
defaults write com.apple.finder FXPreferredViewStyle -string "clmv"
killall Finder
```

Set Cover FLow view:

```bash
defaults write com.apple.finder FXPreferredViewStyle -string "Flwv"
killall Finder
```
---

#### Show status bar:

```bash
defaults write com.apple.finder ShowStatusBar -bool true
killall Finder
```
---

#### Show path bar:

```bash
defaults write com.apple.finder ShowPathBar -bool true
killall Finder
```
---

#### Display full POSIX path as Finder window title:

```bash
defaults write com.apple.finder _FXShowPosixPathInTitle -bool true
killall Finder
```
---

#### Keep directories on top when sorting by name:

```bash
defaults write com.apple.finder _FXSortFoldersFirst -bool true
killall Finder
```
---

#### When performing a search, search the current directory by default:

```bash
defaults write com.apple.finder FXDefaultSearchScope -string "SCcf"
killall Finder
```
---

#### Automatically open a new Finder window when a volume is mounted:

```bash
defaults write com.apple.frameworks.diskimages auto-open-ro-root -bool true
defaults write com.apple.frameworks.diskimages auto-open-rw-root -bool true
defaults write com.apple.finder OpenWindowForNewRemovableDisk -bool true
killall Finder
```
---

#### Show the `/Volumes` directory:

```bash
sudo chflags nohidden /Volumes
killall Finder
```
---

#### Show the `~/Library` directory:

```bash
chflags nohidden ~/Library
killall Finder
```
---

#### Disable the warning before emptying the trash:

```bash
defaults write com.apple.finder WarnOnEmptyTrash -bool false
killall Finder
```
---

#### Hide all icons on desktop:

```bash
defaults write com.apple.finder CreateDesktop -bool false
killall Finder
```
---

#### Disable animations when opening a Quick Look window:

```bash
defaults write -g QLPanelAnimationDuration -float 0
killall Finder
```
---

#### Enable text selection in Quick Look windows:

```bash
defaults write com.apple.finder QLEnableTextSelection -bool true
killall Finder
```
---

### Icons

#### Show item info near icons on the desktop and in other icon views:

```bash
/usr/libexec/PlistBuddy -c "Set :DesktopViewSettings:IconViewSettings:showItemInfo true" ~/Library/Preferences/com.apple.finder.plist
/usr/libexec/PlistBuddy -c "Set :FK_StandardViewSettings:IconViewSettings:showItemInfo true" ~/Library/Preferences/com.apple.finder.plist
/usr/libexec/PlistBuddy -c "Set :StandardViewSettings:IconViewSettings:showItemInfo true" ~/Library/Preferences/com.apple.finder.plist
```
---

#### Show item info to the right of the icons on the desktop:

```bash
/usr/libexec/PlistBuddy -c "Set DesktopViewSettings:IconViewSettings:labelOnBottom false" ~/Library/Preferences/com.apple.finder.plist
```
---

#### Enable snap-to-grid for icons on the desktop and in other icon views:

```bash
/usr/libexec/PlistBuddy -c "Set :DesktopViewSettings:IconViewSettings:arrangeBy grid" ~/Library/Preferences/com.apple.finder.plist
/usr/libexec/PlistBuddy -c "Set :FK_StandardViewSettings:IconViewSettings:arrangeBy grid" ~/Library/Preferences/com.apple.finder.plist
/usr/libexec/PlistBuddy -c "Set :StandardViewSettings:IconViewSettings:arrangeBy grid" ~/Library/Preferences/com.apple.finder.plist
```
---

#### Increase grid spacing for icons on the desktop and in other icon views:

```bash
/usr/libexec/PlistBuddy -c "Set :DesktopViewSettings:IconViewSettings:gridSpacing 100" ~/Library/Preferences/com.apple.finder.plist
/usr/libexec/PlistBuddy -c "Set :FK_StandardViewSettings:IconViewSettings:gridSpacing 100" ~/Library/Preferences/com.apple.finder.plist
/usr/libexec/PlistBuddy -c "Set :StandardViewSettings:IconViewSettings:gridSpacing 100" ~/Library/Preferences/com.apple.finder.plist
```
---

#### Increase the size of icons on the desktop and in other icon views:

```bash
/usr/libexec/PlistBuddy -c "Set :DesktopViewSettings:IconViewSettings:iconSize 80" ~/Library/Preferences/com.apple.finder.plist
/usr/libexec/PlistBuddy -c "Set :FK_StandardViewSettings:IconViewSettings:iconSize 80" ~/Library/Preferences/com.apple.finder.plist
/usr/libexec/PlistBuddy -c "Set :StandardViewSettings:IconViewSettings:iconSize 80" ~/Library/Preferences/com.apple.finder.plist
```
---

### Airdrop

#### Enable AirDrop over Ethernet and on unsupported Macs running Lion and higher:

```bash
defaults write com.apple.NetworkBrowser BrowseAllInterfaces -bool true
```
---

### Spring loading

What is spring loading? Check this - very old but still up to date - video: (Spring-loaded Folders (Youtube)[https://www.youtube.com/watch?v=F9kdAxGe9SE]

#### Enable spring loading for directories in Finder:

```bash
defaults write NSGlobalDomain com.apple.springing.enabled -bool true
killall Finder
```
---

#### Remove the spring loading delay for directories:

```bash
defaults write NSGlobalDomain com.apple.springing.delay -float 0
killall Finder
```
---

#### Enable spring loading for all Dock items:

```bash
defaults write com.apple.dock enable-spring-load-actions-on-all-items -bool true
killall Dock
```
---

### Screenshots

#### Change default file name of screenshots:

```bash
defaults write com.apple.screencapture name "newscreenshotname"
killall Finder
```
---

#### Disable drop shadows on screenshots:

```bash
defaults write com.apple.screencapture disable-shadow -bool true
killall Finder
```
---

#### Set location where to store screenshots:

```bash
defaults write com.apple.screencapture location [path]
killall SystemUIServer
```
---

#### Save screenshots on users desktop (default):

```bash
defaults write com.apple.screencapture location -string "${HOME}/Desktop"
killall SystemUIServer
```
---

#### Set screenshot format:

Save screenshot as BMP:

```bash
defaults write com.apple.screencapture type -string "bmp"
```

Save screenshot as JPG:

```bash
defaults write com.apple.screencapture type -string "jpg"
```

Save screenshot as PDF:

```bash
defaults write com.apple.screencapture type -string "pdf"
```

Save screenshot as TIFF:

```bash
defaults write com.apple.screencapture type -string "tiff"
```

Save screenshot as PNG (default):

```bash
defaults write com.apple.screencapture type -string "png"
```
---

### General UI/UX

#### Scrollbar visibility:

Always show scrollbars:

```bash
defaults write NSGlobalDomain AppleShowScrollBars -string "Always"
```

Show scrollbars on scroll:

```bash
defaults write NSGlobalDomain AppleShowScrollBars -string "WhenScrolling"
```

Automatic mode:

```bash
defaults write NSGlobalDomain AppleShowScrollBars -string "Automatic"
```
---

#### Disable smooth scrolling (e.g. on older Macs)

```bash
defaults write NSGlobalDomain NSScrollAnimationEnabled -bool false
```
---

#### Windows:

Disable animations when opening and closing windows:

```bash
defaults write NSGlobalDomain NSAutomaticWindowAnimationsEnabled -bool false
```

Accelerated playback when adjusting the window size (Cocoa applications):

```bash
defaults write NSGlobalDomain NSWindowResizeTime -float 0.001
```
---

#### Expand save panel by default:

```bash
defaults write NSGlobalDomain NSNavPanelExpandedStateForSaveMode -bool true
defaults write NSGlobalDomain NSNavPanelExpandedStateForSaveMode2 -bool true
```
---

#### Disable Notification Center and remove the menu bar icon:

```bash
sudo launchctl unload -w /System/Library/LaunchAgents/com.apple.notificationcenterui.plist 2> /dev/null
```
---

### OS related

#### Require password immediately after sleep or screen saver begins:

```bash
defaults write com.apple.screensaver askForPassword -int 1
defaults write com.apple.screensaver askForPasswordDelay -int 0
```
---

#### Add info to login screen:

Show basic system info on login screen:

```bash
sudo defaults write /Library/Preferences/com.apple.loginwindow AdminHostInfo HostName
```

Add a message to login screen:

```bash
sudo defaults write /Library/Preferences/com.apple.loginwindow LoginwindowText "Live Long & Prosper"
```
---

#### Make your Mac automatically restart after a crash:

```bash
sudo systemsetup -setrestartfreeze on
```
---

#### Disable the sound effects on boot

```bash
sudo nvram SystemAudioVolume=" "
```
---

#### Never go into computer sleep mode

```bash
sudo systemsetup -setcomputersleep Off > /dev/null
```
---

### Printer

#### Expand print panel by default:

```bash
defaults write NSGlobalDomain PMPrintingExpandedStateForPrint -bool true
defaults write NSGlobalDomain PMPrintingExpandedStateForPrint2 -bool true
```
---

#### Automatically quit printer app once the print jobs complete:

```bash
defaults write com.apple.print.PrintingPrefs "Quit When Finished" -bool true
```
---

### iCloud

#### Stop apps from saving to iCloud by default:

```bash
defaults write NSGlobalDomain NSDocumentSaveNewDocumentsToCloud -bool false
```
---

### Typing/Keyboard

#### Enable full keyboard access for all controls (e.g. enable Tab in modal dialogs)

```bash
defaults write NSGlobalDomain AppleKeyboardUIMode -int 3
```
---

#### Make holding down a key repeat characters:

```bash
defaults write -g ApplePressAndHoldEnabled -bool false
```
---

#### Disable automatic capitalization:

```bash
defaults write NSGlobalDomain NSAutomaticCapitalizationEnabled -bool false
```
---

#### Disable smart dashes:

```bash
defaults write NSGlobalDomain NSAutomaticDashSubstitutionEnabled -bool false
```
---

#### Disable automatic period substitution:

```bash
defaults write NSGlobalDomain NSAutomaticPeriodSubstitutionEnabled -bool false
```
---

#### Disable smart quotes:

```bash
defaults write NSGlobalDomain NSAutomaticQuoteSubstitutionEnabled -bool false
```
---

#### Disable auto-correct:

```bash
defaults write NSGlobalDomain NSAutomaticSpellingCorrectionEnabled -bool false
```
---

### Trackpad

#### Enable tap to click for this user and for the login screen:

```bash
defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad Clicking -bool true
defaults -currentHost write NSGlobalDomain com.apple.mouse.tapBehavior -int 1
defaults write NSGlobalDomain com.apple.mouse.tapBehavior -int 1
```
---

#### Map bottom right corner of trackpad to right-click:

```bash
defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad TrackpadCornerSecondaryClick -int 2
defaults write com.apple.driver.AppleBluetoothMultitouch.trackpad TrackpadRightClick -bool true
defaults -currentHost write NSGlobalDomain com.apple.trackpad.trackpadCornerClickBehavior -int 1
defaults -currentHost write NSGlobalDomain com.apple.trackpad.enableSecondaryClick -bool true
```
---

### Bluetooth

#### Increase sound quality for Bluetooth headphones/headsets:

```bash
defaults write com.apple.BluetoothAudioAgent "Apple Bitpool Min (editable)" -int 40
```
---

### Apps

#### Safari:

Privacy: don’t send search queries to Apple:

```bash
defaults write com.apple.Safari UniversalSearchEnabled -bool false
defaults write com.apple.Safari SuppressSearchSuggestions -bool true
```

Press Tab to highlight each item on a web page:

```bash
defaults write com.apple.Safari WebKitTabToLinksPreferenceKey -bool true
defaults write com.apple.Safari com.apple.Safari.ContentPageGroupIdentifier.WebKit2TabsToLinks -bool true
```

Show the full URL in the address bar:

```bash
defaults write com.apple.Safari ShowFullURLInSmartSearchField -bool true
```

Set home page to `about:blank` for faster loading:

```bash
defaults write com.apple.Safari HomePage -string "about:blank"
```

Prevent Safari from opening ‘safe’ files automatically after downloading:

```bash
defaults write com.apple.Safari AutoOpenSafeDownloads -bool false
```

Allow using Backspace key to go to the previous page in history:

```bash
defaults write com.apple.Safari com.apple.Safari.ContentPageGroupIdentifier.WebKit2BackspaceKeyNavigationEnabled -bool true
```

Hide bookmarks bar by default:

```bash
defaults write com.apple.Safari ShowFavoritesBar -bool false
```

Remove useless icons from bookmarks bar:

```bash
defaults write com.apple.Safari ProxiesInBookmarksBar "()"
```

Hide sidebar in Top Sites:

```bash
defaults write com.apple.Safari ShowSidebarInTopSites -bool false
```

Disable thumbnail cache for History and Top Sites:

```bash
defaults write com.apple.Safari DebugSnapshotsUpdatePolicy -int 2
```

Make Safari’s search banners default to Contains instead of Starts With:

```bash
defaults write com.apple.Safari FindOnPageMatchesWordStartsOnly -bool false
```

Enable debug menu:

```bash
defaults write com.apple.Safari IncludeInternalDebugMenu -bool true
```

Enable the Develop menu and the Web Inspector:

```bash
defaults write com.apple.Safari IncludeDevelopMenu -bool true
defaults write com.apple.Safari WebKitDeveloperExtrasEnabledPreferenceKey -bool true
defaults write com.apple.Safari com.apple.Safari.ContentPageGroupIdentifier.WebKit2DeveloperExtrasEnabled -bool true
```

Add a context menu item for showing the Web Inspector in web views:

```bash
defaults write NSGlobalDomain WebKitDeveloperExtras -bool true
```

Enable continuous spellchecking:

```bash
defaults write com.apple.Safari WebContinuousSpellCheckingEnabled -bool true
```

Disable auto-correct:

```bash
defaults write com.apple.Safari WebAutomaticSpellingCorrectionEnabled -bool false
```

Disable autofill from Adress Book:

```bash
defaults write com.apple.Safari AutoFillFromAddressBook -bool false
```

Disable autofill of passwords:

```bash
defaults write com.apple.Safari AutoFillPasswords -bool false
```

Disable autofill of credit card data:

```bash
defaults write com.apple.Safari AutoFillCreditCardData -bool false
```

Disable autofill of miscellaneous forms:

```bash
defaults write com.apple.Safari AutoFillMiscellaneousForms -bool false
```

Warn about fraudulent websites:

```bash
defaults write com.apple.Safari WarnAboutFraudulentWebsites -bool true
```

Block pop-up windows:

```bash
defaults write com.apple.Safari WebKitJavaScriptCanOpenWindowsAutomatically -bool false
defaults write com.apple.Safari com.apple.Safari.ContentPageGroupIdentifier.WebKit2JavaScriptCanOpenWindowsAutomatically -bool false
```

Enable “Do Not Track”:

```bash
defaults write com.apple.Safari SendDoNotTrackHTTPHeader -bool true
```

Update extensions automatically:

```bash
defaults write com.apple.Safari InstallExtensionUpdatesAutomatically -bool true
```

Disable the standard delay in rendering a Web page:

```bash
defaults write com.apple.Safari WebKitInitialTimedLayoutDelay 0.25
```
---

#### Mail:

Disable send and reply animations:

```bash
defaults write com.apple.mail DisableReplyAnimations -bool true
defaults write com.apple.mail DisableSendAnimations -bool true
```

Copy email addresses as `foo@bar.com` instead of `Foo Bar <foo@bar.com>`:

```bash
defaults write com.apple.mail AddressesIncludeNameOnPasteboard -bool false
```

Activate shortcut `⌘ + Enter` to send email:

```bash
defaults write com.apple.mail NSUserKeyEquivalents -dict-add "Send" "@\U21a9"
```

Display emails in threaded mode, sorted by date (oldest at the top):

```bash
defaults write com.apple.mail DraftsViewerAttributes -dict-add "DisplayInThreadedMode" -string "yes"
defaults write com.apple.mail DraftsViewerAttributes -dict-add "SortedDescending" -string "yes"
defaults write com.apple.mail DraftsViewerAttributes -dict-add "SortOrder" -string "received-date"
```

Disable inline attachments (just show the icons):

```bash
defaults write com.apple.mail DisableInlineAttachmentViewing -bool true
```

Disable automatic spell checking:

```bash
defaults write com.apple.mail SpellCheckingBehavior -string "NoSpellCheckingEnabled"
```
---

#### iTerm 2:

Disable the annoying prompt when quitting iTerm:

```bash
defaults write com.googlecode.iterm2 PromptOnQuit -bool false
```
---

#### Time Machine:

Prevent Time Machine from prompting to use new hard drives as backup volume:

```bash
defaults write com.apple.TimeMachine DoNotOfferNewDisksForBackup -bool true
```

Disable local Time Machine backups:

```bash
hash tmutil &> /dev/null && sudo tmutil disablelocal
```
---

#### Activity Monitor:

Show the main window when launching Activity Monitor:

```bash
defaults write com.apple.ActivityMonitor OpenMainWindow -bool true
```

Visualize CPU usage in the Activity Monitor Dock icon:

```bash
defaults write com.apple.ActivityMonitor IconType -int 5
```

Show all processes in Activity Monitor:
```bash
defaults write com.apple.ActivityMonitor ShowCategory -int 0
```

Sort Activity Monitor results by CPU usage:

```bash
defaults write com.apple.ActivityMonitor SortColumn -string "CPUUsage"
defaults write com.apple.ActivityMonitor SortDirection -int 0
```
---

#### Address Book:

Enable the debug menu in Address Book:

```bash
defaults write com.apple.addressbook ABShowDebugMenu -bool true
```
---

#### TextEdit:

Use plain text mode for new TextEdit documents:

```bash
defaults write com.apple.TextEdit RichText -int 0
```

Open and save files as UTF-8 in TextEdit:

```bash
defaults write com.apple.TextEdit PlainTextEncoding -int 4
defaults write com.apple.TextEdit PlainTextEncodingForWrite -int 4
```

#### Disk Utility:

Enable the debug menu in Disk Utility:

```bash
defaults write com.apple.DiskUtility DUDebugMenuEnabled -bool true`<br>`$ defaults write com.apple.DiskUtility advanced-image-options -bool true
```
---

#### Mac App Store:

Enable the WebKit Developer Tools in the Mac App Store:

```bash
defaults write com.apple.appstore WebKitDeveloperExtras -bool true
```

Enable Debug Menu in the Mac App Store:

```bash
defaults write com.apple.appstore ShowDebugMenu -bool true
```

Enable the automatic update check:

```bash
defaults write com.apple.SoftwareUpdate AutomaticCheckEnabled -bool true
```

Check for software updates daily instead of weekly:

```bash
defaults write com.apple.SoftwareUpdate ScheduleFrequency -int 1
```

Download newly available updates in background:

```bash
defaults write com.apple.SoftwareUpdate AutomaticDownload -int 1
```

Install System data files & security updates:

```bash
defaults write com.apple.SoftwareUpdate CriticalUpdateInstall -int 1
```

Automatically download apps purchased on other Macs:

```bash
defaults write com.apple.SoftwareUpdate ConfigDataInstall -int 1
```

Turn on app auto-update:

```bash
defaults write com.apple.commerce AutoUpdate -bool true
```

Allow the App Store to reboot machine on macOS updates:

```bash
defaults write com.apple.commerce AutoUpdateRestartRequired -bool true
```
---

#### Photos:

Prevent Photos from opening automatically when devices are plugged in:

```bash
defaults -currentHost write com.apple.ImageCapture disableHotPlug -bool true
```
---

#### Google Chrome & Google Chrome Canary:

Disable backswipe on trackpads:

```bash
defaults write com.google.Chrome AppleEnableSwipeNavigateWithScrolls -bool false
defaults write com.google.Chrome.canary AppleEnableSwipeNavigateWithScrolls -bool false
```

Disable backswipe on Magic Mouse:

```bash
defaults write com.google.Chrome AppleEnableMouseSwipeNavigateWithScrolls -bool false
defaults write com.google.Chrome.canary AppleEnableMouseSwipeNavigateWithScrolls -bool false
```

Use the system-native print preview dialog:

```bash
defaults write com.google.Chrome DisablePrintPreview -bool true
defaults write com.google.Chrome.canary DisablePrintPreview -bool true
```

Expand the print dialog by default:

```bash
defaults write com.google.Chrome PMPrintingExpandedStateForPrint2 -bool true
defaults write com.google.Chrome.canary PMPrintingExpandedStateForPrint2 -bool true
```