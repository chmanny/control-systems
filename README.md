# Control Systems in Python

This repository contains Python tools for control systems engineering, developed for a Control Systems course. It includes two interactive Jupyter Notebooks:

1. **Root Locus Analysis** ([rlocus.ipynb](rlocus.ipynb)) — A step-by-step mathematical breakdown of the root locus method.
2. **Interactive PID Controller Designer** ([control_system_designer.ipynb](control_system_designer.ipynb)) — A real-time dashboard for tuning PID controllers with visual feedback inspired by the [MATLAB Control System Toolbox](https://www.mathworks.com/help/control/index.html)

This project was developed for a Control Systems course, implementing the calculations as a step-by-step Jupyter Notebook.

---

## Root Locus Analysis (`rlocus.ipynb`)

A detailed, step-by-step Jupyter Notebook implementing the [Root Locus](https://en.wikipedia.org/wiki/Root_locus_analysis) method, a graphical technique used to analyze system stability and performance as the feedback gain $K$ is varied.

### Features

- **Geometric Analysis:** Calculates poles, zeros, asymptote centroid ($\sigma_c$), and asymptote angles.
- **Critical Points:** Solves for breakaway and break-in candidates ($dK/ds = 0$).
- **Stability Thresholds:** Analyzes imaginary axis crossings ($\omega$ and corresponding gain $K$) using symbolic solving.
- **Visualization:** Draws the root locus plot with damping ratio ($\zeta$) and natural frequency ($\omega_n$) grids.

> [!note]
> The imaginary axis crossing points are not calculated using the Routh-Hurwitz stability criterion. For simplicity, they are computed by substituting $s = j\omega$ into the characteristic equation $P_k(j\omega) = 0$ (where $P_k(s) = D(s) + k N(s) = 0$) and solving for real values of $\omega$ and $k$.

### How to Use

1. Launch Jupyter Lab or open the project in VS Code with the Jupyter extension.
2. Select `.venv` as your notebook kernel.
3. Run the cells to see:
   - LaTeX-formatted transfer function decomposition.
   - Numerical verification of valid/invalid breakaway points.
   - Step-by-step imaginary axis crossings.
4. Modify the transfer function in the first cell to analyze different systems. Enter the coefficients of the numerator and denominator of the open-loop transfer function as lists. You must enter all coefficients (even for terms with 0 coefficients). E.g.:

   ```python
   num = [2, -4]  # 2s - 4
   denum = [1, 2, 2]  # s^2 + 2s + 2
   ```

### Visualization

Below is a generated plot of the root locus for the transfer function $G(s) = \frac{2s - 4}{s^2 + 2s + 2}$:

![Root Locus Plot](assets/sample.png)

---

## Interactive PID Controller Designer (`control_system_designer.ipynb`)

An interactive dashboard for designing PID controllers for linear time-invariant (LTI) systems. By adjusting the $K_p$, $K_i$, and $K_d$ gains via sliders or direct input, you can instantly observe the effects on the system's root locus, step response, and Bode plot.

### Features

- **Real-time tuning:** Drag sliders or type exact values to adjust PID gains ($K_p$, $K_i$, $K_d$).
- **Performance evaluation:** Displays overshoot and settling time with pass/fail indicators against user-defined specifications.
- **Three synchronized plots:** Root locus with design boundaries, step response with specification overlays, and open-loop Bode magnitude diagram.
- **Flexible:** Works with any plant transfer function $G(s)$ — just provide numerator and denominator coefficients.

### How to Use

1. Open [control_system_designer.ipynb](control_system_designer.ipynb) in Jupyter or VS Code.
2. Select `.venv` as your notebook kernel.
3. Run all cells from the top.
4. Use the sliders or type values in the text boxes to adjust the PID gains.
5. To analyze a different plant, modify the `num` and `den` lists in the plant definition cell. E.g.:

   ```python
   num = [10]
   den = [1, 6, 11, 6]  # s^3 + 6s^2 + 11s + 6
   ```

---

## Requirements
https://www.mathworks.com/help/control/index.html
The project requires **Python >= 3.12**.

### Dependencies
All required packages are managed in `pyproject.toml`:

| Dependency | Purpose |
| :--- | :--- |
| `control` | Control systems library (transfer functions, root locus) |
| `numpy` | Numerical calculations, polynomials, and roots |
| `matplotlib` | High-quality plotting and visualization |
| `sympy` | Symbolic mathematics (derivative, equation solving) |
| `ipykernel` | Jupyter Notebook kernel support |
| `ipywidgets` | Interactive widgets (sliders, text inputs, layout) |

---

## References

1. **Textbooks:**
   - Benvenuti, L., De Santis, A., & Farina, L. *[Sistemi dinamici. Modellistica, analisi e controllo](https://search.worldcat.org/title/849463082)*. McGraw-Hill.
   - Bolzern, P., Scattolini, R., & Schiavoni, N. *[Fondamenti di controlli automatici](https://search.worldcat.org/title/918981992)*. McGraw-Hill Education.
2. **Online Resources:**
   - [Python Control Systems Library Documentation](https://python-control.readthedocs.io/)
   - [MATLAB Control System Toolbox Documentation](https://www.mathworks.com/help/control/index.html)
   - [Wikipedia: Root Locus](https://en.wikipedia.org/wiki/Root_locus)
   - [SymPy Documentation](https://docs.sympy.org/)