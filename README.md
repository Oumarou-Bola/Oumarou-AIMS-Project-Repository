# Optimizing Cost in Transportation Networks

## Project Overview
This project focuses on proposing methods and techniques to address inefficiencies in global transportation network design. By studying various network distance measures, we implemented Python-based analysis to evaluate their performance across different transportation datasets.

### Project Supervisor
**Dr. Philip Knight** – University of Strathclyde

### Author
**Oumarou Moussa Bola**

## Repository Contents
This repository includes materials related to our analysis of transportation networks. Specifically, it contains one of six Jupyter notebooks that focus on the **Paris dataset**. The structure of this notebook is similar to the other five in the project.

Inside this repository, you will find:
- **Jupyter Notebook**: The Python implementation for analyzing the Paris transportation network.
- **Dataset**: The Paris Network dataset used in our study.
- **Generated Images**: Visualizations from previous simulations.

## Theoretical Background

### Problem Definition
Transportation networks often lack optimal efficiency, leading to increased travel costs, congestion, and environmental impacts like CO₂ emissions. The goal of this study is to explore network distance metrics and develop strategies to optimize these networks, making them more cost-effective and sustainable.

### Communicability Metric (Detailed proof can be found in the related report)
The **communicability function** measures how effectively information or movement propagates between nodes in a network. It is computed using the spectral decomposition of the adjacency matrix `A`:
   
   ```math
   C_{pq} = \sum_{j=1}^{n} \phi_j(p) \phi_j(q) e^{\lambda_j}
   ```
   
where $ϕ_j(p), ϕ_j(q)$ are the p-th and q-th elements of the j-th orthonormal eigenvector of `A`, associated with the eigenvalue $λ_j$. This metric captures both direct and indirect connections, offering insights into network efficiency.

The communicability **distance metric** is then defined as:
   
   ```math
   \xi_{pq} = C_{pp} + C_{qq} - 2C_{pq}
   ```
   
where $C_{pp}$ and $C_{qq}$ measure self-communicability, while $C_{pq}$ measures the interaction between nodes `p` and `q`. 

**Proof that Communicability Distance is Euclidean:** 

Using the spectral decomposition of `A`, we rewrite $C_{pq}$ as:
   
   ```math
   C_{pq} = \sum_{j=1}^{n} \phi_j(p) \phi_j(q) e^{\lambda_j}
   ```
   
Thus, the communicability distance satisfies:
   
   ```math
   \xi_{pq} = ||x_p - x_q||^2
   ```
   
where $x_p = e^{\Delta/2} \phi_p$, proving that the communicability distance is Euclidean.

### Hybrid Distance Measure (Detailed proof can be found in the related report)
To address inefficiencies in transportation networks, we introduce a **hybrid metric** that incorporates:
- **Traditional shortest-path distance ($d_{pq}$)**
- **CO₂ emissions per trip ( $d_{CO_2}(p, q)$ )**
- **Communicability distance ($C_{pq}$)**

The hybrid distance is defined as:
   
   ```math
   H_{pq} = \alpha d_{pq} + \beta d_{CO_2}(p, q) + \gamma C_{pq}
   ```
   
where `α, β, γ` are tunable parameters that allow for balancing the contributions of cost, environmental impact, and network efficiency.

**Proof that $H_{pq}$ is a Valid Distance Metric:**
1. **Non-negativity:**
   
   ```math
   H_{pq} \geq 0, \quad \text{since} \quad d_{pq} \geq 0, \quad d_{CO_2}(p, q) \geq 0, \quad C_{pq} \geq 0.
   ```
   
2. **Symmetry:**
   
   ```math
   H_{pq} = H_{qp}, \quad \text{since all terms are symmetric.}
   ```
   
3. **Triangle Inequality:**
   
   ```math
   H_{pq} \leq H_{pw} + H_{wq}, \quad \forall p, q, w \in V.
   ```
   
Thus, $H_{pq}$ satisfies the conditions of a metric.

### Rewiring Algorithms
To improve transportation network efficiency, a **rewiring strategy** was developed. The goal is to adjust the network structure by:
- Modifying connections to balance communicability and shortest paths.
- Ensuring connectivity while optimizing travel efficiency.

The rewiring process follows:
   
   1. Compute communicability and shortest-path distributions.
   2. Identify regions with inefficient connectivity.
   3. Adjust edges to improve balance while maintaining network integrity.

## Project Objectives & Key Findings
Our primary objective is to explore and develop techniques that improve the efficiency of transportation networks. Key findings from our analysis include:

- **Network Distance Metrics**: We analyzed various distance measures to assess their effectiveness in identifying well-connected hubs and areas that require improved connectivity.
- **Resistance Metric**: Demonstrated effectiveness in detecting both well-connected hubs and regions needing better integration.
- **Hybrid Metric**: Showed that adjusting the balance between travel cost, environmental impact, and network efficiency can yield optimized transportation routes.
- **Rewiring Strategy**: Successfully modified network structures to enhance connectivity whilst reducing inefficiencies.

## Contact
For more informations, details or dataset repositories used in this project, feel free to reach out:
📧 **oumarou@aims.ac.za**  
<!--🔗 **Repository**: [GitHub Repository](https://github.com/OMB227/Oumarou-AIMS-Project-Repository.git)-->


