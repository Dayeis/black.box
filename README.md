<a href="https://dashboard.unzoner.com/sub"><img align="left" src="https://api.unzoner.com/api/v1.0/countries/available/flags.png"></a><br><br>

<img align="right" src="https://raw.githubusercontent.com/ab77/black.box/master/images/unzoner.jpg" width="125"> `black.box` is a VPN policy routing appliance, which runs on `ARMv7` CPU equipped [Raspberry Pi](https://en.wikipedia.org/wiki/Raspberry_Pi), DD-WRT routers and other[[n8](#footnotes)] devices.

`Unzoner` is a subscription-based service, designed specifically for Internet content un-blocking. Together, they un-block video streaming content across tablets, smartphones, desktops, laptops and TVs over Wi-Fi or LAN. Unzoner subscriptions can also be created manually for use with compatible software, such as [Tunnelblick](http://unzoner.com/#tunnelblick-and-windows) and [Kodi](http://unzoner.com/#kodi).

> <img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/logo.png" width="64"> **TL;DR** find a Raspbery Pi and [flash](http://etcher.io/) it with [this](https://s3.eu-central-1.amazonaws.com/belodetech/blackbox.img.gz) image or try [this](#qemu-or-virtualbox) on a PC or [router](#dd-wrt)
<br>

# instructions

> Due to a [PayPal](https://developer.paypal.com/docs/classic/express-checkout/integration-guide/ECRecurringPayments/) [limitation](https://stackoverflow.com/questions/22682410/express-checkout-for-recurring-payments-does-not-work-for-german-payers), subscriptions are not available in Germany (and China), please use Bitcoin instead or find a way to create PayPal accounts in other region(s).

1. obtain a [Rasberry Pi 3](https://www.amazon.co.uk/Raspberry-Pi-Official-Desktop-Starter/dp/B01CI5879A) starter kit, download and uncompress the [.img](https://s3.eu-central-1.amazonaws.com/belodetech/blackbox.img.gz) file, burn it to a fast 4GB+ SD card with [Etcher](http://www.etcher.io/)[[n3](#footnotes)], then insert the card into the Pi <img align="right" src="https://raw.githubusercontent.com/ab77/black.box/master/images/etcher.gif" hspace="5" vspace="10" width="250">
2. connect the Pi to the Internet using a spare Ethernet port on your router[[n6](#footnotes)] and a 2.5A+ power supply[[n2](#footnotes)]
3. after initial initialisation of around 10-20 minutes depending on your bandwidth[[n5](#footnotes)] and SD card speed[[n10]](#footnotes), visit [http://blackbox.local/](http://blackbox.local/) or [http://blackbox-2.local/](http://blackbox-2.local/) URL
4. click subscribe (if un-blocking) to setup up a PayPal billing agreement[[n11](#footnotes)] and claim your **1 month free** trial or PAYG using Bitcoin[[n7](#footnotes)]
5. once subscribed, you will be redirected back to the [dash](#dashboard) where you can monitor the status of the device
6. configure services you'd like to unblock or disable policy routing and configure exceptions
7. when the dash lights up green, connect to a new Wi-Fi network called `black.box` (passphrase: `blackbox`) or set your default gateway to the `black.box` LAN IP (LAN mode) as shown on the [dash](#dashboard)
8. now try accessing some previously blocked Internet content[[n9](#footnotes)]
9. for issues, please email [support](mailto:blackbox@unzoner.com), IRC channel [#netflix-proxy](https://webchat.freenode.net/?channels=#netflix-proxy) on Freenode, or use the live chat link on the dash
10. to be advised when important stuff happens, subscribe to push notifications on the [dash](#dashboard)

# about
`black.box` devices operate in three distinct modes. Devices connected to the `black.box` Wi-Fi network or routed via the device's Ethernet (LAN) IP address, can (a) typically access popular streaming [services](#services) from anywhere in the world; (b) to provide privacy and anonymity via 3rd party VPN providers; or (c) etablish private VPN links between two or more locations. Application source code is available at [https://github.com/ab77/black.box/tree/master/src](https://github.com/ab77/black.box/tree/master/src) under the [MIT](https://github.com/ab77/black.box/blob/master/src/LICENSE) license.

```
+---------+         +-----------------+
| iOS     |  Wi-Fi  |                 |  Google, Facebook, etc.
| Android | +-----> |    black.box    | +--------------------->
|         |         |    ---------    |
+---------+         |    VPN policy   |
                    |    router       |
+---------+         |                 |
| macOS   |  Wi-Fi  |                 |
| Windows | +-----> |                 |
| Linux   |   LAN   |                 |
+---------+         |                 |
                    |                 |
+---------+         |   Sling TV      |            +----------+
|  Kodi   |  Wi-Fi  |   Netflix       |   tunnel   |          |
|  QEMU   | +-----> |   Hulu          | +--------> | Exit US  +----+
|  DD-WRT |   LAN   |   etc.          |            |          |    |
|  VBox   |         |                 |            +-----+----+ UK |
+---------+         +-----------------+                 |          |
                                                        +----------+
```

## unblocking mode (default)
In the default un-blocking mode, coupled with an active unzoner subscription, `black.box` device allows access to popular streaming [services](#services) in the target region from anywhere in the world. In this mode, the device additionally supports obfuscation/cloaking, in order to function in hostile deep packet inspection (DPI) environments, as well as experimental WAN acceleration mode.

PayPal subscription or Bitcoin credit is required to create a subscription. Subscriptions are priced at **€9.95** per month, with initial **1 month free** (if paid by PayPal). PayPal subscriptions can be [cancelled](#cancellation) at any time.

Alternatively, pay up-front using Bitcoin for as much time as you need. Price quoted based on EUR/BTC exchange rate. Top-up at any point prior to the existing Bitcoin credit expiry, or after. Any unused Bitcoin credit will be rolled over if topping up prior to existing credit expiry. Topping up after credit expiry will strike a new exchange rate.

For performance reasons, un-blocking traffic is not encrypted[[n4](#footnotes)]. When policy routing is enabled (default), all traffic goes out via the local Internet interface, except for selected services. When disabled, all traffic is sent via the tunnel, except for selected services. For security reasons, the tunnel interface may be restricted to only allow specific network ports[[n1](#footnotes)] for streaming, while the local interface is always unrestricted.

## VPN mode
In VPN mode, the device supports a number of popular VPN services, such as [VPNArea](http://vpnarea.com/front?a_aid=blackbox) and [Private Internet Access](https://privateinternetaccess.com). Separate subscriptions/accounts required to access supported VPN services.

## server (pairing) mode
In the server pairing mode, multiple devices can be used to establish private encrypted links. Leave one at home/office and dial back in securely when travelling or on holidays. `Unzoner` subscription is currently not required in this mode.

# dashboard
Once the device is running, the dash is accessible by navigating to [http://blackbox.local/](http://blackbox.local/) while connected to the `black.box` Wi-Fi network or from the LAN. Please do not share your device GUID(s) (the long alpa-numeric string you see in the dash URL) as they are effectively credentials for anyone to access your devices settings and modify them. So, keep them secret.

A live demo dashboard is available [here](https://dashboard.unzoner.com/?guid=49c32595eea15e71129322fbe314a96b).

![black.box dashboard](https://raw.githubusercontent.com/ab77/black.box/master/images/dashboard.png)

If multiple regions are available to un-block, click a country flag in the top right corner of the [dash](#dashboard). The device will re-boot with the new settings and un-block the selected country.

# services
A number of popular services can be selected on the [dash](#dashboard). If the service you require is missing please, email [support](mailto:blackbox@unzoner.com), IRC channel [#netflix-proxy](https://webchat.freenode.net/?channels=#netflix-proxy) on Freenode or use the live chat link on the dash to request it. Also, disabling `Policy Routing` (optionally disabling `Local DNS`) as well as setting all `Services` to `none` will make unknown services work.

# cancellation
Please visit PayPal to cancel your `black.box` subscription.

<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/paypal.png" width="600">

# QEMU or VirtualBox
If you don't have a compatible device, or waiting for one to arrive, you can use your PC with [QEMU](http://www.qemu-project.org/) or Oracle [VirtualBox](https://www.virtualbox.org/) to run `black.box`.

> You can always configure compatible software on your PC, such as [Tunnelblick](http://unzoner.com/#tunnelblick-and-windows) for use with Unzoner without advanced features, such as policy based routing.

## VirtualBox (macOS)
* install QEMU using `Homebrew` or `MacPorts` (we just need the `qemu-img` tool)

```
brew install qemu || sudo port install qemu
```

* install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* download, uncompress, resize and convert the image

```
mkdir -p ~/black.box\
  && cd ~/black.box\
  && wget https://s3.eu-central-1.amazonaws.com/belodetech/blackbox-qemux86_64.img.gz\
  && gunzip blackbox-qemux86_64.img.gz\
  && qemu-img resize -f raw blackbox-qemux86_64.img +2G\
  && VBoxManage convertfromraw blackbox-qemux86_64.img blackbox-qemux86_64.vdi --variant Fixed\
  && rm blackbox-qemux86_64.img
```

* open VirtualBox, create a new `Linux 2.6 / 3.x / 4.x (64-bit)` VM called `black.box` and select the `blackbox-qemux86_64.vdi` image
* set `Network` to `Bridged Adapter` mode and select appropriate uplink
* start the VM and carry on from step [#3](#instructions) in LAN mode

## QEMU (macOS)
* install QEMU and [TunTap](http://tuntaposx.sourceforge.net/download.xhtml) using `Homebrew` or `MacPorts`

```
(brew install qemu || sudo port install qemu)\
  && (brew install tuntap || sudo port install tuntaposx)
```

* start TunTap (MacPorts)

```
launchctl load -w /Library/LaunchDaemons/org.macports.tuntaposx.plist
```

* download, uncompress and resize image

```
mkdir -p ~/black.box\
  && cd ~/black.box\
  && wget https://s3.eu-central-1.amazonaws.com/belodetech/blackbox-qemux86_64.img.gz\
  && gunzip blackbox-qemux86_64.img.gz\
  && qemu-img resize -f raw blackbox-qemux86_64.img +2G
```

* under `System Preferences > Network > Manage Virtual Interfaces`, create `bridge1` and add `Thunderbolt Ethernet` interface to it
* create helper scripts, and mark executable

```
cat << EOF > qemu-ifup.sh
#!/bin/bash
ifconfig bridge1 addm \$1
EOF

cat << EOF > qemu-ifdown.sh
#!/bin/bash
ifconfig bridge1 deletem \$1
EOF

chmod +x qemu-ifup.sh qemu-ifdown.sh
```

* start QEMU

```
sudo qemu-system-x86_64\
  -nographic\
  -drive file=blackbox-qemux86_64.img,media=disk,cache=none,format=raw\
  -net nic,model=virtio,macaddr=$(echo -n "06:" ; openssl rand -hex 5 | sed 's/\(..\)/\1:/g; s/.$//')\
  -net tap,script=qemu-ifup.sh,downscript=qemu-ifdown.sh\
  -machine type=pc\
  -m 1024\
  -smp 2
```

* carry on from step [#3](#instructions) in LAN mode

> if your screen devices are on the same L2 bridge as the QEMU VM, ensure DNS is pointing to the gateway IP.

## QEMU (Linux)
* [download](http://www.qemu-project.org/download/) and install QEMU for your distribution
* install [libvirt](https://libvirt.org/) binary for your platform

```
mkdir -p ~/black.box\
  && cd ~/black.box\
  && wget https://s3.eu-central-1.amazonaws.com/belodetech/blackbox-qemux86_64.img.gz\
  && gunzip blackbox-qemux86_64.img.gz\
  && qemu-img resize -f raw blackbox-qemux86_64.img +2G
```

* start QEMU

```
mkdir -p /etc/qemu\
  && echo "allow virbr0" > /etc/qemu/bridge.conf

sudo qemu-system-x86_64\
  -daemonize\
  -enable-kvm\
  -display none\
  -drive file=blackbox-qemux86_64.img,media=disk,cache=none,format=raw\
  -net nic,model=virtio,macaddr=$(echo -n "06:" ; openssl rand -hex 5 | sed 's/\(..\)/\1:/g; s/.$//')\
  -net bridge,br=virbr0\
  -machine type=pc\
  -m 1024\
  -smp 2
```

* carry on from step [#3](#instructions) in LAN mode

> if your screen devices are on the same L2 bridge as the QEMU VM, ensure DNS is pointing to the gateway IP.

# DD-WRT
Support for [DD-WRT](https://www.flashrouters.com/learn/router-basics/what-is-dd-wrt) flashed routers is currently under development with reduced feature set.

<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/ddwrt-connect.png" width="600">

To install the preview:
* obtain a router with the [latest](http://www.dd-wrt.com/site/support/other-downloads?path=betas%2F2017%2F06-01-2017-r32170%2F) `DD-WRT` firmware (ensure `cURL` and `OpenVPN v2.4` are present in the installed firmware)
* connect to your DD-WRT router using LAN or Wi-Fi
* in Incognito/(In)Private Browsing window, navigate to [DD-WRT](http://dd-wrt.unzoner.com/) and sign-in
* enable `Native IPv6 from ISP` under `Setup -> IPv6`
* navigate to [`Administration -> Commands`](http://dd-wrt.unzoner.com/Diagnostics.asp) page and run

```
curl --insecure https://dd-wrt.unzoner.com/ddwrt | sh
```

* navigate to [`Status -> MyPage`](http://dd-wrt.unzoner.com/MyPage.asp), sign-up and connect

[<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/ddwrt-connected.png" width="200">](https://raw.githubusercontent.com/ab77/black.box/master/images/ddwrt-connected.png) [<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/ddwrt-blackbox.png" width="197">](https://raw.githubusercontent.com/ab77/black.box/master/images/ddwrt-blackbox.png) [<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/ddwrt-diags.png" width="90">](https://raw.githubusercontent.com/ab77/black.box/master/images/ddwrt-diags.png)

# Kodi
Support for [Kodi](https://kodi.tv/) is available without advanced features (e.g. policy based routing) enjoyed by other device types. Requires OpenVPN v2.4 or later.

To install and connect:
* [download](https://kodi.tv/download) and intall Kodi
* install [VPN Manager for OpenVPN](https://github.com/Zomboided/service.vpn.manager)
* create a PayPal [subscription](https://dashboard.unzoner.com/sub) (free trial **not** available)

<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/sub-landing.png" width="600">

* bookmark the page and record your credentials securely
* configure Kodi VPN Manager with `blackbox` VPN provider
* connect with your credentials

# Tunnelblick and Windows
Support for [Tunnelblick](https://tunnelblick.net/) as well as OpenVPN Windows client(s) is available without advanced features (e.g. policy based routing) enjoyed by other device types. Requires OpenVPN v2.4 or later.

To install and connect:
* [download](https://tunnelblick.net/) and intall OpenVPN client
* create a PayPal [subscription](https://dashboard.unzoner.com/sub) (free trial **not** available)

<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/sub-success.png" width="600">

* bookmark the page and record your credentials securely
* download `blackbox` VPN profile for your desired region, import it into Tunnelblick and connect

# iOS
Support for [OpenVPN Connect](https://itunes.apple.com/ca/app/openvpn-connect/id590379981) on iOS is available without advanced features (e.g. policy based routing) enjoyed by other device types.

To install and connect:
* [install](https://itunes.apple.com/ca/app/openvpn-connect/id590379981) OpenVPN Connect client from iTunes Store
* create a PayPal [subscription](https://dashboard.unzoner.com/sub) (free trial **not** available)
* bookmark the page and record your credentials securely
* download `blackbox` VPN profile ([TCP](https://docs.openvpn.net/docs/openvpn-connect/openvpn-connect-ios-faq.html)) for your desired region

[<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/profiles-ios.png" width="200">](https://raw.githubusercontent.com/ab77/black.box/master/images//profiles-ios.png) [<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/download-ios.png" width="200">](https://raw.githubusercontent.com/ab77/black.box/master/images/download-ios.png)

* import the profile into OpenVPN Connect app

[<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/copy-ios.png" width="200">](https://raw.githubusercontent.com/ab77/black.box/master/images/copy-ios.png) [<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/openvpn-ios.png" width="200">](https://raw.githubusercontent.com/ab77/black.box/master/images/openvpn-ios.png)

* connect with your credentials

# Android
Support for [OpenVPN Connect](https://play.google.com/store/apps/details?id=net.openvpn.openvpn&hl=en) on Android is available without advanced features (e.g. policy based routing) enjoyed by other device types.

To install and connect:
* [install](https://play.google.com/store/apps/details?id=net.openvpn.openvpn&hl=en) OpenVPN Connect client from Google Play Store
* create a PayPal [subscription](https://dashboard.unzoner.com/sub) (free trial **not** available)
* bookmark the page and record your credentials securely
* download `blackbox` VPN profile ([TCP](https://docs.openvpn.net/docs/openvpn-connect/openvpn-connect-ios-faq.html)) for your desired region

[<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/profiles-android.png" width="200">](https://raw.githubusercontent.com/ab77/black.box/master/images//profiles-android.png) [<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/download-android.png" width="200">](https://raw.githubusercontent.com/ab77/black.box/master/images/download-android.png)

* import the profile into OpenVPN Connect app

[<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/open-android.png" width="200">](https://raw.githubusercontent.com/ab77/black.box/master/images/open-android.png) [<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/accept-android.png" width="200">](https://raw.githubusercontent.com/ab77/black.box/master/images/accept-android.png) [<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/import-android.png" width="200">](https://raw.githubusercontent.com/ab77/black.box/master/images/import-android.png)

* connect with your credentials

[<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/connect-android.png" width="200">](https://raw.githubusercontent.com/ab77/black.box/master/images/connect-android.png) [<img align="middle" src="https://raw.githubusercontent.com/ab77/black.box/master/images/connected-android.png" width="200">](https://raw.githubusercontent.com/ab77/black.box/master/images/connected-android.png)

# Tomato
Support for [Tomato](https://www.flashrouters.com/learn/router-basics/what-is-tomato) flashed routers is planned in the future.

# technical architecture
`black.box` appliances can functions in a number of modes. In the default `un-blocking` mode, the device automatically connects to the least busy `black.box` exit-node in the target region and routes traffic through the tunnel, while advertising a local Wi-Fi AP to all consumer devices within range.

In `server` mode, the device advertises its private `GUID` and listens for incoming VPN connections from paired device(s). Device(s) in `paired` mode, which have specified the private `GUID` in their configuration, locate and connect to the `server` node, while advertising a local Wi-Fi AP to all consumer devices within range. This mode is useful for establishing point to point links betwen two of more locations.

In `VPN` mode, the device supports connecting to a number of popular VPN services, such as [PIA](https://www.privateinternetaccess.com/), [VPNArea](https://vpnarea.com/) and [VanishedVPN](https://www.vanishedvpn.com.au/). Additional VPN providers can be easily integrated.

There are two more system modes the device can function in, namely `exit-node` and `double-vpn`. These are suitable for white-labelling of the `black.box` service and are not available via the dash. In `exit-node` mode, `black.box` devices advertise themselves to devices running in `un-blocking` mode. This mode is useful for deploying `black.box` exit-nodes anywhere in the world with an Internet connection and a power socket. In `double-vpn` mode, devices both listen for incoming VPN client connections, as well as establish a outbound connection to a down-stream VPN server.

`black.box` devices run on [ResinOS](https://resinos.io/), using [resin.io](https://resin.io/) management back-end. OpenVPN 2.4 is used for building `black.box` VPN tunnels, whether encrypted or otherwise. OpenSSL is compiled with NEON support to accelerate certain cryptographic functions on the `ARMv7` CPUs and linked with OpenVPN. Stunnel and WANProxy are use for obfuscation and/or acceleration. You can expect to get anywhere from 5Mbit/s to 10Mbit/s through the Pi Ethernet interface in unblocking mode and less in VPN mode. VPN providers which use default SHA1 authentication should be a little faster, due to ARMv7 NEON optimisations.

Python 2.7 is used for the main application, together with Linux Bash shell scripts to help interface with the operating system. All Python code is compiled into executables using Nuitka on dynamically provisioned Digital Ocean Droplets for both `armv7l` (QEMU) and `x86_64` architectures and shipped to devices in a secure manner, by first encrypting the payload using OpenSSL. Devices are managed using `resin.io` IoT infrastructure, which runs the `black.box` code inside Docker containers on custom ResinOS images. All runtime code is unpacked onto encrypted disk partitions inside Docker containers with all transient data stored in memory only and disk encryption keys never recorded.

Amazon AWS (EBS) is used to host both the `black.box` API ([demo](https://api.unzoner.com/api/v1.0/ping)) and the device dashboard ([demo](https://dashboard.unzoner.com/?guid=49c32595eea15e71129322fbe314a96b)), which are implemented in Python-Flask and Bootstrap. Amazon RDS is used for transient data storage, persisting for no longer than one hour, and Redis is used for caching.

For subscriptions, the `black.box` API talks to the PayPal Subscriptions API to set-up monthly subscriptions. For Bitcoin payments, the BlockCypher API provides nesessary WebHooks to advise the `black.box` API when a payment has been received as well as a WebSocket notification for the dashboard. No Bitcoin payment provider (middle-man) is used in the Bitcoin payment flow.

Additional management VPS is used to provide `ipinfo` support services as well as execute automated headless video playback tests using  Selenium WebDriver wrapped in Python.

#### footnotes
1. default ports: `80/tcp`, `443/tcp` and `53/udp`
2. The radio in the Pi is weak, please try to locate as close as possible to the streaming device(s) or turn the radio off and use in LAN router mode.
3. [Raspberry Pi 2 Model B](https://www.raspberrypi.org/products/raspberry-pi-2-model-b/) with an [Alfa Network AWUS036NEH](https://www.amazon.co.uk/dp/B003JTM9JY) USB Wi-Fi dongle will also work and may even provide better signal due to the external Wi-Fi antenna.
4. For performance reasons, the tunnel interface provides no additional packet encryption/authentication overheads.
5. The initial application image is currently around 600MB. Subsequent updates are a fraction of that. Monitor by pinging `blackbox.local` from your LAN. If you have multiple `black.box` devices on your LAN, the second device will be called `blackbox-2.local`, the third `blackbox-3.local` and so on. Maximum 5 devices supported.
6. For the paranoid, you can locate the device in your DMZ and restrict access to your LAN, however the device needs unrestricted oubound access to the Internet. Your DMZ should also forward mDNS (avahi-daemon) broadcast packets to your LAN for discovery/dashboard access. The device communicates with a private API at AWS over HTTPS and a number of OpenVPN endpoints to enable functionality.
7. The dash will automatically refresh after Bitcoin payment has been confirmed. This could take a number of minutes, depending on the Bitcoin network load.
8. Supported devices currently include [DD-WRT](https://www.flashrouters.com/learn/router-basics/what-is-dd-wrt) routers, [Kodi](https://kodi.tv/), [Intel NUC](http://www.intel.com/content/www/us/en/nuc/overview.html). If you own a [supported](https://docs.resin.io/hardware/devices/) board, [request](mailto:blackbox@unzoner.com) an image.
9. Try disabling both `Policy Routing` and `Local DNS` on the dash if you are having issues with a particular service. If you have router(s) on your network assigning IPv6 addresses, some IPv6 enabled services may not work (i.e. Netflix). Try disabling IPv6 on your network if this is the case.
10. Not all SD cards are created equal, see [microSD Card Benchmarks](http://www.pidramble.com/wiki/benchmarks/microsd-cards) and get a fast one. Don't get a cheap SD card since even if you get the device up and running initially, it will be very slow and will fail catastrophically shortly after.
11. Subscriptions require PayPal support for recurring payments in the country where the buyer account is located (excludes Germany and Austria).


```
-- v1.0
```

<hr>
<p align="center">&copy; 2016 <a href="http://ab77.github.io/">Unzoner</a></p>
<p align="center"><a href="http://anton.belodedenko.me/"><img src="https://avatars2.githubusercontent.com/u/2033996?v=3&s=50"></a></p>
