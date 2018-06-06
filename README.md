# 2D-porous-flux-model
Modling 2D porous flux for NR flow through support

## Objective
This simulation models the difusion of O2 through a porous layer. 
The simulation is used to optimize the design of a support for 
flow-through Neutron Reflectometry (NR) measurements. The structure 
will support a membrane being measured via NR, while allowing a 
flux of species from one side to the other. The support structure 
must meet the following requirements:
* Extremely flat
* Porous
* Mechanically strong/structurally supporting
* Uniform species concentrations at the sample interface.

## Geometry
The support being modeled has a two-layer structure: a structural 
layer (Si wafer with axial pores [i.e. 'pinholes'] etched through 
it), and a porous diffusion layer.  The structural layer give
mechanical strength and a flat surface, while the porous diffusion
layer allows species to diffuse laterally so that the species 
concentrations are uniform by the time they reach the sample.

## Simulation Domain
The simulation is of the porous diffusion layer
The pores are filled with air, and O2 is drawn out through the 
bottom boundary with a uniform and invariant flux that is 
calculated according to a user-input current density.  The conversion
assumes that a PEMFC fuel cell cathode exists at the bottom boundary,
and the flux is equal to that neeed to support the equivalent oxygen
reduction reaction rate (written here as a global reaction):

     O2 + 4 H(+) + 4 e(-) <--> 2 H2O

The top boundary of the simulation is the polished Si wafer with axial
channels etched straight through it.  This boundary has two domains: 
Beneath the open axial channel, which is assumed to contain air with a 
constant temperature, pressure, and composition (Dirichlet boundary 
condition). The remaining portion of the top boundary is the Si, which 
imposes a zero-flux boundary condition.

The simulation is in 2-D, and the simulation domain spans from the 
mid-point of the axial pore to the point halfway between axial pores.
I.e., the lateral boundaries are symmetry planes and therefore have 
zero-flux boundary conditions.

## Simulation methods
The model uses a finite-folume approach, and models the diffusion of 
the O2 transiently, simulating out to a long enough time to reach 
steady state. At steady state, the maximum variation of the O2 
concentration at the sample (bottom) interface is calculated, in 
order to assess the suitability of the proposed structures.

## User inputs
The user inputs the geometry/microstructure for the porous diffusion 
layer and the boundary conditions:
* Uniform temperature for the entire simulation domain.
* Pressure in axial pores.
* Width of axial pores in Si and distance between axial pores.
* Thickness of porous diffusion layer.
* Diffusion layer porosity and tortuosity
* Avg. pore radius within porous diffusion layer.
* Avg. particle size in porous diffusion layer.
* Current density at PEMFC boundary.