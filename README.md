# polybar-timezone-switcher-script
A custom polybar script to easily switch the timezone of the date displayed.

## Config

```ini
[module/countdown]
type = custom/script
exec = ~/.config/polybar/termdown.sh
exec-if = [ -s ~/.config/polybar/go.txt ]
tail = true
interval = 1
format-underline = #28d3b1

[module/time-switch]
type = custom/script
exec = TZ=$(sed -n $(awk '{print $1}' ~/.config/polybar/tzcount)p ~/.config/polybar/timezones) date +"%I:%M %p" | echo "$(sed -n $(awk '{print $1}' ~/.config/polybar/tzcount)p ~/.config/polybar/timezones): $(cat -)"
click-left = if [ $(awk '{print $1}' ~/.config/polybar/tzcount) -eq $(wc -l ~/.config/polybar/timezones | awk '{print $1}') ]; then awk '{print $1 - $1 + 1}' ~/.config/polybar/tzcount > ~/.config/polybar/tmp && mv ~/.config/polybar/tmp ~/.config/polybar/tzcount; else awk '{print $1 + 1}' ~/.config/polybar/tzcount > ~/.config/polybar/tmp && mv ~/.config/polybar/tmp ~/.config/polybar/tzcount; fi
interval = 0.1
format-underline = #28d3b1
```
