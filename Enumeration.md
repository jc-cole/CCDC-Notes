| Command | What it does and when you’d use it |
|---|---|
| `nmap -sn 192.168.1.0/24` | **Discover hosts.** `-sn` skips the port scan. A `/24` specifies 256 IPv4 addresses. Discovery can use several probe types. On directly connected Ethernet, privileged Nmap normally uses ARP, so calling this an “ICMP ping sweep” misses what’s happening. ([Nmap Network Scanning][1]) |
| `sudo nmap -sS --top-ports 100 -T4 <target>` | **Get a quick TCP inventory.** `-sS` sends SYN probes. `--top-ports 100` selects the 100 most frequently observed ports, rather than ports 1 through 100. `-T4` uses more aggressive timing suited to a reasonably fast, reliable network. Without raw-packet privileges, Nmap’s usual TCP fallback is a connect scan (`-sT`), which uses the OS’s `connect()` call. ([Nmap Network Scanning][2]) |
| `nmap -sV -p 22,80,443 <target>` | **Identify services on selected ports.** `-p` selects the ports. `-sV` sends application probes and interprets replies or banners to identify the protocol, product, and sometimes version. Without `-sV`, the `SERVICE` column often just gives the conventional name for the port. ([Nmap Network Scanning][3]) |
| `sudo nmap -O <target>` | **Estimate the OS remotely.** Nmap fingerprints the network stack. Results are better when it can find at least one open and one closed TCP port. If you can sign in, verify the OS locally. ([Nmap Network Scanning][4]) |
| `nmap --script vuln -p 80,443 <target>` | **Run applicable vulnerability-category scripts** against the selected ports. Scripts can belong to multiple categories, including `intrusive`, `exploit`, or `dos`. For a scored service, read the individual script and choose the check you mean to run. For example, `nmap --script http-title -p 80 <target>` asks a narrower question about the page being served. ([Nmap Network Scanning][5]) |
| `sudo nmap -A -p- -T4 -oN scan.txt <target>` | **Run a detailed scan and save readable output.** `-A` enables OS detection, version detection, default scripts, and traceroute. `-p-` scans ports 1–65535, **TCP only in this command**. `-T4` controls timing and `-oN` writes normal output to `scan.txt`. I’d use this selectively after the first inventory because the extra probes take time and interact with services. ([Nmap Network Scanning][6]) |

[1]: https://nmap.org/book/man-host-discovery.html?utm_source=chatgpt.com "Host Discovery"

[2]: https://nmap.org/book/man-port-scanning-techniques.html?utm_source=chatgpt.com "Port Scanning Techniques"

[3]: https://nmap.org/book/man-version-detection.html?utm_source=chatgpt.com "Service and Version Detection"

[4]: https://nmap.org/book/man-os-detection.html?utm_source=chatgpt.com "OS Detection"

[5]: https://nmap.org/book/man-nse.html?utm_source=chatgpt.com "Nmap Scripting Engine (NSE)"

[6]: https://nmap.org/book/man-port-specification.html?utm_source=chatgpt.com "Port Specification and Scan Order"