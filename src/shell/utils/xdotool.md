# xdotool

## Move mouse to center of active window

`xdotool getactivewindow getwindowgeometry` gets the active window geometry

```
Window 56623115
  Position: 2297,22 (screen: 0)
  Geometry: 1143x1386
```

and adding the `--shell` flag returns the output as machine readable.

```
WINDOW=56623115
X=2297
Y=22
WIDTH=1143
HEIGHT=1386
SCREEN=0
```

Running this with eval stores each geometry value as a shell variable. This can
be put into a script using `bc` to calculate the center position:

```bash
eval $(xdotool getactivewindow getwindowgeometry --shell)
xdotool mousemove -w $WINDOW $(echo $WIDTH/2 | bc) $(echo $HEIGHT/2 | bc)
```
