Transmission Interface Binder
=============================

A standalone application to bind Transmission to a device interface. (tun0, ppp0, etc.)

This OS X application will allow you to tunnel your Transmission traffic through an interface of your choice. Transmission falls short because it only offers the ability to bind to the IP address of an interface, these are dynamic, so every time you reconnect to your VPN this IP will change.

![alt tag](https://raw.githubusercontent.com/joshbernfeld/Transmission-Interface-Binder/master/Preview/main.png)

By downloading this software, you agree the software is provided “as is” without warranty of any kind. You also hold the creator of this software free of all liability and responsibility for any actions or results or adverse situations created as a result of using this software.

Now the that legal stuff is over. You can download the binary for OS X 10.9 (and likely up) from **[here.](https://github.com/joshbernfeld/Transmission-Interface-Binder/blob/master/OS%20X%2010.9/Transmission%20Interface%20Binder.zip?raw=true)**

**How does this work?**

A device interface of your choice is monitored by the application in the background for changes. If the interface is created, destroyed or altered (IP change), its local IP will be retrieved and written into the BindIPV4Address field of the Transmission configuration file. If this happens while Transmission is running, Transmission will be gracefully restarted and will then bind to the newly provided IP address.


**If my VPN disconnects while Transmission is open and the Interface Binder is running, will traffic revert to my default network?**

**No.** When Transmission first starts it will bind to the IP address of your selected interface. If that IP address and interface disappear, it will stay bound to it but no traffic will pass through. You will see your seeders disconnect and any outgoing connections dropped.

**What does it look like when I am not connected to my VPN and I try to open Transmission with the Interface Binder running?**

![alt tag](https://raw.githubusercontent.com/joshbernfeld/Transmission-Interface-Binder/master/Preview/alert.png)

**I tunnel all of my traffic through my VPN, why should I use this?**

If your VPN disconnects while Transmission is running and it is not bound to a manually set IP address, your traffic will revert to your default network.
If you open Transmission while your VPN is disconnected, traffic will travel through your default network.

**Why has this feature not been implemented directly into Transmission?**

The feature is not a particularly easy and straightforward one to implement. Especially considering it needs be done for multiple platforms, some of which may not even support the feature to begin with. Since it is a feature that a small amount of advanced users would use, the amount of code required to implement the feature would not be worth it. Some code patches have been presented which implement the feature, but they are not short. They also need to be recompiled for each version of Transmission, which most people are not capable of doing.
