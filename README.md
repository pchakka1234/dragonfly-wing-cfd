# Dragonfly Wing CFD — Public Test Preview

This is a public preview/test project, not the actual research code. Private research implementation and results are not included.

OpenFOAM case files for a moving dragonfly wing, with meshing, a steady-state setup, and a transient `pimpleFoam` setup driven by tabulated motion.

## Project contents

- `wingMotion_snappyHexMesh/`: block mesh and surface meshing configuration, plus dragonfly STL geometry.
- `wingMotion2D_steady/`: mesh extrusion and steady flow case.
- `wingMotion2D_transient/`: initial conditions, motion settings, `kinematics.dat`, and transient solver configuration with force output.
- `Allrun` / `Allclean`: original workflow scripts.

The transient configuration specifies a 0.1-second run, a 0.000025-second time step, and output every 0.0005 seconds.

## Status and running

This repository preserves an experimental working project. It is not yet a verified, one-command reproduction package. The original scripts and case settings are retained without changing the simulation.

Use an OpenFOAM installation and source its environment before running case utilities. Review the scripts and dictionaries before executing `./Allrun`:

- The steady case uses the OpenFOAM Foundation `foamRun` workflow, while the transient case identifies OpenCFD v2512 and `pimpleFoam`. Compatibility needs checking for your installed version.
- `Allrun` references `wingMotion2D_transient/pointDisplacement`, but the supplied file is located at `wingMotion2D_transient/0/pointDisplacement`. Review this copy step before running.
- Patch names and the mapping between steady and transient cases need validation for the supplied dragonfly geometry.
- `Allclean` deletes generated case data and some initial fields; preserve a copy before using it.

Generated meshes, simulation time directories, and post-processing data are excluded from Git. The original local folder contains approximately 3.5 GB of data; this repository contains the setup and inputs rather than those results. Regenerate meshes and results in a compatible environment. No simulation was run as part of preparing this repository.

## Attribution

The case files contain OpenFOAM headers and use the wing-motion tutorial workflow. Original notices are preserved. This repository does not claim authorship of OpenFOAM or its tutorial framework.
