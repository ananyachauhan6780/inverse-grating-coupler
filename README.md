# High-Efficiency Apodized Grating Coupler on Silicon-on-Insulator Platform with Aluminium Reflector

> Inverse design of an apodized grating coupler using adjoint optimization and metallic reflectors — presented at OPTIX 2026

![Platform](https://img.shields.io/badge/Platform-Silicon%20Photonics-blue) ![Efficiency](https://img.shields.io/badge/Coupling%20Efficiency-~90%25-green) ![Sim](https://img.shields.io/badge/Simulation-Lumerical%20FDTD-orange) ![Conference](https://img.shields.io/badge/Conference-OPTIX%202026-purple)

**Authors:** Tanupriyo Das, Shaatvik Roy, Tejaswi Deka, Ananya Chauhan, Sourabh Roy  
**Affiliation:** Department of Physics, National Institute of Technology Warangal, Telangana, India  

---

## Overview

Silicon Photonics is a key platform for high-speed optical communication. Efficient fiber-to-chip coupling remains a major challenge, with grating couplers being widely used due to their planar fabrication compatibility. A significant limitation is the loss of optical power due to downward radiation into the substrate.

This work investigates the use of metallic reflectors (Al, Ag, Au) placed below the BOX layer to redirect downward-radiated power back into the waveguide, significantly improving coupling efficiency.

**Key result:** Coupling efficiency improved from ~60% to ~90% using a silver reflector.

---

## Design

- Apodized grating structure on a silicon waveguide layer over a BOX (Buried Oxide) structure
- Metallic reflectors (Al, Ag, Au) introduced below the BOX layer
- Input fiber at 5° tilt angle; tapered waveguide at output
- Strong TE mode confinement maintained throughout

**Apodization functions used:**

- Fill Factor: `Λ(x) = λ / (a + b(F₀ - R(x - x_start)))`
- Grating Period: `F(x) = F₀ - R(x - x_start)`
- Combined: `Λ(x) = λ / (a + bF(x))`

---

## Inverse Design Algorithm

Adjoint optimization using the **L-BFGS-B algorithm**:

1. Initial design (starting grating geometry)
2. Forward simulation → coupling efficiency evaluated
3. Adjoint simulation → adjoint field propagated backward from fiber mode
4. Gradient computation using sensitivity information
5. L-BFGS-B optimizer updates parameters with constraints
6. Repeat until convergence → optimized grating geometry

---

## Results

| Reflector | Peak Coupling Efficiency |
|-----------|--------------------------|
| No reflector (baseline) | ~60% |
| Gold (Au) | ~60.6% |
| Aluminium (Al) | ~91.7% |
| Silver (Ag) | ~90% (highest overall) |

- Silver reflector produces the best overall performance
- Al preferred due to **CMOS compatibility**
- Significant reduction in substrate leakage observed
- Strong TE mode confinement confirmed via field profile analysis

---

## Repository Structure

```
apodized-grating-coupler/
├── README.md
├── poster/
│   └── GC_poster.pdf
├── simulation/
│   └── (Lumerical FDTD scripts / lumopt optimization code)
└── results/
    └── (field profiles, coupling efficiency plots)
```

---

## Requirements

- Ansys Lumerical FDTD (with valid license)
- Python 3.x + `lumopt`
- NumPy, SciPy, Matplotlib

---

## References

1. A. Sala, Optics and Photonics Series. OP-TEC, 2016
2. L. Cheng et al., "Grating couplers on silicon photonics," *Micromachines*, vol. 11, no. 7, 2020
3. T. K. Saha and W. Zhou, "High efficiency diffractive grating coupler," *Journal of Physics D*, vol. 42, 2009
4. Z. Zhao and S. Fan, "Design principles of apodized grating couplers," *Journal of Lightwave Technology*, vol. 38, no. 16, 2020

---

## Acknowledgement

We acknowledge the Department of Physics, NIT Warangal for providing necessary facilities. Special thanks to **Prof. Sourabh Roy** for his guidance and mentorship.
