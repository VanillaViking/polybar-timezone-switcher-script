# Timezone Switcher
A custom ![polybar](https://github.com/polybar/polybar) script to easily switch the timezone of the date displayed.

![tz](https://user-images.githubusercontent.com/46510831/194831836-a6026449-3702-480d-b079-bfb092daed5f.gif)


# Setup
In the directory where your polybar config file resides, run:

`echo 0 > tzcount`

`echo UTC-0 >> timezones`

Replace `UTC-0` with the timezone of your choice. You can add as many timezones as you desire.

## Configuration

Paste this into your polybar config:

```ini
[module/time-switch]
type = custom/script
exec = TZ=$(sed -n $(awk '{print $1}' ~/.config/polybar/tzcount)p ~/.config/polybar/timezones) date +"%I:%M %p" | echo "$(sed -n $(awk '{print $1}' ~/.config/polybar/tzcount)p ~/.config/polybar/timezones): $(cat -)"
click-left = if [ $(awk '{print $1}' ~/.config/polybar/tzcount) -eq $(wc -l ~/.config/polybar/timezones | awk '{print $1}') ]; then awk '{print $1 - $1 + 1}' ~/.config/polybar/tzcount > ~/.config/polybar/tmp && mv ~/.config/polybar/tmp ~/.config/polybar/tzcount; else awk '{print $1 + 1}' ~/.config/polybar/tzcount > ~/.config/polybar/tmp && mv ~/.config/polybar/tmp ~/.config/polybar/tzcount; fi
interval = 0.1
```
To change the date format, replace `"%I:%M %p"` in the exec command with the format of your choice.

Formatting sequences can be found in `man date`.

