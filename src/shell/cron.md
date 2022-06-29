# Cron


## `$PATH`

Cron does not have the same environment as the graphical user and may not find
executables unless their full paths are provided.

## Sending notifications

`notify-send` needs the DBUS session address to display the notification.

This job shows a notification every minute after getting the `DBUS_SESSION_BUS_ADDRESS`:

```bash
*/1 * * * * eval "export $(egrep -z DBUS_SESSION_BUS_ADDRESS /proc/$(pgrep -u $LOGNAME gdm-x-session)/environ)"; notify-send "hello world"
```
