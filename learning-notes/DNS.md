# DNS (Domain Name System)

## What is DNS?

DNS is like the phonebook of the internet. It translates human-readable domain names (like `google.com`) into IP addresses (like `142.250.185.46`) that computers use.

DNS (Domain Name System) is a hierarchical, distributed database system that translates domain names into IP addresses and vice versa. Without DNS, we would need to remember IP addresses for every website we want to visit.

---

## Why DNS Was Created

### The Problem Before DNS (pre-1983)

- **HOSTS.TXT file**: A single text file maintained by Stanford Research Institute  
- Downloaded periodically by all hosts on the internet  
- Contained all hostname-to-IP mappings  

As internet grew, this became unsustainable:

- File became too large  
- Updates too frequent  
- Network congestion from downloads  
- No name uniqueness guarantee  
- No scalability  

### The DNS Solution

- **Distributed**: No single point of failure  
- **Hierarchical**: Organized tree structure  
- **Cached**: Faster responses, reduced load  
- **Scalable**: Can handle billions of queries  
- **Delegated**: Different organizations manage different parts  

---

## How DNS Fundamentally Works

DNS operates on a **query-response model**:

1. Application needs IP  
2. Query sent to resolver  
3. Resolver checks cache  
4. If not cached, recursive resolution begins  
5. IP returned  
6. Result cached  

---

## DNS as a Distributed Database

DNS is not a single server but millions worldwide:

- Root servers  
- TLD servers  
- Authoritative servers  
- Recursive resolvers  

This provides:

- Redundancy  
- Performance  
- Scalability  

---

## How DNS Works (Simple Flow)

```text
1. You type: www.example.com
2. Resolver checks cache
3. If not cached → Root → TLD → Authoritative
4. Gets IP
5. Browser connects
```

---

## DNS Hierarchy

```text
                        . (Root)
                         |
        ┌────────────────┼────────────────┐
       .com            .org             .net
        |
    example.com
        |
   ┌────┴────┐
  www      api
```

---

## Types of DNS Records

| Record Type | Purpose | Example |
|-------------|--------|--------|
| A | IPv4 mapping | example.com → 93.184.216.34 |
| AAAA | IPv6 mapping | example.com → IPv6 |
| CNAME | Alias | www → example.com |
| MX | Mail server | mail.example.com |
| TXT | Verification | SPF records |
| NS | Nameservers | DNS servers |
| PTR | Reverse DNS | IP → domain |

---

## Real-World Examples

### Basic Setup

```text
example.com        A       93.184.216.34
www.example.com    CNAME   example.com
```

### Load Balancing

```text
example.com    A    10.0.1.5
example.com    A    10.0.1.6
example.com    A    10.0.1.7
```

### Cloud Microservices

```text
api.example.com      A       54.x.x.x
admin.example.com    A       54.x.x.x
cdn.example.com      CNAME   cloudfront.net
```

---

## DNS Resolution Process

### Steps

```text
Browser Cache → OS Cache → Resolver → Root → TLD → Authoritative → IP
```

---

## Types of DNS Queries

- Recursive Query  
- Iterative Query  
- Non-Recursive Query  

---

## DNS Caching

### Cache Levels

```text
Browser
OS
Router
ISP Resolver
DNS Servers
```

---

## TTL (Time To Live)

```text
example.com    300    A    93.184.216.34
```

- High TTL → Less queries, slow updates  
- Low TTL → Fast updates, more queries  

---

## DNS Commands

```bash
nslookup example.com
dig example.com
dig example.com MX
dig @8.8.8.8 example.com
dig -x 8.8.8.8
```

---

## Public DNS Servers

| Provider | Primary | Secondary |
|----------|--------|-----------|
| Google | 8.8.8.8 | 8.8.4.4 |
| Cloudflare | 1.1.1.1 | 1.0.0.1 |
| OpenDNS | 208.67.222.222 | 208.67.220.220 |

---

## DNS in DevOps

### Internal DNS

```text
database.internal → 10.0.2.15
```

### Service Discovery

```text
service.cluster.local → internal IP
```

### Blue-Green Deployment

```text
Old → 1.2.3.4
New → 5.6.7.8
```

---

## Common DNS Issues

### DNS Propagation Delay
- Can take up to 48 hours  

### Cache Issues

```bash
# Flush DNS

# Linux
sudo systemd-resolve --flush-caches

# Windows
ipconfig /flushdns
```

---

## DNS Resolution Example

```text
Browser → Cache miss
Resolver → Root → TLD → Authoritative
Returns IP
Browser connects
```

---

## Key Takeaways

- DNS converts domain to IP  
- A → IPv4, AAAA → IPv6  
- CNAME → Alias  
- TTL controls caching  
- Used in cloud + microservices  
- Use dig/nslookup for debugging  
