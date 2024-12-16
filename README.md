# How to Root a Samsung Galaxy J5 (2016)

Rooting android your first time is a frustrating experience at best,
with lots of bad tutorials and guides that lead to nowhere.
It took me more than necessary to get root priviledges in my phone, therefore I am writing a quick guide for my future self when
he will need my assistance. This document explanins the steps
I took to succesfully root my android phone.

Note that the process may vary in several ways, mainly depending on model
of the phone you are trying to root. This guide is written specifically
for my Samsung Galaxy J5 (2016), however most of the steps should be
similar if you are lucky and the stars allign correctly.

To root a phone we need something with root priviledges to grant us
the same status. Of course, stock Android will never let us get even a glimpse
of this power for security reasons so we need to find a workaround.
The solution is to boot a cusom recovery image, that has
high priviledges, which will let us install some applications with
root status. We can leverage this to install a special app to give permissions
to other apps during normal system execution.

To recap, we need to do the following to achieve root:
1. Boot a custom recovery image
2. Install a special application
3. Enjoy the power

Note that you might mess things up and loose all your data, so be prepared.
I guess you will also loose your device's warranty.

You have been warned :-)

## 1. Boot a custom recovery image

We need to download a custom recovery image for your phone model.
There are many cool looking alternatives, I used TWRP
and It can be downloaded from the official website. Note that you
need to choose the right version based on your phone.
I downloaded the `.img` file, compressed it in a tar archive and renamed
it `recovery.tar`.

```
wget https://.../something.img
tar -cf something.tar something.img
mv something.img recovery.zip
```

Now we need to put this into our device. We need to boot into download
mode which on my smartphone is `VOL_DOWN + HOME + POWER`. After this
we can interact with the device. I used `odin4` (linux version). To check that
oding can talk to the device, run `odin4 -l`: you should expect some
output. If it does not show anything I cannot help you, It is probably
a driver problem, good luck I believe in you, trust in yourself, you 
are strong. If you get some permission error, you need to set something
on your udev, just foollow closely the help output and you should be good to go.

Then load the recovery mode with `odin4 -a recovery.zip` and, IMMEDIATELY
after it finishes, you need to boot in recovery mode, which on my phone
is `VOL_UP + HOME + POWER`. You need to be QUICK, REALLY QUICK!!! Keep
trying until you manage to do this. If everything was succesfull, you are
now greeted with a cool recovery program.

## 2. Install a special application

We now need to install something that will make other things root. We can use
Magisk, you can download the apk from the official github releases
and rename it to a `.zip` file. We need to send It to the device and
we will use `adb` from the official platform tools. Just extract the 
archive.

On the device, select `advanced -> sideload -> swipe to start sideload`.
On your pc, run `adb sideload app-release.zip`, this should install
magisk and it should show the isntallation on the phone. After this
finishes, reboot your phone, go to your apps and open Magisk, It may ask to
be installed again, just say yes, follow the installation instructions
(just tap two buttons), maybe close it and reopen it, reboot and...
we are root!

You can check this by installing RootChecker.

## 3. Enjoy the power

Now that you are root you can do a bunch of cool things like wipe out
everything and install gentoo. A more useful thing would be to install
an adblocker (i suggest `adAway`) so that you can actually read blogs
and news in peace.


# Installing an alternative OS

There are plenty of alternatives and variations of Android out there,
the only constraint is that they need to support your phone.
You could theoretically make your own build but I have no idea
how you would resolve drivers. I aplogise for my ignorance, you'll
have to figure It out some day.
I found [this](https://xdaforums.com/t/rom-signature-spoofing-unofficial-stable-lineageos-17-1-for-j5-2016.4070629/)
unofficial build of /e/OS, hopefully the liks still works.

After you have installed the custom recovery media, you can
start the sideload just as you did for Makisk in the previous
section, and load the downloaded archive. That is really it,
you should have a working OS.
If the process fails and you cannot boot the OS correctly, you
should be able to access the recovery mode on startup assuming
that you can turn off your device. In my experience, when the
boot broke, I could not power It off so I just removed the
battery and rebooted. Unfortunately, you cannot do this in new phones (sight),
so you may try to make It discharge until ti powerd off, gook luck.
