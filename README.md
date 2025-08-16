# Estimating the Volume of an n-sphere using Monte carlo methods

The main aim of this project was to quickly form a Monte carlo estimator for the volume of an n-sphere. This is something I had done during my degree in my mandatory computational physics course. However, I had lost the code. So, I thought it would be a good exercise to code another one quickly in Jupyter. In this read-me I'll also go over the theory behind the code. 

The theory is rather simple. We take $N$ random vectors $\boldsymbol{X}$ which are uniformly distributed within the interval $[-1,1]^n$, where $n$ is the dimension of the cube. We then find all the points that lay inside our sphere by demanding: 

$$S^n_{\text{estimate}} = \set{ X = (X_1, \cdots, X_n) | \sum_{i = 1}^n X^2_i \leq 1 }$$

The fraction of vectors that satisfy this gives the probability that a uniform random vector lies within the $n$-sphere. To find the volume of the sphere we simply compute the volume of the $n$-cube;

$$C^n_{\text{Vol}} =  2^n$$ .

Which we then multiply with the number of vectors that lay within the n-sphere,

$$
\text{Vol}(S^n) = C^n_{\text{Vol}} \cdot \frac{\left| S^n_{\text{estimate}} \right|}{N}
$$


where $|\cdot|$ represents the cardinality of the set. The exact analytic volume on the other hand is given by:

$$
V(S^n) = \frac{\pi^{n/2}}{\Gamma\left( \frac{n}{2} + 1 \right)}
$$

where $\Gamma$ is the Gamma function.

---

## Error Bars

The standard deviation of the Monte Carlo estimate is computed using:

$$
\sigma = 2^n \cdot \sqrt{ \frac{p(1-p)}{N} }
$$

where $p$ is the fraction of points inside the sphere. This formula can be found via the standard variance of a Bernoulli random vector. 


---

## Plot

The plot shows:
- **Blue points**: Monte Carlo estimates with error bars
- **Orange points**: Exact analytic volume

