---
title: "Lowpass Butterworth Circuit Design"
published: true 
morea_id: reading-butterworth-lowpass
morea_summary: "Designing a filter from order to circuit."
morea_url:
morea_type: reading
morea_labels:
---

# \\(N^\mathrm{th}\\)-order Butterworth Lowpass with Cutoff of \\(\omega_c\\)

Designing a lowpass Butterworth filter of order \\(N\\) with cutoff frequency
\\(\omega_c\\) requires us to do the following:
1. consider the sub-filters required to complete the Butterworth filter based
on the \\(N^\mathrm{th}\\)-order transfer function,
2. set up equations to solve for component values based on the
\\(N^\mathrm{th}\\)-order transfer function for a cutoff frequency of
\\(1\,\mathrm{rad/s}\\).
3. apply frequency shifting by dividing capacitor components by \\(\omega_c\\),
4. and draw out the circuit.

As it is difficult to explain all steps effectively in a purely general manner,
we'll go over one of the problems in Homework 8 as an example, which requires
us to design a \\(5^\mathrm{rd}\\)-order Butterworth filter with a cutoff
frequency of \\(15\,\mathrm{kHz}\\).

Let's begin by considering how our circuit would look like.

## The shape of the Butterworth filter's circuit.

For our convenience, here's the table of normalized Butterworth denominator
coefficients for orders 1 to 10.

<img src="filter-den.png" alt="Butterworth Filter Denominators" width="800"/>

<!--The image here has a transparent white background, which allows for
adaptability to different background colors, but becomes hard-to-read with dark
themes and the like.-->
<!--Image imports usually use `![alt_text](image_file)`, but html allows for
width specification, which allows downscaling of large images.-->

As we are dealing with an \\(5^\mathrm{th}\\) order lowpass frequency, the table
gives us a transfer function of

\\[
H = \frac{1}{(1+s)(1+0.618s+s^2)(1+1.618s+s^2)}.
\\]

Note that the above transfer function can be written as a product of three
different rational expressions:

\\[
H = \frac{1}{1+s} \frac{1}{1+0.618s+s^2} \frac{1}{1+1.618s+s^2}.
\\]

A product of circuits' transfer functions is equivalent to running those
circuits in series with each other. As a result, **we can look at a Butterworth
filter's transfer function and break it up to create multiple circuits that ---
when connected --- create the full Butterworth filter circuit.**

### Sub-circuit for a binomial: an RC circuit.

There's a myriad of configurations that will yield a transfer function of
\\(\frac{1}{1+s}\\).
