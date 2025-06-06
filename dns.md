# 📌 DNS Explained Simply

A concise guide to DNS (Domain Name System), covering domain appraisal, hosts file, host find, primary/secondary DNS, and DORA process with real-life examples.

## 🌐 What is DNS?
- **Definition**: Converts domain names (e.g., `google.com`) to IP addresses (e.g., `142.250.196.78`).
- **Purpose**: Simplifies internet navigation.
- **Example**: Like dialing "Mom" instead of her phone number.

## 🔧 DNS Levels
| Level | Description | Example (`www.shop.amazon.in`) |
|-------|-------------|-------------------------------|
| :globe_with_meridians: TLD | Top-Level Domain | `.in` |
| :computer: SLD | Second-Level Domain | `amazon` |
| :star2: Subdomain | Prefix to SLD | `shop`, `www` |
- **Example**: `shop.amazon.in` directs to Amazon’s shopping portal.

## 💻 Importance of DNS
- Eliminates memorizing IPs.
- Speeds up access via caching.
- Scales global internet.
- **Example**: Phonebook names replace phone numbers.

## 📋 DNS Record Types
| Record | Purpose | Example |
|--------|---------|---------|
| :computer: A | Domain to IPv4 | `google.com ➝ 142.250.196.78` |
| :globe_with_meridians: AAAA | Domain to IPv6 | `example.com ➝ 2606:...` |
| :link: CNAME | Alias | `blog.myshop.com ➝ myshop.com` |
| :envelope: MX | Mail server | `abc.com` email via Gmail |
| :satellite: NS | Name servers | `ns1.hosting.com` |
| :memo: TXT | Security info | SPF, DKIM for email |
| :leftwards_arrow_with_hook: PTR | IP to name | Email spam checks |
| :gear: SRV | Service location | Skype, LDAP |
| :page_with_curl: SOA | Zone admin info | Domain admin details |
| :lock: CAA | SSL control | Blocks fake SSL |
- **Example**: `MX` routes company email to Gmail.

## 🖥️ Hosts File
- **Definition**: Local file mapping domains to IPs before DNS queries.
- **Locations**:
  - Windows: `C:\Windows\System32\drivers\etc\hosts`
  - Linux/Mac: `/etc/hosts`
- **Example Entry**:- **Example**: Office PCs access HR portal via `hrportal.local`.

## 🔍 Host Find Entry
- **Command**: `nslookup www.microsoft.com`
- **Output**:- **Example**: IT team troubleshoots website access issues.

## 🧠 Primary & Secondary DNS
- **Primary**: Main DNS server for queries.
- **Secondary**: Backup if primary fails.
- **Example**:
- Primary: `8.8.8.8` (Google)
- Secondary: `8.8.4.4`
- **Example**: Office uses internal DNS for local systems, Google as backup.

## 📦 DORA Process (DHCP)
| Step | Name | Description |
|------|------|-------------|
| :mag: D | Discover | Device searches for DHCP server |
| :gift: O | Offer | Server offers IP address |
| :handshake: R | Request | Device requests IP |
| :white_check_mark: A | Acknowledge | Server assigns IP |
- **Example**: Laptop on Wi-Fi gets IP to access DNS and websites.

## 💰 Domain Appraisal
- **Definition**: Estimates domain value.
- **Factors**:
- Popularity/length (e.g., `flipkart.com` vs. `bestbargain.in`)
- Brandability
- Keywords
- Extension (`.com` > `.xyz`)
- Sale history
- **Tools**: GoDaddy Appraisal, Estibot, Sedo.
- **Example**: `carinsurance.com` sold for \$49M due to keywords.

## ⚙️ How DNS Works
- Steps for `www.example.com`:
- Browser checks cache.
- OS checks hosts file.
- Recursive resolver queries.
- Root server directs to TLD.
- TLD server points to authoritative server.
- Authoritative server returns IP.
- Browser loads website.
- **Example**: Google Maps finds "Pizza Hut" like DNS finds IPs.

## 🌍 Who Manages DNS?
- **ICANN**: Oversees root zones and TLDs.
- **Registries**: Manage TLDs (e.g., `.org` by Public Interest Registry).
- **Registrars**: Sell domains (e.g., GoDaddy).
- **Example**: Buying `myshop.com` via Hostinger.

