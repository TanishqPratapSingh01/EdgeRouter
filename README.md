# 🌍 EdgeRouter

**EdgeRouter** is a geographic request dispatcher that simulates how a **Content Delivery Network (CDN)** routes user requests to the nearest edge server based on geographic location.

The project demonstrates the core concept behind edge computing by determining a client's approximate location from their IP address and forwarding the request to the geographically closest server. While it is a simulation, it closely mirrors the decision-making process used by modern CDNs such as Cloudflare, Akamai, and AWS CloudFront.

---

## 📖 Overview

When a user sends a request, a real CDN attempts to minimize latency by serving content from the closest available edge server instead of the origin server.

EdgeRouter recreates this routing logic in a simplified environment.

### Request Flow

```
Client Request
      │
      ▼
Extract Client IP
      │
      ▼
GeoIP Lookup
      │
      ▼
Determine Client Coordinates
      │
      ▼
Calculate Distance to Each Server
      │
      ▼
Select Nearest Server
      │
      ▼
Forward Request
```

---

## ✨ Features

* Detects the client's IP address
* Maps the IP to an approximate geographic location using a GeoIP database
* Stores multiple server locations with geographic coordinates
* Calculates the distance between the client and each server
* Selects the nearest server
* Simulates CDN edge routing
* Modular architecture for adding more servers in the future

---

## 🛠 Tech Stack

* **Backend:** Node.js
* **Framework:** Express.js
* **GeoIP Library:** geoip-lite (or any GeoIP database)
* **Language:** JavaScript / TypeScript
* **Distance Calculation:** Haversine Formula

---

## 📂 Project Structure

```
EdgeRouter/
│
├── server/
│   ├── index.js
│   ├── routes/
│   ├── services/
│   │     ├── geoService.js
│   │     ├── routingService.js
│   │     └── distanceCalculator.js
│   └── config/
│         └── servers.js
│
├── README.md
├── package.json
└── .gitignore
```

---

## ⚙️ How It Works

### Step 1

A client sends a request to the dispatcher.

### Step 2

The dispatcher extracts the client's IP address.

### Step 3

A GeoIP database converts the IP address into approximate latitude and longitude coordinates.

Example:

```
IP Address
↓

203.0.113.20

↓

Latitude: 28.61
Longitude: 77.20
Location: Delhi
```

### Step 4

The dispatcher compares the client's coordinates with the coordinates of all available servers.

Example servers:

| Server   | Location  |
| -------- | --------- |
| Server A | Mumbai    |
| Server B | Singapore |
| Server C | London    |

### Step 5

The Haversine Formula calculates the geographic distance between the client and every server.

### Step 6

The closest server is selected and the request is forwarded there.

---

## 🌎 Example

```
Client IP
↓

New Delhi

↓

Distances

Mumbai      → 1148 km
Singapore   → 4160 km
London      → 6700 km

↓

Nearest Server

✅ Mumbai
```

---

## 🚀 Running the Project

Clone the repository:

```bash
git clone https://github.com/your-username/EdgeRouter.git
```

Move into the project:

```bash
cd EdgeRouter
```

Install dependencies:

```bash
npm install
```

Run the application:

```bash
npm start
```

---

## 🧮 Routing Algorithm

The routing decision is based on the shortest geographic distance.

```
For each server:

distance = Haversine(client, server)

Return server with minimum distance.
```

Time Complexity:

```
O(n)
```

Where **n** is the number of edge servers.

---

## 🎯 Learning Objectives

This project demonstrates:

* CDN request routing
* Edge computing concepts
* GeoIP lookup
* IP geolocation
* Geographic distance calculations
* Backend request forwarding
* Express middleware
* Service-oriented backend architecture

---

## 🔮 Possible Improvements

* Add load balancing between equally close servers
* Health checks for unavailable servers
* Dynamic server registration
* Docker support
* Kubernetes deployment
* Interactive map showing request routing
* Caching layer
* Latency-based routing instead of geographic routing
* Real-time routing dashboard
* Support for dozens of edge servers

---

## 📚 Concepts Covered

* Content Delivery Networks (CDNs)
* Edge Computing
* IP Geolocation
* Geographic Routing
* Reverse Proxy Concepts
* Distributed Systems
* Backend Networking
* Haversine Distance Formula

---

## 🤝 Contributing

Contributions, suggestions, and improvements are welcome. Feel free to open an issue or submit a pull request.

---

## 📄 License

This project is licensed under the MIT License.
