# Nicolas Gisin 2011 11 02 on QKD Quantum Key Distribution

## Nonrealism
There is apparently a quantum channel between Lausanne and Geneva, he says it's
in use by banks or maybe just that the banks are interested -- dubious?.

The core idea: Alice and Bob can share a state Ψ which cannot be described 
separately. It's simple quantum nonlocality, we've known about this forever.

Maybe nonlocality is due to us not knowing enough about the details? 

    "Because when I was 6 months old, I learned the hard way that in order to 
    interact with an object I had either to crawl to it or throw something at 
    it."

But no -- quantum nonlocality is real, it can make a difference.

Non-realism, quant-ph/0901.4255

There is a basic vocabulary we need to establish here. Alice and Bob can both
have two independent free choices, which we call x and y respectively. (When
there is a third person Carol, she makes choice z). We can assume that these 
are single bit choices, yes/no, 0 or 1. They feed this into local devices which
produce another set of single bits which we will call a and b. (and later c).
And the (local/nonlocal) hidden variables take the name λ.  

Now, given some assumptions of locality, free choice, and λ-independence of x 
and y (? did he mean x and y are free of λ or λ is not disturbed by x and y?) 
you can already derive the Bell inequalities, and it's not sufficient that we 
"just don't know" some local hidden variables.  

Conclusion: All future theories will **have to** be nonlocal. It's just an
observed fact!

## How Nonrealism Applies to Crypto
Suppose we want to forget about Quantum Physics and we simply know that we're
going to violate the Bell inequalities. We have to make an assumption: that 
Alice's room has no windows. (Otherwise: trivially insecure.) So we assume that
Alice exists in a safe location. Alice opens a door, coordinates these "black 
box" devices with Bob, and then she has to make her decision x and get back 
some results. Alice and Bob both make measurements.

They can publicly derive P(a b | x y), and check whether that violates a Bell
inequality. If it does, then it "contains secrecy" somewhere. And they can use
this to get some sort of shared crypto key that is "hidden" in these 
correlations.

Entanglement is just one resource; any violation of Bell inequalities is a 
resource for crypto. (? are there others ?) The point is, this is device-
independent, Alice and Bob can treat the details as a black box.

In quantum mechanics this looks like:

    ρ entangled ⇔ ρ is not separable ⇔ ρ ≠ Σⁿ ρ₁ⁿ ⊗ ρ₂ⁿ

    P(a b | x y) = Tr{ ρ (M_a^x ⊗ M_b^y) }

You study it a little and then you conclude entanglement. (?)

### Danger of false witnesses

Now suppose M = XXX − XYY − YXX − YYX . Three people have some sort of state 
which can be either X or Y.

If X and Y are the Pauli matrices σ_X and σ_Y then < M > <= 2 for all 
biseparable Ψ_{AB} ⊗ Ψ_C . You measure > 2 and you conclude that it's not 
biseparable and you conclude entanglement.

But now you have a student who is performing this experiment for you, and they
are not perfect at their experimental lineup. They fail to measure along the
correct axis from what's expected by theory. They start to measure < M > > 2
even in cases where no entanglement exists! The "witness" fails to "prove" 
entanglement in the face of certain errors!

So one idea endorsed by the speaker is DIEWs -- entanglement witnesses that are
device-independent and therefore do not make this sort of assumption.
    
    See also: PRL 106 250404 
    The classic DIEW is the Bell Inequality but for more than 2 participants 
    they become different ideas. 

Or you could redefine entanglement witnesses to have bounds which require also
the assumed experimental uncertainty, <M> <= 2 + {some error term}. 

## How crypto changes this idea

We in physics like to ignore certain metaphysical loopholes. One of them is,
"suppose the photons get together and conspire, with local hidden variables,
to make this outcome happen." We just think photons are too simple.

Bell violation can guarantees nonlocality, but now we have to close a 
"detection loophole", one of these metaphysical questions. The idea is that 
photons "refuse to answer the question" that you are posing and become part of
your loss rate, conditional on the choices that you are making, so that they 
can still violate the Bell inequality.

    When you go to crypto, adversaries can use this idea to violate the Bell
    inequalities!

        So if you lose 40% of photons, you can already mount an attack! The 
        adversary acts in that 40% error margin to make you think you've got a
        shared nonlocal secret when instead the attacker knows it. 

Limits on this process: you to have a detection efficiency > 82.8% before you 
can detect that the attacker is pulling this off.

So the Detection Loophole has somehow become a part of Applied Physics now.

## Knowing that the photon is there.

PRL 105 070501, Heralded signal. We are trying to overcome transmission losses
by checking the presence of a photon without actually absorbing it. Photon 
amplifier idea.

    We run a quantum teleportation protocol to transfer the photon's presence 
    to another system:

        a |00> + b|10> → a |00> + b |01>, schematically.

    Except we don't do that, because one of the mirrors is half-silvered, so 
    that it has non-50/50 transmission and reflection probability:

    
                    o (detector)
                    |/ (50/50 mirror)
        (input) >---/----o (detector)
                   /|
                    |/ (biased mirror)
            |1> >---/-----[ operations ] --->
                   /|
                   |0>

    Such a setup can then give us a r |0> + b t |1>. Again, these represent 
    occupation levels, so we can increase the probability of a photon in the 
    new level while in principle preserving its structure and phase (though
    not to 100%)

We can't get 100% but we might be able to cross 82.8%. All of the steps for 
this sort of approach have been demonstrated in experiment but so far they have
not been good enough to really make a useful device.

## And how far distance can we go with quantum crypto?

You cannot go forever, 250 km is a sort of limit. Even with perfect detectors, 
ideal 10GHz single photon sources, and still with the best optical fibers, 
1 qubit over 1000 km will take centuries. There is just too much loss in the
individual photons. Even over 15 km, you lose half the photons. I mean, that's
very good -- 15 km and it's only like you're looking through sunglasses -- but
that's not good enough for going around the world. ^_^

So we need quantum "repeaters." A entangles with B, B entangles with C, and 
then B does something to teleport the A-B shared qubit to C. 

But sometimes a photon gets lost, and you get a problem if BC is not ready when
the AB qubit comes in, and AB's qubit needs to be stored by B in a quantum 
memory. It needs to be long-term and efficient.

They produce pairs of entangled photons with nonlinear crystals, store one photons and send the other one. There is a detector which tells you that the transmitted photons are transmitted but doesn't tell you which one it was, and that can entangle two of those systems.

This has a low success probability, so we have to generate a bunch of them in a given time. This is the "repeater." 

Crystal doped with rare-earth ions, some sort of broadening of absorption with respect to frequency. Absorption causes one of the ions to be in an excited state. Lots of phases, then dephasing = lost of decoherence, and then it gets emitted and my photon gets lost. :<

We shape the system so that there are sharp frequency peaks, You get dephasing and then rephasing, with re-emission in a convenient direction and after a convenient time. 

    See also PRA 79 052329

This isn't quantum memory, but quantum delay time. We have to decide when the photon comes out! So we have three states. |ground>, |excited>, |storage>. Efficiency of quantum memory right now is actually only 20%. Can store 10-20 microseconds, limited by spin dephasing and stuff like that. 

But does this all preserve coherence?!

    PRL 98 113601

With two spectral "gratings" we can read out the qubit twice, and we can send in two pulses. Make the second echo of one pulse = first echo of the other pulse, that lets you probe for an interference fringe.

Then you try to demonstrate entanglement, Nature 469 508-511. 

Have also entangled two crystals arXiv: 1109:0440? 

Bit rate of 1st transatlantic telegram, "The queen desires to congratulate..." 95 words, took 17 hours. 1 letter took 2 minutes, and English has ~2 bits per letter. The delay was due to the capacitance of the copper cables. 

We want quantum nonlocality in a vast quantum network, A entangled with B entangled with C entangled with both A and D and so on.

N nodes, \psi^{\otimes N}

Tempting to assume that "hidden variables" are properties of graph edges, no one global variable. 

P(a b c|x y z) "bi-locality", "bilocal" when = P(a | x, λ₁) * P(b | y, λ₁, λ₂) * P(c | z, λ₂)

λ's are the nonlocal hidden variables. The idea is that we need to invent them to account for the conditional probability distributions.

Independent locality when the sources EPR1 and EPR2 are independent -- as natural as Bell's locality assumption and is implicitly assumed.

All of this is PRL 104 170401-1/4 and other forthcoming papers by Branciard, Rosset, NG, and Pironio.

Set of bilocal probabilities is not a convex set. Choices between alice and Carol might be

    a = c = 0 is bilocal. a = c = 1 is also bilocal. 

But a = c is *not* bilocal. They can't coordinate if A -- B -- C.

Critical threshold that you have to achieve is 1/2. So if I want to prove that I really have something quantum the visibility can be 50%, not 71%. (???)

So Experimental DI QKD have been realized and are curious. we have multimode quantum memories for quantum repeaters, bilocality we can find ways to analyze general topologies.

QUESTIONS

    Can we understand nonlocality better?
    We have to accept it! It's a fact of nature and we need to invent a way to talk about it! Alice isn't crawling or throwing. We need to invent a story and a good explanation, yes. But I don't have one. :D

    Great quote from Yuli, "I think you're still assuming causality here because if you assume that information is leaked before it is created..."

    How far can this hypothetical student's incompetence run?
    Basically there is a limit on Bell violations due to systematic mistakes, but there can be even worse violations if your measurement axis over here depends on the measurement result over there. 