# Load Balancing

## What is Load Balancing?

Load balancing distributes incoming traffic across multiple servers to ensure no single server gets overwhelmed.

Load balancing is a fundamental concept in distributed systems that solves several critical problems:

1. **Scalability**: One server has limits; multiple servers scale horizontally  
2. **Availability**: If one server fails, others handle the traffic  
3. **Performance**: Distributing load prevents bottlenecks  
4. **Resource Optimization**: Efficiently utilize all available servers  

**The Core Problem**:
```
Without Load Balancer:
All traffic → Single Server
- Server gets 1000 req/s
- Server can handle 500 req/s
- Result: 500 req/s dropped, slow responses, server crash

With Load Balancer:
Traffic → Load Balancer → Server 1 (333 req/s)
                       → Server 2 (333 req/s)
                       → Server 3 (333 req/s)
- Each server within capacity
- Fast responses
- System remains stable
```

---

## Load Balancing Theory

### Horizontal Scaling vs Vertical Scaling

**Vertical Scaling (Scale Up):**
```
Upgrade one server: More CPU, RAM, Disk
- Limited by hardware maximums
- Expensive
- Single point of failure
- Downtime during upgrades
```

**Horizontal Scaling (Scale Out):**
```
Add more servers of same size
- Nearly unlimited scaling
- Cost-effective
- No single point of failure
- No downtime to add servers
- Requires load balancing
```

Load balancing enables horizontal scaling.

---

## Traffic Flow

```
                    Load Balancer
                         |
        ┌────────────────┼────────────────┐
        |                |                |
    Server 1         Server 2         Server 3
```

---

## Load Balancing Algorithms

### 1. Round Robin
Distributes requests equally in sequence.

**Example:**
```
Request 1 → Server 1
Request 2 → Server 2
Request 3 → Server 3
Request 4 → Server 1
```

**Pros**:
- Simple
- Fair distribution

**Cons**:
- Ignores server load

---

### 2. Least Connections
Sends traffic to server with fewest active connections.

**Pros**:
- Adapts to load  
- Better for long requests  

**Cons**:
- More complex  

---

### 3. Weighted Round Robin
Servers get traffic based on capacity.

```
Server1 (3) → 50%
Server2 (2) → 33%
Server3 (1) → 17%
```

---

### 4. IP Hash
Same client IP → same server

**Use case**: Session persistence

---

### 5. Least Response Time
Chooses fastest + least loaded server.

---

### 6. Random
Random server selection (works well at scale)

---

## Types of Load Balancers

### Layer 4 (Transport Layer)
- Based on IP & Port  
- Very fast  
- No content inspection  

### Layer 7 (Application Layer)
- Based on HTTP data (URL, headers)  
- Supports smart routing  
- SSL termination, caching  

---

## Real-World Examples

### Basic Architecture
```
Internet
   ↓
Load Balancer
   ├→ Server 1
   ├→ Server 2
   └→ Server 3
```

### Microservices
```
/users → User Service
/orders → Order Service
/products → Product Service
```

---

## Health Checks

Ensure traffic goes only to healthy servers.

### Types:
- TCP Check → Port open?
- HTTP Check → App working?

### Parameters:
- Interval  
- Timeout  
- Healthy/Unhealthy threshold  

---

## Session Persistence (Sticky Sessions)

```
Client → LB → Server 2
Next request → Same Server 2
```

---

## Popular Load Balancers

### Software
- Nginx  
- HAProxy  
- Traefik  
- Envoy  

### Cloud
- AWS ALB / NLB  
- Azure Load Balancer  
- GCP Load Balancing  

---

## Nginx Example

```nginx
upstream backend {
    server 10.0.1.10:8080;
    server 10.0.1.11:8080;
    server 10.0.1.12:8080;
}

server {
    listen 80;
    location / {
        proxy_pass http://backend;
    }
}
```

---

## Load Balancing Patterns

### Active-Active
All servers handle traffic

### Active-Passive
One active, others standby

### Geographic Routing
Users routed to nearest region

---

## Auto Scaling

```
High Load → Add servers → LB distributes traffic
Low Load → Remove servers
```

---

## Troubleshooting

### Uneven Load
- Sticky sessions  
- Long connections  

### Server Unhealthy
- Check `/health` endpoint  

### 502 Error
- Backend down or timeout  

---

## Key Takeaways

✅ Distributes traffic across servers  
✅ Improves scalability & availability  
✅ Layer 4 = fast, Layer 7 = smart  
✅ Health checks prevent failures  
✅ Works with auto-scaling  
