# Adaptive Load-Balanced Crowdsourced Troubleshooting System

## 📌 Overview

This project proposes an **Adaptive Load-Balanced Crowdsourced Troubleshooting System** built on a **distributed microservice architecture**.
The system simulates **four geographically partitioned nodes** (North, South, East, West), each operating independently with its own backend stack.

When a user submits an issue, it is:

1. **Queued & prioritized** based on urgency and wait time.
2. **Matched with the best expert** on that node using a **multi-factor scoring algorithm**.
3. **Routed to peer nodes** if no suitable expert is available locally.
4. **Connected via real-time chat** for user–expert communication.

This approach ensures **fault-tolerance, adaptability, and efficient load balancing** across distributed environments.

## ✨ Key Features

*  **Distributed Microservices** – Four fault-isolated regional nodes (North, South, East, West).
*  **Expert Scoring Algorithm** combining:

  * **Skill Match** (Jaccard Similarity)
  * **Semantic Match** (Sentence-BERT)
  * **Trust Score** (Exponential Moving Average)
  * **Availability** (active/inactive filtering)
  * **Inverse Load** (prefer less busy experts)
*  **Priority Queuing** for issues (based on urgency + wait time).
*  **Fallback & Peer Forwarding** – Issues are retried or sent to another node if unresolved.
*  **Real-time Chat** between user and expert using **WebSockets**.
*  **Fault-Tolerant & Adaptive** to changing expert availability and fluctuating demand.


---

## 🛠️ Tech Stack

* **Backend:** FastAPI
* **Database:** MongoDB
* **Containerization:** Docker
* **Inter-node Communication:** REST APIs
* **Real-time Communication:** WebSockets
* **NLP Models:** Sentence-BERT, Jaccard Similarity
* **Algorithms:** Exponential Moving Average (Trust Score), Greedy Fallback Routing
* **Frontend (basic):** HTML/CSS/JS for issue submission interface

---

## 📂 System Architecture

```
                ┌───────────────┐
   User Issue → │   Frontend     │
                └───────┬───────┘
                        │
             ┌──────────┴──────────┐
             │ Priority Queue &     │
             │ Multi-factor Scoring │
             └──────────┬──────────┘
                        │
        ┌───────────────┴─────────────────┐
        │       Distributed Nodes          │
        │  (North | South | East | West)   │
        └───────┬───────────────┬─────────┘
                │ REST API       │ Peer Forwarding
                │ Communication  │
                ▼                ▼
           Expert Pool      Other Nodes
                │
       Real-time Chat (WebSockets)
                │
           Issue Resolution
```

---


## 🧪 Testing the System

* Submit issues with different **urgency levels** and **keywords** via the frontend.
* Observe **expert allocation decisions** based on skill match, trust score, and load balancing.
* Simulate **node failure** by stopping a container – issues will reroute to available nodes.
* Use the **real-time chat interface** to interact with experts.

---

## 👥 Contributors

* Sarayu Krishna
  

---


