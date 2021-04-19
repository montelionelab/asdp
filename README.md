# asdp
**Automated Determinalion of Protein Structures from NMR data**

ASDP is an automated NMR NOE assignment engine. It uses a distinct bottom-up topology-constrained approach for iterative NOE interpretation and generates 3D structures of the protein that is as close to the true structure as possible.

**Initial Fold Analysis:**
ASDP first builds an initial chain fold based on intraresidue and sequential NOESY data, characteristic NOE patterns of secondary structures, including helical medium-range NOE interactions and interstrand beta-sheet NOE interactions, and unambiguous long-range NOE interactions, based on chemical shift matching and NOESY spectral symmetry considerations. "Ambiguous constraints" are not used in the initial structure calculations.

**Iterative Fold Analysis:**
ASDP generates distance constraint lists and utilizes the programs CYANA, or Xplor for 3D structure generation, and CNSw for refinement on a Linux-based computer cluster. DP scores (Huang et al, JACS 127:1665-74, 2005) are calculated for all intermediate models. Only the top models with highest DP scores and lowest target function (CYANA) or conformational energy (XPLOR) values are selected for iterative NOE analysis. After two cycles of model generation with CYANA or XPLOR and model selection with DP filter, NOESY cross peaks are iteratively assigned using the intermediate 3D structures and contact maps, together with knowledge of high-order topology constraints of alpha-helix and beta-sheet packing geometries. Using a DP filter for model selection improves the accuracy of the selected intermediate structures for iterative NOE analysis and therefore improves the accuracy of NOESY crosspeak assignments and final models.

**Bottom Up Strategy:** 
The ASDP protocol, in principle, resembles the method that an expert would utilize in manually solving a protein structure by NMR. ASDP "bottom up" strategy is quite different from the "top down" strategies used by programs CANDID and ARIA, which rely on "ambiguous constraints". For NOESY spectra with poor signal-to-noise ratios, such automatically assigned "ambiguous constraints" sets may not include any true NOESY assignments, and result in small distortions of the protein structure which may be avoided by the "bottom up" approach of ASDP. CANDID/CYANA also uses a "network anchoring" approach similar to, but less comprehensive than, the topology-constrained approach used by ASDP. For these reasons, some users may prefer to use both ASDP and CANDID/CYANA or ARIA in parallel to assess potential errors in automated NOESY cross peak assignments.

**For citing ASDP you may consider:**

a) Huang, Y. J.; Powers, R. & Montelione, G. T. Protein NMR recall, precision, and F-measure scores (RPF scores): structure quality assessment measures based on information retrieval statistics. J Am Chem Soc 127,1665-74 (2005)

b) Huang, Y. J.; Tejero, R.; Powers, R.; Montelione, G.T. A topology-constrained distance network algorithm for protein structure determination from NOESY data. PROTEINS: Struct. Funct. Bioinformatics 15, 587-603 (2006)

c) Huang, Y.P.; Mao, B.; Xu, F.; Montelione, G.T. Guiding automated NMR structure determination using a global optimization metric, the NMR DP score. J. Biomol. NMR 62: 439 – 451 (2015).
