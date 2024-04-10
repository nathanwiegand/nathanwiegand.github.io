## Softmax explorations cont'd.
### (In which I get excited, then feel dumb about math)

Today I was thinking about softmax again. This time, I was wondering what would happen if you scaled-up one of its terms. How would the other terms go down? Specifically, I was wondering what would happen to the other terms if you averaged the max term with $1$.

Let's start here.
$$
\text{softmax}(z)_i = \frac{e^{z_i}}{\sum_{j=1}^{N} e^{z_j}}
$$

Now, let's assume we scale up the $z_1$ case.
$$
\text{softmax}(z)_1 = \frac{e^{z_1 + c}}{e^{z_1+c}+\sum_{j=2}^{N} e^{z_j}}
$$
That denominator is just pulling out the $e^{z_1}$ term and scaling it.

That's just:
$$
\text{softmax}(z)_1 = \frac{e^ce^{z_1}}{e^ce^{z_1}+\sum_{j=2}^{N} e^{z_j}}
$$

Ok, now let's do a little bit of rewriting. 

Let,
$$
\begin{aligned}
A &= e^{z_1} \\
B &= \sum_{j=2}^{N} e^{z_j}  \\
C &= e^c \\
p &= \text{softmax(.) before scaling} \\
q &= \text{softmax(.) after scaling} \\
\end{aligned}
$$
Then we rewrite the above as 
$$
\begin{aligned}
\text{softmax}(z)_1 &= \frac{e^ce^{z_1}}{e^ce^{z_1}+\sum_{j=2}^{N} e^{z_j}} \\
&= \frac{CA}{CA + B} \\
&= q
\end{aligned}
$$

Now, let's solve for $C$.
$$
\begin{aligned}
q(CA+B) &= CA \\
qCA + qB &= CA \\
qB &= CA - qCA \\
qB &= CA(1-q) \\
\\
C &= \frac{qB}{A(1-q)} \\
 &= \frac{qB}{A(1-q)} \\
 &= \frac{B}{A} \frac{q}{1-q} \\
\\
e^c &= \frac{\sum_{j=2}^{N} e^{z_j} }{ e^{z_1}} \frac{q}{1-q} \\
\end{aligned}
$$

Note, the summation is missing the first term. Let's rewrite so that it's back
$$
\begin{aligned}
e^c &= \frac{-e^{z_1} + \sum_{j=1}^{N} e^{z_j} }{ e^{z_1}} \frac{q}{1-q} \\
&= (\frac{-e^{z_1}}{e^{z_1}}+ \frac{\sum_{j=1}^{N} e^{z_j}}{e^{z_1}})   \frac{q}{1-q} \\
&= (-1 + \frac{1}{p})\frac{q}{1-q} \\
&= \frac{1-p}{p}\frac{q}{1-q}

\end{aligned}
$$

Solving for $c$,
$$
\begin{align}
c &= \ln({\frac{1-p}{p}\frac{q}{1-q}}) \\
 &= \ln{(\frac{1-p}{p})}+\ln{(\frac{q}{1-q})} \\
 &= \ln{(\frac{q}{1-q})} -\ln{(\frac{p}{1-p})} \\
\end{align}
$$

Ok, interesting. We have a way of scaling everything the whole thing by pegging one term. Nice.

But, back to my original goal, I want to find the midpoint between the max term and $1$.

So,
$$
q = \frac{1+p}{2} \\
$$
$$
\begin{align}
c &=\ln{(\frac{\frac{1+p}{2}}{1-\frac{1+p}{2}})} -\ln{(\frac{p}{1-p})}  \\
&= \ln{(\frac{\frac{1+p}{2}}{\frac{1-p}{2}})}  -\ln{(\frac{p}{1-p})}  \\
&= \ln{({\frac{1+p}{1-p}})}  -\ln{(\frac{p}{1-p})}  \\
&= \ln{({\frac{1+p}{p}})}
\end{align}
$$

Ok, at this point I'm feeling pretty damn clever. That was some good algebra I just scratched out.

But then I thought, "wonder what happens if you just _average_ each term of the $z$ vector with the vector $[1, 0, ... 0]$" (assuming that $z_1$ is the maximum value).

Well, I put it all in a spreadsheet, and know what? IT'S EXACTLY THE SAME!

All that algebra, derived an exactly formula for $c$... and I could have just averaged each term!

Oh well, I'm still happy with the result. And I'm happy that I've demonstrated that the thing I thought was a heuristic (averaging terms) is actually exact.

Yes, my hobbies are awesome and you're jealous.