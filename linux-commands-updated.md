# 🐧 Linux Command Line Cheatsheet

> **A comprehensive reference for essential Linux commands used in cybersecurity and system administration**

This document serves as a personal reference for critical Linux commands, designed to be a living document that grows with your expertise. Perfect for cybersecurity professionals, system administrators, and anyone working with Linux systems.

---

## 📍 1. Navigation & Information

Master your environment with these fundamental commands that help you understand your current location and identity in the system.

### `pwd` - Print Working Directory 📂
**Description:** Displays the full path of your current directory location.

```bash
pwd
```
**Output:** `/home/kali`

> 💡 **Pro Tip:** Always use `pwd` before performing critical operations (like recursive deletes) to ensure you're in the correct location.

### `cd` - Change Directory 🚀
**Description:** Navigate between directories with ease.

```bash
cd MyFirstPentest
```

> 🔥 **Pro Tips - Master These Shortcuts:**
> - `cd ~` or `cd`: Returns to home directory instantly
> - `cd ..`: Move up one directory level  
> - `cd -`: Jump to your previous directory (perfect for toggling!)
> - `cd /etc/network`: Absolute path (works from anywhere)
> - `cd ../Notes`: Relative path (depends on current location)

### `ls` - List Files & Directories 📋
**Description:** Display contents of your current location.

```bash
ls
```

> 🎯 **Power User Flags:**
> - `ls -l`: Long format (permissions, owner, size, date)
> - `ls -a`: Show ALL files (including hidden `.` files)
> - `ls -lh`: Human-readable file sizes (4.0K, 1.2M)
> - `ls -la`: Combined detailed view of all files

### `whoami` - Current User Identity 👤
**Description:** Shows your current effective username.

```bash
whoami
```
**Output:** `kali`

> ⚠️ **Security Note:** Essential when working with elevated privileges to confirm your current identity.

### `history` - Command History 📚
**Description:** View your previously executed commands with line numbers.

```bash
history
```

> 🎮 **Navigation Hacks:**
> - Use ↑↓ arrow keys to cycle through history
> - `!<number>`: Re-run specific command (e.g., `!101`)

---

## 🗂️ 2. File & Directory Management

Create, modify, and organize your digital workspace efficiently.

### `mkdir` - Make Directory 📁
**Description:** Create new directories (folders).

```bash
mkdir Notes Reports Loot
```

> 🏗️ **Advanced Usage:** `mkdir -p ProjectX/Scans/Nmap` creates nested directory structure in one command!

### `touch` - Create Files ✨
**Description:** Create new empty files instantly.

```bash
touch scope.txt
```

> 🔄 **Bonus Feature:** Updates modification timestamp of existing files without changing content.

### `cp` - Copy Files & Directories 📄
**Description:** Duplicate files or directories from source to destination.

```bash
cp scope.txt Notes/scope_backup.txt
```

> 🔁 **Directory Copying:** Use `cp -r <source> <destination>` for recursive directory copying.

### `mv` - Move & Rename 🔄
**Description:** Move files/directories or rename them.

```bash
# Rename
mv scope.txt project_scope.txt

# Move
mv project_scope.txt Notes/
```

> ✅ **Efficiency Note:** Unlike `cp`, `mv` doesn't need recursive flags for directories.

### `rm` - Remove Files 🗑️
**Description:** Permanently delete files (⚠️ **IRREVERSIBLE!**)

```bash
rm scope_backup.txt
```

> 🛡️ **Safety First:**
> - `rm -i`: Interactive mode with confirmation prompts
> - Avoid `rm -f` unless absolutely necessary (overrides all prompts)

### `rmdir` - Remove Empty Directory 🧹
**Description:** Delete empty directories only (safety feature).

```bash
rmdir Reports
```

> 🔍 **Safety Check:** Fails if directory contains files, alerting you to review contents first.

---

## 👀 3. Viewing Files

Inspect file contents without opening graphical editors.

### `cat` - Display File Contents 📖
**Description:** Show entire file content on screen.

```bash
cat /etc/hosts
```

> 🔗 **Advanced Usage:** Combine files with `cat file1.txt file2.txt > combined.txt`

### `less` - Paginated File Viewer 📄
**Description:** View large files one page at a time with navigation controls.

```bash
less /etc/services
```

> 🎯 **Navigation Controls:**
> - Arrow keys: Scroll up/down
> - `/`: Search within file
> - `q`: Quit viewer

### `head` / `tail` - File Previews 🔍
**Description:** Display first (`head`) or last (`tail`) 10 lines of files.

```bash
tail /var/log/syslog
```

> 🔴 **Real-time Monitoring:** `tail -f` follows log files in real-time - essential for security analysis!

---

## 🔍 4. Searching & Filtering

Find files and content efficiently across your system.

### `find` - File & Directory Search 🎯
**Description:** Search filesystem hierarchically based on multiple criteria.

```bash
# Find file named "hosts" starting from root
find / -name "hosts"

# Find all .txt files in current directory and subdirectories
find . -type f -name "*.txt"
```

### `grep` - Text Pattern Matching 🔎
**Description:** Search for specific text patterns within files.

```bash
grep "kali" /etc/passwd
```

> 🔗 **Pipeline Power:** `history | grep "apt"` searches command history for apt usage.

---

## 🔐 5. Permissions Management

Control access and security with proper permission handling.

### `sudo` - Execute with Elevated Privileges 👑
**Description:** Run single commands with administrator (root) privileges.

```bash
sudo apt update
```

> 🛡️ **Security Best Practice:** Preferred over direct root login - more secure and auditable.

### `chmod` - Change File Permissions 🔒
**Description:** Modify read (r), write (w), and execute (x) permissions.

```bash
# Add execute permission
chmod +x script.sh

# Set specific permissions (Owner: rwx, Group/Others: r-x)
chmod 755 script.sh
```

> 📊 **Permission Structure:** Owner | Group | Others
> - 7 (rwx): Full control
> - 5 (r-x): Read and execute only

---

## 📚 6. Getting Help

Access comprehensive documentation and command references.

### `man` - Manual Pages 📖
**Description:** Access official documentation for any command with complete feature listings.

```bash
man cp
```

> 🎓 **Learning Strategy:** Always try `man <command>` before searching online - it's the most authoritative source. Press `q` to exit.

---

## 🌐 7. Network Diagnostic Commands

Essential command-line utilities for network configuration interrogation and connectivity diagnosis. These tools are indispensable for system administration and security assessment reconnaissance.

### `ip a` - IP Address Information 🔍
**Description:** Modern iproute2 suite command for displaying and manipulating routing, network devices, interfaces, and tunnels. The `a` argument shows address information for all configured network interfaces (replaces legacy `ifconfig`).

**Syntax:** `ip [ OPTIONS ] OBJECT { COMMAND | help }`

```bash
ip a
```

> 📊 **Output Analysis:**
> - **link/ether**: Layer 2 MAC (Media Access Control) address
> - **inet**: Layer 3 IPv4 address with CIDR notation (e.g., `/24` = 255.255.255.0 subnet mask)
> - **brd**: Broadcast address for the subnet
> - **scope global**: Address valid and reachable from all networks
> - **valid_lft/preferred_lft**: Address lifetimes for dynamic assignment

### `nslookup` - DNS Name Resolution 🔎
**Description:** Query Domain Name System (DNS) for domain-to-IP mappings and specific DNS record types (MX, NS, etc.).

**Syntax:** `nslookup [ -option ] { HOST | -SERVER }`

```bash
nslookup example.com
```

> ⚠️ **Lab Environment Note:** In isolated networks, external domain queries may return `** server can't find...: REFUSED` - this confirms proper network isolation and is expected behavior.

### `ping` - Network Connectivity Test 📡
**Description:** Transmits ICMP ECHO_REQUEST packets to test host reachability and measure round-trip latency.

**Syntax:** `ping [ -options ] DESTINATION`

```bash
ping 192.168.56.101
```

> 🔍 **Output Interpretation:**
> - **icmp_seq**: Packet sequence number (tracks lost packets)
> - **ttl (Time to Live)**: Hop counter decremented at each router
>   - TTL 64: Typically Linux/Unix systems
>   - TTL 128: Typically Windows systems
> - **time**: Round-trip latency in milliseconds
> - **Ctrl+C**: Terminate continuous ping

### `traceroute` - Network Path Analysis 🗺️
**Description:** Display routing path and measure transit delays across IP networks using progressively increasing TTL values to elicit ICMP TIME_EXCEEDED responses from intermediate routers.

**Syntax:** `traceroute [ -options ] HOST`

```bash
traceroute 192.168.56.101
```

> 🎯 **Path Analysis:**
> - **Single hop**: Direct connection on same network segment
> - **Multiple hops**: Each router in the path to destination
> - **Response times**: Latency measurements for each hop
> - **Asterisks (*)**: Timeouts or filtered responses

---

## 🎯 Updated Quick Reference Summary

| Category | Essential Commands |
|----------|-------------------|
| **Navigation** | `pwd`, `cd`, `ls`, `whoami` |
| **File Management** | `mkdir`, `touch`, `cp`, `mv`, `rm` |
| **File Viewing** | `cat`, `less`, `head`, `tail` |
| **Search** | `find`, `grep` |
| **Permissions** | `sudo`, `chmod` |
| **Network Diagnostics** | `ip a`, `nslookup`, `ping`, `traceroute` |
| **Help** | `man`, `history` |

---

> 🌟 **Network Security Tip:** These diagnostic commands form the foundation of network reconnaissance and troubleshooting. Master them for effective system administration and security assessment!

---

*Happy command line mastering! 🚀*