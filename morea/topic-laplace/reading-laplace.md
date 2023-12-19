---
title: "Introduction to Laplace Transform"
published: true
morea_id: reading-laplace
morea_summary: "How to solve the Laplace transform"
morea_type: reading
morea_labels:
---

# Laplace Transformation Definition
The Laplace Transformation is a linear transformation between two vector spaces. It is used as a bypass strategy to solve complex differential equations by transforming the differential equation into an algebraic expression that is easier to solve.
  
Given a differential equation, that we are unable to solve, we apply the Laplace transform "&#8466; " to map it from the t-domain into an algebraic equation in the s-domain.  

<center><img src="assets/Laplace1.png"> </center>  
 
We can then find a solution to the algebraic equation in the s-domain. Afterwards, we can use the inverse Laplace Transform “&#8466; $$^{-1}$$" to return the solution to the t-domain.
  
There are several advantages of using the Laplace Transformation when analyzing circuits  

* Since differential equations represent a RLC circuit in the time domain, the Laplace Transform is a powerful tool that allow us to use algebraic operations to analyze the circuit.
* It can provide insight into how a circuit behaves at different frequencies.
* It allows us to find the transfer function of the circuit. Knowing the transfer function can help us determine the circuit response to different inputs.
* It can be used to separate the transient and steady-state responses of a circuit.
* It is a simpler operation than convolution.
  
# The Laplace Transform Formula
Given a function f(t), the Laplace transform is defined as the transformation of $$f$$ to the function $$F$$. The following equation defines it:  
<div align="center">$$F(s)= \mathscr{L} {[f(t)]}= \int_{0}^{\infty} f(t)e^{-st} \; dt $$  </div>

Where $$s$$ is a complex variable with a real part $$\sigma$$  and an imaginary part $$\omega$$  
<center> $$s=\sigma+j\omega$$ </center>
  
If the integral converges, the Laplace Transform of the function exists. If it diverges, the Laplace Transform of the function doesn’t exist.
  
Examples:  
Find the Laplace Transform of $$f(t)=1$$
  
<div align="center">$$\mathcal{L}{(1)}= \int_{0}^{\infty} e^{-st} \; dt$$</div>
<div align="center">$$= \left. -\frac{e^{-st}}{s}  \right|_{0}^{\infty}$$</div>
<div align="center">$$=\frac{1}{s}$$</div>
  
Find the Laplace Transform of $$f(t)=t$$  

<div align="center">$$ \mathcal{L}{(t)}= \int_{0}^{\infty} te^{-st} \; dt$$ </div>
Using integration by parts:  
<div align="center">$$= \left. \frac{te^{-st}}{s}  \frac{e^{-st}}{s^2}\right|_{0}^{\infty}$$</div>
<div align="center">$$=\frac{1}{s^2}$$</div>
  
Find the Laplace Transform of $$f(t)=e^t$$ 
<div align="center">$$\mathcal{L}{(e^t)}= \int_{0}^{\infty} e^te^{-st} \; dt$$</div>
<div align="center">$$= \int_{0}^{\infty} e^{-st+t} \; dt$$</div>
<div align="center">$$= \int_{0}^{\infty} e^{-(s-1)t} \; dt$$</div>
<div align="center">$$= \left. -\frac{e^{-(s-1)t}}{s-1}  \right|_{0}^{\infty}$$</div>
<div align="center">$$=\frac{1}{s-1}$$</div>
  
Luckily, the most common Laplace Transforms have already been integrated and are available in a table ready for use.  

# Properties of the Laplace Transform  
The Laplace Transform is a linear transformation so it preserves:  
* Scalar Multiplication  
<div align="center">$$\mathcal{L}{[C*f(t)]}=C*\mathcal{L}{[f(t)]}$$</div>
* Addition
<div align="center">$$\mathcal{L}{[f(t)+g(t)]}=\mathcal{L} {[f(t)]}+\mathcal{L} {[g(t)]}$$</div>
In general
<div align="center">$$\mathcal{L}{[C*f(t)+D*g(t)]}=C*\mathcal{L} [f(t)]+D*\mathcal{L}{[g(t)]}$$</div>  
  
## Several more properties are listed in the table below

<center><img src="assets/Laplace4.png"> </center>  

# Examples

## Example 1:
<div align="center">$$f(t)={u(t)-u(t-1)}$$</div> &nbsp;  

<div align="center">Using the Time Shift Property:</div>
<div align="center">$$F(S)=\frac{1}{s}-\frac{e^{-s}}{s}$$</div>

## Example 2:
<div align="center">$$f(t)=2tu(t-4)$$</div> &nbsp;  

<div align="center">Using the Time Shift Property:</div>
<div align="center">$$f(t)=2(t-4+4)u(t-4)$$</div>
<div align="center">$$f(t)=2((t-4)u(t-4)+4u(t-4))$$</div>
<div align="center">$$F(S)=2(\frac{e^{-4s}}{s^2}+\frac{4e^{-4s}}{s})$$</div>
<div align="center">$$F(S)=\frac{2e^{-4s}}{s^2}+\frac{8e^{-4s}}{s}$$</div>

## Example 3:
<div align="center">$$f(t)=10te^{-t}sin(2t)u(t)$$ </div> &nbsp;  

<div align="center">Using the Frequency Differentiation Property:</div>
<div align="center">$$F(S)=-10(\frac{d}{ds}[\frac{2}{(s+1)^2+4}])$$ </div>
<div align="center">$$F(S)=-10(\frac{-4(s+1)}{((s+1)^2+4)^2})$$ </div>
<div align="center">$$F(S)=\frac{40(s+1)}{(s+2s+5)^2}$$ </div>

## Example 4: 
<div align="center">$$f(t)=5cos(t)\delta(t-2)$$ </div>
<div align="center">$$= F(s)=5cos(2)e^{-2s} \;$$ </div>

## Example 5:
<div align="center">$$f(t)=2tu(t)-\frac{d}{dt}\delta(t)$$ </div> &nbsp;  

<div align="center">Using the Time Differentiation Property:</div>
<div align="center">$$F(S)=\frac{2}{s^2}-4s(1-0)$$ </div>
<div align="center">$$F(S)=\frac{2}{s^2}-4s$$ </div>

## Example 6:
<center><img src="assets/lapace5.png"> </center>  
<div align="center">$$f(t)={2u(t)+2u(t-1)-4u(t-2)}$$ </div>
<div align="center">$$F(S)=\frac{2}{s}+\frac{2e^{-s}}{s}-\frac{4e^{-s}}{s}$$ </div>

## Example 7:
<center><img src="assets/Laplace6.png"> </center>  
<div align="center">$$f(t)={2tu(t)-2tu(t-2)-2u(t-2)}+2u(t-6)-2tu(t-6)+2tu(t-7)$$ </div>
<div align="center">$$F(S)=\frac{2}{s^2}-\frac{2e^{-2s}}{s^2}-\frac{2e^{-2s}}{s}+\frac{2e^{-6s}}{s}-\frac{2e^{-6s}}{s^2}+\frac{2e^{-7s}}{s^2}$$ </div>

## Example 8:
<center><img src="assets/Laplace7.png"> </center>
<div align="center">$$f(t)={-5tu(t)+10tu(t-2)-5tu(t-4)}+10u(t-4)-5tu(t-6)+5tu(t-8)$$ </div>
<div align="center">$$F(S)=-\frac{5}{s^2}+\frac{10e^{-2s}}{s^2}-\frac{5e^{-4s}}{s^2}+\frac{10e^{-4s}}{s}-\frac{5e^{-6s}}{s^2}+\frac{5e^{-8s}}{s^2}$$  </div>