# RGB-LAB

So it turns out that comparing the difference between RGB colors is actually a really shitty way to determine color distance. There are colors which have similar RGB representations while being perceptually distant, and perceptually similar colors with vastly different representations.

So I decided to run a series of large scale double-blind (heh) experiments on human perception, analyzing the output with a dizzying array of statistical techniques and-- oh wait, no I didn't, because scientists have gotten that all figured out since the late '70s.

## rgb2lab([r, g, b])

The first function is rgb2lab, it does kind of exactly what you'd expect, making the usual sRGB assumptions.

## lab2rgb([l, a, b])

The second one is lab2rgb, and it's kind of the inverse of lab2rgb. That is, in an ideal world, you could expect that `lab2rgb(rgb2lab([a, b, c]))` would return `[a, b, c]`, which probably won't be the case due to quirks of floating point arithmetic. 

But if you feed functions values which lie squarely within the acceptable range (R, G, B between 0 and 255), things should be okay.

## deltaE([labA], [labB])

This function calculates DeltaE, the perceptual color distance between any two random colors in the L*a*b* space.
