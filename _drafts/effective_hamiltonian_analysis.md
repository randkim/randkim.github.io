---
title: 'Effective Hamiltonian theory and its applications in quantum information'
date: 2022-06-06
permalink: /posts/2022/06/10_1139/
tags:
  - paper_analysis
---

The two-level system and the Rotating Wave Approximation (RWA) were one of the first things I learnt during my undergraduate Quantum Mechanics course. However, there is a seemingly paradoxical effect that results from the combination of these concepts: the light, or ac Stark shift. Before studying the paper in depth, let us first review why this is paradoxical.

Section 1: What's the Paradox?
------
Consider a two-level system interacting with a laser, which is detuned away from resonance. In the interaction picture, he Hamiltonian describing this system is rather straightforward:
  \begin{equation}
    \hat{H} = \frac{\hbar \Omega}{2} \bigg[\ket{2}\bra{1} \exp(-i\Delta t) + \ket{1}\bra{2} \exp(i\Delta t) \bigg]
  \end{equation}
Where $\Omega$ is the Rabi frequency and $\Delta$ is the detuning. As the laser couples the two states to each other, the energy separation between the two levels are shifted through an effect named the ac Stark effect. This effect is described through the following Hamiltonian:
  \begin{equation}
    \hat{H}_{eff} = -\frac{\hbar \Omega^2}{4\Delta} \bigg[\ket{2}\bra{2} - \ket{1}\bra{1} \bigg]
  \end{equation}
Here, we can see how the paradox mentioned above comes by. The effects of the dynamics of the system scale with $\Omega/\Delta$, while the ac Stark shift scales with $\Omega^2/\Delta$. Thus, at large detunings, the effects of the ac Stark shift is still significant, while the dynamics become negligible as the $\exp(\pm i \Delta t)$ terms are approximated to zero via the RWA. How is it that this seemingly negligible dynamics causes a real and appreciable effect like the ac Stark shift?

Section 2: The Time-Averaged Operator
------
The authors present the use of a time-averaging procedure to tackle this question. This procedure takes a quantum mechanical operator and averages it over all time:
  \begin{equation}
    \overline{\hat{O}(t)} = \int^{\infty}_{-\infty} f(t=t') \hat{O}(t') dt'
  \end{equation}
Where $f(t)$ is a real-valued and unit area function. For our purpose, we take $f(t)$ to act as a low-pass filter: that is, the effects of any high-frequency or rapidly oscillating components of the quantum mechanical operator are ignored in the corresponding time-averaged version. This is, in fact, a generalisation of the RWA, where we assume a specific form of such a function $f(t)$ such that any terms oscillating faster than the natural evolution of the system (the Rabi frequency) is ignored.

<i> There is an interesting consequence of both the time-averaging procedure presented here and the RWA, which is that causality is no longer true. The reason is because in both cases, we ignore some sort of high-frequency component; and since some time components are ignored, causality can no longer hold. This might have unforeseen problems in some quantum gates and algorithms which makes use of such far detunings and still take the RWA. I will look more into this complication in the future post. </i>

We can play around with this definition of time-averaging for a bit. Ignoring the integration limits for simplicity,
  \begin{align}
    \frac{\partial}{\partial t} \overline{\hat{O}(t)} = \int^ \bigg[\frac{\partial f(t-t')}{\partial t} \hat{O}(t') dt' + f(t-t')\frac{\partial \hat{O}(t')}{\partial t} dt' \bigg]
  \end{align}
Considering each term separately using integration by parts,
  \begin{align}
    \int \frac{\partial f(t-t')}{\partial t} \hat{O}(t') dt' = \int \frac{\parital f(t-t') \cdot dt'}{dt} \hat{O}(t') = f(t-t') \hat{O}(t') \vert^{\infty}_{-\infty} - \int \frac{\partial \hat{O}(t')}{\partial t'} \frac{dt'}{\partial t}
  \end{align}


D F James and J Jerke. Effective Hamiltonian theory and its applications in quantum information. <i>Canadian Journal of Physics</i>. <b>85</b>(6): 625-632. https://doi-org.libproxy1.nus.edu.sg/10.1139/p07-060


------
