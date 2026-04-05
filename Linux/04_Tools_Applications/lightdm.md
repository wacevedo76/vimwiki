for debian, create dwm.destop -> /usr/share/xsessions
example file:
  [Desktop Entry]
  Encoding=UTF-8
  Name=Dwm
  Comment=Dynamic window manager
  Exec=dwm
  Icon=dwm
  Type=XSession

You can also run a custom script from the Exec= directive
script location recommendation: /usr/local/bin
