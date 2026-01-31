# station_03_generative_adv_nw
GAN

Ex: Generator generates an image.
Discriminator decides if it is real or fake.
Initially generator is not skilled, but in course of time ,generator can work  even alone.
Discriminator can be said to be an image classifier.
**GAN Architecture**
Say a blank canvas.

* **Success** is achieved when the "Fake" becomes indistinguishable from the "Real."

* # Understanding GANs: Real vs. Fake

## 1. Overview
In a GAN architecture, the learning process is driven by a competitive "Minimax" game between two neural networks: the **Generator** (the forger) and the **Discriminator** (the judge).



[Image of Generative Adversarial Network architecture diagram]


## 2. Core Definitions

| Term | Source | Role in Training |
| :--- | :--- | :--- |
| **Real** | **Training Dataset** | The ground-truth examples (e.g., actual photos) that the AI aims to replicate. |
| **Fake** | **Generator** | Synthetic data created from random noise, designed to deceive the Discriminator. |

---

## 3. The Competition Logic

### The Discriminator (The Judge)
The Discriminator acts as a binary classifier. Its job is to distinguish between the two inputs:
* **Input (Real):** Expected output is **1** (100% confidence it is real).
* **Input (Fake):** Expected output is **0** (00% confidence it is real).

### The Generator (The Forger)
The Generator creates "Fake" images from random noise. It never sees the real images; it only learns through the "rejection" or "acceptance" feedback provided by the Discriminator.

---

## 4. The Objective Function
The training objective is to reach a **Nash Equilibrium**, where the Generator produces data so realistic that the Discriminator can only guess with 50% accuracy. This is mathematically represented by the value function $V(D, G)$:

$$\min_{G} \max_{D} V(D, G) = \mathbb{E}_{x \sim p_{data}(x)} [\log D(x)] + \mathbb{E}_{z \sim p_{z}(z)} [\log(1 - D(G(z)))]$$

> **Note:** As training progresses, the "Fake" data distribution shifts to match the "Real" data distribution ($p_g \approx p_{data}$).

---

## 5. Summary
* **Real data** provides the goalpost.
* **Fake data** is the iteration.
* **Success** is achieved when the "Fake" becomes indistinguishable from the "Real."
