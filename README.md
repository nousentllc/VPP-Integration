# The Two-Layer VPP Architecture: A Unified Energy Valuation Framework (UEVF) Approach

> **A rigorous mathematical framework for integrating Virtual Power Plants (VPPs) into wholesale markets, resolving the conflict between passive price responsiveness and active capacity accreditation.**

---

## 📄 Overview

**Author:** Justin Candler (Nous Enterprises LLC)  
**Date:** January 14, 2026

This technical report formalizes a **"Two-Layer" architecture** for VPP integration. By applying the **Unified Energy Valuation Framework (UEVF)**, this work resolves the "Identity Crisis" of Distributed Energy Resources (DERs)—whether they are economic assets responding to price or reliability assets responding to risk.

The framework introduces a **Locational Marginal Reliability Value (MRV)** procurement rule satisfying the KKT optimality condition ($\hat{MRV}=MC$) and a **Price-Conditioned Counterfactual Baseline** ($B^{cf}$) to eliminate "Phantom DR" (double-counting).

## 🔑 Core Problem: The Valuation Paradox

Current market designs (e.g., FERC Order 2222) often conflate economic efficiency with system reliability. This leads to two critical failures:
1.  **Double Counting:** Resources are compensated via capacity payments for load reductions they would have undertaken voluntarily to avoid high energy prices.
2.  **The Copper Plate Paradox:** Aggregations often ignore transmission topology, under-incentivizing recruitment in high-risk, constrained areas (e.g., behind MISO CIL flowgates).

## 🛠️ The Two-Layer Solution

We propose a bifurcated control architecture:

* **Layer 1 (The Operating Signal):** Real-time dynamic pricing ($\pi_{t}$) drives autonomous, economic load shifting for "Everyday Optimization".
* **Layer 2 (The Reliability Overlay):** A distinct VPP Resource Adequacy (RA) product serves as insurance for "Tail Risk" hours where price signals alone are insufficient.

## 📊 Key Findings & Innovations

### 1. The KKT Procurement Condition
We reject arbitrary "Planning Reserve Margin" targets. Instead, the optimal VPP quantity $Q^{*}$ is defined where the marginal cost of capacity equals its marginal reliability value:
$$\hat{MRV}_{i,z}(Q^{*}) = MC_{z}(Q^{*})$$

### 2. The "Phantom DR" Filter
To ensure baseline integrity, we introduce a **Price-Conditioned Counterfactual Baseline** ($B^{cf}$) trained on non-event days. This isolates active dispatch effects from passive price elasticity.
* **Theorem:** If $\mathbb{E}[B_{t}^{cf} - Y_{t} | \delta_{t}=0] \approx 0$, then capacity payments reward only incremental reliability contributions.

### 3. The Duration Dominance Law
Using chronological probabilistic simulation of a "Winter Tail" event (Dunkelflaute), we demonstrate that **10-hour assets** provide exponentially higher reliability value than standard 4-hour assets.
* **Simulation Result:** A 4-hour battery portfolio depleted by Hour 18 of a winter storm, while a 10-hour portfolio bridged the "Duration Wall," delivering **3.5x higher reliability value**.

## 🔬 Methodology: The UEVF Engine

The analysis utilizes a four-module computational stack:
1.  **Module A:** Chronological Reliability Simulation (calculating Expected Unserved Energy, EUE).
2.  **Module B:** Perturbative MRV Calculation (identifying the marginal value of specific VPP injections).
3.  **Module C:** Dynamic Attribution (calculating counterfactual baselines via Gradient Boosted Regressors).
4.  **Module D:** ASCDE-Constrained Optimization (minimizing Adjusted System-Level Cost of Delivered Electricity).

## 🚀 Implementation Blueprint

To operationalize this architecture, the report outlines a **"Trustless" Settlement Layer**:
* **Unified Telemetry:** IEEE 2030.5 / OpenADR 3.0 via secure WebSocket.
* **Auditability:** Every settlement event is cryptographically hashed ($SHA256$) to create an immutable chain of custody for capacity credits.
* **Entropic Survival:** Capacity accreditation includes a $p_{surv}$ factor to account for participant fatigue and churn.

## 📜 Citation

If you use this framework in your research or deployment, please cite as follows:

```bibtex
@techreport{candler2026uevf,
  title={The Two-Layer VPP Architecture: A Unified Energy Valuation Framework (UEVF) Approach to Dynamic Pricing and Resource Adequacy},
  author={Candler, Justin},
  institution={Nous Enterprises LLC},
  year={2026},
  month={January}
}
