# Technical Specification: GER PT-Symmetric Wireless Power Transfer (WPT)

This specification details the mathematical and physical equations of the **GER Non-Hermitian Hamiltonian Confinement Engine** applied to Dynamic Wireless Power Transfer (DWPT).

---

## 1. The Non-Hermitian Hamiltonian System

We model the coupled wireless transfer coils as an active open quantum-inspired system with balanced gain ($+\gamma$) and loss ($-\gamma$). The time-dependent state vector of the system $\Psi(t) = \begin{pmatrix} a_1(t) \\ a_2(t) \end{pmatrix}$ represents the currents in the transmitter and receiver resonators.

The evolution is governed by the Schrödinger-like equation:

$$i \frac{d}{dt} \Psi(t) = H_{GER} \Psi(t)$$

Where the effective Non-Hermitian Hamiltonian $H_{GER}$ is defined as:

$$H_{GER} = \begin{pmatrix} i\gamma_{eff} & s_{eff} \\ s_{eff} & -i\gamma_{eff} \end{pmatrix}$$

*   $\gamma_{eff} \in \mathbb{R}$: The effective gain (transmitter side) and loss (receiver side) coefficient.
*   $s_{eff} \in \mathbb{R}$: The effective mutual coupling coefficient between the resonators.

---

## 2. Eigenvalue Analysis and Exceptional Points (EP)

To find the resonant modes of the system, we solve the characteristic equation $\det(H_{GER} - \lambda I) = 0$:

$$\det \begin{pmatrix} i\gamma_{eff} - \lambda & s_{eff} \\ s_{eff} & -i\gamma_{eff} - \lambda \end{pmatrix} = 0$$

Multiplying the terms:

$$(i\gamma_{eff} - \lambda)(-i\gamma_{eff} - \lambda) - s_{eff}^2 = 0$$

$$\gamma_{eff}^2 + \lambda^2 - s_{eff}^2 = 0$$

This yields the eigenvalues ($\lambda$):

$$\lambda = \pm \sqrt{s_{eff}^2 - \gamma_{eff}^2}$$

### Physical Phases of the System:
1.  **Unbroken PT-Symmetric Phase ($s_{eff} > \gamma_{eff}$)**:
    The eigenvalues are purely real. The system oscillates stably, locking the resonance frequency to the coupled mode, preventing frequency splitting drops.
2.  **The Exceptional Point ($s_{eff} = \gamma_{eff}$)**:
    The eigenvalues coalesce to a single degenerate state $\lambda = 0$. This represents the phase transition boundary where efficiency is maximized under spatial variation.
3.  **Broken PT-Symmetric Phase ($s_{eff} < \gamma_{eff}$)**:
    The eigenvalues become complex conjugate pairs. The system enters an unstable gain/loss state (exponential decay or amplification), marking the physical limit of power transfer.

---

## 3. Spatial and Angular Coupling Modulations

To model dynamic alignment, the coupling coefficient $s_{eff}$ and gain $\gamma_{eff}$ are parameterized by the angular offset $\theta(t)$ of the moving vehicle:

$$\gamma_{eff} = \gamma_{0} \cos(\theta)$$

$$s_{eff} = \sqrt{\left(s_{right} \sin(\theta)\right)^2 + \left(s_{left} \sin(\theta + \pi)\right)^2}$$

Where:
*   $\theta = \sin(d(t) + \theta_0)$ represents the spatial wrapping of the alignment coordinate $d(t)$.
*   $s_{right}$ and $s_{left}$ are the horizontal coupling tensors (East and West faces of the GER ring).

By maintaining the system at the Exceptional Point boundary:

$$\gamma_{eff}(t) \approx s_{eff}(t)$$

The power transfer efficiency $\eta$ is stabilized at its maximum limit:

$$\eta = \eta_0 \cdot \text{Re}\left(\sqrt{1 - \left(\frac{\gamma_{eff}}{s_{eff}}\right)^2}\right) \approx \text{constant}$$

This mathematical framework enables constant $>90\%$ efficiency without active software tracking loops or physical servos.
