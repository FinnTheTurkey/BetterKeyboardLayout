The "Non-standard Canadian Anglophone Multilingual Keyboard", aka "better"
==========================================================================
The "Non-standard Canadian Anglophone Multilingual Keyboard", which I refer to as the "better" keyboard layout, is an unholy mashup of the traditional English (US) keyboard layout and the excellent French (Canada) keyboard layout.
The aim is to let people who are primarily Anglophone but have to write in French decently often a way to efficiently write french without sacraficing speed while typing in English.

This keyboard layout is only available for Linux. It is fully compatible with Wayland and can be selected using the GNOME settings package after a bit of configuration.

But, like, what is it?
-----------------------
This layout puts all the unique characters of French (Canada) keyboards, such as the accents, behind Alt Gr (Right Alt).
This means that by default it is identical to an English (US) keyboard, but once you press AltGr you access the key's meaning in French (Canada)

For example, the key that has " and ' in English (US) continues to be the same, but when AltGr is pressed, it transforms into the accent grave kay, like it is in French (Canada)

Note that in French (Canada) that key would also have "{". Since "{" is already easily accessible in English (US), there is no reason for the "better" keyboard layout to include it on that key.

Here is a visual picture of the keymap, via GNOME Settings:
![This is the keyboard layout](layout.png)

How to install
--------------
As always with Linux, installing this keyboard layout requires changing some config files.
Note: I have only tested this on GNOME with Wayland, but it _should_ work on other desktops as well.

1. Add the layout file.

Download or copy and paste the file in this repository called "better", and put it in `/usr/share/X11/xkb/symbols`

That folder is where all keyboard layouts are stored. This shouldn't ever be a problem, but if for some reason you don't have the English (US) keyboard layout installed, then this layout won't work as well as it depends on Engish (US)

2. Tell the rest of the system it exists.

I don't think this is strictly nessesairy, but if you want the "better" keyboard layout to show up in GNOME Settings, then you need to do this step.

Open up `/usr/share/X11/xkb/rules/evdev.xml` in your favorite editor.

Find where it says `<layoutList>`
  
After the `<layoutList>`, add the following text:
```xml
    <layout>
	 <configItem>
		 <name>better</name>
		<shortDescription>en-fr-better</shortDescription>
		 <description>English/French (Canada, better)</description>
		 <countryList>
			 <iso3166Id>US</iso3166Id>
			 <iso3166Id>CA</iso3166Id>
		 </countryList>
		 <languageList>
			 <iso639Id>eng</iso639Id>
			 <iso639Id>fra</iso639Id>
		 </languageList>
	 </configItem>
    </layout>
```

Now either restart your system, or log out and log in again to restart GNOME.

3. Select it
 
If you're on GNOME, open up GNOME Settings, navigate to "Keyboard", then add a layout. "better" should be under English (Canada), and will show up as "English/French (Canada, better)"

If you're not on GNOME, then check your distro's keyboard settings. If it's not there, then I have no idea what you should do. Have fun!
