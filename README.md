Research Proposal
Title
Comparative Benchmarking of Sparse Volumetric Data Structures for Rocket Combustion Simulations with a Proposed Morton Spatial Hash Representation

1. Introduction
Modern rocket combustion simulations generate large three-dimensional volumetric datasets containing temperature, pressure, and density fields. These datasets are typically highly sparse, meaning that only a small portion of the computational domain contains active combustion phenomena while the majority of the space remains empty.
Traditional dense grid representations allocate memory for every voxel regardless of activity, resulting in significant memory overhead and computational inefficiency. Sparse volumetric data structures provide an alternative by storing only active regions of interest.
However, there is currently no clear guideline regarding which sparse representation is most suitable under varying sparsity conditions, especially in dynamic rocket combustion environments where flame fronts continuously evolve.
This project aims to perform a comprehensive benchmark study of major sparse volumetric data structures and introduce a Morton Spatial Hash representation as a lightweight alternative for dynamic combustion domains.

2. Problem Statement
Rocket combustion domains exhibit several computational challenges:
Extremely large three-dimensional grids.
High levels of sparsity.
Dynamic flame propagation.
Frequent neighborhood queries required by CFD solvers.
Memory limitations during large-scale simulations.
Existing structures offer different trade-offs between memory efficiency and computational performance. A systematic evaluation is needed to determine their suitability for sparse aerospace simulation environments.

3. Objectives
The primary objectives of this research are:
To benchmark major sparse volumetric data structures used in scientific computing.
To evaluate their performance under varying sparsity conditions.
To propose a Morton Spatial Hash representation for sparse combustion domains.
To develop a decision framework for selecting appropriate data structures based on simulation characteristics.

4. Research Questions
RQ1: Which volumetric data structure provides the best memory efficiency for sparse combustion domains?
RQ2: Which representation provides the fastest lookup and neighborhood traversal performance?
RQ3: How do different structures scale as sparsity increases?
RQ4: Can a Morton Spatial Hash representation provide competitive performance compared to Octrees and OpenVDB?

5. Data Structures Evaluated
Baseline Methods
A. Dense Array
A standard NumPy three-dimensional array used as a performance baseline.
Hypothesis:
Fastest direct access.
Highest memory consumption.
B. Spatial Hash Table
Stores only active voxels using coordinate-based hashing.
Hypothesis:
Fast insertion speed.
Efficient for highly sparse domains.
C. Octree
Hierarchical spatial subdivision structure.
Hypothesis:
Excellent compression for clustered flame regions.
Efficient neighborhood traversal.
D. OpenVDB
Industry-standard sparse volumetric representation.
Hypothesis:
Best overall balance between memory efficiency and traversal performance.

Proposed Method
E. Morton Spatial Hash (Proposed)
The proposed method combines:
Morton (Z-order) encoding.
Spatial hashing.
Sparse voxel storage.
Instead of storing coordinates directly, voxel coordinates are transformed into Morton codes before insertion into the hash structure.
Expected advantages:
Improved spatial locality.
Reduced cache misses.
Faster neighborhood access.
Low implementation complexity.
This method will be benchmarked against all baseline approaches.

6. Methodology
Phase 1: Dataset Generation
Synthetic combustion datasets will be generated to emulate:
Rocket flame plumes.
Expanding combustion fronts.
Turbulent sparse regions.
Clustered flame pockets.
Grid resolutions:
64³
128³
256³
512³ (if resources permit)
Sparsity levels:
1%
5%
10%
20%
50%

Phase 2: Implementation
All structures will be implemented using Python within Google Colab.
A unified interface will be developed to ensure fair comparison.

Phase 3: Benchmark Evaluation
The following metrics will be collected:
Memory Footprint
Total RAM consumption.
Build Time
Time required to construct the structure.
Point Lookup Latency
Time required to retrieve a voxel.
Neighbor Traversal Time
Performance of stencil-like operations used in CFD solvers.
Dynamic Update Time
Cost of inserting, deleting, and moving active voxels.
Compression Ratio
Memory savings relative to a dense grid representation.

7. Expected Contributions
This research is expected to provide:
Contribution 1
A comprehensive benchmark comparing:
Dense Arrays
Hash Tables
Octrees
OpenVDB
Morton Spatial Hash
under identical experimental conditions.
Contribution 2
A novel Morton Spatial Hash implementation tailored for sparse combustion domains.
Contribution 3
A sparsity-based decision framework indicating the most appropriate representation for different simulation scenarios.
Contribution 4
An open-source benchmark suite implemented in Google Colab for reproducible experimentation.

8. Expected Outcomes
The project is expected to:
Identify optimal structures for different sparsity regimes.
Quantify performance trade-offs among popular sparse representations.
Demonstrate the practicality of Morton Spatial Hashing for dynamic volumetric simulations.
Provide a foundation for future aerospace and CFD-oriented sparse data storage research.

9. Conclusion
This research proposes a systematic evaluation of sparse volumetric data structures for rocket combustion simulations and introduces a Morton Spatial Hash representation as a lightweight alternative for dynamic sparse domains. The findings will provide valuable insights into memory-performance trade-offs and establish practical guidelines for future scientific simulation frameworks.

