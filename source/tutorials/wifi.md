[[
title: Wifi Tutorial
description: How to Connect to PAL3.0/Eduroam
tags: [wifi, tutorial]
]]

# Connect with Network Manager

Click on the wireless icon in your tray area. Select "Connect to Hidden Wi-Fi Network" or choose PAL3.0 and enter these settings.

    Network Name: "PAL3.0"

    Wireless Security: WPA & WPA2 Enterprise

    Authentication: Protected EAP (PEAP)

    Key Type (if present): TKIP

    Phase2 Type / Inner Authentication: MSCHAPV2

    Identity / Username: Your Purdue Login

    Password: Your Purdue Password

    Anonymous Identity: (leave blank)

    Client Certificate File (if present): (None)

    CA Certificate File: /etc/ssl/certs/AddTrust_External_Root.pem or /etc/ssl/certs/AddTrust_External_CA_Root.pem

    Private Key File: (None)

    Private Key Password: (leave blank)

    'PEAP' version: choose 'Version 0'.

![image](PAL3example.png)

Click save.

# Connect with iwd

These instructions will allow you to connect to Eduroam using iwd, the replacment for wpa_supplicant.

Create the file /var/lib/iwd/eduroam.8021x

    [Security]
    EAP-Method=PEAP
    EAP-Identity=anonymous
    EAP-PEAP-Phase2-Method=MSCHAPV2
    EAP-PEAP-Phase2-Identity="Username"
    EAP-PEAP-Phase2-Password="Password"
    
    [Settings]
    Autoconnect=true
    
Manually connect with

    $ iwctl station <wifi station> connect eduroam
    
Get wifi stations with

    $ iwctl station list
