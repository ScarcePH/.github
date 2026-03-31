# 👟 Scalable Shoe Reselling Platform (Async OCR Validation System)

## Overview

This project is a **web-based shoe reselling platform** designed with a **production-style architecture** that combines e-commerce workflows with asynchronous processing.

It solves a real operational problem:
**reducing manual validation workload** by automatically filtering invalid payment submissions using OCR before they reach the admin.

The system is fully deployed and supports both **user and admin roles**, with a mobile-responsive frontend.

---

## 🧩 Architecture

```id="arch1"
Client (React Web App - Mobile Responsive)
        ↓
Backend API (Order, Auth, Inventory)
        ↓
Task Queue (Cloud Tasks)
        ↓
Workers:
  - OCR Worker (payment validation)
  - Email Worker (admin notification)
        ↓
Database
```

---

## ⚙️ Core Features

### 🛒 User Features

* Register / Login or continue as **Guest**
* Browse shoe listings
* Add to cart or **direct checkout**
* Upload **proof of payment screenshot**
* Real-time order submission flow

---

### 🧑‍💼 Admin Features

* Dashboard with business insights:

  * Orders (weekly metrics)
  * Revenue & profit tracking
  * Best-selling shoes
  * Performance comparison (week/month deltas)
* Order management:

  * Approve / Decline orders
* Inventory management system

---

## 🔄 Smart Payment Validation Flow (Key Feature)

This is the core differentiator of the system.

1. User submits order with payment screenshot
2. Backend enqueues OCR validation job
3. OCR Worker extracts text from image
4. System checks for sample keywords like:

   * “transaction complete”
   * “sent funds”
   
5. If **valid → proceed**, else **filtered out automatically**
6. Email Worker notifies admin of valid orders
7. Admin reviews and approves/declines
8. Email worker notifies customers order

---

## 🧠 Engineering Highlights

* Designed **asynchronous validation pipeline** using task queues
* Reduced admin workload by **automating payment pre-validation (OCR filtering)**
* Implemented **decoupled worker architecture** for scalability and fault isolation
* Built **event-driven workflow** (Checkout → OCR → Email → Admin Action)
* Structured system to support **horizontal scaling of workers**
* Separated concerns across services (API vs Workers)

---

## 🛠️ Tech Stack

**Frontend**

* React (mobile responsive)

**Backend**

* Python Flask

**Infrastructure**

* Cloud Tasks (async job queue)
* Worker services (OCR + Email)

**Integrations**

* Mailtrap (email notifications)
* OCR processing (image → text extraction)

---

## 📦 Repositories

* Frontend: https://github.com/ScarcePH/frontend
* Backend: https://github.com/ScarcePH/backend
* OCR Worker: https://github.com/ScarcePH/ocr-worker
* Email Worker: https://github.com/ScarcePH/email-worker

---

## 🌐 Live Demo

Frontend: [Scarceph.com]([url](https://scarceph.com/))


### Test Flow

1. Add item to cart or checkout directly
2. Upload payment screenshot
3. OCR validates payment text
4. Admin/User receives email notification
5. Admin approves or declines order
6. User receives email notification of order

---

## 🚧 System Constraints & Design Decisions

* No payment gateway integration.
  → Manual validation with OCR-assisted filtering
* OCR is used as a **pre-validation layer**, not final verification
* Admin remains the final authority for order approval

---

## 🔐 Future Improvements

* Retry mechanism with exponential backoff (worker jobs)
* Dead-letter queue for failed OCR/email jobs
* Payment gateway integration (If business permit is available)
* Observability (logging, monitoring, alerts)
* Fraud detection beyond keyword matching

---

## 📌 Why This Project Matters

This project demonstrates:

* Real-world **e-commerce system design**
* **Async processing and worker architecture**
* Practical use of **OCR for business automation**
* Ability to build and deploy **multi-service systems**
* Focus on **scalability and operational efficiency**

It goes beyond basic CRUD by solving a **real operational bottleneck** using system design.
