Julia Meyer, Phase Transitions in Quantum Wires (2011-06-15)

Why quantum wires?
*   In 1-D, particles "have to collide". Instead of a Fermi liquid with 
    quasifermions you get Tomonaga-Luttinger liquids with collective *boson* 
    excitations.
*   With a linearized spectrum, you get a harmonic (quadratic) Hamiltonian in
    terms of these boson fields.
*   Wigner crystal idea: --wwww--o---wwww-- (springs). But this description 
    does not require the tight bindings seen in this model.
    *   So is this description good enough? It *is* a low-energy approximation
        with linear dispersion. How can we break this? We can use a "spin-
        incoherent" and "nonlinear" Luttinger liquid description.

So we go beyond 1D with 1D geometries. You still have 1D conductance 
quantization, G = n * 2e²/h, this is not changed by interactions. You interpret
it as "new channels", and there is a transition from 1D to quasi1D.

*   In a Wigner picture for Quasi1D you see electrons take diagonal paths like
    /\/\/\/\ between the boundaries. Particles repel into barrier.

Then there are sub-band transitions in the weak interaction regime. You start
with a 2DEG and parabolic confinement and screened Coulomb interactions. 
Quantized into the parabola, there is some sort of x-direction behavior which
remains. These are the bands. Interactions can exist in-band or cross-band.

*   Spin interactions could open up an energy gap, or otherwise you get a 
    Luttinger liquid.
*   2nd oscillator can be set so that the level is barely filled, which means
    there is no left- vs right-mover distinction. That creates a strong in-band
    interaction due to Pauli exclusion.
*   cross-band interactions include pairwise tunneling and density-based 
    scattering
*   A linear spectrum will give log divergences, a parabolic spectrum will give
    square root divergences.
*   At very high chemical potentials, you can get coupled Luttinger liquids. 
    This happens after a characteristi energy in the parabolic spectrum E_p ,
    the "F regime."
*   In E-regime, we can try renormalization. So we focus on μ < 0, the C and D
    regimes:

    \  \    |F   /  /
     \  \   |   /  /
      \  \  |G /  /
       \ E`-+-` -/---- E_p = m V²
        \   |D  /
    =====\==+==/======
            |C

Immediately interesting questions like what is the C-analogue of dimensions 
getting "frozen out"...?

We do a perturbation theory with a lot of coupling constants. It leads to:

>   in-band 1 :: δx ∝ log( E₀/|ω| )
>   cross-band :: δx ∝ log( E₀/|ω + μₑ| )
>   in-band 2 :: δx ∝ √( m/(ω + 2 μₑ) )

But in-band 2 doesn't happen now because μ < 0 forces band 2 to be unoccupied.

In C-regime, cross-band interactions just die out as in-band 1 interactions 
cause an orthogonality catastrophe, which is just what you would have expected.

D-regime? √( m/(ω + 2 μₑ) ) dominates,  

*   if .. = band 1 and __ = band 2: 

    |  ...      ____      ...  |  ___________  |  ...      ________  |
    |     ...  /    \  ...     |     $   $     |     ...  /   $      |
    |        .*      *.        |     $   $     |        .*    $      |
    |     ...  \____/  ...     |  ___$___$___  |     ...  \___$____  |
    |  ...                ...  |               |  ...                |

*   Some details occur with Green's functions, to make band 2 become a 2DEG
    (impenetrable, too)
*   Renormalization is small, negative. But if the renormalization of the 
    *spin* coupling goes negative, it could open a spin gap. Sadly, this 
    doesn't actually happen in this case.
*   Low-energy physics modified to include "polaron formation" -- modulation of
    band 2 by band 1.
    *   Lifschitz transition of impenetrable polarons.

Now: G-regime? Seems like something interesting should happen. Still to be 
explored.

There is zigzagification as you increase density. There are surprising results
as you keep increasing:

               . .      `.`.`        .   .       ` . ` . ` . `
    .....  →  . . .  →   . .   →   . . . .   →   .   .   .      → (...)
                        . . .     .   .   .       .   .   .  .
      1         2         4          3              4           ← (rows)

Perfect (zigzag) crystal transitions to inhomogeneous charge distribution as a
function of y. How does nature do that? The zigzag pattern must break, defects
must form.

We put x-periodic boundaries on a finite box and minimize energies. We find 
defects emerge as soon as you get to 5 rows, with particles missing from the 
zigzag lattice. 2 regimes in 5 rows: increasing defects, but then a constant
number of them, after a moment:
          |     _____|
          | ,-       | 
    ______|/         | (number of defects vs rows)
    2,3,4 | i     ii | ...?
     rows | 5 rows   | 

A simplified model where you force the zigzag lattice into straight rows will 
miss phase 5i but will have phase 5ii . More complicated situations suggest
that 5i → 5ii is a first-order phase transition.

Can Wigner crystals and multiple rows be observed? Not clearly in conductance,
but there may be a gap in the density of states. 