# Network Fundamentals: Section Intro

[← Back to index](../README.md)

**Objectives:** 1.2 (appliances, applications, functions) · 1.6 (topologies, architectures, types) · 2.3 (wireless devices and technologies)

This intro covers what a network is, PANs and LANs, the basic home network chain, converged networks and the "five nines" of availability.

---

## 1. What is a network?

**Simple version:** Two or more devices connected so they can share data. It doesn't have to be the internet, and it doesn't have to involve a computer.

**Two ways to connect:**
- **Wired:** Ethernet, fiber optic
- **Wireless:** Wi-Fi, cellular, Bluetooth

**Analogy:** A road system. Paved roads (wired) and shipping lanes (wireless) are built differently, but both move cargo (data).

**Where you see it:** Laptop on Wi-Fi, phone on 5G, watch paired to phone. Those are all networks.

---

## 2. PAN vs. LAN

### PAN: Personal Area Network
- Covers the space around **one person** (a few meters)
- Most common tech: **Bluetooth**
- Example: smartwatch ↔ phone, AirPods ↔ laptop
- **Analogy:** whispering to the person next to you

### LAN: Local Area Network
- Covers **one location**: a home, an office, a floor
- Common tech: **Ethernet, Wi-Fi**
- Example: home Wi-Fi connecting tablet, TV and laptop
- **Analogy:** the hallways inside one house

**Size order (covered later):** PAN → LAN → CAN → MAN → WAN

---

## 3. The basic home network chain

**Desktop → Switch → Router → Modem → Internet**

| Device | Job | Analogy |
|---|---|---|
| Switch | Connects devices **inside** your network | Hallways between rooms |
| Router | Connects **your network** to **other networks** | Mailroom deciding where letters go |
| Modem | Translates the ISP signal for your router | Loading dock to the public road |

**Real-world note:** A home ISP box is usually modem + router + switch + Wi-Fi in one. Businesses use separate devices. The exam treats them as separate roles.

**Dev angle:**
- `localhost:3000` → never leaves your machine
- Teammate hits `192.168.1.25:3000` on the same Wi-Fi → stays in the LAN
- Deployed to the cloud → goes all the way out through the modem to the internet

---

## 4. Converged networks

**Old way:** separate networks for voice (phone lines), data (computers) and video (cable TV).

**Now:** one network carries **voice + data + video** together as **IP packets**.

**Analogy:** One delivery truck carries letters, packages and newspapers, because everything is just a box with an address.

**Where you see it:**
- Phones treat calls, texts, browsing and streaming all as data
- Zoom calls share the office connection with email and downloads
- VoIP desk phones plug into the same network as computers

**Why it matters:** Voice and video are **delay-sensitive**. Converged networks use **QoS (Quality of Service)** to prioritize real-time traffic. *(More on QoS later.)*

---

## 5. High availability and the five nines

**Availability** = percentage of time a network or service is up.

100% uptime isn't realistic. Uptime goals are set in an **SLA (Service Level Agreement)**.

**Five nines = 99.999% ≈ 5 minutes of downtime per year.**

See the full table: [Uptime cheat sheet](../cheat-sheets/uptime-nines.md)

**Analogy:** A store promising to be closed only 5 minutes all year, outages included.

**Dev angle:** Cloud providers publish SLAs as percentages. That number tells you how much downtime is allowed before you're owed credits.

---

## What CompTIA is likely to test

- **Five nines = 99.999% ≈ 5 min/year**
- **Bluetooth = PAN**
- **Switch** = within a network · **Router** = between networks
- **Converged network** = voice + data + video on one IP network
- **SLA** = where the uptime target is defined

## Common traps

- ❌ Mixing up five nines (~5 min) and four nines (~53 min). Each extra 9 cuts downtime by 10×.
- ❌ Treating 100% uptime as the goal. High availability is the goal.
- ❌ Confusing modem and router. The modem faces the ISP; the router directs traffic.
- ❌ Assuming "network" means the internet. Bluetooth headphones + phone is a network.

---

## Key Terms

### Network
- **Term:** Two or more devices connected to share data
- **Analogy:** A road system moving cargo
- **Example:** Laptop and printer on home Wi-Fi
- **Exam tip:** Includes wired *and* wireless; doesn't require the internet

### PAN (Personal Area Network)
- **Term:** Very short-range network around one person
- **Analogy:** Whispering to the person next to you
- **Example:** Smartwatch paired to a phone over Bluetooth
- **Exam tip:** Bluetooth → PAN. Smallest network type.

### LAN (Local Area Network)
- **Term:** Network covering one location, like a home or office
- **Analogy:** Hallways inside one house
- **Example:** Office Wi-Fi and Ethernet connecting every desk
- **Exam tip:** Size order: PAN → LAN → CAN → MAN → WAN

### Switch
- **Term:** Connects devices within the same network
- **Analogy:** Hallways connecting rooms in a building
- **Example:** The box under a desk with many Ethernet cables
- **Exam tip:** Works *inside* a LAN

### Router
- **Term:** Connects different networks and directs traffic between them
- **Analogy:** The mailroom deciding where outgoing letters go
- **Example:** Home router sending LAN traffic to the internet
- **Exam tip:** Routers connect networks; switches connect devices

### Modem
- **Term:** Converts the ISP's signal into data your network can use (modulator-demodulator)
- **Analogy:** Loading dock where the building meets the public road
- **Example:** The cable or fiber box from your ISP
- **Exam tip:** Faces the ISP side; not the same as a router

### Wireless Access Point (WAP)
- **Term:** Lets wireless devices join a wired network
- **Analogy:** A doorway in from outside
- **Example:** Wi-Fi unit mounted on an office ceiling
- **Exam tip:** Big part of Objective 2.3

### Converged Network
- **Term:** One network carrying voice, data and video as IP packets
- **Analogy:** One delivery truck carrying letters, packages and newspapers
- **Example:** Zoom calls and file downloads on the same office connection
- **Exam tip:** Voice/video need QoS on converged networks

### Availability / Uptime
- **Term:** Percentage of time a network or service is working
- **Analogy:** Percentage of hours a store is actually open
- **Example:** Status page showing "99.98% uptime this month"
- **Exam tip:** 100% isn't realistic; high availability is the goal

### Five Nines
- **Term:** 99.999% availability
- **Analogy:** A store closed only 5 minutes all year
- **Example:** Carrier-grade phone systems, critical data centers
- **Exam tip:** ≈ 5 min downtime/year. Four nines ≈ 53 min.

### SLA (Service Level Agreement)
- **Term:** Formal agreement defining expected service levels, like uptime
- **Analogy:** A written warranty promise
- **Example:** Cloud provider promising 99.99% uptime or service credits
- **Exam tip:** SLA = where the uptime target is officially stated
