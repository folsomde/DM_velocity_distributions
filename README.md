# README
This repository contains supplemental data for Folsom et al. (2025), "Dark Matter Velocity Distributions for Direct Detection." The relevant data are stored in the JSON file, which is formatted as follows:

* `haloIDs : list(int)`, the snapshot-99 (z=0) Subfind IDs of the MW-like halos. 
* `hasGSE : list(bool)`, `True` if and only if the MW-like halo has undergone a GSE-like merger
* `hasLMC : list(bool)`,  `True` if and only if the MW-like halo has an LMC-like halo within its virial radius
* `scale_factors : list(float)` The Solar radius ($R_\odot$ = 8.3 kpc) divided by the $R_M$ of each unscaled halo
* `scaled : dict` (similarly, `unscaled`)
    - `densities : list(float)` The DM densities (in GeV/cm^3) within the Solar annulus, i.e. the square torus with $|r_\mathrm{cyl} - R_\odot|$ < 1 kpc and $|z|$ < 1kpc 
    - `galactocentric : dict`, values computed in the galactocentric frame
        - `speed_dists : list(list(float))`, the galactocentric DM speed distributions within the Solar annulus (in 1e-3 s/km) for each MW-like halo, computed by a KDE with Epanechnikov kernel and bandwidth set by Silverman's rule.
        - `bandwidth : list(float)`, the bandwidths produced by Silverman's rule, used to compute `speed_dists`
        - `maxwellians : dict`, parameters for the truncated Maxwell--Boltzmann fits, computed via the bootstrap method described in Appendix B
            - `v0 : list(float)` median of the 10,000 best-fit peak speeds (in km/s)
            - `v0_lower, v0_upper : list(float)` 16th and 84th percentiles of the 10,000 best-fit peak speeds (in km/s)
            - `vesc : list(float)` median of the 10,000 best-fit truncation speeds (in km/s)
            - `vesc_lower, vesc_upper : list(float)` 16th and 84th percentiles of the 10,000 best-fit truncation speeds (in km/s)
    - `geocentric : dict`, values computed in the geocentric frame (taking the Earth's velocity as on March 9, 2000)
        - `bandwidth : list(float)`, `speed_dists : list(list(float))` as above, but computed in the geocentric frame.
* `speed_geo : list(float)`, the velocities (in km/s) at which the **geo**centric `speed_dists` are evaluated
* `speed_gal : list(float)`, the velocities (in km/s) at which the **galacto**centric `speed_dists` are evaluated

A sample Jupyter notebook script is provided to showcase some aspects of these data. For further inquiry, feel free to contact Dylan Folsom (dfolsom@princeton.edu).

## License
These data are licensed under [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/). These data are produced from the results of the `TNG50` simulation, which is publicly available at https://tng-project.org.
