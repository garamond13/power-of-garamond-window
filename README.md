# Power of garamond window

In the research Finding the best methods for image scaling (https://github.com/garamond13/Finding-the-best-methods-for-image-scaling) I presented the garamond window.

w(x) = `1.0 - pow(abs(x) / R, n)`, where n is in the range (0.0, +inf] and R is the kernel radius \
at n=1.0, w(x)=linear window \
at n=2.0, w(x)=welch window \
as n aproaches +inf, w(x)=box window

Here, I will present the power of garamond window with one extra free parameter (m). 

w(x) = `x < R : pow(1.0 - pow(abs(x) / R, n), m) : 0.0`, where n and m are in the range [0.0, +inf] and R is the kernel radius \
at m=1.0, w(x)=garamond window \
at m=0.0, w(x)=box window \
at n=1.0 m=1.0, w(x)=linear window \
at n=2.0 m=1.0, w(x)=welch window \
as n aproaches +inf and m<=1.0, w(x)=box window

Similarly to the generalized normal window (gnw) (https://ieeexplore.ieee.org/document/6638833) and the said window (https://www.hpl.hp.com/techreports/2007/HPL-2007-179.pdf), the power of garamond window can approximate other windows. In contrast to the gnw and the said window, approxiations can be scaled to any radius. Here, I will show the test results of approximating some windows using the same settings for all kernels (base=sinc, kernel-blur=1.0, kernel-radius=5.0, antiringing=0.0, light=gamma). The test image, 960x540 will be upscaled to 1920x1080. The table below shows mesured differences in psnr (dB) between a native window and its power of garamond approximation at some (n) and (m).

| approximation | psnr |
| --- | --- |
| (lanczos) n=1.861 m=1.384 | 57.843 |
| (hann) n=1.942 m=2.277 | 61.777 |
| (cosine) n=1.906 m=1.106 | 60.0923 |
| (blackman a=0.16) n=1.879 m=3.366 | 60.4385 |
