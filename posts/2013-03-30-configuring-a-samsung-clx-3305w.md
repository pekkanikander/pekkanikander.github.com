---
layout: post
title: "Manually configuring a Samsung CLX-3305W"
description: ""
category: 
tags: [printing, wlan, bonjour]
---
{% include JB/setup %}

## Samsung CLX-3305W with Mac OS X 10.7 over existing WLAN

My father in law couldn't get his Samsung CLX-3305W to work from his
Mac OS 10.7 Macs on his already existing WLAN.  The problem turned out to be that
his WLAN base station does not properly pass through 
[Bonjour][bonjour], the local
name service protocols that Apple devices use to locally discover each
other and various devices, such as printers.  Or that Mac OS X 10.7
has problems with Bonjour and bridging.  Anyway, if the WLAN base
station does not pass Bonjour packets from the printer to the Mac or
vice versa, the Mac does not "see" the printer, and printing fails.
One way to solve the problem is not to use Bonjour, but give the
printer a static IP address and configure the Mac to use the static IP
address to connect to the printer.  A perhaps more proper way would be
to give the printer a static DNS name, but most people don't have the
luxury of running a local DNS server.  Hence, I took the a little bit
hacky road of assigning a static IP address to the printer.  It seems
to work just fine.

[bonjour]: http://en.wikipedia.org/wiki/Bonjour_(software)

To summarise, the steps to solve the problem was as follows.  There
may be simpler ways, with fewer steps, but this one works, or at least
worked for me twice.

1. Connect the printer directly to a Mac with an Ethernet cable.
2. Add the printer normally, with Bonjour.
3. Log in to the printer's Web-based admin interface.
4. Configure the printer to join the WLAN.
5. Configure the printer *use a static IP address*.
6. Disconnect the Ethernet and delete the previously added printer
   from the Mac `Print & Scan`.
7. Add the printer again, this time using IPP and the static IP address.

While the steps above may be enough for a typical
[IETFer](http://www.ietf.org), for the benefit for those who don't
know what a static IP address is that well, there are detailed steps
below.   If you find any errors or misleading steps, please [let me
know][feedback] and I'll fix this blog post.

1. Get an Ethernet cable.  Connect one end of the cable to the back of
the printer, the other end to your Mac.  Do *not* connect the printer
and the Mac with an USB cable.

    *  If you have previously added the printer with USB, it may be good
       to remove any previous printer drivers that you may have added
       previously, for example, by connecting the the printer with an
       USB cable to your Mac.  This is just to avoid confusion later.
       But see below.

2. Add the printer normally, with Bonjour.

    1. On the Mac, launch ``System Preferences`` .
    2. In ``System Preferences``, select ``Print & Scan``.
    3. In `Print & Scan`, if you have any previous Samsung CLX-3305W
       printers, consider removing them; see above.
    4. Click the `+` below the printer list to add a new printer.
    5. Depending on your settings and operating system version, there
       may be a box showing the printer in `Nearby Printers`, or
       not.  If it is there, simply select it.  Otherwise click ``Add
       Printer or Scanner...``.

        * On the Add dialog box, you should see your CLX-3300 Series
          printer.  Select it and `Add` it.
  
3. Log in to the printer's Web-based admin interface.

    1. Launch the Print Queue for the newly added printer.

        * If you are still in System Preferences `Print & Scan`,
          select the new Samsung CLX-3305 printer and click
          `Open Print Queue...`.

    2. Select `Settings` and then `the General Tab`.
    3. Click the `Show Printer Webpage...` button.

       ![Mac Open Printer Webpage](/images/Mac-Open-Printer-Webpage.tiff)

    4. A new window is opened on your web browser, with the printer's
       Web-based admin interface.
       
       ![Samsung CLX3305W Login window](/images/Samsung-CLX3305W-login-window.tiff)

    5. Click `Login` on the right upper hand side of the window.
       (Expand or scroll the window if you don't see the button.)
    6. Log in with the ID `admin` and Password `sec00000`.

       ![Samsung CLX3305W Login Dialog](/images/Samsung-CLX3305W-login-dialog.tiff)

    7. The printer asks you to change the password.  Do as you please.
       If you do change the password, do make sure that you remember
       the new password in the future.  On the other hand, if you have
       a good enough firewall between the Internet and your WLAN,
       maybe you should not change the password so that you will find
       it easily again.  But you may want to disable uPnP on the
       printer. 

4. Configure the printer to join the WLAN.

    1. Select `Settings` -> `Network Settings` and then `Wireless` from
       the Settings area on the left.

       ![Samsung CLX3305W Wireless settings](/images/Samsung-CLX3305W-wireless-wizard.tiff)

    2. In Wireless settings, enable Wireless and use the `Wizard` to
       find your WLAN and set the right password.
        * Click `Wizard`
        * Select the right SSID and click `Next>>`
        * Enter your WLAN WPA password, twice, and click `Next>>`
        * Click `Apply`
    3. You may want to disable WiFi Direct to prevent further
       confusion from having multiple WLANs at your house.
        * Select `Wi-Fi Direct` from the Settings area on the left.
        * Turn `Wi-Fi Direct` to `Off`
        * Click `Apply`

       ![Samsung CLX3305W Wifi Direct](/images/Samsung-CLX3305W-wifi-direct.tiff)
  
5. Configure the printer to *use a static IP address*.

    1. On the Mac, figure out your WLAN IPv4 network prefix.
    2. Go to the `System Preferences` and open `Network`.

        * If you have the WiFi icon in your icon bar, select `Open
          Network Preferences...` from it.

        * Alternatively, open System Preferences from the apple menu,
          click `Show All` and then `Network`.

    3. Select `WiFi`, and record the IP [network
       prefix](http://en.wikipedia.org/wiki/Subnetwork),
       e.g. `192.168.0` or `10.5.1`.  

        * In general, the network prefix are the first three numbers
          before the third period.  (That is not strictly true.  But that
          is close enough for our purposes.)

        ![Mac System Preferences Network Wifi](/images/Mac-System-Preferences-Network-Wifi.tiff)

    4. Pick up an IP address that is likely to be unused.

        * For example, if your network prefix is `192.168.0`, then `192.168.0.13` may be unused.

        * If you want to be sure that the IP address you picked up is unused, use [ping to
          test](http://www.vcn.com/knowledgebase/article.php?id=081).

    5. In the printer configuration window, select `TCP/IPv4` 
       from the Settings area on the left.
    6. For `Assign IP Address`, select `Manually`. 
    7. In the `IP Address:` field, enter the unused IP address you
       picked. 
    8. If you know your subnet mask, gateway address and DNS server
       names, you may enter them but they are not needed.

       ![Samsung CLX3305W TCP/IPv4 settings](/images/Samsung-CLX3305W-tcpip.tiff)

    9. Click `Apply`.

6. Configure the printer not to go asleep.

    1. In the printer configuration window, go to `Settings` ->
       `Machine Settings`.
    2. Disable `Auto Power Off:` ja `System Timeout:`.
       These prevent your printer from going to sleep, enabling
       you to print over WLAN without needing to go to the printer
       and manually waking it up.

       ![Samsung CLX3305W Machine settings](/images/Samsung-CLX3305W-keep-awake.tiff)

7. Disconnect the Ethernet cable from between your Mac and the
   Printer.

8. Delete the recently added printer.

    1. Go to `System Preferences` and there to `Print & Scan`.
    2. Select the right printer and click `-`.
    3. Click `Delete Printer`.

9. Power cycle the printer to make sure it uses the WLAN and
   the newly configures static IP address. 

10. Add a new printer using the static IP address.

    1. In `System Preferences` `Print & Scan`, click `+`.
    2. In the opened `Add` dialogue, click `IP`.
    3. In the `Address:` field, enter the static IP address
       that you previously configured for the printer,
       e.g. `192.168.0.13`.
    4. For the protocol, select `Internet Printing Protocol - IPP`.
    5. Give a nice name for your printer, e.g. `Samsung Living Room`.
    6. For `Use:` (the driver), you can use `Generic PostScript
       Printer` if you don't get any better proposal for the printer
       type.

       ![Mac Add Printer manually](/images/Mac-Add-Printer.tiff)

    7. Click `Add`.
    8. Go through any further dialogue boxes you may get.

That should do it.  If you try, and it doesn't work, please [send me
e-mail][feedback].

[feedback]: mailto:pekka.nikander@iki.fi?subject=Re:%20Manually%20configuring%20a%20Samsung%20CLX-3305W
