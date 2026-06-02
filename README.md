# 🚀 Project AirBase-Charger: Repurposing Obsolete 65W E-Waste into a High-Efficiency DIY Desk Charger

### 👉 [**View Full Step-by-Step Video Guide on YouTube**] ## Project Overview

Project AirBase-Charger is a hardware-only (no-code) engineering effort to repurpose an obsolete, functional 65W HP laptop power adapter into a modern, safe, and highly efficient 25W+ smart-device charging station. 

The goal was to bypass the current wave of "fake" high-wattage market chargers, save a high-quality salvaged component from a landfill, and document the rigorous, analytical troubleshooting required to make standard fixed-voltage laptop bricks work with proprietary, fine-tuned smartphone fast-charging protocols.

## Component Breakdown & Architecture

The system consists of two primary power stages and a certified connection layer.

### 1. Prime Mover: Salvaged HP 65W Power Brick
* **Source:** Salvaged from a non-functional laptop.
* **Original Output:** Fixed 19.5V DC at 3.33A.
* **Condition:** Checked for stable, noise-free output using a multimeter.

### 2. Smart Stage: HW-773 Buck Converter Module (V0.0.0)
* **Controller:** ASIC-based (IP6525T or similar).
* **Input:** Wide-voltage DC (up to 30V). Safe and efficient at 19.5V.
* **Output:** Hardwired Power Delivery (PD) & Quick Charge (QC) profiles up to 30W+.
* **Thermal Management:** Inductor ("MAGIC 220") and IC generate high heat. Hardwired in an un-sealed enclosure for natural convection.

### 3. Connection Layer: Nu Republic 100W/5A Display Cable
* **Data Channel:** Certified 5A E-Marker chip embedded in the Type-C housing.
* **Function:** Communicates power delivery capabilities to the phone and calculates real-time output wastage for visual verification.

---

## Engineering Challenges & Troubleshooting Log

This section documents the analytical problem-solving required to move the project from prototype to reliable utility.

### Challenge 1: Isolate the "Super Fast Charging 2.0" Throttling Issue

A persistent protocol mismatch on Samsung devices was observed: standard fixed 20V laptop-charging streams would scale, but the highly picky Samsung "Super Fast Charging 2.0" (45W) handshake, which relies on **PPS (Programmable Power Supply)** and high **current (up to 4.5A)**, failed to trigger.

* **Hypothesis A: Frayed Salvaged Wire Resistance.**
* **Hypothesis B: Insufficient Cable E-Marker Chip registers.**
* **Hypothesis C: Power Source Current Ceiling.**

#### Diagnostics: Variable Isolation

I designed an analytical diagnostic to isolate the true culprit: I temporarily desoldered the module from the HP brick (65W, 3.3A limit) and connected it to a massive **170W Lenovo Legion brick** (20V, 8.5A limit).

The 8.5A reservoir removed all input power restrictions.

#### Diagnosis: ASIC Firmware Limitation

Even with 170W of available input power and a certified 5A cable, the phone still only displayed the standard "Super Fast Charging" flag at a consistent, stable 32W at the input side. 

This **flawless diagnostic isolated the true bottleneck**: the issue was not the power source, the leads, or the cable. The HW-773's hardwired ASIC controller lacked the proprietary vendor tokens in its firmware registers to complete the 4.05A PPS handshake required for Samsung's 2.0 designation.

#### Conclusion for the HP Build

The existing hardware configuration was working beautifully and hitting the absolute native physical saturation of the phone's standard fast-charging tier. For zero cash investment, saving 25 minutes on every full cycle is a definitive engineering win.

---

## Mechanical Assembly & Ruggedization

Getting rid of a traditional "box as a chassis" design and using the heavy HP brick as the rigid mechanical foundation solved structural wiggling problems completely.

### 1. The Friction Lock: 3-Zip-Tie Mechanical Anchoring

Since drilling into the dense, high-voltage internal components of the HP brick case is dangerous, I designed a non-destructive mechanical friction lock using three parallel zip-ties. This rugged connection slots into the HW-773's castellated mounting tabs, preventing any back-and-forth movement from cable tugs.

### 2. Thermal & Electrical Insulation: 4-Corner Pad Air-Gap

The "MAGIC 220" inductor and IC reach temperatures of $60^\circ\text{C}$ to $80^\circ\text{C}$ ($140^\circ\text{F}$ to $176^\circ\text{F}$) under a 3A load. Placing foam tape directly under these components traps heat, potentially causing thermal throttling or melting adhesive.

I engineered a solution using four tiny tape pads at the outer edges only. This creates a tiny, elevated **air gap directly underneath the hot components**, allowing for natural air convection and preventing heat buildup.

### 3. Ventilated Box Shield

The custom ventilated small plastic box enclosure turns into a simple, hassle-free dust and finger shield. It provides crucial physical damage protection while natural convection gaps around the edges serve as exhaust vents for thermal management.

## Project BOM (Bill of Materials)

| Component | Source/Type | Purpose in Circuit | Estimated Cost |
| :--- | :--- | :--- | :--- |
| **HP 65W Power Brick** | Salvaged | Prime DC Power Source (Fixed 19.5V, 3.33A) | ₹0 (E-Waste Recycle) |
| **HW-773 Buck Converter Module** | IP6525T Controller | DC-DC Step-Down (Smart Power Negotiator) | ~₹300 |
| **Nu Republic Blaze Fusion Spot** | Certified 5A E-Marker | certified Data Channel & Visual Wattage Verification | ~₹300 |
| **Nylon Zip Ties** | Household | Non-destructive Mechanical Anchoring Solution | ~₹10 |
| **Foam Pads** | DIY Supply | Corner-Pads (Thermal Air Gap creation) | ~₹10 |
| **Plastic Dust Shield Box** | Household | Dust & Physical Protection Enclosure | ~₹20 |
| **MATTE BLACK Electrical Tape** | DIY Supply | Aesthetic Side Anchors (factory-finish look) | ~₹20 |
| | | | |
| **TOTAL** | | | **₹660 (Highly Optimized DIY Build)** |

*Compared to a branded 65W GaN retail charger (₹1,500-₹2,500), this build saves significantly on e-waste while providing heavy-duty performance.*

### 👉 [**View Full Assembly Video on YouTube**] ```

---


#DIY electronics #Upcycle #Ewaste #HW-773 #PowerDelivery #QuickCharge #SamsungFastCharging #IoT #IoT Engineering
