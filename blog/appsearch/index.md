---
title: How to Add an AppImage to Linux Desktop Search
date: 2025-08-26
description: This guide will enable you to search for an AppImage via the search function found in many desktop environments. Tested on Cinnamon, should work for other desktops.
categories: ['Tutorial']
draft: false # Change to true to not render the post in on the website
image: "/blog/image/appsearch.png"
---


### Preface
When using Linux, you may come across an application with the extension .AppImage. It is an all in one application that works on any Linux distro, but there are a couple of issues. One of which is that the app won't automatically show up in desktop searches. Luckily, all it takes is 5 minutes to fix this.

### Method 1: Terminal

The first step is optional, but good practice for organizing files. Move the **.AppImage** from your Downloads folder to the correct location. This location varies based on if you want the application to be searchable by all users or just a select number

Access for all users
```bash
mv /dir/of/appimage/<APPNAME>.AppImage /usr/local/bin/
```
or
Access for a specific user
```bash
mv /dir/of/appimage/<APPNAME>.AppImage /home/<USERNAMEHERE>/.local/share/applications/
```

If you have the **icon** for the application, then place it in the proper location

For All users
```bash
mkdir -p /usr/share/Obsidian/icons/
mv /dir/of/<ICONNAME>.png /usr/share/Obsidian/icons/
```

For a specific user
```bash
mv /dir/of/<ICONNAME>.png /home/<USERNAMEHERE>/.local/share/icons/
```

On Debian, the search bar uses **.desktop** files as a kind of detailed shortcut. The location used is under /usr/share/applications/ for all users, but for specific users it also uses /home/\<USERNAMEHERE\>/.local/share/applications/

For all users
```bash
vim /usr/share/applications/<APPNAME>.desktop
```

Inside of the file, enter the following lines

```bash
[Desktop Entry]
Name=<APPNAME>
Comment=Documentation Application Utilizing Markdown
Exec=/usr/local/bin/<APPNAME>.AppImage
Icon=/home/<USERNAMEHERE>/Pictures/<ICONNAME>.png
Terminal=false
Type=Application
Categories=Accessories;
```

For specific users
```bash
vim /home/<USERNAMEHERE>/.local/share/applications/<APPNAME>.desktop
```

Inside of the file, enter the following lines

```bash
[Desktop Entry]
Name=<APPNAME>
Comment=Feel free to write anything here
Exec=/home/<USERNAMEHERE>/.local/share/applications/<APPNAME>.AppImage
Icon=/home/<USERNAMEHERE>/.local/share/icons/<ICONNAME>.png
Terminal=false
Type=Application
Categories=<SEARCHCATEGORYYOUWANT>;
```

From here, try searching for your application!


