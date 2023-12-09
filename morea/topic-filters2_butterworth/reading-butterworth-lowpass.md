---
title: "Lowpass Butterworth Circuit Design"
published: true 
morea_id: reading-butterworth-lowpass
morea_summary: "An example of designing a Butterworth lowpass filter."
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

## Setting up the sub-filters for the Butterworth transfer function.

For our convenience, here's the table of normalized Butterworth denominator
coefficients for orders 1 to 10.

<!--The HTML below allows conditional display of images between light and dark mode.-->
<!-- HTML also allows for manually specified widths of images. -->
<!-- HTML just allows for more control of content in general. -->

<picture>
  <source srcset="./assets/filter-den-dark.png" media="(prefers-color-scheme: dark)" width="100%">
  <source srcset="./assets/filter-den-light.png" media="(prefers-color-scheme: light)" width="100%">
  <img src="./assets-filter-den-light.png" width="100%">
</picture>

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

There's a myriad of configurations that will yield a transfer function \\(H_1 =
\frac{1}{1+s}\\), but one of the simplest configurations available for us would
be a simple RC circuit, with a voltage follower placed in between the resistor
and capacitor and components values of 1.

<picture>
  <source srcset="./assets/rc-circuit-dark.png" media="(prefers-color-scheme: dark)" width="100%">
  <source srcset="./assets/rc-circuit-light.png" media="(prefers-color-scheme: light)" width="100%">
  <img src="./assets-rc-circuit-light.png" width="100%">
</picture>

Whenever we deal with odd-order Butterworth filters, we will need to use this
RC circuit when designing our filter.

### Sub-circuit for a trinomial: a Sallen-Key lowpass filter.

The Sallen-Key filter lowpass uses two resistors, two capacitors, and an
op-amp. If we set the resistors to be equal to \\(1\, \Omega\\), our circuit
would resemble this:

<picture>
  <source srcset="./assets/sallen-key-lp-dark.png" media="(prefers-color-scheme: dark)" width="100%">
  <source srcset="./assets/sallen-key-lp-light.png" media="(prefers-color-scheme: light)" width="100%">
  <img src="./assets-sallen-key-lp-light.png" width="100%">
</picture>

That yields a transfer function of

\\[H = \frac{1}{C_1 C_2 s^2 + 2 C_2s + 1}.\\]

This allows us to represent the trinomials in the required Butterworth transfer
function. Now, we are able to select component values to yield the desired
Butterworth filter's transfer function

## Determining component values.

We already know that the RC circuit representing the binomial requires
component values of \\(1\,\Omega\\) and \\(1\,\mathrm{F}\\). The trinomials
require a small amount of work, however. Let \\(\alpha\\) represent the
coefficient of \\(s\\), and let's compare the \\(\alpha=0.618\\) trinomial with
the Sallen-Key lowpass configuration.

\\[\frac{1}{1 + \alpha s + s^2}\ \mathrm{vs.}\ \frac{1}{C_1 C_2 + 2C_2 s +
s^2}.\\]

We see that, given a target transfer function of the form \\(\frac{1}{1 +
\alpha s + s^2}\\), we can set capacitors to match the desired transfer
function in terms of \\(\alpha\\) with the following equations:

\\[C_2 = \frac{\alpha}{2},\quad C_1 = C_2{}^{-1}.\\]

Let's refer back to the original desired transfer function.

\\[H = \frac{1}{(1+s)(1+0.618s+s^2)(1+1.618s+s^2)}.\\]

Using the two equations we found earlier, we see that our capacitor values will
be as follows:
+ a \\(1\,\mathrm{F}\\) capacitor for the RC circuit,
+ \\(C_2 = 0.309\,\mathrm{F}\\) and \\(C_1 = 3.236\,\mathrm{F}\\) capacitors
for the \\(\alpha=0.618\\) Sallen-Key, and
+ \\(C_2 = 0.809\,\mathrm{F}\\) and \\(C_1 = 1.24\,\mathrm{F}\\) capacitors for
the \\(\alpha=1.618\\) Sallen-Key.

All resistors will be \\(1\,\Omega\\).

## Applying frequency shifting.

If our target cutoff frequency was just \\(1\,\mathrm{rad/s}\\), we could use
those components to create our final filter circuit, as the capacitor values we
used were designed for cutoff frequencies of \\(1\,\mathrm{rad/s}\\). Since our
target cutoff frequency is \\(15\,\mathrm{Hz}\\) however, we will have to apply
frequency shifting to our components.

From our reading, if we want to shift our frequency by some constant \\(K_f\\),
where \\(K_f = \cfrac{\text{target freq}}{\text{base freq}}\\), we need to
multiply inductors by \\(K_f\\) and divide capacitors by \\(K_f\\). Since our
base frequency is \\(1\,\mathrm{rad/s}\\) and our target frequency is
\\(15\,\mathrm{kHz} = 9.42 \times 10^{4} \mathrm{rad/s}\\), we just have to
divide our capacitors by \\(9.42 \times 10^{4}\\). Our resistors will remain
unchanged, but our new capacitor values will then be as follows:
+ a \\(1.06 \times 10^{-5}\,\mathrm{F}\\) capacitor for the RC circuit,
+ \\(C_2 = 3.28 \times 10^{-6}\,\mathrm{F}\\) and \\(C_1 = 3.44 \times 10^{-5}\,\mathrm{F}\\) capacitors for the \\(\alpha=0.618\\) Sallen-Key, and
+ \\(C_2 = 8.59 \times 10^{-6}\,\mathrm{F}\\) and \\(C_1 = 1.32 \times 10^{-5}\,\mathrm{F}\\) capacitors for the \\(\alpha=1.618\\) Sallen-Key.

Now that we have our final component values, all we have to do here is draw out
the circuit with the correct component values, as seen below:

<picture>
  <source srcset="./assets/sallen-key-lp-complete-dark.png" media="(prefers-color-scheme: dark)" width="100%">
  <source srcset="./assets/sallen-key-lp-complete-light.png" media="(prefers-color-scheme: light)" width="100%">
  <img src="./assets-sallen-key-lp-complete-light.png" width="100%">
</picture>

Notice that the RC circuit came at the very end, and that it did not need a
voltage follower. This is due to the fact that all the current running into the
\\(v_o\\) node has to then run into ground. Had this RC circuit been put at the
start, a voltage follower would be required to make sure that none of the current
runs into the Sallen-Key filters. The drawn circuit uses one less op-amp, but
you may prefer to use the additional op-amp to get something that very clearly
resembles the transfer function.

## In summary.

It feels like we did a lot, but it all boils down to a few steps:
+ pick a filter order,
+ select correct components and correct number of components based on desired
order,
+ determine component values,
+ apply the necessary frequency shifting for a desired target frequency if
applicable, and
+ draw out the circuit.

A few variations of this problem exist. 
+ Sometimes, we'll have to find the cutoff frequency and/or order before doing
any of the above-mentioned steps.
+ We may be asked to design a highpass filter instead of a lowpass filter, which
will switch component positions, values, and modify the transfer function, which
will require us to approach component value selection with different equations.

However, this is the general set of steps needed to design a Butterworth filter
with an arbitrary order and cutoff frequency. Homework 8 --- which focuses on
filter design --- is extremely thorough, so if you're able to eventually
complete that assignment, you will most likely be fine with dealing with filter
design for the rest of EE 213.
