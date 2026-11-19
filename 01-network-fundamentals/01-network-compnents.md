# Network Components

[← Back to index](../README.md)

**Objective:** 1.2 (compare and contrast networking appliances, applications and functions)

The whole point of a network is to move data from one machine to another. This lesson is the "cast of characters": the 15 pieces that make that happen. Each one gets covered in more depth later, so the goal here is just to know **what each one does** and **how it differs from the ones it gets confused with**.

> **Quick note on "layers":** You'll see "Layer 1," "Layer 2" and so on below. That's the OSI model, which comes later in the course. For now, just remember the number next to each device. It'll click once you get there.

---

## The big picture

One analogy covers the whole lesson. **Think of the network as a city:**

| Component | In the city |
|---|---|
| Clients | Residents |
| Servers | Businesses that provide services |
| Hub | A town crier shouting every message to everyone |
| Switch | A mail carrier who knows each house |
| Wireless access point | A radio tower for people without a road connection |
| Router | Highway interchange connecting different cities |
| Firewall | Border checkpoint |
| Load balancer | A host seating guests across several servers at a restaurant |
| Proxy | A personal assistant who runs errands for you |
| IDS / IPS | Security camera / security guard |
| Controller | City traffic control center |
| NAS | Public library |
| SAN | Private warehouse only certain businesses can use |
| Media | The roads themselves |
| WAN links | Interstate highways and flight routes between cities |

---

## 1. Clients

**What it is:** Any device a person uses to access the network.

- Laptops, desktops, phones, tablets, smart TVs, even a Wi-Fi thermostat
- If it connects to the network to *use* something, it's a client

**Analogy:** Residents of the city. They go out and use services.

**Dev example:** Your browser hitting `localhost:3000` is the client. So is Postman when you test an API.

---

## 2. Servers

**What it is:** A device (or software) that **provides** resources to other devices.

- Web servers, email servers, file servers, database servers
- Can be dedicated hardware **or** just software running on a regular machine

**Analogy:** Businesses in the city. Residents come to them for something.

**Dev example:** `npm run dev` turns your laptop into a web server. An Express or Spring Boot app is server software.

**Exam tip:** "Server" is a **role**, not a type of box. Any machine running server software is acting as a server.

---

## 3. Hubs (legacy, but tested)

**What it is:** An old device that connects devices on a LAN by **repeating every signal out every port**.

- Doesn't know who's plugged in where
- Everyone receives everything, which means more collisions, more errors, worse performance and less security
- Evolution: **hub → bridge → switch**

**Analogy:** A town crier standing in the square shouting every letter out loud. Everyone hears it, even if it was meant for one person.

**Where you'd see it:** Almost nowhere today. CompTIA uses hubs mostly as **wrong answer choices**.

**Exam tip:** Hub = **Layer 1**. Dumb repeater. If a question describes "sends traffic out all ports," think hub.

---

## 4. Switches

**What it is:** A smarter hub that **learns which device is on which port** and only sends traffic to the right one.

- Learns devices by their **MAC address** (a hardware ID burned into each network card) and stores them in a **MAC address table**
- More efficient bandwidth, better security, fewer collisions

**Analogy:** A mail carrier who knows every house on the route and delivers each letter only to its address.

**Where you'd see it:** The box in an office closet or under a desk with lots of Ethernet cables. Your home router has a tiny switch built in (those 4 LAN ports on the back).

**Exam tip:** Switch = **Layer 2**, uses **MAC addresses**. (A "Layer 3 switch" or multilayer switch can also route; that comes later.)

---

## 5. Wireless Access Points (WAP / AP)

**What it is:** A device that lets **wireless** devices connect to a **wired** network.

- Sends data over **radio waves** instead of cables
- Like a hub, it's a **shared medium**: everyone nearby on that channel shares the airtime

**Analogy:** A radio tower that lets people without a road connection still join the city.

**Where you'd see it:** The white disc on an office ceiling. At home, it's built into your router.

**Exam tip:** A WAP **bridges** wireless to wired. It is **not** a router, even though home routers include one.

---

## 6. Routers

**What it is:** A device that **connects different networks** and decides the best path for traffic based on **IP addresses**.

- Switch = traffic *within* a network
- Router = traffic *between* networks
- Uses **routing protocols** to learn paths (covered later)

**Analogy:** A highway interchange connecting different cities. It reads the destination city (IP address) and picks the road.

**Dev example:** When your app calls an external API, your home router is what sends that request out of your LAN toward the internet.

**Exam tip:** Router = **Layer 3**, uses **IP addresses**. Switch = Layer 2, MAC addresses. This pairing gets tested constantly.

---

## 7. Firewalls

**What it is:** A security barrier that **allows or blocks traffic based on rules**.

- Rules are written as **ACLs (Access Control Lists)**: lists of "allow this, deny that"
- Usually sits between your internal network and the internet
- Can be **hardware**, **software**, or both

**Analogy:** A border checkpoint. Guards check every vehicle against a list of who's allowed in or out.

**Where you'd see it:**
- Windows Defender Firewall and macOS Firewall (software, on one machine)
- A dedicated box at the edge of an office network (hardware)
- Cloud "security groups" (AWS, Azure) that only open port 443 to your app

**Exam tip:** Firewall = **ACLs / rules**. If the question says "filters traffic based on predefined rules," it's a firewall.

---

## 8. Load Balancers

**What it is:** Spreads incoming traffic across **multiple servers** so no single one gets overwhelmed.

- Improves performance, capacity and **reliability** (if one server dies, the others keep going)
- Can be a device or software

**Analogy:** A restaurant host seating guests evenly across several servers so no one waiter gets slammed.

**Dev example:** When your app scales to 3 instances behind AWS Elastic Load Balancing, NGINX, or a platform like Vercel or Heroku, a load balancer decides which instance handles each request.

**Exam tip:** Keywords: **"distribute traffic across multiple servers," "prevent bottleneck," "high availability."** Ties back to the five nines from the intro.

---

## 9. Proxy Servers

**What it is:** A middleman between a user's device and the internet.

- **Web filtering** (blocking certain sites)
- **Caching** (saves copies of popular content to speed things up)
- **Hides the user's real IP address** for privacy and security

**Analogy:** A personal assistant who makes calls on your behalf. The other side only ever talks to the assistant, never you.

**Where you'd see it:** School or corporate networks that block social media. Dev tools also use proxies, like a React dev server proxying `/api` calls to your backend.

**Exam tip:** Two kinds you'll hear about later:
- **Forward proxy:** sits in front of **clients** (filtering, hiding users)
- **Reverse proxy:** sits in front of **servers** (NGINX in front of your app)

---

## 10. IDS vs. IPS

### IDS: Intrusion Detection System
- **Detects** suspicious activity and **alerts** an admin
- Does **not** block anything

### IPS: Intrusion Prevention System
- Detects **and acts**: blocks traffic, drops malicious packets
- Sits **inline**, so traffic flows *through* it

**Analogy:**
- IDS = a **security camera**. It sees the break-in and sounds the alarm.
- IPS = a **security guard**. He sees it and tackles the intruder.

**Exam tip:** This is one of the most-tested pairs.
- **IDS = detect + alert** (passive)
- **IPS = detect + prevent** (active, inline)
- If the answer involves *stopping* or *blocking*, it's IPS.

---

## 11. Controllers

**What it is:** A central unit that manages how other network devices behave.

- In **SDN (Software-Defined Networking)**, the controller tells switches and routers what to do through software instead of configuring each one by hand
- You'll also see **wireless LAN controllers (WLCs)**, which centrally manage lots of access points at once

**Analogy:** A city's traffic control center that sets every traffic light from one room instead of sending someone to each intersection.

**Where you'd see it:** Large office or campus Wi-Fi (Cisco, Aruba, UniFi controllers) and cloud and data center networks.

**Exam tip:** Controller = **centralized management**. SDN = network behavior controlled by software.

---

## 12. NAS: Network-Attached Storage

**What it is:** A dedicated **file storage** device that plugs into the network so many clients can share files.

- Clients see **files and folders**
- Connects over normal Ethernet

**Analogy:** A public library. Anyone with a card walks in and grabs specific books (files).

**Where you'd see it:** A Synology box in a small office, or a shared "Z: drive."

**Exam tip:** NAS = **file-level** storage.

---

## 13. SAN: Storage Area Network

**What it is:** A **dedicated high-speed network** that gives servers access to **block-level** storage.

- Servers see the storage as if it were a **local hard drive**
- Built for huge amounts of data: disk arrays, tape libraries
- Common tech: **Fibre Channel**, **iSCSI** (covered later)

**Analogy:** A private warehouse with its own private road. Only certain businesses (servers) can use it, and they treat it like their own back room.

**Where you'd see it:** Enterprise data centers running big databases or virtual machines.

**Exam tip:** **NAS = file-level** vs. **SAN = block-level**. Also, a NAS is a *device*; a SAN is a whole *network*.

---

## 14. Media

**What it is:** The **physical path** data travels over.

- **Copper:** Ethernet (twisted pair), coax
- **Fiber optic:** light through glass; faster and longer distance
- **Wireless:** radio waves

Each has trade-offs in speed, distance, cost and interference.

**Analogy:** The roads themselves: dirt roads, paved streets and highways all get you there differently.

**Exam tip:** Media = **Layer 1** (physical). Expect detailed cable questions later in the course.

---

## 15. WAN Links

**What it is:** Connections that link networks over **large distances**: between cities, states or countries.

- Technologies: **leased lines**, **satellite**, **cellular**, and more

**Analogy:** Interstate highways and flight routes connecting cities across the country.

**Where you'd see it:** A company with offices in Wilmington and Philadelphia connecting both sites, or your phone's cellular data.

**Exam tip:** WAN = **large geographic area**. Watch for keywords like "connect branch offices" or "between cities."

---

## What CompTIA is likely to test

- **Hub vs. switch vs. router**: what each forwards and based on what
- **IDS vs. IPS**: detect vs. prevent
- **NAS vs. SAN**: file vs. block
- **Firewall = ACLs/rules**
- **Load balancer = spreads traffic across servers**
- **Proxy = intermediary**, caching, filtering, hiding IPs
- **Scenario questions**: "A company needs X. Which device?"

## Common traps

- ❌ **Picking hub** when the question describes sending traffic only to the right port. That's a switch.
- ❌ **Calling a WAP a router.** It connects wireless to wired; it doesn't route between networks.
- ❌ **IDS blocking traffic.** It only alerts. Blocking = IPS.
- ❌ **NAS vs. SAN swap.** NAS shares *files*; SAN provides *blocks* that look like local disks.
- ❌ **Load balancer vs. proxy.** Load balancer spreads load across servers. Proxy stands in for someone. (A reverse proxy *can* load balance, which is why they get mixed up.)
- ❌ **Firewall vs. IPS.** Firewall enforces rules you wrote. IPS looks for *attacks and anomalies*.

## Quick device cheat table

| Device | Layer | Forwards based on |
|---|---|---|
| Hub | 1 | Nothing (repeats to all ports) |
| Switch | 2 | MAC address |
| Wireless AP | 2 | MAC address (over radio) |
| Router | 3 | IP address |
| Firewall | 3–7 | Rules / ACLs |

---

## Key Terms

### Client
- **Term:** Any device a user uses to access the network
- **Analogy:** A resident using the city's services
- **Example:** Laptop browser, phone app, smart TV
- **Exam tip:** Client *requests*; server *provides*

### Server
- **Term:** A device or software that provides resources to others
- **Analogy:** A business serving customers
- **Example:** Web, email, file and database servers; your `npm run dev`
- **Exam tip:** A role, not a box. Software can make any machine a server.

### Hub
- **Term:** Legacy device that repeats incoming data out every port
- **Analogy:** A town crier shouting every message to everyone
- **Example:** Rarely seen today; mostly in old networks
- **Exam tip:** **Layer 1**. Usually a wrong answer. Evolved: hub → bridge → switch.

### Bridge
- **Term:** Early device that connected network segments and learned addresses; the step between hub and switch
- **Analogy:** A gatekeeper between two neighborhoods who learns who lives on which side
- **Example:** Mostly replaced by switches
- **Exam tip:** **Layer 2**, like a switch but with very few ports

### Switch
- **Term:** Connects devices on a LAN and forwards traffic only to the correct port
- **Analogy:** A mail carrier who knows every house
- **Example:** Office closet switch; LAN ports on a home router
- **Exam tip:** **Layer 2**, uses **MAC addresses** and a MAC address table

### MAC Address
- **Term:** A unique hardware ID assigned to a network card
- **Analogy:** A device's serial number, or name tag
- **Example:** `3C:22:FB:9A:10:4E` in your Wi-Fi settings
- **Exam tip:** Switches use MAC addresses; routers use IP addresses

### Wireless Access Point (WAP / AP)
- **Term:** Lets wireless devices join a wired network using radio waves
- **Analogy:** A radio tower for people with no road connection
- **Example:** Ceiling-mounted Wi-Fi units in offices
- **Exam tip:** Bridges wireless to wired. **Not** a router.

### Router
- **Term:** Connects different networks and forwards traffic by IP address
- **Analogy:** A highway interchange picking the road to the right city
- **Example:** Home router sending your traffic to the internet
- **Exam tip:** **Layer 3**, **IP addresses**. Between networks, not within.

### Firewall
- **Term:** Security device or software that allows or blocks traffic based on rules
- **Analogy:** A border checkpoint with an approved list
- **Example:** Windows Defender Firewall; AWS security groups
- **Exam tip:** Uses **ACLs**. Can be hardware, software or both.

### ACL (Access Control List)
- **Term:** An ordered list of rules saying what traffic is allowed or denied
- **Analogy:** A bouncer's guest list
- **Example:** "Allow TCP 443 from anywhere; deny everything else"
- **Exam tip:** Firewalls and routers use ACLs to filter traffic

### Load Balancer
- **Term:** Distributes traffic across multiple servers
- **Analogy:** A restaurant host spreading guests across waiters
- **Example:** AWS Elastic Load Balancing, NGINX in front of 3 app instances
- **Exam tip:** Keywords: distribute, prevent bottleneck, high availability

### Proxy Server
- **Term:** An intermediary between a user and the internet
- **Analogy:** A personal assistant making calls for you
- **Example:** A school web filter; a dev server proxying `/api`
- **Exam tip:** Caching, filtering, hides the user's IP. Forward = clients; reverse = servers.

### IDS (Intrusion Detection System)
- **Term:** Monitors for suspicious activity and alerts admins
- **Analogy:** A security camera with an alarm
- **Example:** Snort set to alert mode
- **Exam tip:** **Detects and alerts only**. Passive. Doesn't block.

### IPS (Intrusion Prevention System)
- **Term:** Detects threats and actively blocks them
- **Analogy:** A security guard who stops the intruder
- **Example:** A next-gen firewall dropping malicious packets
- **Exam tip:** **Detects and prevents**. Sits **inline**.

### Controller
- **Term:** Central unit that manages the behavior of other network devices
- **Analogy:** A traffic control center running every light from one room
- **Example:** A wireless LAN controller managing 50 APs; an SDN controller
- **Exam tip:** Controller = centralized management

### SDN (Software-Defined Networking)
- **Term:** Managing network behavior through software from a central controller
- **Analogy:** Updating every traffic light from one dashboard instead of rewiring each one
- **Example:** Cloud and data center networks
- **Exam tip:** Separates the "brains" (controller) from the devices moving traffic

### NAS (Network-Attached Storage)
- **Term:** A dedicated storage device that shares files over the network
- **Analogy:** A public library where people check out books
- **Example:** A Synology box; a shared office drive
- **Exam tip:** **File-level** storage. A single device.

### SAN (Storage Area Network)
- **Term:** A dedicated high-speed network giving servers block-level storage
- **Analogy:** A private warehouse with its own private road
- **Example:** Enterprise storage for databases and VMs
- **Exam tip:** **Block-level**. A whole network. Fibre Channel or iSCSI.

### Media
- **Term:** The physical path data travels over: copper, fiber or wireless
- **Analogy:** The roads themselves
- **Example:** Ethernet cable, fiber run, Wi-Fi signal
- **Exam tip:** **Layer 1**. Each type has speed, distance and interference trade-offs.

### WAN Link
- **Term:** A connection between networks over large distances
- **Analogy:** Interstate highways between cities
- **Example:** Connecting two branch offices; cellular data
- **Exam tip:** Leased lines, satellite, cellular. Keyword: geographic distance.