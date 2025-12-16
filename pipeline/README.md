# 🐳 Docker Workshop – Beginner Guide

**Author:** MuleMED

**Based on:** Data Engineering Zoomcamp (Alexey Grigorev)

---

## 📌 What is this?

This project is a **simple Docker workshop** for beginners.
It teaches you how to:

* Run Python programs using Docker
* Build your own Docker image
* Pass arguments to containers
* Run PostgreSQL using Docker
* Understand how Docker is used in data engineering

You do **not** need to be a Docker expert. Everything here is step-by-step.

---

## 🧠 What you will learn (in simple words)

By the end of this workshop, you will know how to:

* Use Docker instead of installing everything on your computer
* Run a Python script inside a container
* Give inputs (arguments) to a Docker container
* Run a database (PostgreSQL) using Docker
* Understand how data pipelines are executed in real projects

---

## 📂 Project structure

```
dezoomcamp-docker/
├── README.md
└── pipeline/
    ├── Dockerfile
    ├── pipeline.py
    ├── pyproject.toml
    └── .venv/
```

### What each file means

* **pipeline.py** → A simple Python script (our pipeline)
* **Dockerfile** → Instructions Docker uses to build the image
* **pyproject.toml** → Python project configuration
* **.venv/** → Virtual environment for local Python work

---

## 🧰 Requirements

Before starting, install:

* Docker
* Git

Check Docker:

```bash
docker --version
```

---

## 🚀 Getting started

### 1️⃣ Clone the repository

```bash
git clone https://github.com/alexeygrigorev/workshops.git
cd workshops/dezoomcamp-docker
```

---

## 🐍 Run the Python script (without Docker)

Go to the pipeline folder:

```bash
cd pipeline
```

Run the script:

```bash
python pipeline.py 1
```

Output:

```
Hello Pipeline, month = 1
```

---

## 🐳 Build the Docker image

From inside the `pipeline` folder:

```bash
docker build -t test:pandas .
```

This creates a Docker image called **test:pandas**.

---

## ▶️ Run the pipeline using Docker

```bash
docker run -it --rm test:pandas 12
```

What this means:

* `test:pandas` → the image name
* `12` → argument passed to the script (month)
* `--rm` → container is deleted after running

Output:

```
Hello Pipeline, month = 12
```

---

## 🐘 Run PostgreSQL using Docker

Start a Postgres database:

```bash
docker run -it --rm \
  -e POSTGRES_USER=root \
  -e POSTGRES_PASSWORD=root \
  -e POSTGRES_DB=ny_taxi \
  -v ny_taxi_postgres_data:/var/lib/postgresql/data \
  -p 5432:5432 \
  postgres:18
```

### What this does

* Creates a database named `ny_taxi`
* Username: `root`
* Password: `root`
* Saves data in a Docker volume

---

## 🔌 Connect to PostgreSQL

From another terminal:

```bash
psql -h localhost -p 5432 -U root -d ny_taxi
```

Password:

```
root
```

---

## 🧠 Why Docker is important

Docker helps you:

* Avoid "it works on my machine" problems
* Run the same code anywhere
* Package Python + libraries + config together
* Run databases without installing them locally

This is how **real data engineering pipelines** are run.

---

## 🎯 Who this is for

* Absolute beginners
* Students learning data engineering
* Anyone following Data Engineering Zoomcamp
* Developers who want to understand Docker basics

---

## 👤 Author

**MuleMED**
Learning and building real-world data & software systems 🚀

---

## 📝 Notes

This project is for **learning purposes**.
Feel free to experiment, break things, and rebuild.

Docker skills come from practice 💪
