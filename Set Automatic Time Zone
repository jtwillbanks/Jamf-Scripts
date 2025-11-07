#!/bin/bash

uuid=$(/usr/sbin/system_profiler SPHardwareDataType | grep "Hardware UUID" | awk '{ print $3 }')
dTPref="/private/var/db/timed/Library/Preferences/com.apple.preferences.datetime.plist"
tPref="/private/var/db/timed/Library/Preferences/com.apple.timed.plist"

# Enable location services
/usr/bin/defaults write /var/db/locationd/Library/Preferences/ByHost/com.apple.locationd LocationServicesEnabled -int 1
/usr/bin/defaults write /var/db/locationd/Library/Preferences/ByHost/com.apple.locationd.$uuid LocationServicesEnabled -int 1

# Enable automatic timezone
/usr/bin/defaults write "$tPref" TMAutomaticTimeZoneEnabled -bool YES
/usr/bin/defaults write "$tPref" TMAutomaticTimeOnlyEnabled -bool YES
/usr/bin/defaults write "$dateTimePrefs" timezoneset -bool YES
/usr/sbin/chown "_timed:_timed" "$tPref" "$dTPref"

# Restart Location Services
/usr/bin/killall locationd
