# Computational Electrophysiology: Action Potentials, Waves, and Neural Computation - Notebooks

Companion Jupyter notebooks for the book *Computational Electrophysiology*
(R. Weber dos Santos, B. M. Rocha, and N. Z. Monteiro — UFJF). Each notebook
reproduces the simulations and figures of one chapter, using the compact,
delay-based cellular model developed in the text and its extension to coupled
cells, tissue, and small neural circuits.

The models are deliberately simple: membrane capacitance, voltage-dependent
conductances with distinct response delays ($\tau_m$, $\tau_h$, $\tau_K$), and
electrical or synaptic coupling. This keeps the code short enough to read
alongside the equations while still reproducing the behavior discussed in each
chapter.

## Contents

| Notebook | Chapter | Topic |
|---|---|---|
| `chap2.ipynb` | 2 | The action potential |
| `chap3.ipynb` | 3 | Propagation and waves in excitable tissue |
| `chap4.ipynb` | 4 | Neural networks |

Each notebook saves its figures as `Figure N.png` and `Figure N.pdf` in the
current working directory.

---

### `chap2.ipynb` — The action potential

The single-cell, delay-based action-potential model. Starting from the membrane
current balance and the resting potential, voltage-gated sodium and potassium
conductances are built with characteristic delays, reproducing the chapter
figures:

- the action potential and its phases (Fig. 1.1);
- sodium and potassium conductance responses (Figs. 1.9, 1.11);
- sub- and supra-threshold stimulation and the sigmoidal upstroke (Figs. 1.12, 1.13);
- the response to a second stimulus and the two contributions to refractoriness
  (Figs. 1.14, 1.15);
- the numerical strength–interval curve (Fig. 1.16).

### `chap3.ipynb` — Propagation and waves in excitable tissue

Couples the cellular model in space, from a 1D cable (monodomain) to 2D and 3D
tissue:

- action-potential propagation along a 1D cable (Fig. 2.2);
- conduction velocity vs. tissue conductivity and sodium-conductance scale
  (Figs. 2.6, 2.7);
- effect of the potassium scale on APD and wavelength (Fig. 2.8);
- 2D wavefront snapshots (Fig. 2.9);
- the S1–S2 vulnerable window and three propagation outcomes (Fig. 2.10);
- spiral-wave rotation (Fig. 2.11) and a bent 3D scroll wave (Fig. 2.12).

### `chap4.ipynb` — Neural networks

The chemical-synapse branch of the same cellular model, up to the artificial-neuron
reduction:

- constant-stimulus voltage traces and repetitive firing (Fig. 3.1 onward);
- a chemical-synapse model with excitatory/inhibitory action;
- a three-neuron circuit and its firing-frequency maps;
- a single artificial-neuron surrogate fitted to the circuit's input–output map,
  with a sensitivity (Sobol) analysis.

---

## Requirements

Python 3.9 or newer. Install the dependencies with:

```bash
pip install numpy scipy matplotlib pandas numba scikit-image
```

Per-notebook minimum:

| Notebook | Required | Optional |
|---|---|---|
| `chap2.ipynb` | `numpy`, `matplotlib` | — |
| `chap3.ipynb` | `numpy`, `matplotlib`, `numba`, `scikit-image` | — |
| `chap4.ipynb` | `numpy`, `scipy`, `matplotlib`, `pandas` | `numba` (falls back to pure Python if absent) |

> **numba** compiles the tissue (`chap3`) and frequency-map (`chap4`) loops and
> makes the larger sweeps practical. In `chap4` it is optional: a pure-Python
> fallback runs the same equations, only slower. `chap3` uses `numba` and
> `scikit-image` (for `find_contours` / `marching_cubes`) directly.

## Citation

If you use these notebooks, please cite the book.
