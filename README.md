# Github-Auto-Trigger

# Expose On-prem Jenkins to Cloud Github account for Auto Build Trigger when push the code.
Here’s a clean and copy-ready section for your GitHub README file to document **Ngrok installation and systemd service setup** for Jenkins:

---

## 🚀 Ngrok Installation & Configuration for Jenkins

### 🔧 Install Ngrok

```bash
wget https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-stable-linux-amd64.zip
unzip ngrok-stable-linux-amd64.zip
sudo mv ngrok /usr/local/bin/
```
### Connect your ngrok account (optional but recommended)

Create a free account at:
👉 https://ngrok.com

Then, after logging in, you’ll find your auth token under “Setup & Installation”.

Copy it and run:

**ngrok config add-authtoken <your_auth_token_here>**

### 🛠️ Create a systemd service for Ngrok

```bash
sudo vi /etc/systemd/system/ngrok.service
```

Paste the following content:

```ini
[Unit]
Description=Ngrok Tunnel for Jenkins
After=network.target

[Service]
ExecStart=/usr/local/bin/ngrok http 8080
WorkingDirectory=/root
Restart=always
User=root

[Install]
WantedBy=multi-user.target
```

### ▶️ Enable and Start the Service

```bash
sudo systemctl daemon-reload
sudo systemctl enable ngrok
sudo systemctl start ngrok
```

> ✅ This will expose Jenkins running on port 8080 to the internet via Ngrok. You can view the public URL using `curl http://localhost:4040/api/tunnels`.

---

Let me know if you'd like to add auto-authentication with your Ngrok token or expose a different port!
