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
