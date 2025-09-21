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


# 🚦 Rate Limiting & Throttling

## 📌 What is Rate Limiting?
Rate limiting is a mechanism to **control the number of requests** a user/system can make to an API or service within a defined time period.  
Example: **100 requests per minute per user**.

### ✅ Why use it?
- Prevent abuse (DDoS, spamming APIs)  
- Ensure fair usage across users  
- Reduce server overload & improve stability  
- Control infrastructure costs  

---

## 🔹 Throttling vs Rate Limiting
- **Rate Limiting** → Restrict max requests in a given time window (**hard cap**)  
- **Throttling** → Control *speed/frequency* of requests (**slows down but doesn’t fully block**)  

---

## 🔹 Common Algorithms
1. **Fixed Window Counter** → Simple, but can allow bursts at edges  
2. **Sliding Window** → Smoother, more accurate  
3. **Token Bucket** → Tokens refill at a fixed rate, supports short bursts  
4. **Leaky Bucket** → Requests processed at a constant rate, excess dropped/queued  

---

## 🔹 Implementation Areas

### 🔸 Frontend
- Debouncing & throttling API calls  
- Disabling buttons after click  
- Tracking request count in local state  

⚠️ Only for **UX improvement** (not security)

### 🔸 Backend
- Middleware-based (e.g., `express-rate-limit`)  
- In-memory (for small apps)  
- Distributed store (Redis/Memcached) for scalability  
- API Gateway / Load Balancer (NGINX, AWS API Gateway, Cloudflare)  

✅ Enforces **real protection**

---

## 🔹 Example Code

### Frontend (JS Throttle Example)
```javascript
let lastCall = 0;
function callApi() {
  const now = Date.now();
  if (now - lastCall < 1000) {
    console.log("Wait before calling again");
    return;
  }
  lastCall = now;
  fetch("/api/data");
}


const rateLimit = require("express-rate-limit");

const limiter = rateLimit({
  windowMs: 1 * 60 * 1000, // 1 minute
  max: 100, // limit each IP to 100 requests per minute
  message: "Too many requests, please try again later."
});

app.use("/api/", limiter);


