# 🧪 Medical Laboratory GraphQL API

A GraphQL API for managing **patients, laboratory tests, samples, and diagnostic results**.
Built to simulate a real-world diagnostic lab backend with relational data and test workflows.

---

## 🚀 Project Goal

To design and implement a **GraphQL-based backend** that allows:

* Managing patients and their diagnostic history
* Tracking lab tests and categories
* Creating and monitoring sample workflows
* Recording and validating test results
* Supporting lab and technician entities

---

## 🏗️ Data Models

### 👤 Patient

* `id`
* `name`
* `date_of_birth`
* `gender`
* `email`
* `phone`

### 🧬 Test

* `id`
* `name`
* `category`
* `price`
* `turnaround_time`
* `unit`

### 🧪 Sample

* `id`
* `patient_id`
* `test_id`
* `collected_at`
* `status` → `collected | in_progress | completed`

### 📊 Result

* `id`
* `sample_id`
* `value`
* `reference_range`
* `status`

### 🏥 Lab

* `id`
* `name`
* `address`
* `accreditation`

### 👩‍🔬 Technician

* `id`
* `name`
* `certification`
* `specialization`

---

## 📡 GraphQL Queries

### 1️⃣ Get Patient Tests

```graphql
query {
  patient(id: 1) {
    name
    samples {
      test { name }
      collectedAt
      status
    }
  }
}
```

### 2️⃣ Get Sample Result

```graphql
query {
  sample(id: 1) {
    test { name }
    result { value referenceRange }
  }
}
```

### 3️⃣ Get Tests by Category

```graphql
query {
  tests(category: "blood") {
    name
    price
    turnaroundTime
  }
}
```

---

## ✍️ Mutations

### ➕ Create Sample

```graphql
mutation {
  createSample(input: {
    patientId: 1
    testId: 1
  }) {
    sample {
      id
      status
    }
  }
}
```

### 🧾 Record Result

```graphql
mutation {
  recordResult(input: {
    sampleId: 1
    value: "7.5"
    referenceRange: "6.0-8.0"
  }) {
    result {
      id
      status
    }
  }
}
```

---

## ✅ Features Implemented

✔ Patient sample tracking
✔ Reference range validation
✔ Test category filtering
✔ Turnaround time display
✔ Sample workflow status
✔ Multiple tests support
✔ Technician assignment

---

## 🧪 Expected Test Cases

1. Patients can have multiple samples
2. Results validated against reference range
3. Tests filter by category
4. Turnaround time returned
5. Sample status updates correctly
6. Multiple tests linked
7. Technician assigned to processing

---

## 🛠️ Tech Stack

* GraphQL
* Node.js
* Apollo Server (or similar)
* JavaScript / TypeScript

---

## ▶️ How to Run

```bash
git clone https://github.com/adarsh985/Graph-QL.git
cd Graph-QL
npm install
npm run dev
```

Server will start at:

```
http://localhost:4000/graphql
```

---

## 📸 Demo

Screenshots of queries and responses are available in the `/docs` folder
(as shown in the presentation).

---

## 📌 Future Improvements

* Authentication & roles (admin / technician)
* Pagination & filtering
* Lab analytics dashboard
* Real database integration
* Report PDF generation
* Notification system

---

## 👨‍💻 Author

**Adarsh**
GraphQL Lab Management Project

---

## 📄 License

MIT License
