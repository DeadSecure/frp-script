🌍 **Languages**: English | [فارسی](README-fa.md)

# Easy FRP

A comprehensive bash script that simplifies the installation, configuration, and management of [FRP (Fast Reverse Proxy)](https://github.com/fatedier/frp) - a high-performance reverse proxy application focused on NAT penetration.

This script automates the entire FRP setup process and provides an intuitive menu-driven interface for managing your FRP deployments.

**Built for [FRP](https://github.com/fatedier/frp) by [fatedier](https://github.com/fatedier)**

📚 **Documentation:** [GoFRP Official Docs](https://gofrp.org/en/docs/)

## Features

✨ **One-Click Installation** - Automatically downloads and installs the latest FRP version  
🖥️ **Interactive Setup** - Menu-driven configuration for both server and client  
⚙️ **Advanced Configuration** - Browse, view, and edit existing configurations  
🔧 **Service Management** - Start, stop, and manage systemd services  
📊 **Status Monitoring** - View running services and configuration files  

## Quick Start

### Install

**⚠️ Run the script as root**

```bash
bash <(curl -Ls https://raw.githubusercontent.com/mikeesierrah/frp-script/main/frp-setup.sh)
```

## Configuration

### Server Configuration
Servers are configured in `/root/frp/server/` with the naming pattern:
```
server-<port>.toml
```

### Client Configuration  
Clients are configured in `/root/frp/client/` with the naming pattern:
```
client-<server-port>.toml
```

### Service Management
Services follow systemd template naming:
- Server services: `frps@server-<port>`
- Client services: `frpc@client-<server-port>`

## Example Usage

### Basic Server Setup
1. Run the script and choose option 1 (Install FRP)
2. Choose option 2 (Setup FRP Server)
3. Configure your desired port and authentication token
4. Server will start automatically

### Basic Client Setup
1. Ensure FRP is installed (option 1)
2. Choose option 3 (Setup FRP Client)
3. Enter your server details and local ports to expose
4. Client will connect automatically

### Managing Existing Configurations
1. Choose option 4 (Advanced Configuration)
2. Select Server or Client configuration
3. Pick the configuration file to edit
4. Service will restart automatically after editing

## Troubleshooting

### Check Service Status
```bash
# View all FRP services
systemctl list-units | grep frp

# Check specific service
systemctl status frps@server-7000
systemctl status frpc@client-7000
```

### View Logs
```bash
# Server logs
journalctl -u frps@server-7000 -f

# Client logs  
journalctl -u frpc@client-7000 -f
```

### Manual Configuration
Configuration files are located at:
- **Server**: `/root/frp/server/*.toml`
- **Client**: `/root/frp/client/*.toml`

## Important Note

**This script implements only the basic functionality of FRP for simplicity and speed.** 

FRP is an incredibly powerful and feature-rich reverse proxy solution with extensive capabilities including:

🔄 **Load Balancing** - Distribute traffic across multiple backend servers  
🔀 **Port Multiplexing** - Share single ports across multiple services  
🌐 **Real IP Forwarding** - Pass client IP addresses via X-Forwarded-For headers (perfect for IP limiting)  
📊 **Bandwidth Limiting** - Control traffic flow for each proxy  
🎯 **Custom Routing** - Route based on domains, paths, and headers  
⚡ **Connection Pooling** - Optimize performance with persistent connections  
🛡️ **Authentication Methods** - Token, OIDC, and custom auth systems  
📈 **Monitoring & Metrics** - Built-in dashboard and statistics  
🔧 **Plugin System** - Extend functionality with custom plugins  

### What This Script Covers

For the sake of **simplicity and quick deployment**, this script maps sensible default values for basic FRP setups. The configurations generated here represent just the tip of the iceberg - **one of the simplest possible implementations** of what FRP can do.

### For Power Users

If you're a power user with specific requirements such as:
- Complex load balancing scenarios  
- Advanced authentication mechanisms
- Custom header manipulation
- Bandwidth controls and traffic shaping
- Multi-tenant deployments
- Plugin integrations

**Please refer to the [official FRP documentation](https://gofrp.org/en/docs/)** and manually edit the generated configuration files using the "Advanced Configuration" option in this script.

The purpose of this script is that it gets you started quickly with working configurations that you can then customize to unlock FRP's full potential.

## Contributing

Found a bug or want to contribute? Feel free to:
1. Open an issue
2. Submit a pull request
3. Suggest improvements

## Donation

If this script helped you, consider:
- 💝 **Donating $5 to someone in need** - spread kindness!
- ☕ **Supporting the FRP developers** at [fatedier/frp](https://github.com/fatedier/frp)

## License

This script is provided as-is under the MIT License. FRP itself is licensed under the Apache License 2.0.

**FRP Project**: https://github.com/fatedier/frp  
**FRP Documentation**: https://gofrp.org/en/docs/  
**Original Author**: [fatedier](https://github.com/fatedier)


