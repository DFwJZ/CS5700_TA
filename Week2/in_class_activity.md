# Peer-to-Peer Network and Application Layer Protocols Exploration Activity Guide (Week 2)

## Purpose:
To demonstrate fundamental networking concepts by establishing a direct peer-to-peer connection, configuring IP addresses, and exploring basic network protocols. This hands-on experience will illustrate core principles of computer communication and data transfer.

## Peer-to-Peer Network (25-35min)

### Setup (10-15 min)
Connect two laptops with an Ethernet cable.

#### On Windows:
1. Set static IP on Windows:
   a. Open Network settings
   b. Click "Change adapter options"
   c. Right-click Ethernet > Properties
   d. Select "Internet Protocol Version 4" > Properties
   e. Choose "Use the following IP address"
   f. Enter IP: 192.168.1.1 (for first laptop) or 192.168.1.2 (for second)
   g. Subnet mask: 255.255.255.0
   h. Click OK

#### On macOS:
2. Set static IP on Mac:
   a. Go to System Preferences > Network
   b. Select Ethernet
   c. Set Configure IPv4: Manually
   d. IP Address: 192.168.1.1 (for first Mac) or 192.168.1.2 (for second)
   e. Subnet Mask: 255.255.255.0
   f. Click Apply

### CLI setup:

#### Windows (powershell admin):
```powershell
Get-NetAdapter
New-NetIPAddress -InterfaceAlias "Ethernet" -IPAddress 192.168.1.1 -PrefixLength 24
Get-NetIPAddress -InterfaceAlias "Ethernet"
```

#### MacOS (shell/terminal)
```bash
ifconfig en0
sudo ifconfig en0 inet 192.168.1.1 netmask 255.255.255.0
ifconfig en0
```

### Step-by-Step Activity (10-15min)

1. Test Connection (5 mins):
   - Open Terminal/Command Prompt
   - Ping the other laptop: `ping 192.168.1.2` (from first laptop)

2. File Sharing (10 mins):
   - Create a folder on Desktop
   - Right-click > Share (Windows) or Sharing & Permissions (Mac)
   - On other laptop, access shared folder via File Explorer (Windows) or Finder > Go > Connect to Server (Mac)

Or set up a local temp server using:
```bash
python3 -m http.server 9999
```

### Cleanup (5min):

#### On macOS (shell/terminal):
```bash
sudo ifconfig en0 dhcp
```

#### On Windows (powershell admin):
```powershell
Set-NetIPInterface -InterfaceAlias "Ethernet" -Dhcp Enabled
```

## Application Layer Protocol Activity (25min)

### HTTP Headers look up (10 mins):
- In Terminal/Command Prompt: `curl -I https://www.northeastern.edu`
- Discuss what each header means

### DNS Lookup (10 mins):
- Run: `nslookup www.northeastern.edu`
- Explain IP addresses and DNS servers

### Reflection (5 mins):
- How does this differ from your home network?
- What did you learn about internet infrastructure?
  a. Does internet communication rely on DNS based or IP?
  b. Why do we need DNS?