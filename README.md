# Wave pendulums

[The wave pendulum](https://sciencedemonstrations.fas.harvard.edu/presentations/pendulum-waves) was first constructed by the philosopher and physicist [Ernst Mach](https://plato.stanford.edu/entries/ernst-mach/).

The idea is quite simple. The period of oscillation for a pendulum is approximately `2 * sqrt(length)`, where the period is the number of seconds required for a full swing of the pendulum.

Imagine stringing multiple pendulums of different lengths from the same anchor. A longer pendulum will make fewer cycles in a given time period than a shorter pendulum. If P1 is the longer and P2 the shorter, P2 will make `sqrt(P2 length) / sqrt(P1 length)` more cycles per time interval. If we want a pendulum to make, say, X cycles in a given time interval, we can solve for the length. That length will be:

length = time interval * (1 / 2 * time interval) ^ 2

By building pendulums with lengths that increase a increasing integral fractions of the number of cycles between sync-ups, you create a system that will swing in sync every `number of cycles` swings and, in between, will swing at proportionally faster rates as the pendulums decrease in size.

For example, for 8 cycles and 8 pendulums and a max length of 1000, we have the following lengths:

```
1000
790
640
529
444
379
327
284

1000 * (8 / 8) ^ 2

1000 * (8 / 9) ^ 2 // cycles 1 more time per interval than previous

...

1000 * (8 / 15) ^ 2 // cycles 8 more times per interval than previous
```

The effect is that the pendulums start out in sync. However, they quickly fall out of sync, since the shorter pendulums have a shorter period, and therefore they complete more oscillations in a given time interval. The wave pendulum has the lengths chosen such that the pendulum will periodically sync back up: in this case, after `number of cycles` swings have occurred.

The wave nature of the system emerges from the fact that the motion of the pendulums in the X-Y plane appears to create a wave in the Z plane. This phenomenon is known as a [transverse wave](https://en.wikipedia.org/wiki/Transverse_wave), a wave in which the propagation occurs perpendicular to the direction of energy transfer. One common example of a transverse wave is light.

## simulating the system

With the help of [https://burakkanber.com/blog/physics-in-javascript-rigid-bodies-part-1-pendulum-clock/](https://burakkanber.com/blog/physics-in-javascript-rigid-bodies-part-1-pendulum-clock/) to simulate the physical system using [Verlet integration](https://en.wikipedia.org/wiki/Verlet_integration#Velocity_Verlet), it is trivial to create a simulation using HTML5 canvas to visualize different sorts of wave situations. One can vary the number of pendulums and the number of cycles that defines a period in which the pendulums will find themselves back in sync. If you were to count a single pendulum from the start, you'll notice that it goes through exactly this number of cycles before the system comes back into sync as it began originally.