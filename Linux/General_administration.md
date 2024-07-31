# General Linux Administration
## xdg-utils
  The `xdg-utils` package commonly used to to control the applications, files, or directories that are set as default applications set by the user or the desktop enviornment.  
### Configure Default Applications
To configure the default applications used to open files based on their extensions, you need to set the MIME type associations. This can bedone using the `xdg-mime` command or by editing the configuration files directly.  
#### Method 1: Using the `xdg-mime`
1. Determine the MIME type of a file:
  ```bash
  xdg-mime query filetype <file>
  ```
  For example, to find the MIME type of a PDF file:
  ```bash
  xdg-mime query filetype example.pdf
  ```
2. Set the Default Application for a MIME type:
  ```bash
  xdg-mime default <application.desktop> <MIME_type>
  ```
  For example, to set the default application for PDF files to `evince`:
  ```bash
  xdg-mime default evince.desktop application/pdf
  ```
#### Method 2: Edition Configuration Files
The default applications are usually configured in .desktop files and MIME type association files. Here are the typical locations:

1. User-Specific Settings:
  * ~/.config/mimeapps.list
  * ~/.local/share/applications/mimeapps.list
2. System-Wide Settings:
  * `/etc/xdg/mimeapps.list`
  * `/usr/share/applications/`  

To set a default application, edit the mimeapps.list file and add an entry for the MIME type and the corresponding .desktop file.

##### Example: Editing mimeapps.list
