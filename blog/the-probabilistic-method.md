---
layout: post
author: jesse
title: The probabilistic method
---

# The Probabilistic Method

Consider the following questions:

You drop 10 infinitely small m&m's in the plane and they all land in a random place. Is it possible to cover all of these m&m's with disks of radius 1, such that the disks do not overlap?

One can arrange the disk in a hexagonal circle packing on the plane. For a fixed configuration of m&m's, this pattern of disks can now be placed in a random way on the plane.  The fraction of the plane that is covered by the disks is $$\frac{\pi \sqrt{3}}{6} \approx 0.907$$. Therefore the probability that an arbitrary m&m is covered by one of the disks is also approximately $$0.907$$. By linearity of expectation, the expected total number of m&m covered by the disks following this procedure is approximately $$9.07$$. Since this is an average, this implies that there has to be at least one way of placing the circle packing, such that the number of covered m&m's is greater or equal to $$9.07$$. Since every outcome of the number of covered m&m's is an integer, we conclude that there exists a placement for which all m&m's are covered. 

<!-- Include simpler exercise with 2 point on the the line, and a dashed line with 0.6 filled and 0.4 empty -->
