---
title: "Astronomical Spectroscopy 103"
date: 2020-06-10T06:00:23+06:00
hero: location.JPG
theme: Toha
menu:
  sidebar:
    name: Spectroscopy 103
    identifier: spectroscopy-103
    parent: astrophysics
    weight: 10
--- 	

### Temperature by color

This was arguably the first part of astrophysics that broke my perception. Originally I thought, well, most flames are red, and pictures of the sun are red, so that means red stars should be hot, right? Actually, no, relatively hot stars are blue to white.

{{< img src="/posts/spectroscopy/spectroscopy103/Sirius_A_and_B_Hubble_photo.jpg" align="center">}}

{{< vs 3 >}}

The Sun's temperature is roughly 5,770 Kelvin (5,497 degrees Celsius), while the blue color of Senkaku VII (Rigel) can reach 11,000 Kelvin (10,726 degrees Celsius). This difference in color is also explained by the spectrum. The colors we see are actually the strongest kind of light in the visible spectrum of the star. What does this mean? It means that all of this light, red, orange, yellow, green, blue, indigo, and violet, gets into our eyes, but it is of course the strongest of the visible light that our visual system recognizes. It should be noted that sometimes the sun appears red to the naked eye because the atmosphere affects the sun's light, not because of its color.

{{< img src="/posts/spectroscopy/spectroscopy103/Hertzsprung-Russel_StarData.png" align="center">}}

{{< vs 3 >}}

Interested readers can look for the Sun: Sun (yellowish-white), Vega: Vega (bluish-white), Sirius: Sirius (bluish-white), and Sagittarius IV: Betelgeuse (reddish), which is located in the upper right and has recently undergone a dramatic change in brightness.

### Theoretical explanation

(If you are not interested, you can skip to the summary section)

First of all, let's explain the concept of “Blackbody”. “As the name suggests, a blackbody is a black object. A perfect blackbody does not have any electromagnetic waves (understood as light) reflected from its surface, so its surface is “black”, but the blackbody itself radiates electromagnetic waves outward. For example, if you think of the human body as a blackbody, we radiate infrared light, which is called Blackbody Radiation. A star can also be considered a blackbody. So the human body and stars have something in common! (lol)

If we were to draw a statistical picture of a blackbody in terms of wavelength of light and intensity of light it would look something like this:

{{< img src="/posts/spectroscopy/spectroscopy103/F18-0220Planck20black20body.jpg" align="center">}}

{{< vs 3 >}}

We can see that it resembles a mountain, with the top of the mountain being both the strongest beam of light. The four curves from the bottom to the top represent the spectra of four stars with low to high temperatures, and the value of the wavelength at which the peak is located (λ_max) shifts to the upper left as the temperature increases (shown by the curved dotted line in the figure). The hotter the star, the bluer its color. It can be seen that relatively hot stars are bluish and relatively cool stars are reddish. More theoretically, this image can be represented by the Planck Function.

$$B_\lambda(\lambda, T) = \frac{2hc^2}{\lambda^5} \frac{1}{e^{hc/kT\lambda} - 1}$$

The reader should not be intimidated by this equation, by varying the wavelength and temperature we can get a statistical graph of blackbody radiation similar to the image shown above. So just think of this equation as a formalization of the blackbody radiation curve. A closer derivation of Planck's equation with respect to wavelength leads to an illuminating Wien's Displacement Law:

$$\lambda_{peak} = \frac{b}{T}$$

The color-temperature relationship is then well explained: as the temperature increases T becomes larger, then the right-hand side of the equation becomes smaller, the wavelength becomes smaller, and the color of the corresponding light changes toward blue.

Integrating Planck's equation leads to the Stefan-Boltzmann Law, which is another clear-cut solution:

$$L = A \times \sigma T^4 = 4 \pi R^2 \sigma T^4$$

A brief look at the equation shows the intensity of light on the left, R is the radius of the object on the right, and T is the temperature. So the higher the temperature the brighter the object, and the larger the radius the brighter the object. This is also an explanation for the speculation about the change in the brightness of Cepheus IV: Cepheus IV's radius changes dramatically in old age, so the brightness changes dramatically along with it.

### Summary

1. Stars that are relatively hot (around 10,000 degrees Celsius) appear blue, and stars that are relatively cold (around 5,000 degrees Celsius) appear red

2. The light from a star is a mixture of colors, and what we see is only the color of the strongest light.

3. Theoretical explanation: the size of a star's radius at the same temperature determines its brightness, and vice versa for the same radius, the temperature determines its brightness.

