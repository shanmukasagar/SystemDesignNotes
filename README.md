## 📌 What is System Design?

**System Design** is the process of defining the **architecture, components, modules, interfaces, and data flow** of a system to meet given requirements.  
It answers: **“How do we build the system?”**

### 🔹 Example
For an **Online Food Delivery App** (like Swiggy/Zomato):  
- **Requirements**: Users should order food, restaurants receive orders, delivery partners deliver them.  
- **System Design** defines:  
  - How frontend, backend, database, APIs interact.  
  - How to handle millions of users (scalability).  
  - Which database to use (MongoDB, PostgreSQL).  
  - How to ensure fast performance (caching, load balancing).  
  - How to ensure reliability (replication, failover).  

---

## 📌 High-Level Design (HLD) vs Low-Level Design (LLD)

| Aspect | High-Level Design (HLD) | Low-Level Design (LLD) |
|--------|--------------------------|-------------------------|
| **Focus** | Big picture (system architecture) | Detailed design (class-level, module-level) |
| **Audience** | Architects, senior engineers, stakeholders | Developers implementing the system |
| **Output** | Architecture diagrams, database schema, data flow | Class diagrams, pseudocode, API contracts |
| **Level of Detail** | Abstract (components & interactions) | Concrete (internal working of components) |
| **Example (Food Delivery App)** | - Components: User Service, Restaurant Service, Delivery Service, Payment Service <br>- How they interact via APIs | - Database tables: `users`, `orders`, `restaurants` <br>- API details: `POST /order` request/response <br>- Classes: `OrderManager`, `PaymentGateway` |

👉 Analogy:  
- **HLD = Map of a city (roads, areas)**  
- **LLD = Street-level map (houses, shops)**  

---

## 📌 Functional vs Non-Functional Requirements

### 🔹 Functional Requirements  
Describe **what the system should do** (features, behavior).  

**Examples (Food Delivery App):**  
- User can search restaurants.  
- Place an order.  
- Make payments.  
- Track delivery.  

👉 Business requirements visible to the end user.  

---

### 🔹 Non-Functional Requirements (NFRs)  
Describe **how the system should perform** (quality attributes).  

**Examples (Food Delivery App):**  
- **Scalability** → Handle 1M users at peak hours.  
- **Performance** → Search results < 1 second.  
- **Availability** → 99.99% uptime.  
- **Security** → Encrypted payments.  
- **Maintainability** → Modular, easy to update.  

👉 Not direct features, but critical for success.  

---

## ✅ Recap
- **System Design** → Architecture & approach to meet requirements.  
- **HLD** → Big picture (what components exist & how they interact).  
- **LLD** → Detailed design (how each component is implemented).  
- **Functional requirements** → Features (What).  
- **Non-functional requirements** → Qualities (How well).

# 🚀 Scalability – Summary

Scalability is the ability of a system to handle **increasing users, requests, or data** by adding resources.  

---

## 🔹 Key Techniques & Technologies

1. **Load Balancing**  
   - Distributes traffic across multiple servers.  
   - Tech: **NGINX, HAProxy, AWS ELB**  

2. **Caching**  
   - Stores frequently accessed data in memory for fast retrieval.  
   - Tech: **Redis, Memcached, CDN (Cloudflare, AWS CloudFront)**  

3. **Database Scaling**  
   - Make databases handle more load using:  
     - **Replication** (read replicas)  
     - **Sharding** (split data across servers)  
   - Tech: **PostgreSQL, MySQL, MongoDB, Cassandra**  

4. **Asynchronous Processing (Queues)**  
   - Offload heavy tasks to background workers.  
   - Tech: **Kafka, RabbitMQ, Amazon SQS**  

5. **Microservices Architecture**  
   - Break system into smaller services, scale each independently.  
   - Tech: **Docker, Kubernetes, Istio**  

6. **Auto Scaling (Cloud Infra)**  
   - Automatically add/remove servers based on traffic.  
   - Tech: **AWS Auto Scaling, GCP Instance Groups, Azure VM Scale Sets**  

7. **Content Delivery Network (CDN)**  
   - Deliver static content (images, videos, CSS/JS) from servers close to users.  
   - Tech: **Cloudflare, AWS CloudFront, Akamai**  

8. **API Gateways & Reverse Proxies**  
   - Manage routing, caching, and rate limiting.  
   - Tech: **Kong, NGINX, AWS API Gateway**  

9. **Distributed Data Stores**  
   - Handle massive data across multiple regions.  
   - Tech: **Cassandra, CockroachDB, DynamoDB**  

10. **Monitoring & Performance Tools**  
    - Detect bottlenecks and scale accordingly.  
    - Tech: **Prometheus, Grafana, ELK Stack, Datadog**  

---

## ✅ Recap
- **Vertical Scaling** → Add more power (CPU/RAM) to one server.  
- **Horizontal Scaling** → Add more servers and distribute load.  
- Modern systems use a **mix of both**, with load balancing, caching, database scaling, and cloud auto scaling.  

