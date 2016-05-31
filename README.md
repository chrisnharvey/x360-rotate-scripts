# x360 Rotate Sripts

Copyright (c) 2016 Chris Harvey

Scripts to fix issues with x360 laptops in Linux.

## Why?

For me, when using my HP Pavilion x360 laptop, there was strange things happening when flipping
the laptop into tablet mode, then back into laptop mode.

When flipping into tablet mode, an icon would appear in GNOME to let me know the touchpad was
disabled, but it wasn't.

When flipping back into laptop mode, Airplane mode would auotmatically enable.

I'm pretty sure this is not the functionality anybody wants, so these scripts disable all of
this from happening and remaps the "flip back" action with a command to disable the touchpad,
and the "flip front" action with a command to re-enable the touchpad.

## Contributing

The way I've done this is probably massively over-complicated, its pretty much transcribed from
everything I was trying late at night to solve this problem and works pretty well for my needs.

If anyone has a better way of doing this, then you're very welcome to submit a pull request.

## Installing

1. Add the ```opt/rotate``` files into ```/opt/rotate``` on your machine and make them executable.
2. Add the ```home/username``` files into your home directory.

## Setting it up

You will need to check that these scripts have the correct keycodes for your laptop.

First, find the ID of your touchpad using the following command

```bash
xinput --list
```

Then replace the number ```13``` with your ID in ```/opt/rotate/back.sh``` and ```/opt/rotate/front.sh```.

Next, find the keycodes for the "flip back" and "flip front" actions by using the following
command.

```bash
xmodmap -pk | grep -i wlan
```

Replace ```wlan``` with the function which is triggered when flipping back, then note down the keycode and
do the same for the "flip front" action, and add it to the ```/opt/rotate/Xmodmap``` file, replacing
```201``` and ```246```.

Now run the following command

```bash
xbindkeys -k
```

and get the keycode for your "flip back" and "flip front" actions, then replace the keycodes in
```/opt/rotate/xbindkeysrc``` with your respective keycodes.

Reboot and enjoy!
