# DISCLAIMER

This script is outdated. Please use the [info-timezone](https://github.com/polybar/polybar-scripts/tree/master/polybar-scripts/info-timezone) script in the official polybar scripts repository.



# Timezone Switcher
A custom ![polybar](https://github.com/polybar/polybar) script to easily switch the timezone of the date displayed.

![tz](https://user-images.githubusercontent.com/46510831/194831836-a6026449-3702-480d-b079-bfb092daed5f.gif)


# Setup
In the directory where your polybar config file resides, run:

`echo UTC-0 >> timezones`

Replace `UTC-0` with the timezone of your choice. You can add as many timezones as you desire.

Copy `tz-switcher.sh` into your config directory

## Configuration

Paste this into your polybar config:

```ini
[module/time-switch]
type = custom/script
exec = ~/.config/polybar/tz-switcher.sh
tail = true
click-left = kill -USR1 %pid%
```
To change the date format, replace `FORMAT` variable in tz-switcher.sh with the format of your choice.

Formatting sequences can be found in `man date`.

