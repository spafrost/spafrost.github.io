---
layout: post
title:  "Swollen Li-Ion Battery in Ubiquiti Unifi Cloud Key Gen 2+"
date:   2020-09-04 10:50:18 +0000
categories: tech networking lab
---

If your Cloud Key doesn’t gracefully shut down anymore, the Li-Ion battery inside may be swollen like mine was. 

Let me preface this. I love my UniFi gear, its been reliable and easy to use and I would buy it again – I have recommended similar to friends and family. This could just be an edge case and doesn’t mean they will all do this. I am not looking for compensation or publicity. I am posting this so that others who are out of warranty can get in and resolve this issue without having to “discover as they disassemble”. Batteries can be dangerous, follow this at your own risk – I take no responsibility if you follow these instructions and cause personal injury or property damage. Batteries and Electronics can be dangerous, if in doubt – consult a qualified professional. 

I had a power outage this morning and once my UPS was exhausted my PoE switch went down – and so did everything it powers. That includes a 18 month old Gen 2 Cloud Key +. When I powered back up, one of my cheap Netgear PoE passthrough switches lost its configuration – so I quickly moved some connections around to get back up and running. While moving those connections, I accidentally unplugged my Cloud Key from the US-16-POE switch that powers it.

I noticed that it didn’t give the usual “SHUTTING DOWN IN (X)S” message, and instead died ungracefully along with a clatter from the hard drive head. When I powered it back up, “HARD DRIVE ERROR” showed on the screen. I searched the web, and found this thread describing a similar issue.

Unsurprisingly the device is out of warranty, so I decided to just ignore it for now … until I couldn’t because I was curious.

I plugged a USB-C into the power port, and disconnected PoE. Luckily for my troubleshooting, the USB-C wasn’t quick charge compatible – but what I did see was an error message to the effect of”USB-C INCOMPATIBLE” , and then the usual “SHUTTING DOWN” message. That confirmed, in my mind at least, that it wasn’t a software fault – but rather an issue with the battery, or super cap, or whatever powered the safe shutdown.

So the screwdriver came out, and here is how you get inside with minimal damage. I got inspiration fromthe [FCC listing internal photos here](https://web.archive.org/web/20220110085844/https://fccid.io/SWX-UCKG2P/Internal-Photos/Internal-Photos-3822353). **The device still works without the battery, and if you can – I recommend removing it, as I am guessing the CK keeps trying to charge it/load it and that could have interesting results.**

First, you need to get behind the rear beauty strip. I went in alongside the ethernet port. Watch out, this plastic scars if you bend it too far.

![Getting under the cloud key rear plastic](https://i.imgur.com/i9IRSLs.jpg)

Peel slowly enough and you can do this without too much damage

![CK2 rear plastic removed](https://i.imgur.com/7pnt3Wz.jpg)

Pop out the screws you can see, and then pull out the rear chassis plate.

![CK2 rear chassis place](https://i.imgur.com/ouvztI1.jpg)

Flip the device, and pull up the plastic around the screen in the same way as the back. Be blinking careful, there is a ribbon cable in here!

![lifting ck2 screen](https://i.imgur.com/H8wv6Mh.jpg)

See the cable here, don’t rip it! My advice is to go in from the top, not the bottom as I did. Now take out the two screwsit reveals.

![delicate ribbon cable](https://i.imgur.com/aaBBNou.jpg)

You now need to get the Rack kit connector surround off. Its clipped in, so I went in with a fine screwdriver. There are 4 clips, so target those.

![removing rack kit connector](https://i.imgur.com/k3rWRba.jpg)

Now remove the ribbon cable, you can see the clips here. Poke the cable back inside the unit.

![remove this connector](https://i.imgur.com/sDQpqxH.jpg)

You now need to get the Hard Drive release catch out. This is done from inside by deforming the clips with a screwdriver and pushing it out. Its the grey bit in the middle.

![hard drive catch](https://i.imgur.com/84zckdG.jpg)

A push on the back now slides the insides out of the front, like so.

![slide the guts out](https://i.imgur.com/ZdN9k4n.jpg)

Mine was REALLY tough to push at first, this is why. Getting this out was terrifying due to the amount of force required, and the risk of puncturing the cell.

![scary pillow](https://i.imgur.com/o8dcbTT.jpg)

As it slides apart, watch out for the sil-pad and aluminium spacer on top of the chipset. If you don’t make sure it comes out straight, this happens!

![spacer and thermal pad](https://i.imgur.com/MjcOoNY.jpg)

Luckily, I didn’t damage anything and a bit of fiddling got it all apart.

The battery finally out

![the battery](https://i.imgur.com/maDGE8F.jpg)

It still has something in it,

![measuing the battery](https://i.imgur.com/2i2rzuI.jpg)

Here are the numbers,

![battery details](https://i.imgur.com/VUSMiJK.jpg)

Here is what’s inside.

![spicy pillow](https://i.imgur.com/D3ZaAip.jpg)

I will probably end up rebuilding the battery with some bare cells. Glad I looked inside!