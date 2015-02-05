---
title: Quantum Entanglement in Plain-ish English
subtitle: With many simplications and bad assumptions
permalink: quantum-entanglement
---

This morning I was challenged to explain quantum entanglement. Normally I'd blow this off, but I'm sick and unemployed and this is interesting, so I'm taking it on.

Quantum Mechanics is a really interesting field and it has the fun property of sounding really intense and magical. If I wave away even a bit of the voodoo, I'll feel good about it.

## Working From Last Principles

> Where did we get that (equation) from? Nowhere. It is not possible to derive it from anything you know. It came out of the mind of Schrödinger.
>
> — Richard Feynman

If you want a great rockstar scientist story, here you go. Schrödinger was a scientist who came up with the fundamental equation for how we describe particles while ostensibly cheating on his wife at some chalet. This equation is what we've used to understand quantum mechanics as a whole, and it requires some background. Let's work by analogy.

Imagine you're Newton. You want to figure out the relationship between an object's mass and its velocity as it falls. You'd probably get a bunch of objects of known mass, drop them from a known height a few thousand times, and then chart the results. You'd find that all the graphs look very similar and they follow some sort of pattern. Once you see the pattern you can figure out what law it follows and express it as an equation. The equation will have some variables and some constants. You might see that the speed doubles as the mass doubles (spoiler: it doesn't). You might see that the speed is always 9.81 times the mass. Your equation has to have a mass variable, and a constant of 9.81 in it, then. If you have a constant that doesn't have a name yet, you give it a name. So far so good. Working from first principles!

Okay, now imagine you're measuring something really complicated. The graphs look really complex and have many, many dependencies. You work really hard and figure out that there _is_ a pattern, though! Your formalized equation has like twelve different constants and another dozen variables. Still workable.

Now, imagine that instead of an equation that gives you a number it's an equation that gives you another equation. Say you want to find the speed of a particle, but the only equation you know doesn't give you the speed, it just gives you another equation that you have to solve to get the actual speed. So, it's a two-step process. Okay.

For the final trick, imagine you're working in reverse. Imagine that someone out there gives you this wacky-looking equation that you solve to get more equations and that equation gives you some numbers. You don't know what the fuck the numbers are at all, but they're _something_ and now we need to work in reverse and run experiments to figure out what in the hell is happening, even. Welcome to quantum mechanics!

Erwin Schrödinger came up with the wave equation. The wave equation describes something about a particle. We're unraveling it and starting to learn what all the constants and the variables are. We're running experiments to verify our findings. Slowly, we're figuring out what it all means. Most importantly, though, we're learning that this magical equation is right.

We have Schrödinger's equation. When we solve it for a particle we get another equation that describes the particle. This is called the particle's wavefunction. The wavefunction has some variables and some constants in it, and even though we might not be 100% sure of how exactly they work, we are making conclusions. We started with math. We looked at the equations and we saw that if the equations are right, this has consequences for how the world works. We ran experiments and found out that those consequences are real.

## Unraveling The Wavefunction

So, what did we learn from this equation?

1. Energy is quantized. Let's think about that by analogy again. A piece of metal looks like it's continuous. We can cut it in half and then again and again into smaller and smaller pieces and we'll just have metal, right? Well no, because it's made of atoms. An atom is a single, _discrete_ thing. You can point to it using a microscope. A chunk of metal is not actually continuous, it's made of blocks, units. Energy, turns out, is the same. An electron can't have any arbitrary amount of energy. Its energy can only be one of a _set_ of possible energies, a quanta. That's what quantum means, that energy is not continuous, but discrete. Experiments confirm this a thousand times over.
2. You cannot solve for the momentum and the position of a particle at the same time. Due to the way the math works, you can only know one with certainty, and never both. This is Heisenberg's Spooky Uncertainty Principle you might have heard about. You can't know both where a particle is and where it's going at the same time.
3. Some variables can only be determined when others are determined first. You know the whole dead cat in a box experiment? There is an intermediate step in wavefunction solving in which you're presented with a set of possible partial solutions and all of them are equally likely. You then proceed with solving and arrive at the Right One. If you like thought experiments you might say that a particle exists in all of those states at the same time, and solving for the right state _forces_ (or collapses, as it were) it into onto a single one. You might even say that measuring the particle affects the particle. To me, this smells like warping the English language to sensationalize a mathematical concept, but whatever.
4. In some systems, the wave functions of the particles depend on each other. So far we've been talking about a single particle, but what if you have a bunch all in the same place? You start trying to solve for the wavefunctions of them all and you see that they all depend on each other. For example, imagine you're trying to solve for particles A and B which are in the same system. You might learn from the equations that if particle A has the property X = -1, by definition particle B _has_ to have property X = +1. The equations depend on each other in a very specific way. If you solve X for A, you'll get the answer for B. That's basically the idea of quantum entanglement. The particles are dependent and are therefore "entangled". Sensational!

## Implications

What are the implications of this, then? Here is the basic premise of what we've talked about:

- when we try to solve for two particles at once, the solutions are mutually-dependent
- whenever we're solving for a particle we choose a single correct solution out of a set

So. We take two particles that we're solving for and move them across a room from each other. We solve for A. We learn something about B. Cool. What if they're across the whole universe from each other? We solve for A, and we learn something about B. Except ... B is a million light-years away. We just got information about something infinitely far and we did it infinitely fast. Did information about this particle just travel to us faster than light?

Einstein called this "spooky action at a distance."

Here's the thing though: We didn't actually transmit anything. We can't change properties of particle A to change the properties of particle B in a useful way. If we change particle A and solve the equations again, as you remember, the answer we get is random from a set of potential answers. The information at B, then, is also random. We're "transmitting" noise at this point, with no actual influence from us. This is all at the thought experiment stage, too, there is a whole set of other physical complications that make the whole thing really difficult.

This phenomenon, while cool, is not actionable.

***

### References
- [Michio Kaku: Why Einstein Gets the Last Laugh](https://www.youtube.com/watch?v=QErwOK3S5IE)
