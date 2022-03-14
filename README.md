
# Create Self-Signed SSL Certificate

## Prerequisites ✅
1. Download and extract this project - [_SELF-SIGNED-CERT-SSL.zip](https://bitbucket.org/KingsleyChimezie/create-self-signed-ssl-certs/raw/909eff16c22ecd25ec98cf29bde51b6f95eed745/_SELF-SIGNED-CERT-SSL.zip)
1. Have your local web server set up, I recommend Apache via [AMPPS](https://ampps.com/downloads/) stack.

## Video Guide / Demo 🎥
[![<Enter Alt Text - KMP>](https://img.youtube.com/vi/WY1MxGzjI0o/0.jpg)](https://youtu.be/WY1MxGzjI0o "KCC Video Guide")

---
## Create Self Signed Certificate - Windows

1. [Download and install Win64 OpenSSL v1.1.1m](https://slproweb.com/products/Win32OpenSSL.html#:~:text=of%20the%20installation.-,Win64%20OpenSSL%20v1.1.1m,-EXE%20%7C%20MSI)

1. Copy the extracted project folder **_SELF-SIGNED-CERT-SSL** to anywhere in your C drive e.g. - `C:\`
    - Edit **1-domains.ext**
        - Add YOUR_HOSTNAME, YOUR_HOST_IP  
        - Any other hostname or IP, make sure you follow the next number e.g. `DNS.3` or `IP.3`.
    - Edit **2-genssl.txt** (optional)
        - Search for `/C=IE/CN=Kingsley Chimezie Creations (KCC)` - edit appropriately with your details
        - Search for `/C=IE/ST=Leinster/L=Dublin/O=Server/CN=localhost` - edit appropriately with your details

1. Copy all content in 2-genssl.txt (CTRL+A - CTRL+C)

1. Run **start.bat** found in the project folder OR go to `C:\Program Files\OpenSSL-Win64` and run start.bat from there.

1. start.bat will open a Command Prompt terminal window - navigate into the project folder in your C drive from the terminal.
    ```
    $ cd C:\_SELF-SIGNED-CERT-SSL
    $ <RIGHT CLICK TO PASTE COPIED CONTENT FROM 2-genssl.txt>
    $ <PRESS ENTER>
    ```

1. You should see generated content in the project folder in your C drive

1. Double click **RootCA.crt**
    1. Click "Install certificates..."
    1. Select "Local Machine" --> click "Next"
    1. Select "Place all certificates in the following store" --> click "Browse..."
    1. Select 2nd folder "Trusted Root Certification Authorities" --> click "OK" --> click "Next"
    1. Click "Finish"  
    - N.B: To enable SSL on other computers that browser the domains/IPs you added in 1-domains.ext:
        1. Copy and use the same RootCA.crt to any other computer
        1. For Windows, just follow the above steps to install the RootCA.crt
        1. For Mac, add the RootCA.crt in your keychain and enable "always trust"


### Configure self-signed SSL with AMPPS

- In the project folder in your C drive - i.e. `C:\_SELF-SIGNED-CERT-SSL`
    
1. Enable file name extensions.  
For Windows 10, at the top of your folder settings: click "view" --> enable "file name extensions"

1. Copy the **server.crt** file

1. Navigate to the folder **SSL_LOCATION-WINDOWS-AMPPS** and then **ssl_crt - Shortcut (C Drive)**  
If you did not install AMPPS in the default C drive location, go to: `<YOUR_AMPPS_LOCATION>\apache\conf\ssl_crt`
    - change server.crt to **server.crt.bak**
    - paste the copied server.crt file

1. Go back to the project folder in your C drive - i.e. `C:\_SELF-SIGNED-CERT-SSL`

1. Copy the **server.key** file

1. Navigate to the folder **SSL_LOCATION-WINDOWS-AMPPS** and then **ssl_key - Shortcut (C Drive)**  
If you did not install AMPPS in the default C drive location, go to: `<YOUR_AMPPS_LOCATION>\apache\conf\ssl_key`

    - change server.key to **server.key.bak**
    - paste the copied server.key file

1. Start or Restart AMPPS

1. Browse any of the domains you set in 1-domains.ext using HTTPS - e.g. https://localhost or https://127.0.0.1

### Configure self-signed SSL with XAMPP
...

---
© 2022 Kingsley Chimezie | [Kingsley Chimezie Creations](https://kingsley.tech)
