On an Arch Linux system running Hyprland (Wayland), you have several tools available to scan for and configure your HDMI monitor.


  1. hyprctl (Recommended)
  Since you are using Hyprland, this is the most direct tool. It is built into the compositor and provides detailed information about connected displays.

  To list all connected monitors and their current configurations, run:
   1 hyprctl monitors
  To see all available monitors (including those not currently active or configured), use:


   1 hyprctl monitors all

  2. wlr-randr
  This is the Wayland equivalent of the classic xrandr tool for wlroots-based compositors like Hyprland. It is excellent for quick command-line queries and adjustments.


  If you don't have it installed:
   1 sudo pacman -S wlr-randr
  To scan for monitors:
   1 wlr-randr


  3. nwg-displays (GUI)
  If you prefer a graphical interface to arrange your monitors and set resolutions, nwg-displays is a popular choice for Hyprland users. It generates the necessary output configuration for you.

  To install it:
   1 sudo pacman -S nwg-displays


  4. kanshi
  While not a "scanner" per se, kanshi is used to define display profiles that automatically switch when you connect or disconnect your HDMI monitor.

  To install it:
   1 sudo pacman -S kanshi


  Next Step: I recommend starting with hyprctl monitors to see how Hyprland currently perceives the HDMI connection. If you'd like help writing the configuration for your hyprland.conf, let me know the output of
  that command!

