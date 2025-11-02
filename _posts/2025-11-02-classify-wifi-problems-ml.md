---
layout: post
title: "How to Classify WiFi Problems with Machine Learning"
subtitle: "A practical summary of our IEEE CCNC 2019 research on diagnosing WiFi pathologies"
cover-img: /assets/img/wireless_pathologies.png
thumbnail-img: /assets/img/wireless_pathologies.png
share-img: /assets/img/wireless_pathologies.png
tags: [machine learning, research, wifi, networks, ai]
comments: true
---

WiFi problems are among the most frustrating issues users face — slow speeds, dropped connections, or mysterious lag that no restart seems to fix.  
But what if your router could **automatically diagnose what’s wrong**, without needing a network expert?

That’s exactly what our research set out to achieve in the paper  
[*On the Employment of Machine Learning Techniques for Troubleshooting WiFi Networks*](https://www.researchgate.net/publication/331417572),  
presented at **IEEE CCNC 2019**.

---

## 🧩 The Problem

As WiFi networks grow denser — with laptops, IoT devices, smart TVs, and microwaves all sharing the same spectrum — diagnosing poor performance becomes extremely complex.

Even experts struggle to pinpoint whether the issue comes from:
- **Contention** (too many WiFi devices competing for the same channel),
- **Low signal-to-noise ratio (SNR)**,
- **Non-WiFi interference** (like Bluetooth or microwave ovens),
- **Hidden terminal** problems, or
- **Capture effect** (when one signal overpowers another).

Traditional troubleshooting requires specialized equipment and deep knowledge of the 802.11 protocol — something the average user doesn’t have.

---

## 💡 Our Approach

We designed a **machine learning framework** that allows any **low-cost WiFi access point (AP)** to become “intelligent.”  
By analyzing data already available from the AP’s network drivers (like transmission success rates and channel access frequency), the system can automatically **classify the root cause** of a connection issue.

Two detection modes were developed:

1. **Passive Mode** – Gathers performance metrics without sending any extra network traffic.  
   → Low overhead, ideal for everyday monitoring.

2. **Active Mode** – Uses controlled test packets (probing) to collect richer data.  
   → Slightly more overhead, but achieves higher accuracy.

---

## 🧠 The Machine Learning Models

We evaluated four popular classification algorithms:

- **Decision Trees**
- **Random Forests**
- **Support Vector Machines (SVM)**
- **K-Nearest Neighbors (KNN)**

Each algorithm was trained and fine-tuned on a **dataset of over 5,000 labeled samples**, representing real-world WiFi problems reproduced in a controlled testbed.

The features used were two simple but powerful metrics:

- **Normalized Channel Access (NCA):** How often a device gets to transmit.  
- **Frame Delivery Ratio (FDR):** The ratio of successful transmissions.

By combining these with information about the **modulation scheme (MCS)** used, the models learned to differentiate between all five WiFi pathologies.

---

## 📊 Results

After fine-tuning and cross-validation, the results were remarkable:

| Algorithm | Active Accuracy | Passive Accuracy |
|------------|----------------|------------------|
| Decision Tree | 97.8% | 92.8% |
| Random Forest | 98.1% | 94.6% |
| SVM | 98.7% | 94.1% |
| **K-Nearest Neighbors (KNN)** | **99.2%** | **95.1%** |

The **KNN model** achieved near-perfect classification accuracy — **99% for active probing** and **95% for passive detection** — with minimal computational requirements.

---

## ⚙️ Why It Matters

This work demonstrates that:
- **Machine learning can make WiFi networks self-diagnosing.**
- **Commodity routers** can be transformed into **intelligent monitoring tools**.
- The approach is **affordable, deployable, and scalable** for both home and enterprise networks.

Future extensions include **multi-label detection**, allowing the system to recognize multiple overlapping issues simultaneously — a step toward fully **autonomous WiFi troubleshooting**.

---

## 🔬 Reference

**Ilias Syrigos**, **Nikos Sakellariou**, **Stratos Keranidis**, and **Thanasis Korakis**,  
*"On the Employment of Machine Learning Techniques for Troubleshooting WiFi Networks,"*  
IEEE CCNC, 2019.  
[Read the full paper on ResearchGate](https://www.researchgate.net/publication/331417572_On_the_Employment_of_Machine_Learning_Techniques_for_Troubleshooting_WiFi_Networks)

---

{: .box-note}
**Summary:**  
Our model allows routers to detect and explain WiFi performance issues automatically using simple ML models — without expensive hardware or expert intervention.  
It’s a practical example of how AI can improve everyday connectivity.
