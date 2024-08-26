# ASE molecular dynamics modules for simulations with an external electric field

Kaoru Hisama

You can specify efield variable (ndarray [Ex, Ey, Ez]) to induce an external electric field in Langevin dynamics.

## Citation

Kaoru Hisama, Gerardo Valadez Huerta, and Michihisa Koyama, Computational Materials Science 111955 (2023).
https://doi.org/10.1016/j.commatsci.2022.111955

## requirement

- ASE, pfp_api_client (version 1.3.0 or later) (for codes in "YSZ" and "HClaq" directory)
This code only work in Matlantis (https://matlantis.com/), the PFP hosting service.

Note that your "calculator" in your simulation should include "get_charge()" method which calculate the charge in each step.
Such as the PFP calculator.

- ASE, LAMMPS with Python API (for codes in "YSZ_Buckingham" directory)

For the installation of LAMMPS Python package, see the information as follows.

https://docs.lammps.org/Python_install.html


## Usage

Place the file `langevin_ExternalField.py` in the working directory, then import the module to your simulation.

```
from langevin_ExternalField import Langevin
```

It is similar to the original Langevin code in ASE (ase.md.langevin), except for the `efield` variable.

Set up and run simulation like an example as follows,

```
dyn = Langevin(atoms=your_atoms, timestep=dt, 
               temperature_K = T, friction=0.01, efield=efield, trajectory = "your_simulation.traj", loginterval=50)

steps = 200000
dyn.run(steps)

```

## Examples

- HClaq: HCl aquoues calculation with PFP+D3 dispersion.

- YSZ: YSZ with PFP

- YSZ_Buckingham: YSZ with Buckingham potential implemented in LAMMPS