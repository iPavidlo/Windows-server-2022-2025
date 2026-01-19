# Windows-server-2022
How to deploy Windows Server 2022-2025 on a VPS (for beginners)

First, you need to buy a VPS. I recommend [contabo.com](https://contabo.com/) (and I will use it as an example throughout this guide).
However, you can choose any other provider, but when choosing, consider the hardware requirements of WS 2022/25.

A Cloud VPS 20 for $8 will be sufficient for learning WS 2022/25.

When purchasing the VPS server, choose the simplest option (you can choose an NVMe disk).

In the "Login & password for your server" section,
enter a password and remember it.

Then complete the registration.

These guys have a problem with login – the password might not arrive immediately or might not work for login.
So don't panic – just reset the password, and you will receive a new one that you can use to log in.

You can safely go to the new website https://new.contabo.com/

There you will see your server.
Click on the three dots and go to the VNC line (we will need this to monitor what is happening on the server). Configure it by setting a password.


<img width="1493" height="590" alt="Screenshot 2026-01-12 at 20 56 50" src="https://github.com/user-attachments/assets/7cfd6246-6446-4ae5-a593-ec556e1f0006" />

If you have Windows, download any VNC client.
If you have macOS, click on Finder, then press the command+K combination.

Enter a line like this (you should have received this data during setup): for example - vnc://163.98.73.102:63155
Then enter the password you created.

Now you can see what's happening on your server; you can even click on things there. But we don't need that right now. This window is for monitoring.

Next, we need to connect to the server and start configuring it. Since the server currently has Ubuntu installed, we need to transform it into WS 2022/25.

Connect to your server via SSH. Your server information should include an external IP address (for example, 207.180.211.223)

Ssh root@207.180.211.223
Then enter the password 
If you forgot password =)) you can will recover him . Choose ypu server than Click on the three dots and go to Reset credentials.

NExt Enter the following command:

```bash
curl -O https://raw.githubusercontent.com/bin456789/reinstall/main/reinstall.sh && bash reinstall.sh windows --iso 'https://go.microsoft.com/fwlink/p/?LinkID=2195280&clcid=0x409&culture=en-us&country=US' --image-name 'Windows Server 2022 SERVERSTANDARD' --password ‘12345678’
```

Why did we specify --image-name 'Windows Server 2022 SERVERSTANDARD' immediately?

Because if you don't specify it, the script will throw an error during execution, and manually entering the OS selection will be difficult.

Possible options:

'Windows Server 2022 SERVERSTANDARDCORE',  
'Windows Server 2022 SERVERSTANDARD',  
'Windows Server 2022 SERVERDATACENTERCORE',  
'Windows Server 2022 SERVERDATACENTER',  

You can specify one of these.


<img width="1616" height="916" alt="0113 011862 (NOTICE Dounlon conplete oswindous isc" src="https://github.com/user-attachments/assets/7241e9da-d365-47c2-93ed-339daac1128a" />


--iso 'https://go.microsoft.com/fwlink/p/?LinkID=2195280&clcid=0x409&culture=en-us&country=US'

acctual ISO image here 

2025 : https://www.microsoft.com/en-us/evalcenter/download-windows-server-2022

2022 : https://www.microsoft.com/en-us/evalcenter/download-windows-server-2025

You need copy URL from ISO image. ( choose you language )

<img width="1097" height="586" alt="Screenshot 2026-01-18 at 20 57 16" src="https://github.com/user-attachments/assets/f5f745e3-e854-4fdc-88b6-4c7dac15c042" />


After running the script, you will be prompted to reboot the system.
Enter the command `reboot`

***** INFO *****  
windows  
Username: administrator  
Password: 12345678  
Reboot to start the installation.  

The script will provide you with the login credentials for the server. Save them.

Then, via VNC, you simply observe the installation. Once everything is installed, you will see the Windows login screen.


Then connect via RDP using the external IP address 207.180.211.223
Username: administrator
Password: 12345678
