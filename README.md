CVE-2017-16995 Privilege Escalation Exploit
Overview
This repository contains an exploit for CVE-2017-16995, a privilege escalation vulnerability affecting certain versions of the Linux kernel. The exploit leverages a flaw in eBPF to escalate privileges to root.

Affected Systems
- Ubuntu 16.04 (4.4.0-116-generic and earlier)
- Fedora 27 (Kernel versions prior to patch)
- Other Linux distributions with vulnerable kernel versions


Compilation
```bash
gcc exploit.c -o exploit -Wall -Wextra -O2 -pthread
```

Execution
```bash
./exploit
```

If successful, the exploit will spawn a root shell (`#` prompt).
Mitigation
To protect your system from this vulnerability, apply the latest kernel patches by running:

```bash
sudo apt update && sudo apt upgrade -y
```

Alternatively, you can disable unprivileged eBPF execution:

```bash
sysctl -w kernel.unprivileged_bpf_disabled=1
```

To make it persistent:

```bash
echo "kernel.unprivileged_bpf_disabled=1" | sudo tee -a /etc/sysctl.conf
```

