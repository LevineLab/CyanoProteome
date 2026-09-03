# CyanoProteome
Proteome allocation model for N2-fixing cyanobacteria. Modified from [ProteomePhyto](https://github.com/LevineLab/ProteomePhyto/).

---

## The model

This single-cell model optimizes for cell growth assuming a steady-state environment under a range of temperature, irradiance, and external nutrient concentrations. We expand the model from Leles et al. (2023) to incorporate nitrogen fixation and phosphorus metabolism, allowing the cells to use dissolved inorganic nitrogen (DIN) and/or $N_2$ fixation as possible N sources, as well as phosphate and/or phycosphere-related phosphorus (PRP) as possible P sources. 

**We simulate four types of cells:**

-*Trichodesmium* (cylindrical cells in a filament that fix nitrogen during the day) in a colony

-Free-living *Trichodesmium*

-Round *Trichodesmium* (free-living round hypothetical phenotype)

-*Crocosphaera* (free-living round cells that fix nitrogen at night)

We assume that each type of cell has a phycosphere proportional to its radius, which provides access to phycosphere-derived nutrients. While here we focus on the acquisition of phosphorus, the results are generalizable to other limiting nutrients for N2-fixers which can be provided by bacteria in the phycosphere (e.g. iron). 

Julia installation guidelines can be found here (https://docs.julialang.org/en/v1/manual/installation/) and the required packages to run the code above are: JuMP, Ipopt, CSV, DataFrames

Code developed by Daniela Osorio Rodriguez and Suzana Goncalves Leles.

**A fully annotated sample notebook is found in the file trichodesmium_temperature_limitedPO4**. This corresponds to the proteome-allocation optimization model for colonial *Trichodesmium* under a range of temperatures, with phosphorus supplied exclusively as inorganic phosphate (PO₄) and phycosphere-related phosphorus (PRP, here called DOP). All other notebooks in the repository are generated in a similar format.

---

## Repository Architecture

The repository is split into five main directories. Please see each directory for information about each file.

### **`validation`** 

This folder includes all the source code used to generate the model validations against experimental data for *Trichodesmium* and *Crocosphaera* shown in Fig. 3.

### **`temperature`** 

This folder includes the source code used to generate the growth curves, allocations, and rates under a range of temperatures for the 4 phenotypes described above under replete or limited PO4 and access to phycosphere-related phosphorus (PRP). Used to generate Fig. 4, Fig. S2, and Fig. S3. 

### **`light`** 

This folder includes the source code used to generate the growth curves, allocations, and rates under a range of light for colonial *Trichodesmium* and *Crocosphaera* under replete or limited PO4 and access to phycosphere-related phosphorus (PRP). Used to generate Fig. s9.

### **`phosphorus`** 

This folder includes the source code used to generate the growth curves, allocations, and rates under a range of phosphorus or PRP for colonial *Trichodesmium*. Used to generate Fig. 5.

### **`temperature_subclades`** 

This folder includes the source code used to generate the growth curves, allocations, and rates under a range of temperatures for 4 clades of *Trichodesmium thiebautii* that vary in cell diameter, length, and colony morphology under environmental conditions (limited PO4 and access to phycosphere-related phosphorus (PRP)). We compared the outcomes at optimal temperatures of 27 °C and 29 °C. Used to generate Fig. 6, Fig. S6 and Fig. S8.

### **`sensitivity_tests`** 

This folder includes the source code used to generate the sensitivity tests under a range of temperature, phosphorus, and varying diffusion and establishing whether PO4 and PRP could use separate transporters. Used to generate Fig. S4 and Fig. S10.

---

## Relevant References

Leles, S. G., & Levine, N. M. (2023). Mechanistic constraints on the trade-off between photosynthesis and respiration in response to warming. Science Advances, 9(35), eadh8043.

Leles, S.G., Breithaupt, L., Krinos, A., Alexander, H., Moeller, H.V., Flanjak, L., Laufkotter, C., Litchman, E., Aranguren-Gassis, M. & Levine, N. M. (2025). New niches for larger phytoplankton in a warmer, more resource-limited ocean. bioRxiv, 2025-06.

Cleveland, C. S., Bhatnagar, A. M., Barnes, S. J., Zhao, Y., & Webb, E. A. (2026). Genomics and biogeography of novel Trichodesmium isolates from the Sargasso Sea. bioRxiv, 2026-07.

