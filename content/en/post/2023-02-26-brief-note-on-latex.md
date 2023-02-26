---
title: "A Brief Note on Latex"
date: 2023-02-26T11:41:03+08:00
tags: ["LaTeX", "Math"]
---

## Line break
```
$$
a \pm b \newline
a \mp b
$$
```
$$
a \pm b \newline
a\mp b
$$

## Arrow with annotation
```
$$
a \xrightarrow{s} b \newline
C {\xrightleftharpoons[\beta(V)]{\mkern10mu\alpha(V)\mkern10mu}} O
$$
```
$$
a \xrightarrow{s} b \newline
C {\xrightleftharpoons[\beta(V)]{\mkern10mu\alpha(V)\mkern10mu}} O
$$

## Arithmetic Basics
```
$$
a \cdot b \newline
a \times b \newline
a \div b
$$
```
$$
a \cdot b \newline
a \times b \newline
a \div b
$$


## Tangent half-angle formula
```
$$
\sin x=\sin(2\cdot \frac{x}{2})=2\cdot\sin\frac{x}{2}\cdot\cos\frac{x}{2}=\frac{[2\cdot\sin\frac{x}{2}\cdot\cos\frac{x}{2}]}{[\cos^{2}\frac{x}{2}+\sin^{2}\frac{x}{2}]}=\frac{2\tan\frac{x}{2}}{1+\tan^{2}\frac{x}{2}}
\newline
\cos x=\cos(2\cdot \frac{x}{2})=\cos^{2}\frac{x}{2}-\sin^{2}\frac{x}{2}=\frac{[\cos^{2}\frac{x}{2}-\sin^{2}\frac{x}{2}]}{[\cos^{2}\frac{x}{2}+\sin^{2}\frac{x}{2}]}=\frac{1-\tan^{2}\frac{x}{2}}{1+\tan^{2}\frac{x}{2}}
\newline
\tan x=\frac{2\tan\frac{x}{2}}{1-\tan^{2}\frac{x}{2}}
$$
```
$$
\sin x=\sin(2\cdot \frac{x}{2})=2\cdot\sin\frac{x}{2}\cdot\cos\frac{x}{2}=\frac{[2\cdot\sin\frac{x}{2}\cdot\cos\frac{x}{2}]}{[\cos^{2}\frac{x}{2}+\sin^{2}\frac{x}{2}]}=\frac{2\tan\frac{x}{2}}{1+\tan^{2}\frac{x}{2}}
\newline
\cos x=\cos(2\cdot \frac{x}{2})=\cos^{2}\frac{x}{2}-\sin^{2}\frac{x}{2}=\frac{[\cos^{2}\frac{x}{2}-\sin^{2}\frac{x}{2}]}{[\cos^{2}\frac{x}{2}+\sin^{2}\frac{x}{2}]}=\frac{1-\tan^{2}\frac{x}{2}}{1+\tan^{2}\frac{x}{2}}
\newline
\tan x=\frac{2\tan\frac{x}{2}}{1-\tan^{2}\frac{x}{2}}
$$

## Higher Order Derivatives
```
$$
f^{\prime\prime}=\frac{d^2 f}{dx^2}
$$
```
$$
f^{\prime\prime}=\frac{d^2 f}{dx^2}
$$

## L'Hôpital's rule
```
$$
\lim_{x\to 0}\frac{\sin x}{x}\stackrel{\text{H}}{=} \lim_{x\to 0}\frac{\cos x}{1}=1
$$
```
$$
\lim_{x\to 0}\frac{\sin x}{x}\stackrel{\text{H}}{=} \lim_{x\to 0}\frac{\cos x}{1}=1
$$

## Integral
```
$$
\int_{a}^{b} x^2 dx
$$
```
$$
\int_{a}^{b} x^2 dx
$$

## Multiple integral
```
$$
\iint_D f(x,y) dxdy
$$
```
$$
\iint_D f(x,y) dxdy
$$