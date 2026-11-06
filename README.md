# 🌐 Computer Networks And Network Programming

![Course Code](https://img.shields.io/badge/Course-25CS2208E-blue?style=flat-square)
![Credits](https://img.shields.io/badge/Credits-3-brightgreen?style=flat-square)
![Trimester](https://img.shields.io/badge/Trimester-T05-orange?style=flat-square)
![Category](https://img.shields.io/badge/Category-Project--Based_Learning-purple?style=flat-square)

> **Welcome to the official repository for the Computer Networks And Network Programming course.**  
> This repository contains projects, implementations, and coursework guided by the official syllabus detailed in the `"Computer Networks And Network Programming"` specification.

---

## 📋 Course Overview

| Attribute | Details |
| :--- | :--- |
| 🏫 **Institution** | KLEF, Y25 B.Tech |
| 📅 **Trimester** | T05 |
| 🎯 **Category** | Project-Based Learning (PCC) |
| ⏱️ **Structure** | 2-0-0-4 (8 Contact Hrs/Week) |
| 🔑 **Pre-requisite**| DMS (25CS2208E) |

A twelve-week curriculum featuring three interlocking builds to design and operate a campus internetwork, implement a protocol stack, and engineer a network for traffic with a strict deadline.

---

## 🏗️ The SETU Programme

Everything built over the twelve weeks is judged against the SETU programme specification. The repository is structured into three main infrastructure projects:

### 📂 Repository Structure

```bash
setu/
├── link/               # 🔌 P1: The Infrastructure (Weeks 1-3, 8-11)
│   ├── topology/       # containerlab / netns definitions
│   ├── ansible/        # inventory, roles, playbooks
│   ├── design/         # ADDRESS-PLAN.md, TOPOLOGY.md, POLICY.md
│   ├── verify/         # reachability matrix, convergence timer
│   └── diagnostics/    # one log per Fault Bank case
│
├── stack/              # ⚙️ P2: The Implementation (Weeks 4-7)
│   ├── src/            # byte_stream.c, reassembler.c, receiver.c, sender.c
│   ├── tests/          # testing harnesses for kernel-interop
│   └── measure/        # throughput vs. loss, predicted vs. observed
│
├── edge/               # 🚀 P3: Traffic With a Deadline (Week 12)
│   ├── topology/       # edge topology configs
│   ├── qos/            # Quality of Service configurations
│   ├── measure/        # measurement logic for time-sensitive traffic
│   └── BUDGET.md       # the latency budget, term by term
│
└── JOURNEY.md          # 📓 Weekly design decision logs (What, Why, Cost)
```

> **Note on `JOURNEY.md`:** This is a critical log containing one design decision entry per week. Each entry must document *what* decision was made, *why* it was made, alternatives rejected, and the accepted cost.

---

## 🧠 Advanced Modules Highlights

* **📡 Module 4: Below the IP Address**  
  Covers Ethernet, switching, media, wireless, and constrained links. Key concepts include the frame and FCS guarantees, MAC learning, VLANs, spanning tree, and link aggregation. Explores RF link budgets, CSMA/CA, hidden nodes, Wi-Fi 6 & 7 updates, and the capacity problems of constrained links.

* **🛠️ Module 5: Running What You Built**  
  Focuses on operations, security, and automation. Apply a formal troubleshooting methodology to diagnose Fault Bank faults and utilize observability tools. Security topics include ACLs, stateful firewalls, zero trust at the edge, and VPN MTU costs. Automation is handled via idempotent Ansible and Python scripts against reachable devices.

* **⏱️ Module 6: Predictability**  
  Explores real-time networking, multicast, and Quality of Service (QoS). Topics include jitter, playout buffers, queue disciplines, DiffServ, policing versus shaping, and PTP clock synchronization. Defend a strict latency budget under contention, ensuring metrics like `$p50 \le 8$` ms and `$p99 \le 20$` ms end-to-end delay are met.

---

## 🏅 Certification Tracks

Course assessments are tagged with objectives and domains for named industry exams (such as **CompTIA Network+** and **CCNA**), allowing targeted revision by domain. 

While the syllabus teaches mechanisms vendor-neutrally, exams like the CCNA test configuration and verification in Cisco IOS syntax. Students are encouraged to work through Cisco configuration guides to translate these concepts before testing.

---

## 📚 Reference Literature

* 📘 **Computer Networking: A Top-Down Approach** (8th Ed.) — *James F. Kurose & Keith W. Ross*
* 📙 **TCP/IP Illustrated, Volume 1: The Protocols** (2nd Ed.) — *Kevin R. Fall & W. Richard Stevens*
* 📗 **Unix Network Programming, Volume 1: The Sockets Networking API** (3rd Ed.) — *W. Richard Stevens, Bill Fenner & Andrew M. Rudoff*
* 📕 **Computer Networks: A Systems Approach** (6th Ed.) — *Larry L. Peterson & Bruce S. Davie*
* 📓 **High Performance Browser Networking** — *Ilya Grigorik*
* 🐧 **The Linux Programming Interface** — *Michael Kerrisk*
* 📖 **CompTIA Network+ Study Guide: Exam N10-009** (6th Ed.) — *Todd Lammle & Jon Buhagiar*
* 🛡️ **CCNA 200-301 Official Cert Guide Library** (2nd Ed.) — *Wendell Odom*

---
*Built for the Y25 Computer Science and Information Technology cohort.*
