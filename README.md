# pangolin
Pangolin tunnel configuration and utilities

## About Pangolin

Pangolin is a tunneling server that works with Newt clients to create secure WireGuard tunnels. It provides a web-based dashboard for managing tunnel connections and serves as the central hub for the tunneling infrastructure.

### Official Repository

- **GitHub**: [fosrl/pangolin](https://github.com/fosrl/pangolin)
- **Description**: A tunneling server for managing WireGuard connections
- **Latest Version**: 1.6.1

## Installation

Pangolin can be installed using the official installer script. The installation process includes:

- Automatic Docker installation (if not present)
- Pangolin server setup with web dashboard
- Gerbil tunnel management
- Traefik reverse proxy
- Optional CrowdSec security integration

### Quick Installation

```bash
# Download the installer for your platform
wget -O installer "https://github.com/fosrl/pangolin/releases/download/1.6.1/installer_linux_$(uname -m | sed 's/x86_64/amd64/;s/aarch64/arm64/')"

# Make it executable
chmod +x ./installer

# Run the installer
./installer
```

### Installation Example

For a complete installation example including Docker setup and configuration, see:
[installation-example-including-docker.txt](installation-example-including-docker.txt)

This file contains a detailed installation log showing:
- Ubuntu server setup
- Docker installation
- Pangolin configuration
- Container deployment
- Initial setup process

### Post-Installation

After installation, access the Pangolin dashboard at:
```
https://your-domain.com/auth/initial-setup
```

## Part of Tunnel Meta Repository

This repository is included as a submodule in the [tunnel](https://github.com/hellbrueck/tunnel.git) meta repository, which is part of the larger [NetSysLab](https://github.com/hellbruh/NetSysLab) network infrastructure toolkit.

### Repository Hierarchy:
```
NetSysLab (meta repository)
└── tunnel/ (submodule)
    └── pangolin/ (submodule) ← This repository
``` 