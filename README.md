# Docker Cron Python Automation

Automate Python scripts with Docker and cron — a lightweight, portable scheduling solution.

## Project Overview

This project showcases a fully containerized approach to running scheduled Python scripts using **cron** inside **Docker**. It’s designed for repeatable tasks like data processing, notifications, or any routine automation, all while keeping the host environment clean and consistent.

This project highlights skills in:

* **Python scripting** for automation.
* **Docker** for containerization and portability.
* **Cron** for task scheduling.

## Features

* Run Python scripts on a defined schedule without relying on the host machine.
* Fully containerized: works consistently across any platform.
* Easy to extend: add more scripts and schedule them in the `crontab`.
* Logs output to Docker logs for easy monitoring.
* Option to manually run scripts on demand using `docker exec`.

## How It Works

1. **Place Python scripts** in the project directory (e.g., `script.py`).
2. **Define schedules** in the `crontab` file.
3. **Build the Docker image** and run the container. Cron will execute scripts according to your schedule.
4. **Optionally, run scripts manually** using Docker commands.

## Getting Started

### Prerequisites

* Docker installed on your system.

### Setup

Clone the repository:

```bash
git clone https://github.com/yourusername/docker-cron-python.git
cd docker-cron-python
```

Edit the `crontab` to set the schedule for your scripts. Example: run `script.py` every day at 2 AM:

```cron
0 2 * * * python /app/script.py
```

Build and run the Docker container:

```bash
docker build -t docker-cron-python .
docker run -d --name cron-python docker-cron-python
```

### Manual Run

To execute a Python script manually inside the running container:

```bash
docker exec -it cron-python python /app/script.py
```

This is useful for testing scripts or running them outside the scheduled cron time.

### Monitoring

View live logs from the container:

```bash
docker logs -f cron-python
```

### Extending

* Add more scripts to `/app`.
* Add dependencies by including a `requirements.txt` in the Dockerfile:

```dockerfile
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
```

* Update `crontab` to schedule new tasks.

---

If you want, I can also **add a small workflow diagram** showing cron scheduling + manual run, which makes it visually stand out for a portfolio. Do you want me to do that?
