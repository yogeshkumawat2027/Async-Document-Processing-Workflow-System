# 🚀 Async Document Processing Workflow System

A production-style full stack application that enables users to upload documents, process them asynchronously, track progress, review extracted data, and export final results.


## 🌐 Repositories

* Backend: https://github.com/yogeshkumawat2027/docflow-backend
* Frontend: https://github.com/yogeshkumawat2027/docflow-frontend
---

## 📌 Overview

This project demonstrates a real-world asynchronous workflow using:

* Background job processing (Celery)
* Real-time progress tracking (Redis Pub/Sub)
* Scalable backend architecture (FastAPI)
* Interactive frontend (Next.js)

---

## 🧠 Tech Stack

### Frontend

* Next.js (TypeScript)
* Axios
* WebSocket

### Backend

* FastAPI (Python)
* Celery (Background Tasks)
* Redis (Broker + Pub/Sub)
* PostgreSQL (Database)

---

## 🏗️ Architecture

```id="4a8g2m"
Client (Next.js)
       ↓
FastAPI Backend
       ↓
Redis (Broker + Pub/Sub)
       ↓
Celery Worker
       ↓
PostgreSQL
```

---

## ⚙️ Features

* Upload one or multiple documents
* Asynchronous document processing
* Real-time progress tracking
* Job states: Queued, Processing, Completed, Failed
* Search, filter, and sorting
* Review and edit extracted data
* Finalize results
* Retry failed jobs
* Export as JSON and CSV

---

## 🧪 Backend API Testing (Local Environment)

⚠️ **Note:** Backend deployment is currently not fully functional on cloud due to background worker limitations (explained below).
Therefore, the following screenshots are from the **local working environment**.

### 🔹 Upload API

<img src="https://github.com/user-attachments/assets/6078c5d6-ab72-4103-b1dc-4db3b8cf9ed8" width="100%"/>

### 🔹 Job Listing API

<img src="https://github.com/user-attachments/assets/6d8d853d-431b-4098-8034-13585004fe6c" width="100%"/>

### 🔹 Job Detail API

<img src="https://github.com/user-attachments/assets/7b15cc85-6c4c-44c2-bccb-3b9a1351ed6b" width="100%"/>

### 🔹 Status Tracking

<img src="https://github.com/user-attachments/assets/21b8fd50-9540-46a5-b8e1-04c548b8232a" width="100%"/>

---

## 💻 Frontend UI (Local)

The frontend is fully functional and integrated with the backend locally.

### 🔹 Dashboard

<img src="https://github.com/user-attachments/assets/77fd291d-f1ae-46b6-84fe-99c9d8545a4a" width="100%"/>

### 🔹 Upload Interface

<img src="https://github.com/user-attachments/assets/c8786268-8cf7-4fff-9e80-478a27241175" width="100%"/>

### 🔹 Job Detail Page

<img src="https://github.com/user-attachments/assets/af9b0447-7212-4ffb-ab65-0fc874973746" width="100%"/>

### 🔹 Processed Output

<img src="https://github.com/user-attachments/assets/49f04880-c678-4612-ab99-1b7b1e77df83" width="100%"/>

### 🔹 Finalized Result

<img src="https://github.com/user-attachments/assets/846bb072-59f2-4ee1-a4aa-809e6c6e7af1" width="100%"/>

---



---

## 🚀 Deployment Status

The application was deployed using Render with:

* FastAPI Web Service
* Celery Worker (Background Service)
* PostgreSQL
* External Redis

---

## ⚠️ Deployment Limitation (Important)

Due to limitations of free-tier deployment on Render:

* Celery Worker (background tasks) becomes inactive after some time
* Redis Pub/Sub events are not reliably maintained
* Backend background processing does not run continuously

👉 As a result:

* Backend APIs may not function correctly in deployed environment
* Async processing is not consistently triggered in production

---

## ✅ Important Clarification

* The **complete asynchronous workflow is fully implemented and working locally**
* All required features (Celery, Redis Pub/Sub, job tracking) are properly integrated
* The limitation is **deployment-related**, not implementation-related

---

## 🧠 Engineering Decisions

### Celery

Used for asynchronous processing to avoid blocking API requests.

### Redis

Used as:

* Message broker for Celery
* Pub/Sub system for real-time updates

### Async Architecture

Ensures:

* Non-blocking execution
* Better scalability
* Clean separation of concerns

---

## 🧱 Local Setup

### Backend

```id="v4u9t8"
cd backend
python -m venv venv
venv\Scripts\activate

pip install -r requirements.txt

uvicorn app.main:app --reload
```

Run Celery Worker:

```id="r9h0lu"
celery -A app.workers.tasks worker --loglevel=info
```

---

### Frontend

```id="l7s2df"
cd frontend
npm install
npm run dev
```

---

## 📦 Sample Output

```json id="u2dx2k"
{
  "title": "Sample Document",
  "category": "General",
  "summary": "Auto-generated summary",
  "keywords": ["sample", "document"]
}
```

---

## ⚖️ Trade-offs

* Simulated document processing instead of heavy OCR/AI
* Free-tier deployment affects worker reliability

---

## 🚧 Limitations

* No authentication
* Worker not persistent on free tier
* No production-grade deployment (yet)

---

## 🎥 Demo Video

👉 Add your demo video link here

---

## 🤖 AI Usage

AI tools were used for:

* Architecture guidance
* Code structuring

Final implementation and debugging were done manually.

---

## 👨‍💻 Author

**Yogesh Kumawat**
Full Stack Developer
