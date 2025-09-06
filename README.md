# ITSC-300: Firewall Fundamental Project
Palo Alto Networks Academy  

---

##Overview

This capstone project was completed for ITSC-300.  
The objective was to design and configure a Palo Alto Networks VM-Series firewall in a simulated enterprise environment using VMware Workstation.

Our team (Aira Therens, Gia Huy Pham, Chan Quyen Khuu) worked through a set of structured tasks to build firewall interfaces, zones, policies, security profiles, and GlobalProtect VPN. A final demo video was submitted for grading.

---

##Objectives

The lab required us to:

1. **Load Base Configuration**  
   - Reset environment with `Initial.xml` snapshot.  
   - Commit and verify changes.

2. **Configure Interfaces & Zones**  
   - Ethernet1/1 → 203.0.113.20/24 (Internet)  
   - Ethernet1/2 → 192.168.1.1/24 (Users)  
   - Ethernet1/3 → 192.168.50.1/24 (Extranet / DMZ)  
   - Virtual Router `VR-1` with default route.  
   - Management profile `Allow-ping` tested via CLI pings.  
   - Zones created: **Internet** (black), **Users** (green, with User-ID), **Extranet** (orange).

3. **Configure Security & NAT Policy Rules**  
   - Source NAT rules for outbound traffic.  
   - Users (192.168.1.0/24) → Internet.  
   - Extranet host (192.168.50.10) → Internet.  
   - DMZ accessible to internal hosts (apps: SSH, SSL, HTTP, FTP, ping).  
   - Block applications: Facebook, Twitter, YouTube, Reddit, 2600.org.  
   - Block URL categories: advertisements, phishing, malware, unknown.  
   - Logging enabled on interzone default policy.

4. **Create & Apply Security Profiles**  
   - Three-tiered URL filtering:  
     - Tier 1 → Government, financial, research, search engines.  
     - Tier 2 → Online storage & backup.  
     - Tier 3 → Allow all.  
   - Antivirus, Anti-Spyware (with DNS sinkhole), and Vulnerability Protection enabled.  
   - File blocking: PE files + multi-encoded files.  
   - WildFire enabled for malware analysis.  

5. **Configure GlobalProtect**  
   - Portal + Gateway setup.  
   - External IP pool: 172.16.5.200–172.16.5.250.  
   - Separate tunnel zone created.  
   - Authentication profiles (LDAP/local).  
   - IPsec required.  
   - Security rules for portal/gateway + Internet access.

---

##Verification Tests

- Internal hosts pinged firewall & DMZ.  
- Internal hosts tested NAT connectivity to Internet.  
- DMZ server accessed from internal network (FTP/SSH/HTTP).  
- Blocked sites (FB, Twitter, YouTube, Reddit, 2600.org) were inaccessible.  
- WildFire test file generated alerts.  
- DNS sinkhole list included `phproxy.org`.  

---

##Project Errors

### Part 4 – URL Filtering & Sinkhole
- Internal clients could **not access box.net** even though `online-storage-and-backup` was allowed.  
- nslookup for `phproxy.org` did not trigger sinkhole events despite multiple checks:
  - File `dns-sinkhole.txt` confirmed in place.  
  - Entry `phproxy.org` present.  
  - Policy applied correctly.  

### Part 5 – GlobalProtect
- Portal & Gateway were fully configured (auth profiles, tunnel, IP pools).  
- Clients could not connect via GlobalProtect.  
- Believed to be a **license issue**: cross-checked with other groups who experienced the same failure.  

---

##Team Members

- Aira Therens  
- Gia Huy Pham  
- Chan Quyen Khuu  

---

##Lessons Learned

- Zone setup & tagging is straightforward, but NAT rules require careful scope definitions.  
- Application filtering works well for common social media, but URL filtering is brittle (categories may overlap).  
- DNS Sinkhole requires precise policy order and logging.  
- GlobalProtect functionality may depend on licensing; lab environments have limitations.  
- Even partial implementations reinforce understanding of layered security.  
