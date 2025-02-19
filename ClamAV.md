# Overview

The Virus Scanner interface scans your cPanel account for security threats. If ClamAV® Virus Scanner identifies a security threat, the system prompts you to perform an action.

# Scan a service

To begin a scan on your account, perform the following steps:

1. Select the service to scan.
- Scan Mail — This setting scans all of your account’s mail folders.
- Scan Entire Home Directory — This setting scans your account’s home directory.
- Scan Public FTP Space — This setting scans all of the folders that you can publicly access through FTP services.
- Scan Public Web Space — This setting scans all of the folders that you can publicly access through the web.
2. Click Scan Now. During the scan a new interface will appear with the following information:
- File — This displays the number of files that the system has scanned. It also displays the total number of files to scan.
- Data — This displays the amount of data that the system has scanned. It also displays the total amount of data to scan.
- Scanner Progress — This displays the scan’s progress.
- Infected Files — This lists files in which the scan detects malicious software. The system may require several minutes to complete the scan. After the system completes the scan, it will return you to the Virus Scanner interface.


# Install ClamAV Scanner

To install or uninstall ClamAV, navigate to WHM’s Manage Plugins interface (WHM >> Home >> cPanel >> Manage Plugins), and then click "Install ClamAV for cPanel".

We strongly recommend that at least three gigabytes (GB) of RAM exist on your server if you install ClamAV. Your server may experience performance issues if it lacks enough RAM and you use ClamAV.
 

Please see our documentation for more information on ClamAV: https://docs.cpanel.net/whm/plugins/configure-clamav-scanner/
