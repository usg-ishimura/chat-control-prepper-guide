# Chat control 2.0 prepper guide (just in case)

The chat control controversal EU proposal aims at breaking messaging apps end-to-end encryption introducing a state of mass surveillance in Europe. Motivated by the alleged defense of minors on the internet it's in fact violating EU people civil and privacy rights. This proposal could lead to false positives, data leaks and law enforcement abuse.

This guide shows how to configure a safe XMPP server with OMEMO cryptography, to protect confidentiality of personal comunications.

You will need a VPS and a domain name associated to it from a cloud provider of your choice, possibly choose a datacenter near your location, you can choose on prem hosting as well. In this guide I use Debian 12 running openfire XMPP server and Conversations an Android FLOSS app that supports e2e encryption that you can download from f-droid on your phone.

Once you secured your server and logged with SSH to it, you can run:

```sh
wget https://www.igniterealtime.org/downloadServlet?filename=openfire/openfire_5.0.2_all.deb -O openfire_5.0.2_all.deb
sudo su
apt update
apt install openjdk-17-jre-headless
apt --fix-broken install
dpkg -i openfire_5.0.1_all.deb
systemctl start openfire
apt install ufw
ufw allow 22  # or the custom port you use for SSH
ufw allow 9090
ufw allow 9191
ufw allow 5222
ufw allow 5269
ufw enable
```
At http://domain.federation.org:9090 (a template domain name, you can choose yours) you can follow this setup wizard steps, it would be safer if you completed the setup locally and only then opened ports on firewall:

<img width="1366" height="607" alt="Screenshot_20250813_182402" src="https://github.com/user-attachments/assets/783d2a2d-ab81-4cf0-8148-82f9b24ef9ee" />
<img width="1364" height="524" alt="Screenshot_20250813_182416" src="https://github.com/user-attachments/assets/0efd2358-ea4e-4430-a9b1-48be8b8de43c" />
<img width="1364" height="535" alt="Screenshot_20250813_182426" src="https://github.com/user-attachments/assets/fae87aa8-7fd0-40d1-b92b-cc7e2d7e188b" />
<img width="1366" height="573" alt="Screenshot_20250813_182507" src="https://github.com/user-attachments/assets/89a26249-8393-4dcb-87bf-30d1818433f4" />
<img width="1364" height="448" alt="Screenshot_20250813_182608" src="https://github.com/user-attachments/assets/34f40ec4-a3aa-4cf9-a02e-22170853aa91" />

Then from f-droid at this link https://f-droid.org/it/packages/eu.siacs.conversations/ you can download Conversations and register your username to the federation like so:

![WhatsApp Image 2025-08-13 at 18 36 29](https://github.com/user-attachments/assets/4c5cae0f-5c7d-48d3-b090-488f48883fa9)

OMEMO will be implemented by default, and you will be able to add contacts from your federation or others and begin an end-to-end encrypted chat.

![WhatsApp Image 2025-08-13 at 19 05 20](https://github.com/user-attachments/assets/e50d5606-beb6-4d21-b3aa-5bc5347a0ac5)
