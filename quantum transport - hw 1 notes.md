# Characteristic functions and cumulants

Characteristic Functions: Λ(φ) = < exp(i φ Z) >

Moments: < Zⁿ > = [ (∂/∂iφ)ⁿ Λ(φ) ] @ φ = 0

Compute the characteristic function for Z = Z₁ + Z₂ = ∫ dz₁ h(z₁, z − z₁).

    Λ₁₊₂(φ) = ∫ dz₁ ∫ dz₂ h(z₁, z₂) exp(i φ (z₁ + z₂)).

If independent this shows: Λ₁₊₂(φ) = Λ₁(φ) Λ₂(φ) because h(z₁, z₂) = h₁(z₁) h₂(z₂).

So that gives us a pseudolinear *cumulant* definition:

    « Zⁿ » = [(∂/∂iφ)ⁿ log Λ(φ) ] @ φ = 0

... because the logarithm guarantees that if variables are independent, their multiplicative characteristic functions turn into additive cumulants. To guarantee pseudolinearity we should also show  « (k Z)ⁿ » = kⁿ « Zⁿ » but this is pretty straightforward: for Z' = k Z, we have Λ'(φ) = < exp(i φ k Z) > = Λ(k φ). So we have by substituting φ = θ / k:

    « (k Z)ⁿ » = [(∂/∂iφ)ⁿ log Λ(k φ) ] @ kφ = 0 
     = kⁿ [(∂/∂iθ)ⁿ log Λ(θ) ] @ θ = 0
     = kⁿ « Zⁿ » 

For small n:

    « Z⁰ » = log Λ(0) = log 1 = 0.
    « Z¹ » = [ 1/Λ(φ) * (∂/∂iφ) Λ(φ) ]₀ = < Z > / Λ(0) = < Z >
    « Z² » = [ 1/Λ(φ) * (∂/∂iφ)² Λ(φ) − 1/Λ²(φ) * ((∂/∂iφ) Λ(φ))² ]₀ 
           = < Z² > − < Z >²
    « Z³ » = < Z³ > − 3 < Z > < Z² >  + 2 < Z >³

The first cumulant will be familiar to you as the mean and the second will be familiar to you as the variance.

# Poisson statistics

Divide the interval (0, T) into subintervals of size dt and let events happen at a rate r: r dt is the probability of an event in that dt. Also denote ζ = r T for some sort of special "expected total number" of events. For one event, we have a simple characteristic function 

    λ(φ) = (1 − r dt) * 1 + r dt exp(i φ)
    λ(φ) = 1 + ζ (dt/T) [exp(i φ) − 1]

Now raise this to the n = T/dt to get the full characteristic function:

    Λ(φ) = [λ(φ)]ⁿ = (1 + ζ/n [exp(i φ) − 1])ⁿ

In the limit as n → ∞ this is actually just:

    Λ(φ) = exp(ζ (exp(i φ) − 1))

    Λ(φ) = exp(-ζ) exp(ζ exp(i φ))

But if you'll let me Taylor-expand the second exp:

    Λ(φ) = exp(-ζ) Σ ζⁿ exp(i n φ) / n!

This is actually seen to be a characteristic function for a random variable N with pdf:

    f(n) = exp(-ζ) ζⁿ / n!

We also have very simple cumulants because log Λ = ζ (exp(i φ) − 1). Every derivative brings out no factor at all, and:

    « Nⁱ » = 0 if i == 0, else ζ

(Of course the zeroth cumulant is 0, as it must be.)

Unfortunately often « N² » / < N > ≠ 1 as this proposes, but is some smaller number. This number is therefore called a "Fano factor", f. Then the real distribution can be described as (f N) because  « (f N)² » / < f N > = f « N² » / < N >.

# Levitov formula.

    log Λ = ∫ 2 τ dE/h Σₐ log{ 
        1 + Tₐ [exp(iφ) − 1] fL (1 − fR) + Tₐ [exp(-iφ) − 1] fR (1 − fL) 
    }

...where fR is the Fermi filling function for the right reservoir and fL is the same for the left reservoir. It means that we count + as left-to-right and − as right-to-left and electrons never go against the voltage, and all channels are independent at all energies. Remember that φ is a characteristic function for some random variable `n`, which in this case represents a number of electrons transported through the junction. Thus we have some nice relations:

    φ ↔ n, n e = q, ne/τ = q/τ = I.

I'm assuming that the first statement has to do with some sort of (n, φ) uncertainty relation like one often sees with superconductors, but I don't really know.

Bracketed part: 

    γₐ(i φ) = 1 + Tₐ [exp(iφ) − 1] fL (1 − fR) + Tₐ [exp(-iφ) − 1] fR (1 − fL)

I include the i φ so that I can represent derivatives as primes:

    γₐ(0) = 1.

    γₐ'(0) = Tₐ fL (1 − fR) − Tₐ fR (1 − fL) = Tₐ (fL − fR)

    γₐ''(0) = Tₐ [fL (1 − fR) + fR (1 − fL)]

Thus our first cumulant is:

    log Λ = 2τ/h ∫ dE Σₐ log γₐ(i φ)(E)
    
    < n > = 2 τ / h ∫ dE Σₐ γₐ' / γₐ = 2 τ / h Σₐ Tₐ ∫ dE (fL − fR)
    
    < I > = n e / τ = 2 e²/h * ΔV * Σₐ Tₐ 

    G = < I > / ΔV = (2 e²/h) Σₐ Tₐ

Thus the sum of the transmission eigenvalues gives the conductance when multiplied by this conductance quantum G₀ = 2 e²/h. Then there is the current noise around this variable, which is:

    « n² » = 2τ/h ∫ dE Σₐ [ γₐ''/γₐ −  (γₐ'/γₐ)² ]
    
    « n² » = 2τ/h ∫ dE Σₐ [ γₐ''/γₐ −  (γₐ'/γₐ)² ]

    « n² » = 2τ/h ∫ dE Σₐ [ Tₐ [fL (1 − fR) + fR (1 − fL)] − Tₐ² (fL − fR)² ]

    « I² » = e²/τ² « n² ».

As might be expected, as we look for longer τ the current gets averaged, having a variance which decreases like 1/τ. It also has a main component depending on the dimensionless conductance Σₐ Tₐ but this noise is dampled slightly by a term proportional to Σₐ Tₐ².

At zero temperature you would have fL fL = fL, fR fR = fR, and if the voltage is higher on the left than on the right, fL fR = fR. This would cause the expression to say:

    « n² » = 2τ/h ∫ dE Σₐ (Tₐ − Tₐ²) (fL − fR) = 2eτ/h Σₐ (Tₐ − Tₐ²) |ΔV|

    « I² » = |G₀ e ΔV /τ| Σₐ (Tₐ − Tₐ²)

This means that the 0-temperature current noise can detect the difference between ten channels open with transmission probability 0.5, and 5 open plus 5 closed channels. The first has current noise; the second does not. 

Another nice limit is to consider the zero-bias noise when fL = fR:

    « n² » = 2τ/h ∫ (kT dα) Σₐ [ 2 Tₐ [f − f²] ]

To work this out, note that:

    f(α) = 1/(1 + exp(α)) = exp(-α/2) / cosh(α/2) 
    1 − f(α) = exp(α) /(1 + exp(α)) = exp(+α/2) / cosh(α/2)
    
Thus:

    f − f² = [cosh(α/2)]⁻² = d/dα [2 tanh(α/2)]

Evaluated from -∞ → ∞ this gives me another factor of 2. Thus we're at:

    « n² » = 16 τ kT / h Σₐ Tₐ
    « I² » = e²/τ² « n² » = 8 G kT / τ

So the zero-bias current noise does not tell us something about these  transmission eigenvalues that we didn't already know from the average current,  but it might be able to tell us a temperature or a time for which the sample has been taken. 