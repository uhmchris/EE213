---
title: "Laplace Transform of RLC"
published: true
morea_id: reading-laplaceinitial-RLC
morea_summary: "How to apply Laplace transform to resistors, inductors, and capacitors with initial conditions"
morea_type: reading
morea_labels:
---

# Performing Laplace Transform On Resistors, Inductors, and Capacitors With Initial Conditions

## Prerequisite Knowledge
Before continuing, you must have covered:  
* Voltage-current relationships for ideal resistors, capacitors, and inductors  
* Methods of circuit analysis  
* Laplace transformation  
* Inverse Laplace transformation  

## General steps in applying the Laplace transform:
1. Transform the circuit from time domain to the s-domain.
2. Use methods of circuit analysis such as nodal, mesh, source transformation, superposition, and other techniques that you are familiar with.
3. Transform the solution back to time domain using inverse transform.  

## Laplace Transformation of Ideal Resistors, Capacitors, and Inductors  
### Resistors  
<center><img src="timetos-domainvisual-resistor.png" alt="centered image"> </center>  
  
The Laplace transformation of a resistor's impedence with a value of $$R\, \Omega$$ is $$R\, \Omega$$.
   
The voltage-current relationship for a resistor in the time domain is  
<div align="center"> $$V(t) = Ri(t)$$  </div>  
By taking the Laplace transform, it is transformed into the s-domain
<div align="center"> $$V(s) = RI(s)$$ </div>  

### Inductors  
<center><img src="timetos-domainvisual-inductor.png" alt="centered image"> </center>  
  
Unlike resistors which dissipate energy and thus are independent of frequency (also expressed through Ohm's Law), inductors store energy when *current* flows through them, and thus are frequency-dependent.
  
This can also be expressed through the equation
<div align="center"> $$V_{L}(t) = L\frac{di_{L}(t)}{dt}$$ </div>
  
By taking the Laplace transform, it is transformed into the s-domain
<div align="center"> $$V_{L}(s) = L[sI_{L}(s)-i_{L}(0^-)] = sLI_{L}(s) - Li_{L}(0^{-}) $$  
$$V_{L}(s) - sLI_{L}(s) + Li_{L}(0^{-}) = 0$$ </div>
  
The second equation might provide a better perspective of how each component contributes to the total voltage. Notice that on the table of circuits above in s-domain, $$sLI_{L}(s)$$ represents the voltage drop across the inductor, and $$Li_{L}(0^{-})$$ represents the initial voltage going across the inductor when $$t=0$$ in the form of a voltage source. Due the term being negative, the polarity of the voltage source is opposite to the polarity of $$V(s)$$.
  
The voltage source can be turned into a current source using **source transformation** with the current source parallel to the inductor. This can also be obtained by isolating $$I(s)$$ from the previous equations  
<div align="center"> $$I_{L}(s) = \frac{V_{L}(s)}{sL} + \frac{i_{L}(0^-)}{s} $$  
$$I_{L}(s) - \frac{V_{L}(s)}{sL} - \frac{i_{L}(0^-)}{s} = 0$$ </div>
  
The second equation might provide a better perspective of how the current is split between branches. Going back to the table, $$\frac{V_{L}(s)}{sL}$$ represents the current going across the inductor, and $$\frac{i_{L}(0^-)}{s}$$ represents the current that was initially going across the inductor when $$t=0$$.
  
### Capacitors  
<center><img src="timetos-domainvisual-capacitor.png" alt="centered image"> </center>  
  
Similar to inductors, capacitors also store energy and are frequency-dependent, but it occurs when there's *voltage* going across it.
  
This can be expressed through the equation  
<div align="center"> $$i_{C}(t) = C\frac{dv_{C}(t)}{dt}$$ </div>
  
By taking the Laplace transform, it is transformed into the s-domain  
<div align="center"> $$I_{C}(s) = C[sV_{C}(s) - v_{C}(0^{-})] = sCV_{C}(s) - Cv_{C}(0^{-})$$  
$$I_{C}(s) - sCV_{C}(s) + Cv_{C}(0^{-}) = 0$$</div>
  
On the table above for capacitors, $$sCV_{C}(s)$$ represents the current going across the capacitor, and $$Cv_{C}(0^{-})$$ represents the current that was initially going across the capacitor when $$t=0$$ in the form of a current source. Due to the the second term being negative, the direction of the current is going to the same node as $$I_{C}(s)$$
  
The current source can also be transformed back into a voltage source in series with the capacitor using source transformation. Additionally, $$V_{C}(s)$$ can be isolated from the previous equation, resulting in  
<div align="center"> $$V_{C}(s) = \frac{I_{C}(s)}{sC} + \frac{v_{C}(0^{-})}{s}$$  
$$V_{C}(s) - \frac{I_{C}(s)}{sC} - \frac{v_{C}(0^{-})}{s} = 0$$</div>
  
On the table, since $$\frac{v_{C}(0^{-})}{s}$$ is positive, it has the same polarity as $$V_{C}(s)$$. However, the second equation may provide a better perspective on the voltages going across each component.
<!-- $$
\mathscr{L}\{f(t)\}=\int_{t=0}^{\infty}f(t)e^{-st}dt
$$ -->