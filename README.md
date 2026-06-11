# NodeUsageStatus

NodeUsageStatus is a utility for monitoring and displaying node usage information with easy installation and lightweight integration.

## Features

- Real-time node monitoring
- Usage status tracking
- Lightweight resource
- Easy install/remove support
- Blueprint compatible

---

# Automatic Installation

Install using Blueprint:

```bash
cd /var/www/pterodactyl
yes | blueprint -i node
yes | blueprint -r node
```

Or run installer directly:

```bash
bash <(curl -s https://raw.githubusercontent.com/nobita329/NodeUsageStatus/refs/heads/main/install.sh)
```

---

# Remove / Uninstall

```bash
bash <(curl -s https://raw.githubusercontent.com/nobita329/NodeUsageStatus/refs/heads/main/remove.sh)
```

---

# Manual Wings Setup

If changes do not appear automatically, rebuild Wings manually.

### Step 1: Download and Extract Wings

Run:

```bash
WINGSDIR="/srv/wings" && \
mkdir -p $WINGSDIR && \
cd $WINGSDIR && \
LOCATION=$(curl -s https://api.github.com/repos/pterodactyl/wings/releases/latest \
| grep "tag_name" \
| awk '{print "https://github.com/pterodactyl/wings/archive/" substr($2, 2, length($2)-3) ".zip"}') && \
curl -L -o wings_latest.zip $LOCATION && \
unzip wings_latest.zip
```

---

### Step 2: Install Go

Install Go using the official guide:

:contentReference[oaicite:0]{index=0}

Verify installation:

```bash
go version
```

---

### Step 3: Build and Restart Wings

Run:

```bash
systemctl stop wings && \
go build -o /usr/local/bin/wings && \
chmod +x /usr/local/bin/wings && \
systemctl start wings
```

This build process may take several minutes.

Check Wings status:

```bash
systemctl status wings
```

Restart queue service if needed:

```bash
systemctl restart pteroq
```

---

# Usage

After installation, NodeUsageStatus will automatically display node usage and resource information.

---

# Support

Report bugs or request features through GitHub issues.

# License

Free to use and modify.