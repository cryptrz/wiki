# Double-click .exe files

To execute a `.exe` file with a double-click on Ubuntu, you need to use Wine, a compatibility layer that allows running Windows applications on Linux. Here's how you can set it up:

## Step 1: Install Wine

First, you need to install Wine on your system. You can do this by running the following commands in the terminal:

`bashsudo apt update
sudo apt install wine`

## Step 2: Install Wine Binfmt

To enable running `.exe` files directly, you also need to install `wine-binfmt`:

`bashsudo apt install wine-binfmt`

## Step 3: Copy Wine Desktop File

Copy the `wine.desktop` file to the applications directory so that it appears in the "Open With" menu:

`bashsudo cp /usr/share/doc/wine/examples/wine.desktop /usr/share/applications/`

Alternatively, you can copy it to your local applications directory:

`bashcp /usr/share/doc/wine/examples/wine.desktop ~/.local/share/applications/`

## Step 4: Associate .exe Files with Wine

Now, right-click on an `.exe` file, go to "Properties," then to the "Open With" tab. Select "Show other applications" and choose Wine from the list. If Wine is not listed, you may need to navigate to `/usr/bin/wine` and select it manually[2](https://ubuntuforums.org/showthread.php?t=2442707)[5](https://www.stableit.blog/2021/08/how-to-associate-exe-files-with-wine-on.html).

## Step 5: Double-Click to Run

After setting up Wine as the default application for `.exe` files, you should be able to run them by double-clicking. However, if your file manager doesn't allow this directly, ensure that the executable bit is set for Wine itself (though this is typically not necessary for Wine to work).

## Note

Running `.exe` files via Wine might not always work perfectly, as it depends on the compatibility of the application with Wine. Additionally, Wine requires more resources than native Linux applications, so it's recommended to use native alternatives when possible[9](https://forum.manjaro.org/t/how-to-install-exe-file-with-double-click-default-installer-wine/84704).

### Citations:

1. [https://stackoverflow.com/questions/42044798/how-do-i-run-a-script-on-linux-just-by-double-clicking-it](https://stackoverflow.com/questions/42044798/how-do-i-run-a-script-on-linux-just-by-double-clicking-it)
2. [https://ubuntuforums.org/showthread.php?t=2442707](https://ubuntuforums.org/showthread.php?t=2442707)
3. [https://superuser.com/questions/131104/double-click-to-run-sh-file](https://superuser.com/questions/131104/double-click-to-run-sh-file)
4. [https://www.reddit.com/r/linux4noobs/comments/x4h2c3/execute_bash_scripts_by_doubleclicking/](https://www.reddit.com/r/linux4noobs/comments/x4h2c3/execute_bash_scripts_by_doubleclicking/)
5. [https://www.stableit.blog/2021/08/how-to-associate-exe-files-with-wine-on.html](https://www.stableit.blog/2021/08/how-to-associate-exe-files-with-wine-on.html)
6. [https://unix.stackexchange.com/questions/363622/a-program-made-in-c-runs-on-double-click-in-windows-but-not-in-linux](https://unix.stackexchange.com/questions/363622/a-program-made-in-c-runs-on-double-click-in-windows-but-not-in-linux)
7. [https://askubuntu.com/questions/138908/how-to-execute-a-script-just-by-double-clicking-like-exe-files-in-windows](https://askubuntu.com/questions/138908/how-to-execute-a-script-just-by-double-clicking-like-exe-files-in-windows)
8. [https://askubuntu.com/questions/1230553/how-to-associate-exe-files-with-wine-on-ubuntu-20-04](https://askubuntu.com/questions/1230553/how-to-associate-exe-files-with-wine-on-ubuntu-20-04)
9. [https://forum.manjaro.org/t/how-to-install-exe-file-with-double-click-default-installer-wine/84704](https://forum.manjaro.org/t/how-to-install-exe-file-with-double-click-default-installer-wine/84704)

---
