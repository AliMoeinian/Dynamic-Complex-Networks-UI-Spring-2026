## Materials Overview

### Assignment 1: Foundational Graph Theory & Structural Properties
* **Focus:** Mathematical formulation of network topologies, connectivity constraints, and structural boundaries.
* **Theoretical Concepts:** Network robustness, Single Point of Failure (SPOF) vulnerabilities, Eulerian paths/conditions, Hamiltonian trajectories, Average Degree, Degree Distribution $P(k)$, Network Diameter, Clustering Coefficients, and K-Core decomposition frameworks.
* **Analytical Problems:** Structural comparison of power grid connectivity safety, deep exploration of Metcalf's Law (including its formulation pitfalls over sparse vs. fully-connected and unweighted systems), bipartite network limits, and advanced mathematical proofs regarding Centrality metrics (Degree vs. Betweenness Centrality).

### Assignment 2: Stochastic Graph Modeling & Random Networks
* **Focus:** Mathematical evaluation of the Erdős-Rényi (ER) random network paradigm.
* **Theoretical Concepts:** Formal definitions and perspectives behind $G(N, p)$ and $G(N, M)$ models. Analysis of why empirical real-world systems drastically diverge from Poisson degree distributions.
* **Phase Transitions:** Step-by-step examination of random network evolution across the four structural regimes:
  * *Subcritical Regime:* Isolated components and absence of a Giant Component.
  * *Critical Point:* Emergence of structural thresholds.
  * *Supercritical Regime:* Growth of a dominant cluster alongside sparse, isolated components.
  * *Connected Regime:* Global network unification.
* **Analytical Scenarios:** Investigating the "Small-World Property" using topological distance scaling ($\langle d \rangle \sim \ln N$), tracking clustering coefficient independence over system scales, and evaluating isolated node probabilities within strict network boundaries.

### Lab 1: Algorithmic Network Manipulation via NetworkX
* **Focus:** Graph data structures, programmatic mutations, and structural profiling using Python.
* **Programmatic Scope:** Full pipeline setup utilizing the `NetworkX` library, managing environment dependencies via regional mirror infrastructures, programmatic abstraction of directed/undirected/multi-graphs, dynamic vertex/edge ingestion, and state deletion operations.
* **Empirical Task:** Generating a synthetic Erdős-Rényi network wrapper ($N=100, P=0.05$), extracting localized degree sorted metrics, mapping structural connectivity configurations, and rendering property histograms to mathematically classify the system as sparse or dense.

### Assignment & Lab 3: Scale-Free Networks, Power-Laws & Targeted Degradation
* **Focus:** Non-uniform topologies, heavy-tailed distributions, and structural vulnerability mapping.
* **Core Concepts:** Power-Law dynamics ($P(k) \sim k^{-\gamma}$), the mathematical threshold of a catastrophic "Hub", and calculating maximum hub size boundaries ($k_{max} = k_{min} N^{\frac{1}{\gamma-1}}$).
* **Network Generation:** Programmatic assembly of scale-free models compared directly against uniform random baselines using the Configuration Model, Degree Preserving Randomization, and Hidden Parameter frameworks.
* **Robustness & Failure Simulation:** Programmatic execution of automated attack simulations to gauge system survival:
  * *Scenario A (Random Error):* Stochastic removal of 10% of global vertices.
  * *Scenario B (Targeted Malicious Attack):* Intentional elimination of the top 10% highest-degree hubs.
  * *Evaluation Metrics:* Real-time logging of Connected Component counts, Giant Component compression rates, and average shortest path expansion across network variations.

### Assignment & Lab 4: The Barabási-Albert (BA) Generative Model
* **Focus:** Structural evolution mechanisms, continuous growth dynamics, and preferential attachment equations.
* **Core Mechanisms:** Growth ($m$ links injected per step) and Preferential Attachment probability formulations:
  $$\Pi(k_i) = \frac{k_i}{\sum_{j} k_j}$$
* **Analytical Evaluations:** Tracking the architectural constraints of the pure BA model, specifically its asymptotic clustering coefficient collapse ($C \to 0$) as network bounds grow infinitely ($N \to \infty$). Real-world behavioral mapping to social platforms (Instagram follower distributions and micro-blogging copying mechanisms on Twitter/X).
* **Programmatic Task:** Building dynamic BA graphs via `networkx.barabasi_albert_graph`, plotting log-log distribution lines to extract alpha exponents, and evaluating clustering behaviors empirically across progressive node horizons ($N \in \{1000, 2000, 5000, 10000\}$).

### Capstone Project: Robust Link Prediction in an Adversarial Environment
* **Focus:** Deep graph machine learning, topological vulnerabilities, and robust message-passing design.
* **Scenario:** Constructing an end-to-end link prediction framework, implementing surrogate-based adversarial topology attacks, and deploying defensive safeguards to protect Graph Neural Networks (GNNs).
* **Project Phases & Architecture:**
  1. **Phase 1: Deep Structural Link Prediction Baseline**
     * Adapting representation paradigms for edge tasks, analyzing the conceptual limitations of pure node-level GCN embeddings, and evaluating how localized subgraph structures (such as the SEAL framework) restore distance-aware representation.
     * Implementing strict `RandomLinkSplit` pipelines to isolate training, validation, and test sets to ensure zero data leakage by stripping test edges completely during training.
     * Target metrics: Baseline performance must reach $\text{AUC-ROC} \ge 0.88$ and $\text{Average Precision (AP)} \ge 0.88$ on clean citation topologies.
  2. **Phase 2: Topological Adversarial Ingestion (Attacker Design)**
     * Adapting the Nettack framework from classification variants to edge targets under a restricted structural perturbation budget ($k \le 5\%$ of edges).
     * Developing two attacking modules: Random Attack Baseline (stochastic injection of unnoticeable perturbations) and Gradient-Based Greedy Attacker (utilizing surrogate model gradients to maximize prediction error).
  3. **Phase 3: Deep Architectural Defensive Safeguards**
     * *GNN-Guard Layer Implementation:* Designing a custom PyTorch Geometric `MessagePassing` subclass that computes node feature similarity at the aggregation phase to automatically dampen or eliminate messages traveling across adversarial edges.
     * *Adversarial Training Loop:* Formulating a min-max regularized loss objective that continuously injects dynamically poisoned graph batches during the training optimization loop.
  4. **Phase 4: Cross-Dataset Generalization & Evaluation**
     * Executing the complete pipeline concurrently across the **Cora** and **CiteSeer** networks to verify robustness transferability.
     * Structural constraints: The final robust models must drop less than 3% AUC on clean data compared to the baseline, and limit post-attack AUC degradation to under 10%.
