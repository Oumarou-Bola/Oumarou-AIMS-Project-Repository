# Communicability Distance Matrix and Network Rewiring Strategy

## Communicability Distance Matrix

To implement the novel hybrid measure, we first need to compute the communicability distance matrix. This will provide the foundation for analysing the effectiveness of the new measure and for comparing the communicability shortest path distance with the regular shortest path distance.

### **Definition — Communicability Distance Matrix**

Let $G=(V,E)$ be a network, and let

$$
S=[C_{11},C_{22},\cdots,C_{nn}]^T
$$

Where \( S \) is a column vector of the self communicabilities of every node in the network. Let

$$
D=S\mathbf{e}^T+\mathbf{e}S^T-2C
$$

With:

 - The communicability function matrix defined as:
 
  $$
  C=\left(C_{pq}\right)_{1\leq p,q \leq n}=\text{exp}(A)
  $$
  
- and the following column vector of ones:
  
  $$\mathbf{e}=\mathbf{1}_{n\times 1}=[ 1,1,\cdots,1 ]^T$$  

The communicability distance matrix of the network \( G \) is then given by:

$$
\overline{C}(G)=\sqrt[0]{D}
$$

Where $\sqrt[0]{}$ is the component-wise square root.

---

## Strategy Implementation Road Map

Using the definition above and considering the fact that in a transport network, the shortest path is not necessarily the most efficient path either in terms of travelling time, congestion or environmental impact, we suggest the following road map:

### a) **Implementation of the Communicability Distance in Python**

The first step consists of implementing the communicability distance function in Python.  
The implemented algorithm is given below:

#### **Algorithm 1: Communicability Distance Matrix — Heat-map Visualisation**
<p align="center">
  <img src="FOLDER_NAME/IMAGE_NAME.png">
</p>

Algorithm: Communicability Distance Matrix - Heat-map Visualisation

Input:  Adjacency matrix A of size n × n

Step 1: Compute Communicability Matrix
    B ← expm(A)

Step 2: Initialise Communicability Distance Matrix
    D ← 0_{n × n}    # Initialise a zero matrix D of size n × n

Step 3: Calculate Communicability Distance Matrix
    for i ← 1 to n:
        for j ← 1 to n:
            D[i, j] ← B[i, i] + B[j, j] - 2 × B[i, j]

Step 4: Compute Communicability Distance Matrix C
    C ← A ⊙ D    # Element-wise multiplication of A and D to obtain C

Step 5: Generate Heatmap for Communicability Distance Matrix


