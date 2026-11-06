# 🌐 Computer Networks And Network Programming

> **Course**: 25CS2208E | **Credits**: 3 | **L-T-P-S**: 2-0-0-4 | **Contact Hrs/Wk**: 8
> **Trimester**: T05 | **Mode**: PBL (Project-Based) | **Category**: PCC
> **Pre-requisite**: DMS

---

## 🎯 Course Outcomes (COs)

* **CO1**: Analyze a network as a measured system - layering and encapsulation, header overhead, MTU, the delay equation, throughput as the min-cut, the queueing-delay curve and its knee, Little's Law, bandwidth-delay product, jitter and percentiles - and account for every microsecond of a transfer with numbers defended from captures rather than described (BTL4 Analyze).
* **CO2**: Implement the transport and application layers from scratch in C-sockets, framing, an HTTP/1.1 server and a DNS resolver; blocking, select, poll and epoll with backpressure at ten thousand connections; a reassembler, receiver and sender with a derived retransmission timer and fast retransmit; slow start, AIMD and fast recovery checked against the Mathis relation; TLS termination and prove interoperability by a bidirectional 1 MB transfer against an unmodified Linux kernel TCP peer over an impaired link (BTL6 Create).
* **CO3**: Apply prefix arithmetic, VLSM, summarisation, IPv6 addressing and DHCP relay, longest-prefix match, ARP, distance-vector and link-state routing, the OSPF convergence budget, route selection, NAT, first-hop redundancy, BGP and overlays to design and bring up a campus internetwork as code with a dual uplink, no black-holing on failover, and convergence after a link failure inside a stated budget (BTL3 Apply).
* **CO4**: Analyze the link and physical layers - the frame and what the FCS guarantees, CRC over GF(2), MAC learning, VLANs and trunks, spanning tree and the loop with no brake, link aggregation and its hashing problem, media budgets, Shannon and Nyquist; the RF link budget, CSMA/CA and the hidden node, SNR to data rate, airtime as the real resource, roaming, and constrained low-power links and diagnose faults that produce no error message (BTL4 Analyze).
* **CO5**: Evaluate and operate what was built - the formalised troubleshooting methodology (problem statement, falsifiable hypothesis and test, elimination, evidence, one-change fix, verification), observability and availability arithmetic, ACLs and stateful firewalls where order is policy, identity at the edge and zero trust, VPN MTU cost, token-bucket rate limiting, and idempotent Ansible automation - root-causing Fault Bank faults within a time limit with a complete hypothesis-test-evidence fix-verify log (BTL5 Evaluate).
* **CO6**: Engineer and defend a latency and jitter budget for time-sensitive traffic - jitter and the playout buffer, queue disciplines and what each actually bounds, DiffServ marking, policing and shaping, media bandwidth and the E-model, multicast and group management, and PTP clock synchronisation - measured as p50/p99 distributions under sustained contention against stated targets, with every term on the path named, measured and totalled (BTL6 Create).

---

## 📊 CO-PO/PSO Articulation Matrix

| CO | PO1 | PO2 | PO3 | PO4 | PO5 | PO8 | PO10 | PO11 | PSO1 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **CO1** | H | H | | H | M | | | | H |
| **CO2** | H | H | H | M | H | | | | H |
| **CO3** | H | H | H | | M | | | | H |
| **CO4** | H | H | M | H | | | | | H |
| **CO5** | H | H | | H | H | M | M | | H |
| **CO6** | H | H | H | H | | | M | M | H |

*(H=High (3), M=Moderate (2), L=Low (1), blank = no significant correlation)*

---

## 📚 Module-wise Syllabus

### M1: The Network as a Measured System - layering, delay, queueing and measurement (Weeks 01-02)
* **Topics**: Start with the system working; why layering exists at all; two models (OSI and TCP/IP) and why both survive; encapsulation - what actually gets added at each layer. Header overhead is a number, not a nuisance; MTU as the constraint that propagates upward; where the time goes - the delay equation (serialisation, propagation, queueing, processing). Throughput is the min-cut, not the average; the capture is the instrument - three-point captures and reading a path from three probes. Utilisation as the master variable; deriving the queueing-delay curve and finding the knee; Little's Law and why it is more general than it looks; where M/M/1 lies to you and by how much. Bandwidth-delay product - how much must be in flight; jitter, percentiles, and why the mean lies; impairment, baseline, and the number that lies. What this course owns and what it does not; the bridge to CDIS and SDSR. Loss, buffers, and the trap of adding memory; measurement methodology.
* **Scenarios**: the transfer that stopped at 1.2 MB; the dashboard that was green all night.
* **SETU**: topology skeleton up; baseline measured; EDGE budget v0 stated; STACK CP0 (webget over a kernel socket, a flow-controlled ByteStream).

### M2: Being the Stack - sockets, HTTP, DNS, concurrency, TCP mechanics, congestion control and TLS (Weeks 04-07)
* **Topics**: Sockets are syscalls; listen() and the queue nobody knows is there; the six things that break networked code; framing - the problem underneath every application protocol; HTTP/1.1 implemented; round trips are the currency; DNS at diagnose level and as a load-balancing control plane; diagnosing DNS in seven tests. What ten thousand connections actually costs; four models - a thread per connection, select(), poll(), epoll (and kqueue); level- versus edge-triggered; the event loop and why everything must be non-blocking; backpressure - the part that gets omitted; more than one core; timeouts at scale. UDP, the transport that promises nothing; what TCP promises and the machine that delivers it; sequence numbers and the 32 bits that wrap; the reassembler; flow control - the window is the capacity; reliability - knowing what to resend and when; the retransmission timer derived (Jacobson/Karels); teardown and TIME_WAIT; Nagle meets delayed ACK. October 1986 and why congestion control exists; two windows, one sender; slow start; AIMD and why it is the only one that works; fast recovery versus fast retransmit; the Mathis relation - predict first, then measure, then explain the gap; fairness and the sense in which it is false; buffer sizing revisited; TLS-chain validation and ALPN. DNS in depth - the dependency every other service has and nobody diagrams. Cubic, BBR, and ECN - three answers to "what signal?"; TLS 1.3.
* **Checkpoints**: CP1-CP5 and the Interop Gate: a bidirectional 1 MB transfer against an unmodified Linux kernel TCP peer over a link carrying injected delay and loss.
* **Scenarios**: the failover that took a day; the service that was fine until it wasn't; the transfer that ran at exactly 13 Mbit/s; the upgrade that made it slower.

### M3: Addressing, Routing and Internetworking - deciding where everything lives and what decides the path (Weeks 03, 08)
* **Topics**: The address and the mistake that shaped the internet; prefix arithmetic to fluency; VLSM as a design activity; summarisation - turning many routes into one; the addresses that are not ordinary; IPv6 as a working addressing scheme. DHCP end to end, and DHCPv4 in depth; "it has no address" - the diagnostic order; the first injected fault: a client with no address. Two planes, and why the split is the whole design; longest-prefix match; ARP and the layer boundary it straddles; two algorithms, one graph - distance-vector and link-state; count-to-infinity and the three mitigations. OSPF and the convergence budget; route selection, in order; NAT and the problem it created; first-hop redundancy; BGP is not a shortest-path protocol; overlays and the MTU they cost. The same addressing problem, in a cloud VPC; NAT-the translation that broke the end-to-end model and kept the internet running.
* **SETU-LINK**: the address plan against a +60% growth forecast, DHCP relayed not per-segment, DNS zones, OSPF converging in under 5 s, the second uplink from week 8 with no black-holing; STACK CP6-NetworkInterface (ARP) and a longest-prefix-match router forwarding between three of your own subnets.
* **Scenarios**: the merger that could not be routed; the summary that was never advertised.

### M4: Below the IP Address - Ethernet, switching, media, wireless and constrained links (Weeks 09-10)
* **Topics**: The frame and what the FCS guarantees; CRC over GF(2) as polynomial division; MAC learning; VLANs and trunks; why a layer-2 loop is catastrophic; spanning tree; link aggregation and the hashing problem. Media and two budgets; Shannon and Nyquist - the ceiling on any link; the access port is not one configuration. The RF link budget; why the protocol is CA and not CD; the hidden node; from SNR to a data rate (the MCS ladder); three bands; airtime - the concept that explains everything; roaming and who decides; what Wi-Fi 6 and 7 actually changed; channel planning and airtime fairness. Constrained links: small MTUs, duty cycles, and the capacity problem that looks like a coverage problem. The switch inside the server.
* **SETU-LINK**: VLANs, trunks, STP and LACP; the wireless segment; STACK CP7 - the frame layer with CRC-32 byte-identical to a reference across a corpus including burst errors; EDGE: constrained links. 
* **Fault Bank**: four faults that produce no error message.
* **Scenarios**: the building that went down at 09:14; the lecture theatre that failed at capacity.

### M5: Running What You Built - operations, security and automation (Week 11)
* **Topics**: The troubleshooting methodology, formalised: problem statement, falsifiable hypothesis and test, elimination, evidence, a one-change fix with blast radius and reversal stated, verification from the user's viewpoint. Observability and what each mechanism can see; measuring the right things- cardinality and flow sampling; availability arithmetic and the availability chain. Filtering: ACLs and stateful firewalls - order is policy; identity at the edge and zero trust; VPNs and their MTU cost; rate limiting with the token bucket, and what it is for. Automation and the property that makes it safe: idempotency; Ansible and Python against reachable devices. Ansible - infrastructure as code, at the level you are expected to operate it; the five management approaches, and honestly assessing which you are using; AI in network operations - the two things you are expected to know; documentation - five artefacts, five different questions. 
* **SETU-LINK**: monitored, automated, hardened - the Diagnosis Gate (Fault Bank faults root-caused within the time limit); STACK CP8 - TLS termination, chain validation, ALPN, with expired and wrong-name certificates rejected for the right reason.
* **Scenario**: the change that was never made.

### M6: Predictability - real-time, multicast and QoS (Week 12)
* **Topics**: Jitter; the playout buffer sized on a tail, not a mean; queue disciplines and what each actually bounds; DiffServ, policing versus shaping. Media bandwidth - the codec rate is not the wire rate; the E-model - delay and loss become a number; where the delay budget actually goes. Multicast and group management; PTP, and the error you cannot measure away. 
* **SETU-EDGE**: the requirement to meet or refute - end-to-end delay $p50 \le 8$ ms, $p99 \le 20$ ms; jitter $p99 - p50 \le 12$ ms; loss $\le 0.1\%$ over any 60 s window, all holding while a 200 Mbit/s bulk transfer runs across the same link; every term on the path named, measured and totalled. 
* **The Integration Gate**: edge traffic crosses your fabric, through your router, into your transport; a fault is injected live and diagnosed; the latency budget is defended against the measured p99 under contention.
* **Scenario**: the QoS that was configured everywhere and worked nowhere.

---

## 🛠️ Network Studio (Project-Based Learning)

Twelve weeks, three interlocking builds, one campus. You will design and operate a real internetwork, implement the protocol stack that runs on it, and engineer the network that carries traffic with a deadline - then measure all three and defend the numbers.

### The Twelve Weeks
* **W01**: The network as a measured system
* **W02**: Performance, queueing and measurement
* **W03**: Addressing, subnetting and DHCP
* **W04**: Sockets, HTTP and DNS
* **W05**: Concurrency, epoll and the C10K wall
* **W06**: UDP, TCP mechanics and reliability
* **W07**: Congestion control, fairness and TLS
* **W08**: Routing, forwarding, NAT and IPv6
* **W09**: Ethernet, switching and media
* **W10**: Wireless, RF and channel access
* **W11**: Operations, security and automation
* **W12**: Real-time, multicast and constrained

### Depth Modules
* CCNA domain clinic
* Command appendix
* Packet capture
* Subnetting drill
* Timed mock exam
* Simulators & topologies
* Lab setup & portfolio
* Study plan
* Glossary
* Security concepts
* Network programming in Python

### Repository Structure

```text
setu/
├─ link/            # P1 — the infrastructure
│  ├─ topology/       # containerlab / netns definitions
│  ├─ ansible/        # inventory, roles, playbooks
│  ├─ design/         # ADDRESS-PLAN.md, TOPOLOGY.md, POLICY.md
│  ├─ verify/         # reachability matrix, convergence timer
│  └─ diagnostics/    # one log per Fault Bank case
├─ stack/           # P2 — the implementation
│  ├─ src/            # byte_stream.c reassembler.c receiver.c sender.c ...
│  ├─ tests/          # including the kernel-interop harness
│  └─ measure/        # throughput vs loss, predicted vs observed
├─ edge/            # P3 — the traffic with a deadline
│  ├─ topology/  qos/  measure/
│  └─ BUDGET.md       # the latency budget, term by term
└─ JOURNEY.md       # one decision entry per week: what, why, what it cost
```

> **JOURNEY.md Grading:** Each week you record one design decision, the alternative you rejected, and the cost you accepted. Engineering is choosing under constraint; a repository that shows only the choice and not the constraint has hidden the engineering.

### The Gates
* **Interop (Week 6)**: Passes when your transport completes a bidirectional 1 MB transfer with an unmodified kernel TCP peer over an impaired link.
* **Diagnosis (Week 11)**: Passes when Faults drawn from the Fault Bank are correctly root-caused within the time limit, each with a complete hypothesis→test→evidence→fix→verify log.

> **A Standing Rule for this Studio:** No number on these pages is asserted. Every figure you see is computed by code that is on the page with it, running in your browser as you read. If you change an input and the number does not move, that is a bug and you should report it. You are asked to hold your own project work to the same standard: a throughput figure in your report that you did not measure twice is not a result.

### Certification Tracks
Every week carries two assessment sets aimed at named exams. Each item is tagged with the objective and domain it serves, so you can revise by domain rather than by week when the exam approaches. 
* Includes **Network+ N10-009** (20 items, timed at one minute each as on the real exam) and performance-based items (PBQ) requiring written answers.
* The closing line: "Layering is the reason the internet scaled and the reason debugging it is hard. Both come from the same property, so you don't get to keep one and discard the other." That answer signals you have thought about the model rather than memorised it.

---

## 📖 Reference Books
1. *Computer Networking: A Top-Down Approach* by James F. Kurose & Keith W. Ross (Pearson, 2021, 8th Ed.).
2. *TCP/IP Illustrated, Volume 1: The Protocols* by Kevin R. Fall & W. Richard Stevens (Addison-Wesley, 2011, 2nd Ed.).
3. *Unix Network Programming, Volume 1: The Sockets Networking API* by W. Richard Stevens, Bill Fenner & Andrew M. Rudoff (Addison-Wesley, 2004, 3rd Ed.).
4. *Computer Networks: A Systems Approach* by Larry L. Peterson & Bruce S. Davie (Morgan Kaufmann, 2021, 6th Ed.).
5. *High Performance Browser Networking* by Ilya Grigorik (O'Reilly Media, 2013).
6. *The Linux Programming Interface* by Michael Kerrisk (No Starch Press, 2010).
7. *CompTIA Network+ Study Guide: Exam N10-009* by Todd Lammle & Jon Buhagiar (Sybex/Wiley, 2024, 6th Ed.).
8. *CCNA 200-301 Official Cert Guide Library* by Wendell Odom (Cisco Press, 2024, 2nd Ed.).
