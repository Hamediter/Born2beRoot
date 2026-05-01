*This project has been created as part of the 42 curriculum by [aboutale].*

# 🛡️ Born2beRoot - System Administration & Virtualization

<p align="center">
  <img src="https://img.shields.io/badge/Score-100%2F100-success?style=for-the-badge&logo=42" alt="Score">
  <img src="https://img.shields.io/badge/OS-Debian-red?style=for-the-badge&logo=debian" alt="Debian">
</p>

## 📝 Description
**Born2beRoot** is a System Administration project that involves setting up a strictly monitored and secured virtual server. The goal is to understand virtualization, partitioning (LVM), and basic system security.

### Key Features
- **OS:** Debian (CLI only).
- **Partitioning:** Implementation of LVM (Logical Volume Manager).
- **Security:** UFW firewall, SSH on port 4242, and strict password policies.
- **Monitoring:** A custom bash script that displays system info every 10 minutes.

---

## 🏗️ Infrastructure Overview
The server is built with a focus on the principle of least privilege:
- **Users & Groups:** Specific roles for `sudo` users and members of the `user42` group.
- **Sudo Policy:** Strict rules including custom error messages and TTY requirements.
- **Network:** Only port 4242 is open for SSH, protected by UFW.

---

## 🛠️ Project Description & Design Choices

### Design Choices
*   **LVM Partitioning:** I chose a specific partitioning scheme to allow future disk resizing without data loss, separating `/home`, `/var`, and `/tmp` for better security and stability.
*   **Password Policy:** Implemented using `libpam-pwquality` to enforce complexity (uppercase, digits, length) and a 30-day expiration cycle.
*   **SSH Hardening:** Disabled Root login via SSH and forced the use of a specific port to reduce "brute force" attack surface.

---

## 🚀 Instructions

### Installation
Since this is a virtual machine project, the "source code" is the disk image. However, the monitoring script can be tested:
1.  **Clone the monitoring script:**
    ```bash
    git clone [https://github.com/your-username/born2beroot.git](https://github.com/your-username/born2beroot.git)
    ```
2.  **Run the script (simulated):**
    ```bash
    bash monitoring.sh
    ```

### Useful Commands used during setup
- `lsblk` : Check LVM partitions.
- `ufw status` : Check firewall rules.
- `sudo chage -l [user]` : Check password expiration policy.

---

## 📚 Resources

### References
- [Debian Security Manual](https://www.debian.org/doc/manuals/debian-security/)
- [LVM Guide](https://wiki.debian.org/LVM)
- [How to secure a Linux Server](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-debian-11)

### AI Usage
AI was used for:
- **Scripting:** Optimizing the `awk` and `grep` commands in `monitoring.sh` to get accurate RAM and CPU usage.
- **Troubleshooting:** Understanding the interaction between `PAM` modules and password policies.
- **Documentation:** Structuring the technical choices for this README.
