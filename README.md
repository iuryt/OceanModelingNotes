# Ocean Modeling Notes

I created this repository to collect some of the tricks I have learned while modeling the oceans.

## Horizontal viscosity (𝜈) and diffusivity (ⲕ)

### Grid Reynolds Number (Re)

One of the ways to estimate the horizontal viscosity is using the definition of grid Reynolds Number:

<img src="https://render.githubusercontent.com/render/math?math=\color{black}{Re_{\Delta x} = \dfrac{U_c \Delta x}{\nu},}#gh-light-mode-only">
<img src="https://render.githubusercontent.com/render/math?math=\color{white}{Re_{\Delta x} = \dfrac{U_c \Delta x}{\nu},}#gh-dark-mode-only">

which Uc is the characteristic velocity (you can use the expected maximum velocity from the simulation) and Δx is the grid spacing.

The idea is to keep Re below 10 to avoid the saturation level of spurious mixing, although this might not guarantee that the spurious mixing will be insignificant [1]. 

Thus, 

<img src="https://render.githubusercontent.com/render/math?math=\color{black}{\nu > \dfrac{U_c \Delta x}{10}.}#gh-light-mode-only">
<img src="https://render.githubusercontent.com/render/math?math=\color{white}{\nu > \dfrac{U_c \Delta x}{10}.}#gh-dark-mode-only">

**Example**

For a mesoscale simulation of 10km resolution and expected maximum velocities of 1 m/s, 𝜈 > 1000 m<sup>2</sup>/s.


### Diffusive CFL

...

### Data-driven

For submesoscale-resolving simulations (<= 1 km of resolution) you can try using some of the values estimated from observations. The LatMix experiment [2] found O(1) m<sup>2</sup>/s values for isopycnal dispersion for scales from 1-5 km.

## References

[1]: Ilıcak, M., Adcroft, A. J., Griffies, S. M., & Hallberg, R. W. (2012). [Spurious dianeutral mixing and the role of momentum closure](https://www.sciencedirect.com/science/article/pii/S1463500311001685?casa_token=vaLDrUe78yUAAAAA:lMQRb34IHgAbgxAT0jS6-RXTKm6Uq9u8Etm7nTNNpAZUvcJCowma7A2NZgH1E8Zer5yzZ1dHou4). Ocean Modelling, 45, 37-58.

[2]: Shcherbina, A. Y., Sundermeyer, M. A., Kunze, E., D’Asaro, E., Badin, G., Birch, D., ... & Ledwell, J. R. (2015). [The LatMix summer campaign: Submesoscale stirring in the upper ocean.](https://journals.ametsoc.org/view/journals/bams/96/8/bams-d-14-00015.1.xml) Bulletin of the American Meteorological Society, 96(8), 1257-1279.
