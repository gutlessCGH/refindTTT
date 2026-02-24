# Refind Tricky Transparencies Theme

This Refind boot manager theme uses transparency to vibrantly highlight and reveal a text label for only the selected icon.

![Preview](preview.webp)

### Installation

Copy the theme folder to a `themes` directory inside the refind EFI directory (usually `/boot/EFI/refind`)

**Example**
>                                               
	sudo mkdir /boot/EFI/refind/themes                            (ignore command or error if directory exists)
	sudo cp -r ./refindTTT /boot/EFI/refind/themes/refindTTT	  (right click to open terminal in downloads folder)

Then add `include themes/refindTTT/theme.conf` at the end of /boot/EFI/refind/refind.conf
>

	sudo nano /boot/EFI/refind/refind.conf                    (ctrl+u to paste, ctrl+s to save, ctrl+x to exit)


### Customization

Open /refindTTT/theme.conf and follow directions to edit:

* Maximum number of icons shown (default 7 should fit like the preview on a 1920 pixel wide monitor)
* Timeout before automatic boot
* Selection backgrounds (set alternates to hide text label)

Text color can be modified by editing selection_big.png & selection_small.png.  Paint over the bottom 50 pixels of the white square in big, the bottom 30 pixels of the white square in small.  Keep the edges transparent.

### Setting Custom Icons

If the specific icon isn't automatically applied for a distro, the easiest solution is just to rename the correct one to os_linux.png or os_unknown.png. 

The partition of the install can be renamed to match the distro/icon or vice versa.

More extensive fixes can be done by adding a boot stanza to /boot/EFI/refind/refind.conf

**Example**
>

	menuentry " ****** " {                                      (replace ****** with OS name)
		icon /EFI/refind/themes/refindTTT/icons/******.png      (replace ****** with icon name)
	    loader /vmlinuz-linux-******                            (replace ****** to match file name in /boot )
	    initrd /initramfs-linux-******.img                      (replace ****** to match file name in /boot )
	    options "quiet ******"                                  (replace "quiet ******" with boot options)
	    }
    
Boot options may be found in refind_linux.conf (sudo nano /boot/refind_linux.conf).   After booting into an OS copy the long string in quotes after "Boot with standard options"

Entries can be hidden in Refind by pressing the 'delete' key.
