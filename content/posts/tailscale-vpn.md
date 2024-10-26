+++
title = 'Tailscale VPN on Pwnagotchi'
date = 2024-07-19T21:04:51+02:00
draft = false
ShowReadingTime = true
ShowToc = true
+++

##  Pwnagotchi + Tailscale. Ditch the micro usb cable and SSH into your Pwnagotchi from anywhere securely.

I had an interesting idea yesterday that turned out to work flawlessly. I was really impressed with the results and the its practical use case, so I figured I would share it the community.

In 2023 I think the Pwnagotchi is the only device I have left that I use regularly which requires a micro USB cable and this can be annoying having to make sure I have a cable with me wherever I take it.

Using Tailscale and bluetooth tether to your phone, you are able to install Tailscale directly onto the pwnagotchi and access it via SSH from any PC logged into your private Tailscale network. This allows a sort of wireless tether from any computer logged into your private Tailscale network for easier SSH without the use of a micro usb cable.

**This assumes you have properly configured bt tether and are able to access the internet on your pwnagotchi via bluetooth. Theres plenty of guides out there for that, so I'm going to skip that part.

Installation is pretty straight forward.

-- If you dont already have Tailscale, head to https://tailscale.com and create an account.

-- Download and install Tailscale on whatever computer you want to ssh from.

-- Connect your pwnagotchi to your computer using a micro usb cable and ssh into it.

-- Download and install Tailscale on your pwnagotchi.

apt update

curl -fsSL https://tailscale.com/install.sh | sh

-- Once Tailscale has installed on your pwnagotchi, login using a generated QR link. You can scan the QR code and authenticate from your phone.

tailscale login --qr

-- Once logged in, head back to your computer and log into Tailscale from your computers browser. Go to the "Machines" section, copy your pwnagotchis new Tailscale IP and ssh back in using that IP (dont forget to include the user name) ssh pi@xxx.xxx.xxx.xx.

What also neat is this is (in my opinion) a better way to exfiltrate keys to your computer without the need to upload them online. You can simply scp them to your computer directly through ssh/scp completely wirelessly. This also eliminates the need to pair multiple devices to your pwnagotchis bluetooth. Additionally, you can also access the WebUI using its new Tailscale IP through port 8080.

Hopefully someone finds this as useful as I did. 
