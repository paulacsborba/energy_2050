# Brazil Energy System Model (Calliope)
## Overview

This repository contains a national-scale energy system optimization model for Brazil developed using Calliope. The model focuses on the integration of bioenergy, land-use constraints, and emerging fuels into long-term energy planning.

The framework co-optimizes energy supply, conversion, storage, and transport across multiple sectors, with a particular emphasis on biofuel production pathways and their interaction with land availability and sustainability constraints.

## The model is designed for

- **Long-term energy planning**  
- **Policy analysis** (land use, decarbonization pathways)  
- **Academic research** on energy–land–climate interactions  


## Model Scope
### Sectors included
- Light-duty vehicles (LDV)
- Heavy-duty vehicles (HDV)
- Aviation
- Shipping
- Rail
- Industry
- Buildings

### Energy carriers
- Electricity
- Hydrogen
- Ethanol (1G and 2G)
- Biodiesel / HVO
- Sustainable Aviation Fuel (SAF)
- E-kerosene and e-methanol
- Ammonia
- E-diesel

The model explicitly represents cross-sectoral interactions, enabling competition between electrification, biofuels, and synthetic fuels.

# Bioenergy module 

A dedicated bioenergy subsystem is developed based on original work, with the following features:

### Feedstocks and conversion
- Sugarcane or corn → ethanol (1G and 2G pathways)
- Soybean → biodiesel / HVO
- Ethanol → SAF and e-fuels (indirect pathways)

### Spatial differentiation
- Production zones classified by high, medium, and low suitability
- Region-specific technologies and yields
- Land-use constraints
- Explicit available area constraints per region
- Multiple land regimes implemented via overrides:
- Full potential
- Conservation + SIGEF restrictions
- Direct linkage between land availability and biofuel production capacity

These constraints are implemented through scenario-dependent parameters such as _available_area_.

## Model Structure

The model is modular and organized into:

### Technologies

Defined in separate YAML files:

- Conversion (biofuels, hydrogen, PtX)
- Storage (CO₂, hydrogen, fuels)
- Transport (pipelines, shipping, electricity transmission)
- Demand (sector-specific)
- Locations: high spatial resolution (state-level zones, e.g., MG_Z1, SP_Z2)
- Differentiated by resource quality (high/medium/low)
- Resampled time series (e.g., 360h resolution)

### Config.:
- Linear optimization using Gurobi
- Cost-minimization objective (monetary)
*Includes:*
- Capacity expansion
- Dispatch optimization
- Storage dynamics (cyclic storage enabled)
- Exploration of near-optimal solutions

The model uses SPORES (Spatially-explicit Practically Optimal REsults) to explore alternative system configurations:

- Multiple near-optimal solutions
- Cost slack (e.g., 10–20%)
- Diversity of pathways beyond the single optimum
