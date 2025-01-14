# UWaterloo VPN Install on WSL

This is a guide for setting up the University of Waterloo's VPN on wsl. I personally used this method rather than the traditional windows ui based install as there was no Cisco Secure Client release available for my ARM based Windows machine at the time. The following steps will be outlined:
1. Install and configure the University of Waterloo's VPN client in WSL.
2. Use `tmux` for managing terminal sessions.
3. Set up and use SSH to connect to remote servers.

---

## 1. Install the VPN Client (OpenConnect)

### Step 1.1: Update the System
Before installing the VPN client, update your package list:
```bash
sudo apt update && sudo apt upgrade -y
```

### Step 1.2: Install OpenConnect
OpenConnect is a command-line VPN client compatible with Cisco AnyConnect VPN.
```bash
sudo apt install openconnect -y
```

### Step 1.3: Connect to the VPN
To connect to the University of Waterloo's VPN:
```bash
sudo openconnect cn-vpn.uwaterloo.ca
```
- Enter your WatIAM username and password when prompted.
- For two-factor authentication (2FA), use `push`, `phone`, or `sms` as directed by the University of Waterloo's IT guidelines.

---

## 2. Install and Use `tmux`

`tmux` is a terminal multiplexer that allows you to manage multiple terminal sessions from a single window.

### Step 2.1: Install `tmux`
```bash
sudo apt install tmux -y
```

### Step 2.2: Start a `tmux` Session
Start a new session:
```bash
tmux
```
### Step 2.3: Detach from the Session
To detach from the `tmux` session (leave it running):
```bash
Ctrl+b d
```

### Step 2.4: Run VPN in a `tmux` Session
Once inside a `tmux` session, run your VPN command:
```bash
sudo openconnect cn-vpn.uwaterloo.ca
```
This allows the session to continue running in the background while you return to the main terminal.

### Step 2.5: Reattach to the Session (When Done)
To reattach to your session later:
```bash
tmux attach
```
This will bring you back to the `tmux` session exactly where you left off.

---

## 3. Set Up and Use SSH

### Step 3.1: Connect to the Remote Server
To connect to a server via SSH:
```bash
ssh [username]@[servername].uwaterloo.ca
```
Replace `username` with your WatIAM username and `servername` with the appropriate server's name.

### Step 3.2: Using SSH with a Custom Port
If the SSH server uses a port other than the default (22), specify it with the `-p` flag:
```bash
ssh -p `####` [username]@[servername].uwaterloo.ca
```

---

## 4. Testing and Troubleshooting

### Test VPN Connectivity
Run the following command to test if you can reach internal resources:
```bash
ping [servername].uwaterloo.ca
```

### Test SSH Connectivity
Check if the SSH connection works with verbose output:
```bash
ssh -vvv [username]@[servername].uwaterloo.ca
```

### Troubleshooting
- **VPN Issues:** Ensure OpenConnect is installed correctly and the VPN server address is correct.
- **SSH Issues:** Verify the server is reachable and the correct port is being used. Check firewall rules if needed.

---

By following this guide, you should have a fully functional setup for using the University of Waterloo's VPN, managing sessions with `tmux`, and connecting to remote servers using SSH in WSL.
