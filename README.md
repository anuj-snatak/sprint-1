# Notification API - Complete Setup Documentation (As per Application Template)

---

## Author Details

| Author    | Created On | Version | Last Updated By | Last Edited On |
| --------- | ---------- | ------- | --------------- | -------------- |
| Anuj Jain | 28-07-2025 | v1      | Anuj Jain       | 28-07-2025     |

---

## Purpose

The purpose of the Notification API is to handle and manage all notification-related functionality across different modules of the application. This includes sending emails, SMS, and other user alerts in a decoupled and event-driven manner. The idea behind building this service was to centralize all notification logic, make it reusable, scalable, and easier to maintain.

---

## Pre-requisites

### System Requirements

| Hardware Specifications | Minimum Recommendation |
| ----------------------- | ---------------------- |
| Processor               | Dual-core              |
| RAM                     | 4 GB                   |
| Disk                    | 20 GB                  |
| OS                      | Ubuntu 22.04           |

### Dependencies

#### Build Time Dependencies

| Name    | Version | Description                     |
| ------- | ------- | ------------------------------- |
| Node.js | 18.x    | Required for running the server |
| Docker  | 20.x    | For containerization            |
| Git     | latest  | For source code management      |

#### Run Time Dependencies

| Name           | Version | Description                          |
| -------------- | ------- | ------------------------------------ |
| MongoDB        | 6.x     | To store logs and notification data  |
| Kafka          | 3.x     | For event-driven message consumption |
| Mailgun/Twilio | Any     | To send Email/SMS                    |

#### Other Dependencies

| Name    | Version | Description                     |
| ------- | ------- | ------------------------------- |
| dotenv  | latest  | Environment variable management |
| winston | latest  | For logging                     |

### Important Ports

#### Inbound Traffic

| Port | Description      |
| ---- | ---------------- |
| 9042 | Used by ScyllaDB |

#### Outbound Traffic

| Port | Description         |
| ---- | ------------------- |
| 8080 | Used by Express API |

---

## Architecture

> !\[Architecture Diagram Placeholder]

(Insert system-level architecture diagram showing notification flow from event source to Email/SMS delivery)

---

## Dataflow Diagram

**Explanation**: Whenever a service (like User or Order) triggers an event (e.g., user signup or order placed), that event is sent to Kafka. Notification API listens to those events, processes them using predefined templates, and delivers the final message to the user using the right channel (Email/SMS).

---

## Step-by-step Installation of Notification API

### Step 1: Install Software Dependencies

#### Build Time

```bash
sudo apt install git
sudo apt install docker docker-compose
```

#### Run Time

```bash
sudo apt install mongodb
sudo systemctl start mongodb
```

#### Other Dependencies

```bash
npm install dotenv winston
```

### Step 2: Build / Artifact Generation

```bash
git clone https://github.com/OT-MICROSERVICES/notification-api.git
cd notification-api
npm install
```

### Step 3: Application Deployment

```bash
docker-compose up --build
```

```bash
# Validate the app
curl http://localhost:8080/health
```

---

## Monitoring

Monitoring helps track performance, usage, and errors.

### Metrics

| Parameter          | Description              | Priority | Threshold              |
| ------------------ | ------------------------ | -------- | ---------------------- |
| Disk Utilization   | Disk space usage         | High     | > 90%                  |
| Availability       | Uptime percentage        | High     | >= 99.9%               |
| Memory Utilization | RAM usage                | Medium   | > 80%                  |
| CPU Utilization    | CPU time usage           | Medium   | > 70%                  |
| Network Traffic    | Data in/out              | Medium   | Varies per use-case    |
| Latency            | API response time        | High     | < 300ms                |
| Errors             | Error rate               | High     | > 5/min                |
| Throughput         | Requests per minute      | High     | > 1000 req/min         |
| Security           | Auth + Encryption health | High     | Must be enabled always |

---

## Health Checks

| Name         | Type           | InitialDelaySeconds | PeriodSeconds | TimeoutSeconds | SuccessThreshold | FailureThreshold |
| ------------ | -------------- | ------------------- | ------------- | -------------- | ---------------- | ---------------- |
| notification | ReadinessProbe | 10                  | 10            | 5              | 1                | 3                |
| notification | LivenessProbe  | 10                  | 10            | -              | 5                | 1                |

**Explanation of Parameters**

* **ReadinessProbe**: Checks if app is ready to receive requests.
* **LivenessProbe**: Checks if app is running.
* **InitialDelaySeconds**: Delay before first check.
* **PeriodSeconds**: Time between checks.
* **TimeoutSeconds**: Max wait time.
* **SuccessThreshold**: Minimum success before OK.
* **FailureThreshold**: Failure count before restart.

---

## Logging

| Log Type            | Path             | Description                    |
| ------------------- | ---------------- | ------------------------------ |
| Event Logs          | /logs/event.log  | Logs related to system actions |
| Authentication Logs | /logs/access.log | Tracks login/auth activities   |
| Server Logs         | /logs/server.log | Server-side logs and errors    |
| Threat Logs         | /logs/threat.log | Security threats and alerts    |

---

## Disaster Recovery (DR)

In case of a crash (due to attack, failure, or disaster), the service should:

* Backup logs and templates regularly
* Use Docker to re-deploy quickly
* Kafka replay feature to restore undelivered messages

---

## High Availability (HA)

* Use replicas and load balancer
* Deploy on multiple zones
* Keep service stateless where possible

> DR is for recovery **after** failure. HA is for preventing downtime in the **first place**.

---

## Troubleshooting

| Issue                        | Solution                                    |
| ---------------------------- | ------------------------------------------- |
| Email not sending            | Check Mailgun API key                       |
| Kafka not consuming messages | Check topic name and consumer group config  |
| `.env` values not loaded     | Ensure `dotenv.config()` is present in code |
| Service not starting         | Check `docker-compose logs` for errors      |

---

## FAQs

**Q: Is this application free?**
Yes, it’s completely open-source.

**Q: Can I deploy this on any cloud?**
Yes, it can be deployed on any platform like AWS, Azure, GCP.

**Q: Is there an enterprise version?**
No, currently only open-source version is available.

---

## Contact Information

| Name      | Email                                             |
| --------- | ------------------------------------------------- |
| Anuj Jain | [anuj@mygurukulam.co](mailto:anuj@mygurukulam.co) |

---

## References

| Link                                                                                                                                                                         | Description                          |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------ |
| [https://github.com/OT-MICROSERVICES/documentation-template/wiki/Application-Template](https://github.com/OT-MICROSERVICES/documentation-template/wiki/Application-Template) | Base template followed               |
| [https://www.jenkins.io/doc/book/installing/linux/#debianubuntu](https://www.jenkins.io/doc/book/installing/linux/#debianubuntu)                                             | Format reference for system sections |
| [https://amplifi.com/user-guide/FAQs.html](https://amplifi.com/user-guide/FAQs.html)                                                                                         | Structure idea for FAQs section      |
