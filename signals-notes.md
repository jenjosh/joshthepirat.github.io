#Signals Notes

[TOC]

## Zero Input Response

For a linear system:

$$
\text{Total Response} = \text{Zero Input Response} + \text{Zero State Response}
$$

### Characteristic Features

The characteristic features of an LTI system are:

- Characteristic Polynomial: 
$$
Q(\lambda)
$$

- Characteristic equation: 
$$
Q(\lambda)=0
$$

- Characteristic roots: 
$$
\text{Roots of: }Q(\lambda)=0 \qquad \lambda_1, \lambda_2,...,\lambda_n
$$

- Characteristic modes: 
$$
e^{\lambda_1 t},e^{\lambda_2 t},...,e^{\lambda_n t}
$$

### Finding $y_0(t)$ for an LTI system

#### Models for electric components 

- The model for a resistor: 
$$
v_r(t)=Ry(t)
$$

- The model for an inductor: 
$$
v_l(t)=L \frac{dy(t)}{\,dt}
$$

- The model for a capacitor: 
$$
v_c(t)=\frac{1}{c} \int_{0}^{t}y(\tau)d\tau
$$

Where $I=y(t)$

#### Method

Where $x(t)$ is the input signal, you must write $x(t)=v_c(t)+v_l(t)+v_r(t)$ for all the impedance components in the circuit.

1. First, differentiate both sides to get the loop equation to get an equation in the form: 
$$
Q(D)y(t)=P(D)x(t)
$$

2. Then solve $Q(\lambda)=0$ to get $\lambda_1, \lambda_2,...,\lambda_n$ to get the zero impulse response (The zero impulse response may be in another form depending on whether the roots are repeated or complex etc.): 
$$
y_0(t)=c_1 e^{\lambda_1 t} + c_2 e^{\lambda_2 t}
$$

3. To find the unknowns, use the initial conditions: 
$$
y_0(0) \qquad y'_0(0)
$$

### Solving Differential Equations

#### 2nd Order homogeneous ODEs

For an equation in the form: 
$$
y''+a(x)y'+b(x)y=0
$$

The characteristic equation is: 
$$
\lambda_1^2+a\lambda_2+b=0
$$

And we need to solve for $\lambda_1$ and $\lambda_2$. The solution will be in different forms depending on $\lambda_1$ and $\lambda_2$.

- For two real roots: 
$$
y=C_1e^{\lambda_1 x}+C_2e^{\lambda_2 x}
$$

- For a repeated root: 
$$
y=C_1e^{\lambda_1 x}+C_2xe^{\lambda_2 x}
$$

- For complex roots: 
$$
y=e^{\alpha x}[C_1 \cos{\beta x}+C_2 \sin{\beta x}]
$$

$$
\alpha = -\frac{a}{2} \qquad \beta = \frac{\sqrt{4b-a^2}}{2}
$$

Use the initial conditions to find $C_1$ and $C_2$.

#### 2nd Order Non-Homgenous ODEs

For an equation in the form: 
$$
y''+a(x)y'+b(x)y=f(x)
$$

The solution will be in the form $y=y_c+y_p$ where $y_c$ is the complementary solution, and $y_p$ is the particular solution. We can use the method of undetermined coefficients which uses trial functions which are different depending on the form of $f(x)$.

- For $f(x)=\cos{nx}$  or $\sin{nx}$, the particular solution is: 
$$
y_p=a\cos{nx}+b\sin{nx}
$$

- For $f(x)=x^n+...$, the particular solution is (a polynomial of order $n$): 
$$
y_p=ax^n+bx^{n-1}+...
$$

- For $f(x)=ne^{mx}$, the particular solution is: 
$$
y_p=ae^{mx}
$$

These can be combined together if needed e.g: 
$$
(x-1)\sin{3x} \Rightarrow y_p=(ax+b)\sin{3x}+(cx+d)\cos{3x}
$$
If it is a sum, then $y_p$ is the sum of each $y_p$ option.



In the case of $y=f(x)$, find $y'$ and $y''$, sub into the original ODE and find $a$ and $b$ etc.

Only solve for the initial conditions after you have found the general case.

For linear $n^{th}$ order ODEs, the $2^{nd}$ order conditions apply for the $n^{th}$ order.

#### Eulers' Equation

For an equation in the form 
$$
x^2 y''+axy'+by=f(x)
$$

You must use the chainrule to rewrite the equation: 
$$
x=e^t \Rightarrow t=\ln{x}
$$

This changes the equation into the form 
$$
y''+(a-1)y'+by=f(e^t)
$$

This which is now a linear ODE so you can use other methods to solve it.

#### Legendre Equation

For an equation in the form: 
$$
(\alpha x+\beta)^2 y''+a(\alpha x+\beta)y'+by=f(x)
$$

- You must set $\alpha x+\beta=e^t$
- This then gets it into the form of Euler's equation.

Both this and Euler's' Equation work for higher order DEs.

#### Power Series Solutions

You must assume that: 
$$
y(x)=y(0)+y'(0)x+\frac{y''(0)}{2!}x^2+...=\sum_{n=0}^{\infty}\frac{y^n(0)}{n!}x^n
$$

You must then use Leibnitz' theorem: 
$$
D^n(fg)=\sum_{i=0}^{n} {n \choose i} f^{(i)}g^{(n-i)}
$$
For each term with $f=a(x)$ and $g=y^n$:

- Add these terms together and set to $=0$.
- Let $x=0$ and write $y^{(n+2)}(0)=$
- You must then find $y^{(2)}$, $y^{(3)}$, $y^{(4)}$, \..., $y^{(7)}$ in terms of $y$ and $y'$ or whatever the initial conditions are expressed as and write it out.




## Impulse Response

Zero-state response assumes that the system is in a rest state, we need to know the impulse response $h(t)$ to derive and understand this response.

**The impulse response $h(t)$ is the systems response when the input is the Dirac function ($x(t)=\delta (t)$) with all initial conditions zero at $t=0^-$.**

Any input $x(t)$ can be broken into a sequence of narrow pulses that produce a system response. If a system is linear and time invariant then the system response to $x(t)$ is the sum of its response to all narrow pulse components.

Given that a system is specified by the following differential equation: 
$$
(D^N+a_1 D^{N-1}+...+a_{N-1}D+a_n)y(t)=(b_{N-M}D^M+b_{N-M+1}D^{M-1}+b_{N-1}D+b_N)x(t)
$$

$$
M \leq N
$$

And remembering that the general equation of a system is:
$$
Q(D)y(t)=P(D)x(t)
$$

It can be shown that the impulse response $h(t)$ is given by: 
$$
h(t)=[P(D)y_n(t)]u(t)
$$

Where $u(t)$ is the unit step function and $y_n (t)$ is the solution to the homogeneous differential equation: 
$$
Q(D)y_n (t)=0
$$

Where: 

- The initial conditions $y_n^{(k)}(0)$ are all $1$. 

- $y_n (t)$ is a linear combination of the characteristic modes of the system: 

$$
y_n (t)=c_1 e^{\lambda_1 t}+c_2 e^{\lambda_2 t}+...+c_N e^{\lambda_N t}
$$

### Zero State Response

The output at the time $t$ due to a shifted impulse with amplitude $a$ at time $\tau$ is $a$ multiplied by a shifted response at $\tau$.

|    $\delta (t)$    |    $h(t)$    |
| :----------------: | :----------: |
|   $a \delta (t)$   |   $ah(t)$    |
| $a\delta (t-\tau)$ | $ah(t-\tau)$ |

For an input: 
$$
x(t)=\sum_{i=1}^{n}a_i \delta (t-\tau_i)\Rightarrow y(t)=\sum_{i=1}^{n} a_i h(t-\tau_i)
$$

If both $x(t)​$ and $h(t)​$ are known then $y(t)​$ can be easily found: 
$$
y(t)=\int_{-\infty}^{\infty}x(\tau )h(t-\tau )\,d \tau
$$

This is known as the convolution interval: 
$$
x_1 (t) \ast x_2 (t) = \int_{-\infty}^{\infty} x_1 (\tau) x_2(t-\tau) \,d \tau
$$



## Convolution

### Output of a system using convolution

The output of a system $y(t)$ is: 
$$
y(t) = x(t) \ast h(t)
$$

Where $x(t)$ is the input to the system, and $h(t)$ is the impulse response of the system.

For a complex input $x(t)=x_a(t)+jx_b(t)$, the output $y(t)$ is: 
$$
y(t) = h(t) \ast [x_a(t)+jx_b(t)] = h(t) \ast x_a(t) +j [h(t) \ast x_b(t)]
$$

The real and imaginary components are considered separately.

#### Demonstrating this graphically

A convolution of two signals can be thought of as the amount of overlap between two signals as they move across each other.

You can demonstrate this graphically by:

- Divide the input $x(\tau)$ into pulses.

- The system response at $t$ is then determined by $x(\tau)$ weighted by $h(t-\tau )$ (i.e. $x(\tau) h(t-\tau )$) for the current pulse, PLUS the contribution from all previous pulses of $x(\tau )$

- The summation of all these weighted inputs is the convolution integral $y(t)=x(t) \ast h(t)$

*Note: Remember the variable of integration is $\tau$ and not $t$.*

### Interconnected Systems

For the parallel connection of two systems with impulse responses $h_1 (t)$ and $h_2 (t)$ the output is: 
$$
y(t)=h_1 (t) \ast x(t) + h_2 (t) \ast x(t)
$$

For the series connection of two systems with impulse responses $h_1 (t)$ and $h_2 (t)$ the output is: 
$$
y(t)=h_1 (t) \ast h_2 (t) \ast x(t)
$$

*Note that the order of connection isn't important*

- Integration: 
$$
\text{If} \quad x(t) \Rightarrow y(t) \quad \text{then} \quad \int_{-\infty}^{t} x(\tau)\,d \tau \Rightarrow\int_{-\infty}^{t} y(\tau)\,d \tau
$$

- Differentiation: 
$$
\text{If} \quad x(t) \Rightarrow y(t) \quad \text{then} \quad \frac{dx(t)}{dt}\Rightarrow \frac{dy(t)}{dt}
$$

Knowing that $\int_{-\infty}^{t}\delta(t) \,d \tau = u(t)$ and that $\delta (t) \Rightarrow h(t)$ we can say that if the input of the system is the step function, (i.e. $x(t)=u(t)=\int_{-\infty}^{t} \delta (\tau) \,d \tau$) then the output of the signal, which is called the step response must be: 
$$
g(t)=\int_{-\infty}^{t} h(\tau )\,d \tau
$$

The total response is:

$$
\text{Total Response} = \text{Zero-Input Response} + \text{Zero-State Response}
$$

$$
\sum_{k=1}^{N} c_k e^{\lambda_k t}+x(t)\ast h(t)
$$

### Natural and Forced Responses

The characteristic modes appear in the zero state response (because of the impact on $h(t)$).

The $e^{-t}$ and $e^{-2t}$ terms are collected together and called the **natural response**, whilst the remaining $e^{-2t}$ which is not a characteristic mode is called the **forced response**.

### Summary of Convolution Properties

|                    $\mathbf{x_1(t)}$                     |     $\mathbf{x_2(t)}$     |                $\mathbf{x_1(t) \ast x_2(t)}$                 |
| :------------------------------------------------------: | :-----------------------: | :----------------------------------------------------------: |
|                          $x(t)$                          |       $\delta(t-T)$       |                           $x(t-T)$                           |
|                   $e^{\lambda t} u(t)$                   |          $u(t)$           |           $\frac{1-e^{\lambda t}}{-\lambda} u(t)$            |
|                  $e^{\lambda_1 t} u(t)$                  |  $e^{\lambda_2 t} u(t)$   | $\frac{e^{\lambda_1 t}-e^{\lambda_2 t}}{\lambda_1 - \lambda_2} u(t), \qquad \lambda_1 \ne \lambda_2$ |
|                   $e^{\lambda t} u(t)$                   |   $e^{\lambda t} u(t)$    |                    $t e^{\lambda t} u(t)$                    |
|                  $te^{\lambda t} u(t)$                   |   $e^{\lambda t} u(t)$    |             $\frac{1}{2}t^2 e^{\lambda t} u(t)$              |
|                       $t^{N}u(t)$                        |    $e^{\lambda t}u(t)$    | $\frac{N! e^{\lambda t}}{\lambda^{N+!}}u(t)-\sum_{k=0}^{N} \frac{N!t^{N-k}}{\lambda^{k+1}(N-k)}u(t)$ |
|                        $t^M u(t)$                        |        $t^N u(t)$         |             $\frac{M!N!}{(M+N+1)!}t^{M+N+1}u(t)$             |
|                 $t e^{\lambda_1 t}u(t)$                  |   $e^{\lambda_2 t}u(t)$   | $\frac{e^{\lambda_2 t}-e^{\lambda_1 t}+(\lambda_1 - \lambda_2)te^{\lambda_1 t}}{(\lambda_1 -\lambda_2)^2}u(t)$ |
| $t^M e^{\lambda_1 t}u(t) \qquad \lambda_1 \ne \lambda_2$ | $t^N e^{\lambda_2 t}u(t)$ | $\sum_{k=0}^{M} \frac{(-1)^k M!(N+k)!t^{M-k} e^{\lambda_1 t}}{k! (M-k)!(\lambda_1 -\lambda_2)^{N+k+1}}u(t)+\sum_{k=0}^{N} \frac{(-1)^k N!(M+k)!t^{N-k} e^{\lambda_2 t}}{k! (N-k)!(\lambda_2 -\lambda_1)^{M+k+1}}u(t)$ |
|        $e^{-\alpha t}\cos{(\beta t+\theta)}u(t)$         |    $e^{\lambda t}u(t)$    | $\frac{cos{(\theta-\phi)}e^{\lambda t}-e^{-\alpha t}\cos{(\beta t+\theta-\phi)}}{\sqrt{(\alpha+\lambda)^2 +\beta^2}}\qquad \phi=\arctan{\left( \frac{-\beta}{\alpha + \lambda} \right)}$ |
|                  $e^{\lambda_1 t}u(t)$                   |  $e^{\lambda_2 t} u(-t)$  | $\frac{e^{\lambda_1 t}u(t)+e^{\lambda_2 t}u(-t)}{\lambda_2 - \lambda_1} \qquad Re(\lambda_2) > Re(\lambda_1)$ |
|                  $e^{\lambda_1 t}u(-t)$                  |  $e^{\lambda_2 t}u(-t)$   | $\frac{e^{\lambda_1 t}-e^{\lambda_2 t}}{\lambda_2 -\lambda_1} u(-t)$ |
|                          $u(t)$                          |          $u(t)$           |                           $t u(t)$                           |

### Other Properties

- **Commutative property**: 
$$
\text{The order of operands doesn't matter.}
$$

- **Associative Property**: 
$$
x_1 (t) \ast [x_2 (t) \ast x_3 (t)] = [x_1 (t) \ast x_2 (t)] \ast x_3 (t)
$$

- **Distributive Property**: 
$$
x_1 (t) \ast [x_2 (t) + x_3 (t)] = x_1 (t) \ast x_2 (t) + x_1 (t) \ast x_3 (t)
$$

- **Shift Property**: 
$$
x_1 (t-T_1) \ast x_2 (t-T_2) = c(t-T_1-T_2)
$$

- **Convolution with an impulse**: 
$$
x(t) \ast \delta(t) = x(t)
$$

- **Width duration property**: 
$$
\text{For two functions with durations }T_1 \text{ and } T_2 \text{ the duration of the convolution is }T_1 + T_2
$$

- **Causality property**: 
$$
\text{If both the input and input response are causal, then so is the convolution.}
$$



## Laplace Transforms

The (bilateral) Laplace Transform for a signal $x(t)$ is defined as:
$$
X(s)=\int_{- \infty}^{\infty}x(t) e^{-st} \,dt
$$

In this course, the one sided transform is used: 
$$
X(s)=\mathcal{L}\{ x(t) \} =\int_{0}^{\infty}x(t) e^{-st} \,dt
$$

The Laplace transform is a linear transform:
$$
\mathcal{L} \{ k_1 x_1 (t) + k_2 x_2 (t) \} = k_1 \mathcal{L} \{ x_1 (t) \}+ k_2 \mathcal{L} \{ x_2 (t) \} 
$$

The Laplace transform of the dirac function is: 
$$
\mathcal{L} \{ \delta (t) \}= 1
$$

The Laplace transform of the unit step function $u(t)$ is:
$$
\mathcal{L} \{ u(t) \} = \int_{- \infty}^{\infty} u(t) e^{-st} \,dt = \int_{0}^{\infty} e^{-st} \,dt = \frac{1}{s} ( -e^{-st} )|_{0}^{\infty}
$$

$$
=\frac{1}{s}\left[ (-e^{-s \cdot \infty}) - (-e^{-s \cdot 0}) \right] = \frac{1}{s} (0+1)=\frac{1}{s}
$$

In order for $e^{-s \cdot \infty}=0$ the real part of $s$ must be positive $(Re\{s\}>0)$. The above condition implies that the Laplace transform of a function might exist for certain values of $s$ and not all values of $s$. The set of these values consists the so called Region of Convergence (ROC) of the Laplace transform.

The Laplace transform of the function $x(t)=e^{at} u(t)$ is:
$$
\mathcal{L} \{ e^{at} u(t) \} = \int_{- \infty}^{\infty} e^{at} u(t) e^{-st} \,dt = \int_{0}^{\infty} e^{at} e^{-(s-a)t} \,dt
$$

$$
=\frac{1}{s-a} ( -e^{-(s-a)t} )|_{0}^{\infty}=\frac{1}{s-a}\left[ (-e^{-(s-a) \cdot \infty}) - (-e^{-(s-a) \cdot 0}) \right] = \frac{1}{s-a} (0+1)=\frac{1}{s-a}
$$

For the above to be true, $Re\{s-a\} > 0 \Rightarrow Re \{s\}> Re\{a\}$ 

The Laplace transform of the following equation can be found in a similar way to above:
$$
x(t)=\cos{(\omega_0 t)} u(t)=\frac{1}{2}(e^{j \omega_0 t}+e^{-j \omega_0 t}) u(t) = ... = \frac{1}{(s+j \omega_0)}, \; Re\{s \}>0
$$

This is equal to:
$$
\mathcal{L} \{x(t) \}= \frac{1}{2}\left[ \frac{1}{(s-j \omega_0)} + \frac{1}{(s+j \omega_0)} \right] = \frac{s}{s^2 + \omega_0^2}, \; Re\{s\} > 0
$$

#### Important Laplace Transforms:

$$
\mathcal{L}\{k \delta (t)\} \Rightarrow k
$$

$$
\mathcal{L}\{k u (t)\} \Rightarrow \frac{k}{s}
$$

$$
\mathcal{L}\{kt^n u (t)\} \Rightarrow \frac{k n !}{s^{n+1}}
$$

Where $s=j\omega$

### Inverse Laplace Transform

The Inverse Laplace Transform for transfer functions in the form of $\frac{f(s)}{g(s)}$ can be found using partial fractions:
$$
\frac{ps+q}{(s-a)(s-b)} \Rightarrow\frac{A}{(s-a)}+\frac{B}{(s-b)}
$$

$$
\frac{ps+q}{(s-a)^2} \Rightarrow \frac{A}{(s-a)}+\frac{B}{(s-a)^2}
$$

$$
\frac{ps^2+qs+r}{(s-a)(s-b)(s-c)}\Rightarrow \frac{A}{(s-a)}+\frac{B}{(s-b)}+\frac{C}{(s-c)}
$$

$$
\frac{ps^2+qs+r}{(s-a)^2(s-b)}\Rightarrow \frac{A}{(s-a)}+\frac{B}{(s-a)^2}+\frac{C}{(s-b)}
$$

$$
\frac{ps^2+qs+r}{(s-a)(s^2+bs+c)}\Rightarrow\frac{A}{(s-a)}+\frac{Bs+C}{s^2-bs+c}
$$
Then the important Laplace transforms can be used to find the inverse Laplace transforms of each partial fraction and then using fact that the Laplace transform is linear, the terms can be added together.

The inverse Laplace transform is rarely used because it is feasible only for small dimensions.

### Laplace Transform Properties

#### Time properties

The time properties of the Laplace transform are:

- Time shifting property:
$$
\mathcal{L} \{ x(t-t_0)\}=e^{-st_0} X(s)
$$

- Time differentiation property:
$$
\mathcal{L} \left\lbrace \frac{dx(t)}{dt} \right\rbrace=sX(s)-x(0^-)
$$

- This can be expanded to:
$$
\mathcal{L} \left\lbrace \frac{d^n x(t)}{dt^n} \right\rbrace =s^n X(s)-s^{n-1} x(0^-)-s^{n-2}x'(0^-)-...-x^{(n-1)}(0^-)
$$

- Time integration property:
$$
\mathcal{L} \left\lbrace \int_{0^-}^{\infty} x(\tau) \,d \tau \right\rbrace = \frac{X(s)}{s}
$$

- Time convolution property:
$$
\mathcal{L}\{ x_1 (t) \ast x_2 (t) \}=X_1 (s) X_2 (s)
$$

Sometimes the Laplace transform of a signal can be found using a combination of time differentiation and shifting properties. A complicated signal can be differentiated multiple times so that it becomes dirac spikes. Linear triangles differentiate to become square impulse waves which differentiate to become dirac spikes.

#### Frequency properties

The frequency properties of the Laplace transform are:

- Frequency shifting property:
$$
\mathcal{L} \{e^{s_0 t} x(t) \}=X(s-s_0)
$$

- Frequency differentiation property:
$$
\mathcal{L} \{t x(t)\}=-\frac{dX(s)}{ds}
$$

- Frequency integration property:
$$
\mathcal{L} \left\lbrace \frac{x(t)}{t} \right\rbrace =\int_{s}^{\infty} X(z) \,d z
$$

- Frequency convolution property:
$$
\mathcal{L}\{ x_1 (t)  x_2 (t) \}=\frac{1}{2\pi j} X_1 (s) \ast X_2 (s)
$$

#### Scaling Property

$$
\mathcal{L} \{ x(at) \} = \frac{1}{a}X\left( \frac{s}{a} \right)
$$

The above shows that time compression of a signal by a factor a causes expansion of its Laplace transform in s-scale by the same factor.

#### Other Properties

|            $\mathbf{x(t)}$            |                       $\mathbf{X(s)}$                        |
| :-----------------------------------: | :----------------------------------------------------------: |
| $\int_{-\infty}^{t} x(\tau) \,d \tau$ |  $\frac{X(s)}{s}+\frac{1}{s} \int_{-\infty}^{0^-} x(t) dt$   |
|          $x(t-t_0)u(t-t_0)$           |              $X(s)e^{-st_0} \qquad t_0 \geq 0$               |
|            $x(t)e^{s_0 t}$            |                          $X(s-s_0)$                          |
|              $x(0^{+})$               |          $\lim_{s \to \infty} s X(s) \qquad (n>m)$           |
|              $x(\infty)$              | $\lim_{s \to 0} s X(s) \qquad$ poles of $sX(s)$ in the left hand plane |

### Alternative for type $\mathcal{L}^{-1}\left[ \frac{1}{(s^2+1)^2}\right]$ and $\mathcal{L}^{-1}\left[ \frac{s}{(s^2+1)^2}\right]$

For Laplace Transforms af the type $\mathcal{L}^{-1}\left[ \frac{1}{(s^2+1)^2}\right]$ or $\mathcal{L}^{-1}\left[ \frac{s}{(s^2+1)^2}\right]$ the square in the denominator can introduce complexity.

To solve this there is a trick using the Laplace transform for sine.
$$
\mathcal{L}[\sin{at}]=\frac{a}{s^2+a^2}
$$

Differentiating this with respect to $a$ gives:
$$
\mathcal{L}[t\cos{at}]=\frac{1}{s^2 +a^2}-\frac{2a^2}{(s^2+a^2)^2}
$$

Dividing by $2a$ and using the transform of $\sin{at}$ to get:
$$
\mathcal{L}^{-1}\left[ \frac{a}{(s^2+a^2)^2}\right] =\frac{1}{2a^2}\sin{at}-\frac{1}{2a}t\cos{at}
$$

Letting $a=1$ for the desired result.
Repeating the process by taking:
$$
\mathcal{L}[\cos{at}]=\frac{s}{s^2+a^2}
$$

And differentiating with respect to $a$ again to obtain:
$$
\mathcal{L} [-t\sin{at}]=-\frac{2as}{s^2+a^2)^2}
$$

Hence:
$$
\mathcal{L}^{-1}\left[ \frac{s}{(s^2+a^2)^2}\right] =\frac{1}{2a}t\sin{at}
$$

### Initial and Final values Theorems

#### Initial Value Theorem

So long as the Laplace transforms of $x(t)$ and $\frac{dx(t)}{dt}$ exist, and the power of the numerator of $X(s)$ is less than the power of its denominator:
$$
\lim_{t \to 0}x(t)=x(0^+)=\lim_{s \to \infty} sX(s)
$$

#### Final Value Theorem

So long as the Laplace transforms of $x(t)$ and $\frac{dx(t)}{dt}$ exist, and the poles of $sX(s)$ are all on the left plane or origin:
$$
\lim_{t \to \infty}x(t)=x(\infty)=\lim_{s \to 0} sX(s)
$$

### Laplace Transform for solving differential equations

Using the time differentiation property of the Laplace transform:
$$
\mathcal{L}\left\lbrace \frac{d^n x(t)}{dt^n} \right\rbrace =s^n X(s)-s^{n-1} x(0^-)-s^{n-2}x'(0^-)-...-x^{(n-1)}(0^-)
$$

We can solve differential equations by converting them from the time domain into the frequency domain. This means we can solve simple algebraic equations in the frequency domain, and then use the reverse Laplace transform to get the solutions to the original differential equation.

### Laplace Transform and transfer function

The Laplace transform of the impulse response of a system is called the transfer function of the system: 
$$
H(s)=\frac{Y(s)}{X(S)}
$$

Where $H(s)=\mathcal{L}\{h(t) \}$.
Knowing the transfer function of a system, we can fully determine the behaviour of the system.

### Initial Conditions in systems

In circuits, initial conditions may not be zero since components such as capacitors and inductors may contain charge or current.

#### Capacitors

For a capacitor $C$ with an initial voltage $v(0^-)$, the equation $i(t)=C\frac{dv(t)}{dt}$ holds.
Taking the Laplace transform on both sides gives: $I(s)=C(sV(s)-v(0^-))$. This can be rearranged to give the voltage across the charged capacitor:
$$
V(s)=\frac{1}{Cs}I(s)+\frac{v(0^-)}{s}
$$

Where the first term is the voltage across the capacitor with no charge, and the second term is the effect of the initial charge = voltage source.

#### Inductors

For an inductor $L$ with an initial current $i(0^-)$, the equation $v(t)=L\frac{di(t)}{dt}$ holds.
Taking the Laplace transform on both sides gives: $V(s)=L(sI(s)-i(0^-))$. This can be rearranged to give the voltage across the inductor:
$$
V(s)=LsI(s)-Li(0^-)
$$

Where the first term is the voltage across the inductor with no initial current, and the second term is the effect of the initial current = voltage source.



## Fourier Transform

The Fourier Transform is a Laplace transform where the real part of $s$ is zero.

The Fourier transform is defined as: 
$$
X(\omega)=\mathcal{F}[x(t)]=\int_{-\infty}^{\infty}x(t)e^{-j\omega t} \,d t
$$

$$
x(t)=\mathcal{F}^{-1}[X(\omega)]=\frac{1}{2\pi}\int_{-\infty}^{\infty}X(\omega)e^{j \omega t}\,d \omega
$$

For periodic signals, the Fourier Series are used instead: 
$$
x_{T_0} (t)=\sum_{n= -\infty}^{\infty} D_n e^{jn\omega_0 t}
$$

$$
D_n=\frac{1}{T_0}\int_{\frac{-T_0}{2}}^{\frac{T_0}{2}}x_{T_0}(t)e^{-jn\omega_0 t}\,d t \quad \text{where} \quad \omega_0 = \frac{2\pi}{T_0}
$$

### Useful Functions

The unit rectangular function: 
$$
rect(x)=\left\lbrace 0 \text{ for }|x|>\frac{1}{2} \qquad \frac{1}{2}  \text{ for }|x|=\frac{1}{2}\qquad 1 \text{ for }|x|<\frac{1}{2} \right.
$$

The bandwidth of $rect{\left( \frac{t}{\tau}\right) }=\frac{2\pi}{\tau}$

The unit triangular function: 
$$
\Delta (x)=\left\lbrace 0 \text{ for } |x| \geq \frac{1}{2} \qquad 1-2 \text{ for }|x| < \frac{1}{2}\right.
$$

The interpolation function: 
$$
sinc(x)=\frac{\sin{(x)}}{x}=\frac{\sin{(\pi x)}}{\pi x}
$$

The $sinc{(x)}$ function is an even function.

### Fourier Transform Properties

|                   $\mathbf{x(t)}$                   |                     $\mathbf{X(\omega)}$                     |
| :-------------------------------------------------: | :----------------------------------------------------------: |
|                    $e^{-at}u(t)$                    |                    $\frac{1}{a+j\omega}$                     |
|                     $e^{a|t|}$                      |                  $\frac{2a}{a^2 +\omega^2}$                  |
|                   $te^{-at}u(t)$                    |            $\left( \frac{1}{a+j\omega} \right)^2$            |
|                  $t^n e^{-at}u(t)$                  |           $\left(\frac{1}{a+j\omega}\right)^{n-1}$           |
|                    $\delta (t)$                     |                             $1$                              |
|                         $1$                         |                    $2\pi \delta (\omega)$                    |
|                  $e^{j\omega_0 t}$                  |               $2\pi \delta (\omega-\omega_0)$                |
|                 $\cos{\omega_0 t}$                  | $\pi [\delta (\omega -\omega_0) + \delta (\omega + \omega_0)]$ |
|                 $\sin{\omega_0 t}$                  | $j\pi [\delta (\omega +\omega_0) - \delta (\omega - \omega_0)]$ |
|                       $u(t)$                        |           $\pi \delta (\omega) +\frac{1}{j\omega}$           |
|                     $sgn{(t)}$                      |                     $\frac{2}{j \omega}$                     |
|              $\cos{(\omega_0 t)}u(t)$               | $\frac{\pi}{2} [\delta (\omega -\omega_0) + \delta (\omega + \omega_0)]+\frac{j\omega}{\omega_0^2 - \omega^2}$ |
|              $\sin{(\omega_0 t)}u(t)$               | $\frac{\pi}{2j} [\delta (\omega -\omega_0) - \delta (\omega + \omega_0)]+\frac{\omega_0}{\omega_0^2 - \omega^2}$ |
|            $e^{-at}\sin{\omega_0 t}u(t)$            |        $\frac{\omega_0}{(a+j\omega)^2 + \omega_0^2}$         |
|            $e^{-at}\cos{\omega_0 t}u(t)$            |       $\frac{a+j \omega}{(a+j\omega)^2 + \omega_0^2}$        |
|       $rect{\left( \frac{t}{\tau} \right) }$        |      $\tau sinc{\left( \frac{\omega \tau}{2}\right) }$       |
|               $\frac{W}{\pi}sinc{Wt}$               |          $rect{\left( \frac{\omega}{2W} \right) }$           |
|       $\Delta \left( \frac{t}{\tau} \right)$        | $\frac{\tau}{2} sinc^2{\left( \frac{\omega \tau}{4}\right) }$ |
| $\frac{W}{2\pi}sinc^2{\left( \frac{Wt}{2}\right) }$ |         $\Delta{\left( \frac{\omega}{2W} \right) }$          |
|       $\sum_{n=-\infty}^{\infty}\delta(t-nT)$       | $\omega_0 \sum_{n=-\infty}^{\infty}\delta(\omega-n\omega_0)$ |
|            $e^{\frac{-t^2}{2\sigma^2}}$             |     $\sigma \sqrt{2\pi}e^{\frac{-\sigma^2\omega^2}{2}}$      |

- Linearity: 
$$
x_1(t)+x_2(t) \Leftrightarrow X_1(\omega)+X_2(\omega)
$$

- Conjugate: 
$$
\text{If }x(t) \Leftrightarrow X(\omega) \text{ then } x*(t) \Leftrightarrow X*(-\omega)
$$

- Conjugate symmetry: 
$$
\text{If }x(t)\text{ is real then }X(-\omega)=X*(\omega)
$$

- Duality: 
$$
\text{If }x(t) \Leftrightarrow X(\omega)\text{ then }X(t) \Leftrightarrow 2\pi x(-\omega)
$$

- Scaling property: 
$$
x(at) \Leftrightarrow \frac{1}{|a|}X\left( \frac{\omega}{a}\right)
$$

- Time-shifting property: 
$$
x(t-t_0) \Leftrightarrow X(\omega)e^{-j\omega t_0} \qquad\text{Phase shift increases with frequency.}
$$

- Frequency-shifting property: 
$$
x(t)e^{j\omega_0 t} \Leftrightarrow X(\omega-\omega_0) \qquad\text{To do this in practice, you must multiply $x(t)$ by a sinusoid.}
$$

- Time and Frequency convolution: 
$$
x_1 (t) \ast x_2 (t) \Leftrightarrow X_1 (\omega) X_2 (\omega)\text{ and }x_1(t)x_2(t) \Leftrightarrow \frac{1}{2\pi}X_1(\omega)\ast X_2 (\omega)
$$

- Time differentiation property: 
$$
\frac{dx(t)}{dt} \Leftrightarrow j\omega X(\omega)
$$

- Time integration property: 
$$
\int_{-\infty}^{t} x(\tau) \,d \tau \Leftrightarrow \frac{X(\omega)}{j\omega}+\pi X(0)\delta (\omega)
$$

**The Fourier Transform of a system's impulse response is the system's Frequency Response**

### Connecting Laplace and Fourier Transform

Unlike the Laplace transformation, the Fourier transform doesn't have a Region Of Convergence.

Setting $s=j\omega$ in the Laplace Transform yields:
$$
X(j\omega)=\int_{-\infty}^{\infty}x(t)e^{-j\omega t}\,d t \qquad \text{ where } \qquad X(j\omega)=X(s)|_{s=j\omega}
$$

It is therefore true that $X(\omega)=X(j\omega)$ if $x(t)$ is absolutely integrable where: 
$$
\int_{-\infty}^{\infty}|x(t)|\,d t < \infty
$$

When $x(t)$ is absolutely integrable, the ROC of its Laplace transform includes the imaginary axis. Therefore both the Laplace and Fourier transforms exist and $X(\omega)=X(j \omega)$.

When $x(t)$ is not absolutely integrable, the ROC of its Laplace transform doesn't include the imaginary axis and the Fourier transform may not exist.

### System Stability

A system is BIBO stable (Bounded Input Bounded Output) if every bounded input produces a bounded output.

BIBO stability exists when: 
$$
\int_{\tau=-\infty}^{\infty} |h(\tau)|\,d \tau < \infty
$$

Often $h(t)$ is a linear combination of causal exponential functions of the form $x(t)=e^{at}u(t)$. For stability, $Re\{a\}<0$.

The constant $\mathbf{a}$ which makes the denominator of $\frac{1}{s-a}=0$ is called a pole of the transfer function. 

**To achieve stability, the poles of the transfer function of a causal signal must lie in the left half of the $s$-plane, i.e. all the poles have negative real parts**

An LTI system is stable, only if the ROC of it's Laplace transform includes the imaginary axis.

### Laplace vs Fourier

#### Laplace

- Usual unilateral, therefore useful for transient behaviours, for systems with initial conditions.
- Defined when the Fourier transform doesn't exist (e.g. for growing exponentials).
- More useful for a system transient behaviour and for stability (i.e Laplace transform exists for both stable and unstable systems).

#### Fourier

- Bilateral, therefore more useful for global trends.
- Usually used for signal analysis and for filter design.
- Amenable to a more intuitive interpretation: high $\omega$ means fast oscillations in the signals/systems.




## Frequency Response

We can sub $s=j\omega$ into transfer functions and find the following results. 
$$
\cos{(\omega t)} \Rightarrow |H(j\omega)|\cos{[\omega t+\angle H(j \omega)]}
$$

- Where $H(j\omega )$ is Freq Response.
- Where $|H(j\omega)|$ is the Amplitude response.
- Where $\angle H(j\omega)$ is the Phase response.

This is found by expressing $H(j\omega)$ in polar form: $|H(j\omega)|e^{j\angle H(j\omega)}$

We can also show that an LTI system's response to an everlasting exponential $x(t)=e^{j\omega t +\theta}$ is $e^{j \omega t + \theta}H(j\omega)$

To find the frequency response, find $|H(j\omega)|$ and $\angle H(j \omega)$.

For an input of $x(t)=\cos{(\omega t)}​$ you sub in the value for $\omega​$ and solve the equations.

You can then sub this into: 
$$
y(t)= |H(j\omega)|\cos{[\omega t+\angle H(j \omega)]}
$$

For input $x(t)=\cos{(\omega t \pm \theta)}$ you ignore the $\pm \theta$ until the end and you do: 
$$
y(t)= |H(j\omega)|\cos{[\omega t+\angle H(j \omega) \pm \theta]}
$$

### Frequency response of a system that causes a delay of $T$ seconds

The transfer function of an ideal delay is 
$$
H(s) = e^{-sT}
$$

Therefore:
$$
|H(j\omega)|=|e^{-j\omega T}|=1 \qquad \qquad \angle H(j \omega)=\Phi(j\omega )=-\omega T
$$

Delaying a signal by $T$ has no effect on amplitude, but introduces a linear phase shift with gradient $-T$.

The quantity $-\frac{\,d \Phi(\omega)}{\,d \omega}=\tau_g =T$ is the **Group Delay**.

### Frequency response of an ideal differentiator

The transfer function of an ideal differentiator is $H(s) = s$. Therefore:

- Freq response: 
$$
H(j\omega)=j\omega
$$

- Amplitude response: 
$$
|H(j\omega)|=\omega
$$

- Phase response: 
$$
\angle H(j \omega)=\frac{\pi}{2}
$$

- This agrees with 
$$
\frac{d}{\,d t}(\cos{\omega t})=-\omega \sin{\omega t}=\omega \cos{\left( \omega t + \frac{\pi}{2}\right) }
$$

- Differentiators aren't nice components because they amplifies high freq components such as noise.

### Frequency response of an ideal integrator

The transfer function of an ideal differentiator is $H(s) = \frac{1}{s}$. Therefore:

- Freq response: 
$$
H(j\omega)=\frac{1}{j\omega}=\frac{-j}{\omega}
$$

- Amplitude response: 
$$
|H(j\omega)=\frac{1}{\omega}
$$

- Phase response: 
$$
\angle H(j \omega)=-\frac{\pi}{2}
$$

- This agrees with:
$$
\int(\cos{\omega t})=-\frac{1}{\omega} \sin{\omega t}=\frac{1}{\omega} \cos{\left( \omega t - \frac{\pi}{2}\right) }
$$

- Integrators are nice components because they suppress high freq components such as noise.

### Bode Plots

The **poles** are the roots of the denominator polynomial of the transfer function.

The **zeroes** are the roots of the numerator polynomial of the transfer function.
$$
\text{For: } H(s)=\frac{K(s+a_1)(s+a_2)}{s(s+b_1)(s^2+b_2 s+b_3)}=\frac{Ka_1 a_2}{b_1 b_3}\frac{\left( \frac{s}{a_1}+1\right) \left( \frac{s}{a_2}+1\right)}{s\left( \frac{s}{b_1}+1\right)\left( \frac{s^2}{b_3}+\frac{b_2}{b_3}s+1\right)}
$$

#### Amplitude Response

We let $s=j\omega$ and the amplitude response $|H(j\omega)|$ can be rearranged as:
$$
|H(j \omega)|=\frac{Ka_1 a_2}{b_1 b_3}\frac{\left| \frac{j\omega}{a_1}+1\right| \left| \frac{j\omega}{a_2}+1\right|}{j\omega\left| \frac{j\omega}{b_1}+1\right|\left| \frac{(j\omega)^2}{b_3}+\frac{b_2}{b_3}j\omega+1\right|}
$$

Which when logged can be expressed in blocks using logs: 
$$
20\log{|H(j\omega)}|=20\log{\frac{Ka_1 a_2}{b_1 b_3}}+20\log{\left| 1+\frac{j \omega}{a_1}\right| }+20\log{\left| 1+\frac{j \omega}{a_2}\right| }$$ $$-20\log{|j\omega|}-20\log{\left| 1+\frac{j \omega}{b_1}\right| }-20\log{\left| 1+\frac{j \omega b_2}{b_3}+\frac{(j\omega)^2}{b_3}\right| }
$$

$$
\text{Consider a term: } H_{dB}=20\log{\left| 1+\frac{j \omega}{x}\right| }
$$

The corner frequency is $x$. At this frequency, the max error that occurs between the actual and asymptotic plots is $3dB$. 

The amplitude response is: 
$$
|H(j \omega)|=\left| 1+\frac{j\omega}{x}\right| =\sqrt{1+\frac{\omega^2}{x^2}}\Rightarrow H_{dB}=20\log{\sqrt{1+\frac{\omega^2}{x^2}}} 
$$

The bode diagram for this term consists of two asymptotic curves approached by $H_{dB}$ for very small and large values of $\omega$. These curves will intersect at $x$.

- For values of $\omega << x$: 
$$
H_{dB} \approx 20\log{1}=0
$$

- For values of $\omega >> x$: 
$$
H_{dB} \approx 20\log{\frac{\omega}{x}}
$$

**Therefore the bode plot for this term would be a line along the $H_{dB}$ axis and linear curve intersecting the axis at $\omega=a$ (corner frequency) with a slope of $20dB/decade$, where a decade is a tenfold increase in $\omega$.** 

This is because: at $\omega = a, H_{dB}=0$; at $\omega = 10a, H_{dB}=20$; at $\omega = 100a, H_{dB}=40$. Thus the value of $H_{dB}$ increases $20dB$ for every 10 fold increase in frequency. The asymptote therefore has a slope of $20 dB/decade$.

When there are multiple $H_{dB}$ terms, bode plot for each term is plotted like above, and then each is summed together to create the full bode plot for the full transfer function.

For a second order pole $s^2+b_2 s + b_3$ it is common to express this in the form: $$s^2 + 2 \zeta \omega_n s+ \omega_n^2$$ Where:

-   The scalar $\zeta$ is the damping factor.

-   The scalar $\omega_n$ is the natural frequency.

$$
H_{dB} = -20\log{\left| 1+2j\zeta \left( \frac{\omega}{\omega_n}\right) +\left( \frac{j \omega}{\omega_n}\right)^2 \right| }
$$

- When $\omega << \omega_n$: 
$$
H_{dB} \approx -20\log{1}=0
$$

- When $\omega >> \omega_n$:
$$
H_{dB} \approx -20\log{\left| -\left( \frac{\omega}{\omega_n}\right)^2 \right|} = -40 \log{\left( \frac{\omega}{\omega_n}\right)}
$$


The exact log amplitude is:
$$
H_{dB}=-20\log{\sqrt{\left[ 1-\left( \frac{\omega}{\omega_n}\right)^2\right]^2 +4\zeta^2 \left( \frac{\omega}{\omega_n} \right)^2 }}
$$
This means that the log amplitude plot will be different for different values of $\zeta$.

For complex conjugate poles $\zeta < 1$, whilst for $\zeta \ge 1$ the poles are real and each can be dealt with as a separate first order factor.

The amplitude plot for a pair of complex conjugate zeros is a mirror image about the $\omega$ axis of the plot for a pair of complex conjugate poles.

#### Phase Response

We let $s=j\omega$ and the phase response $\angle H(j\omega)$ becomes: 
$$
\angle{H(j\omega)}=\angle{\left(  1+\frac{j \omega}{a_1}\right)  }+\angle{\left(  1+\frac{j \omega}{a_2}\right)  } -\angle{j\omega}
$$

$$
-\angle{\left(  1+\frac{j \omega}{b_1}\right)  }-\angle{\left(  1+\frac{j \omega b_2}{b_3}+\frac{(j\omega)^2}{b_3}\right)  }
$$

Consider a term:
$$
\angle H(j \omega )= \angle \left( 1+\frac{j\omega}{x} \right) =\arctan{\frac{\omega}{x}}
$$

The corner frequency is once again at $x$. Like the amplitude response, the phase response is made up of asymptotic curves, however three are needed for phase response bode plot.

- For values of $\omega << a$: 
$$
\angle H(j \omega) = 0 ^{\circ}\text{ Used for }\omega < 0.1a
$$

- For values of $\omega >> a$: 
$$
\angle H(j \omega) = 90 ^{\circ}\text{ used for }\omega > 10a
$$

**This means that for $\omega < 0.1a$ and $\omega > 10a$ there will be horizontal lines parallel to the $\omega$ axis at $\angle H(s) = 0 ^{\circ}$ and $\angle H(s) = 90 ^{\circ}$ respectively with a linear curve at an angle of $45 ^{\circ}/decade$ connecting $0.1a$ and $10a$.** 

Now consider the term: 
$$
1+2j \zeta \left( \frac{\omega}{\omega_n}\right) +\left( \frac{j \omega}{\omega_n} \right)^2=1-\left( \frac{\omega}{\omega_n}\right)^2+2 j \zeta \left( \frac{\omega}{\omega_n}\right)
$$

$$
\angle H(j \omega)=-\arctan{\left[ \frac{2\zeta \left( \frac{\omega}{\omega_n}\right) }{1-\left( \frac{\omega}{\omega_n}\right)^2 }\right] }
$$

When $\omega<< \omega_n $:
$$
\angle H(j \omega)\approx -\arctan{0} = 0^{\circ}
$$

When $\omega>> \omega_n$:
$$
\angle H(j \omega)\approx -\arctan{0} = -180^{\circ}
$$

(This means that the instead of a linear curve at an angle of $45 ^{\circ}/decade$, there will be a linear curve at an angle of $90 ^{\circ}/decade$.)

Similarly to the amplitude plot, the phase involves the parameter $\zeta$ resulting in a different plot for each value of $\zeta$.

The asymptote for the phase of complex conjugate poles is a step function that is $0 ^{\circ}$ for $\omega < \omega_n$ and $-180 ^{\circ}$ for $\omega > \omega_n$, whilst the phase plot for complex conjugate zeros is the mirror image of those for the for complex conjugate poles.

*The actual plot can be obtained if you add the error to the asymptotic plot.*



## Zeros, Poles, and Filters

The value of a transfer function at a complex frequency $s=p$ is: 
$$
H(s)=\frac{P(s)}{Q(s)}=b_0 \frac{(p-z_1)(p-z_2)...(p-z_N)}{(p-\lambda_1)(p-\lambda_2)...(p-\lambda_N)}=b_0 \frac{(r_{1}e^{j \phi_{1}})(r_{2}e^{j \phi_{2}})...(r_{N}e^{j \phi_{N}})}{(d_{1}e^{j \theta_{1}})(d_{2}e^{j \theta_{2}})...(d_{N}e^{j \theta_{N}})}
$$

The factor $p-z_i$ is a complex number represented by a vector from $z_i$ to $p$ in the complex plane.

$H(s)$ can be rewritten: 
$$
H(s)=b_0 \frac{r_1 r_2 ... r_N}{d_1 d_2 ... d_N} e^{j[(\phi_1 + \phi_2 +...+ \phi_N)-(\theta_1 + \theta_2 + ... + \theta_N )]}
$$

$$
\text{Magnitude is therefore given by: }|H(s)|_{s=p}=b_0 \frac{r_1 r_2 ... r_N}{d_1 d_2 ... d_N}
$$

$$
\text{And phase is given by: }\angle H(s)_{s=p} = (\phi_1 +\phi_2 +...+\phi_N)-(\theta_1 + \theta_2 + ...+ \theta_N)
$$

If $b_0$ is negative, there is an additional phase $\pi$.

### Gain enhancement by a single pole

For a single pole at $-a+j\omega_0$, the length of the line that connects the pole to the point $j\omega$ is known as $d$. In this situation: 
$$
|H(j\omega)| \propto \frac{1}{d}
$$

At the value $\omega = \omega_0$, $d$ is at it's minimum value. The value $a$ is the horizontal distance from the imaginary axis.

In the case of $a=0$, the pole is on the imaginary axis meaning $d$ is also equal to zero, therefore making the gain infinite.

Adding more poles will change the location of the overall pole. To enhance the gain at a frequency $\omega_0$, a pole can be placed opposite the point $j \omega_0$.

Recall that the poles must lie on the left half of the $s$-plane.

### Gain enhancement by a pair of complex conjugate roots

In reality, a complex pole at $-a+j\omega_0$ must be accompanied $-a-j\omega_0$.

The amplitude response at a specific value of $\omega$, $|H(j\omega)|$ is found by measuring the length of the two lines that connect the poles to the imaginary axis $d$, and $d'$. 
$$
|H(j\omega)| \propto \frac{1}{d d'}
$$

This doesn't affect the system behaviour since $d'$ doesn't change much.

### Gain suppression by a pair of complex conjugate zeros

For areal system with a pair of complex conjugate zeros at $-a \pm j \omega_0$ the amplitude response is: 
$$
|H(j\omega)| \propto r r'
$$

Where $r$ and $r'$ are the lengths from the zeros to the imaginary axis.

As the zero moves closer to the imaginary axis, the gain is suppressed.

### Phase response due to a pair of complex conjugate poles or zeros

Angles formed by the poles $-a \pm j \omega_0$ ($\theta_{1,2}$ respectively) at $\omega = 0$ are equal and opposite.

As $\omega$ increases from $0$, $\theta_1$ reduced in size, and $\theta_2$ increases in size.\
Therefore the sum of the angles $\theta_1 + \theta_2$ increases continually approaching a $\pi$ as $\omega \to \infty$.

For conjugate poles: 
$$
\angle H(j\omega)=-(\theta_1 +\theta_2)$$ For conjugate zeros: $$\angle H(j\omega)=(\theta_1 +\theta_2)
$$

### Simplest lowpass filters

A lowpass filter is a system with a frequency response that has a maximum gain at $\omega = 0$.

The transfer function of a lowpass filter is: 
$$
H(s)=\frac{\omega_c}{s+\omega_c}
$$

$\omega_c$ in the numerator achieves $H(0)=1$. $|H(j\omega)|=\frac{\omega_c}{d}$.

### Butterworth lowpass filter

An ideal lowpass filter has a constant gain of $1$ up to a desired frequency $\omega_c$ and then the gain drops to $0$.

For an ideal filter, the gain needs to be enhanced in the frequencies $0 \to \omega_c$. Therefore a wall of poles is needed facing the imaginary axis opposite the range $0 \to -\omega_c$.

For a maximally flat response, a semicircle of infinite poles is needed.

In reality, only $N$ poles are possible, therefore the filter will be non ideal.

### Bandpass filters

An ideal bandpass filter has a constant gain of 1 placed symmetrically around a desired frequency $\omega_0$, otherwise the gain drops to $0$.

Therefore two semicircles of poles are needed around $\pm j\omega_0$.

### Bandstop filters

An ideal bandstop filter has amplitude response of $0$ around the desired frequency $\omega_0$, otherwise the gain is $1$.

For a second order notch filter with zero gain at $\omega_0$:

- Must have zeros at $\pm j \omega_0$.
- For $\lim_{\omega \to \infty} |H(j\omega)|=1$, the number of poles must equal the number of zeros.
- Therefore, there must be two poles that match up with the zeros and whose distances from the origin must be the same.
- The above requirement can be satisfied if the two conjugate poles are placed along a semicircle of radius $\omega_0$ that lies within the left half plane.

### Butterworth Filters

For a normalised lowpass filter: 
$$
|H(j\omega)|=\frac{1}{\sqrt{1+\omega^{2n}}}
$$

As $n \to \infty$ this gives an ideal lowpass filter response ($1$ if $\omega \leq 1$, $0$ if $\omega > 1$).

Using $s=j \omega \Rightarrow \omega = \frac{s}{j}$ we can show that: 
$$
|H(j\omega)|^2=H(s)H(-s)=\frac{1}{1+\left( \frac{s}{j} \right)^{2n} }
$$

The poles of $H(s)H(-s)$ are given by $1+\left( \frac{s}{j} \right)^{2n}=0\Rightarrow\left( \frac{s}{j} \right)^{2n}=-1$

Since $-1=e^{j\pi (2k-1)} \text{ and } j= e^{j \frac{\pi}{2}}$ we can rearrange to show: 
$$
\left( \frac{s}{j} \right)^{2n}=-1 \Rightarrow s^{2n}=j^{2n}\cdot(-1)=e^{\left( j\frac{\pi}{2}\right) 2n} \cdot e^{j\pi(2k-1)}=e^{jn\pi}\cdot e^{j \pi (2k-1)}
$$

$$
\Rightarrow s^{2n}=e^{j\pi (2k-1+n)}\Rightarrow s=e^{\frac{j \pi (2k-1+n)}{2n}}
$$

Therefore the poles of $H(s)H(-s)$ lie along the unit circle. There are $2n$ poles given by: 
$$
s_k=e^{\frac{j \pi (2k-1+n)}{2n}}  \qquad k=1,2,...,n
$$

Since only $H(s)$ matters, only the first $n$ poles on the left side of the unit circle matter.

Using $e^{j\theta}=\cos{\theta}+j\sin{\theta}$ the transfer function of the Butterworth filters can be shown to be: 
$$
H(s)=\frac{1}{(s-s_1)(s-s_2)...(s-s_N)}
$$

Butterworth filters are a family of filters with poles distributed evenly around the left side of the unit circle where $\omega_c = 1$.

### Butterworth Filters with Sallen-Key

For a Sallen Key filter with transfer function: 
$$
H(s)=\frac{1}{1+C_2 (R_1 + R_2)s+C_1 C_2 R_1 R_2 s^2}
$$

Assuming $\omega_c = 1$ and $n$ is even:

- $C_1 C_2 R_1 R_2 = 1$
- $C_2 (R_1 + R_2)=-2\cos{\left( \frac{2k+n-1}{2n}\pi \right) }$

Thus guaranteeing that $H(s)$ has two poles at: 
$$
\cos{\left( \frac{2k+n-1}{2n} \pi \right) } \pm j\sin{\left( \frac{2k_n-1}{2n} \pi \right) }
$$

For an $n^{th}$ order filter $\frac{n}{2}$ filters must be cascaded.

When $n$ is odd, the remaining real pole can be implemented with an RC circuit. The RC circuit will have a pole at $(-1, 0)$.

To design a Butterworth filter for a cut off frequency of $\omega_c \ne 1$, simply replace $s$ with $\frac{s}{\omega_c}$.



## Signal Transmission, Group Delay, and Windowing Effects

### Distortionless transmission

Distortionless transmission implies that the output is the same as the input apart from:

- A constant multiplicative factor.
- A delay.

Therefore, distortionless transmission implies that: 
$$
y(t)=G_0 x(t-t_d)
$$

Taking the Fourier transform gives: 
$$
Y(\omega) = G_0 X(\omega)e^{-j \omega t_d}
$$

Meaning the transfer function can be written as: 
$$
H(\omega)=\frac{Y(\omega)}{X(\omega)}=G_0 e^{-j \omega t_d}
$$

$$
|H(\omega)|=G_0 \qquad \qquad \angle H(\omega)=-\omega t_d
$$

### Group Delay

Group delay can be used to assess phase linearity: 
$$
t_g (\omega )=-\frac{d}{d \omega}\angle H(\omega )
$$

- For lowpass systems - the phase must be linear over the band of interest and must also pass through the origin.
- For bandpass systems - the phase must be linear over the band of interest but does not have to pass through the origin.

For a passband of width $2W$ centred at $\omega_c$.

Within the passband and for $\omega \geq 0$ the phase can be described as: 
$$
\angle H(\omega)=\phi_0-\omega t_g
$$

The phase is always an odd function, therefore: 
$$
\angle H(-\omega)=-\phi_0 +\omega t_g
$$

Therefore we can rewrite the equation for a distortionless system: 
$$
H(\omega)=G_0 e^{j (\phi_0 -\omega t_g)} \qquad \qquad \omega \geq 0
$$

For a system $Y(\omega)=H(\omega)X(\omega - \omega_c)$ with an input $z(t)=x(t)e^{j \omega_c t}$ it can be obtained: 

$$
y(t)=G_0 x(t-t_g)e^{j[\omega_c (t-t_g)+\phi_0]}
$$

For a system with an input $z(t)=Re\{z(t)\}=x(t)\cos{\omega_c t}$ it can be obtained: 

$$
y(t)=G_0 x(t-t_g)\cos{[\omega_c (t-t_g)+\phi_0]}
$$

The output envelope $x(t-t_g)$ remains undistorted.

The output carrier acquires an extra phase $\phi_0$.

In a modulation system transmission is considered distortionless if the envelope $x(t)$ remains undistorted. This is because the signal is contained solely in the envelope.

### Parseval's Theorem

Energy of a signal: 
$$
E_x=\int_{-\infty}^{\infty}|x(t)|^2 \,d t =\frac{1}{2\pi}\int_{-\infty}^{\infty} |X(\omega)|^2 \,d \omega
$$

The function $|X(\omega)|^2$ is the energy spectral density.

If $x(t)$ is a real signal, then $X(\omega)$ and $X(-\omega)$ are conjugate, therefore $|X(\omega)|^2$ is even.
$$
E_x = \frac{1}{2\pi} \int_{0}^{\infty} |X(\omega)|^2 \,d \omega
$$

### Windowing and its effects

Extracting a segment of a signal in time, is the same as multiplying the signal with a rectangular window.

Energy is spread out from $\omega_0$ to a width of $\frac{2\pi}{T}$. Energy leaks out from the mainlobe to the sidelobes.

If $x(t)$ has two spectral components of frequencies which differ by less than $\frac{4\pi}{T} rads^{-1}$ $\left(\frac{2}{T} Hz \right)$(The mainlobe width) then they will be indistinguishable from the truncated signal. The result is loss of spectral resolution.

#### Lobes

- The Mainlobe is first peak around $\omega = 0$.
- The sidelobes are every other peak. (The rolloff rate is equal to $-20 dB/decade$)

### Remedying Truncation

1. Make the mainlobe as narrow as possible (Wide a window as possible).
2. Avoid big discontinuity in the windowing function ro reduce leakage (e.g. high frequency sidelobes).
3. (1.) and (2.) are incompatible so compromises must be made. (Hamming, Hanning, Bartlett, Blackman, and Kaiser are all commonly used windows.)


|                            Window                            |    Mainlobe width    | Rolloff rate $dB/oct$ |    Peak sidelobe level $(dB)$    |
| :----------------------------------------------------------: | :------------------: | :-------------------: | :------------------------------: |
|       Rectangular: $rect{\left(\frac{t}{T} \right) }$        |   $\frac{4\pi}{T}$   |         $-6$          |             $-13.3$              |
|       Bartlett: $\Delta{\left(\frac{t}{2T} \right) }$        |   $\frac{8\pi}{T}$   |         $-12$         |             $-26.5$              |
| Hanning: $0.5\left[1+\cos{\left(\frac{2\pi t}{T} \right) } \right]$ |   $\frac{8\pi}{T}$   |         $-18$         |             $-31.5$              |
|  Hamming: $0.54+0.46\cos{\left(\frac{2\pi t}{T} \right) }$   |   $\frac{8\pi}{T}$   |         $-6$          |             $-42.7$              |
| Blackman: $0.42+0.5\cos{\left(\frac{2\pi t}{T} \right) }+0.08\cos{\left(\frac{4\pi t}{T} \right) }$ |  $\frac{12\pi}{T}$   |         $-18$         |             $-58.1$              |
| Kaiser: $\frac{I_0\left[\alpha \sqrt{1-4\left(\frac{t}{T} \right)^2 } \right] }{I_0 (\alpha)} \qquad 0 \leq \alpha \leq 10$ | $\frac{11.2 \pi}{T}$ |         $-6$          | $-59.9$$\quad$$(\alpha = 8.168)$ |



## Sampling and Quantization

In discrete time systems, the continuous signals are converted into numbers (sampled) and processed before being converted back into a continous signal.

A sample is kept every $T_s$ units of time in a process called uniform sampling $x[n]=x(nT_s)$.

This ends up giving a a bunch of dirac deltas thatare equivalent to the value of the wave at a specific time.

### Sampling Theroem

The minium sampling rate needed to reconstruct the signal is the **Nyquist Rate** for $x(t)$, and the corresponding interval for $T_s = \frac{1}{2}f_{max}$ is called the **Nyquist Inteval**.

A bandpass signal whose spectrum exists over a frequency band $f_c - \frac{B}{2} < |f| < f_c + \frac{B}{2}$ also has a bandwith of $B Hz$ where $B$ is equal to the maximum frequency $f_{max}$.

If a signal is sampled at a frequency lower than the Nyquist rate then the resulting reconstruction results in a lot of overlap which corrupts the signal meaning you cannot recover the original signal.

Sampling a signal above the Nyquist rate results in larger gaps between the sampled parts of the signal meaning you can easily reconstruct the signal.

To reconstruct the signal, you use a lowpass (not necessarily idea) filter over the non overlapping parts of the sample.

#### Sampling Therorem Mathimatical Proof

The sampled version of $x(t)$ can be expressed as: 
$$
\overline{x}(t)=x(t)\delta_{Ts}(t)=\sum_{n} x(nT_s)\delta (t-nTs)
$$

We can express the impulse train as a Fourier Series: 
$$
\delta_{Ts}(t)=\frac{1}{Ts}\left[ 1+2\cos{\omega_s t}+2\cos{2 \omega_s t} +...\right] \text{\qquad where \qquad}\omega_s=\frac{2\pi}{Ts}
$$

Therefore: 
$$
\overline{x}(t)\left[ x(t)+2x(t)\cos{\omega_s t}+2x(t)\cos{2\omega_s t}+... \right]
$$

Since $2x(t)\cos{\omega_s t} \Leftrightarrow X(\omega - \omega_s)+X(\omega + \omega_s )$: 
$$
\overline{X}(\omega)=\frac{1}{Ts}\sum_{n=-\infty}^{\infty}X(\omega-n\omega_s)
$$

Which is the sampled spectrum of a signal sampled at the Nyquist Rate.

### Aliasing

#### Spectral Folding

In general, a sinusoid of frequency $f Hz$ sampled at a frequency of $f_s$ samples per second, will result in a sampled sinusoid that appears as samples of a continuous-time sinusoid of frequency $|f_a |$ in the band $0 \to \frac{f_s}{2}$, where:
$$
|f_a |=|f-mf_s | \qquad \text{where} \qquad |f_a | \leq \frac{f_s}{2}
$$

Where $m$ is an integer.

E.g. a $6Hz$ sinewave sampled at $5Hz$ will get **folded** to $(6-5)Hz=1Hz$.

#### Anti-Aliasing Filter

To avoid distortion after sampling where $B < \frac{f_s}{2}$ the signal may need a low pass filter with cutoff frequency $\frac{f_s}{2}$ applied before sampling.

This results in a signal with no aliasing but with a loss of higher frequencies.

This is good because without the lowpass filter, the higher frequencies will be lost as well as distortion of the lignal at lower frequencies due to the overlapping samples not being the same as the original wave.

### Practical Sampling

Impluse trains aren't actually very practical sampling signals. In practise a train of pulses may be used instead. (This is like an ideal lowpass filter)

For the train of pulses used with a signal such as $sinc^2{5/pi t}$ with $X(\omega)=0.2\Delta \left( \frac{\omega}{20\pi}\right)$ the Fourier series is used again: 
$$
p_{T_s}(t)=C_0+\sum_{n=1}^{\infty} C_n \cos{n \omega_s t} \qquad \text{then} \qquad C_0=\frac{1}{4} \qquad \text{and} \qquad C_n=\frac{2}{n\pi}\sin{\left( \frac{n\pi}{4}\right) }
$$

Therefore:
$$
\overline{x}(t)=x(t)p_{T_s}(t)=\frac{1}{4}x(t)+C_1x(t)\cos{20\pi t}+C_2 x(t) \cos{40 \pi t} +C_3\cos{60 \pi t}+...
$$

$$
\overline{X}=\frac{1}{4}X(\omega)+\frac{C_1}{2}\left[ X(\omega -20\pi)+X(\omega+20\pi)\right] +\frac{C_2}{2}\left[ X(\omega -40\pi)+X(\omega+40\pi)\right] +\frac{C_3}{2}\left[ X(\omega -60 \pi)+X(\omega +60 \pi)\right] +...
$$

Which allows the use of a lowpass filter to recover $X(\omega)$.

### Ideal Signal Reconstruction

The process of reconstructing a continuous time signal from its samples is also known as **interpolation**.

The filter used for reconstruction muct have a gain of $T_s$ and a bandwidth of any value between $B$ and $(f_s - B)Hz$.

A good choice is the middle value $\gamma=frac{f_s}{2}=\frac{1}{2T_s}Hz$ or $\frac{\pi}{T_s}rads^{-1}$ giving a frequency response of: 
$$
H(\omega)=T_s rect{\left( \frac{\omega}{2\pi f_s}\right)}=T_s rect{\left( \frac{\omega T_s}{2\pi}\right) }
$$

In the time domain, the impulse response of this filter is given by: 
$$
h(t)=sinc{\left( \frac{\pi t}{T_s}\right) }
$$

For the Byquist sampling rate, $T_s=\frac{1}{2B}$, $h(t)=sinc{2\pi B t}$.

For all Nyquist sampling instants $t=\pm\frac{n}{2B}$, $h(t)=0$ except at $t=0$.

Each sample in $\overline{x}(t)$, being an impulse, generates a $sinc$ pulse of height equal to the strength of the sample when it is applied at the input of the filter exactly like **convolution with an impulse**. The addition of all $sinc$ impulses results in $x(t)$.

The filter output is: 
$$
x(t)=\sum_n x(nT_s)h(t-nT_s)=\sum_n x(nT_s)sinc{\left[ \frac{\pi}{T_s}(t-nT_s)\right] }
$$

In the case of the Nyquist sampling rate $T=\frac{1}{2B}$, the filter output becomes: 
$$
x(t)=\sum_n x(nT_s)h(t-nT_s)=\sum_n x(nT_s)sinc{(2\pi Bt-n\pi)}
$$

This is known as the interpolation formula.

### Practical signal reconstruction

In practise a sampling frequency higher than the Nyquist sampling rate is used to allow for the use of non ideal low pass filters.

According to Paley-Weiner criterion, any filter that has a fequency response which is zero above a certain frequency, is not resizable (i.e. all practical filters).

This implies that in practise it is impossible to perfectly recreate a signal from its samples.

However, a filter with gradual cuttoff charateristics is easier to realise than an ideal fitler which is impossible.

Furthermore, as sampling rate increases, the recovered signal approaches the desired signal more closely.

### Scalar Quantisation

The sampling theorem allows us to represent signals by means of samples.

In order to save this samples, they need to be converted from real values $x[n]$ to a format that is in a format that fits the memory model of a computer.

The process that maps the continuous set to a discrete (countable) set is called quantization.

Quantization is irreversible meaning that approximation errors are introduced.

Usually the number of quantisation levels $N$ is a power of $2$ so that each symbol can be represented by a stream of bits.

Typically each sample is quantized independently (**scalar quantisarion**). If the quantisation widths are equal then the quantisation is **uniform**. 
$$
\text{Sampling rate} \left( \frac{kbits}{s}\right) =f_s \cdot (number \; of \; quantisation \; levels)
$$

Where you assume that $B$ is some value above the maximum frequency.

#### Quantisation Error

Low rate quantisation introduces correlation between the quantisation error and the orginal signal.

This correlation leads to artifacting or distortion.



## Discrete Fourier Transforms

To perform spectral analysis on an incoming continuous time signal using computers:

- The signal must be windowed.
- The windowed signal must be sampled.
- A discrete Fourier Transform must be taken (on the **sampled**, **finitie-duration** signal).

For a signal bandwidth limited to $BHz$ it can be reconstructed from samples taken at $f_s > 2B$ and has signal spectrum from $-B \to B$ Hertz.

This $2B$ interval is known as the **spectral width**.

### Spectrum Sampling Theorem

The time sampling theorem has a dual, the spectral sampling theorem.

**The spectral sampling theorem states that the spectrum $X(\omega )$ of a signal $x(t)$, time limited to a duration of $\tau$ seconds, can be rconstructed from the samples of $X(\omega )$ taken at a rate of $R$ samples per $Hz$, where $R>\tau$.**

From this, the periodic extension of $x(t)$ with a period of $T_0 > \tau$ can be constructed into the periodic signal $x_{T_0}(t)$.

This periodic signal can be expressed using a fourier series: 
$$
x_{T_0}(t)=\sum_{n=-\infty}^{\infty}D_n e^{jn\omega_0 t} \qquad \text{where} \qquad \omega_0=\frac{2\pi}{T_0}
$$

$$
D_n =\frac{1}{T_0} \int_{0}^{T_0} x(t) e^{-jn\omega_0 t} \,d t = \frac{1}{T_0}\int_{0}^{\tau} x(t) e^{-jn\omega_0 t} \,d t =\frac{1}{T_0} X(n\omega_0)
$$

The result indicates that the coefficients of the Fourier Series for $x_{T_0}(t)$ are the values of $X(\omega)$ taken at integer multiples of $\omega_0$ and scaled by $\frac{1}{T_0}$.

This implies that the spectrum of the periodic signal $x_{T_0}(t)$ is the sampled version of the spectrum $X(\omega )$.

If the successive cycles of $x_{T_0}(t)$ don't overlap, $x(t)$ can be recovered from $x_{T_0}(t)$.\
This implies that $X(\omega)$ can be reconstructed from its samples.

The samples are separated by a fundamental frquency $f_0 = \frac{1}{T_0}Hz$ or $\omega_0 = 2\pi f_0 rads^{-1}$ of the periodic signal $x_{T_0}(t)$.

Therefore the recovery condition is: $T_0 > \tau \Rightarrow f_0 < \frac{1}{\tau} Hz$.

### Spectral Interpolation Formula

To reconstruct the spectrum from its samples, the samples must be taken at frequency intervals $f_0<\frac{1}{\tau} Hz$. If the sampling rate is $R$ then:
$$
R=\frac{1}{f_0}>\tau \text { samples/Hz}
$$

It has been proved that the signal interpolation formula can be used to recover a continuous signal from its sampled version and there is an equivalent spectral interpolation formula. Assuming that $x(t)$ is time-limited to $\tau$ and centered at $T_c$: 
$$
X(\omega)=\sum_{n=-\infty}X(n\omega_0)sinc{\left( \frac{\omega T_0}{2}-n\pi \right)} e^{-j (\omega - n\omega_0)T_c} \qquad \text{where} \qquad \omega_0=\frac{2\pi}{T_0} \qquad \text{and} \qquad T_0 > \tau
$$

#### Proof of Spectral Interpolation Formula

It is known that: 
$$
x_{T_0}(t)=\sum_{n=-\infty}^{\infty} D_n e^{jn\omega_0 t} \qquad \text{where} \qquad \omega_0 = \frac{2\pi}{T_0}
$$

Therefore: 
$$
\mathcal{F} \{x_{T_0}(t)\}=2\pi \sum_{n=-\infty}^{\infty} D_n \delta (\omega -n\omega_0)
$$

Since $x(t)$ can be rewritten $x(t)=x_{T_0}(t) \cdot rect{\left(\frac{t-T_c}{T_0} \right)} \mathbf{\underline{\overline{|1|}}}$ and $\mathcal{F}\left\lbrace rect{\left( \frac{t}{T_0} \right)} \right\rbrace =T_0 sinc{\left(\frac{\omega T_0}{2}\right) }$: 
$$
\mathcal{F} \left\lbrace rect{\left( \frac{t-T_c}{T_0}\right) }\right\rbrace =T_0 sinc{\left( \frac{\omega T_0}{2}\right) }e^{-j\omega T_c}
$$

From $\mathbf{\underline{\overline{|1|}}}$: 
$$
X(\omega)=\frac{1}{2\pi} \mathcal{F} \left\lbrace x_{T_0}(t)\right\rbrace \ast\mathcal{F}\left\lbrace rect{\left( \frac{t-T_c}{T_0} \right) }\right\rbrace
$$

$$
X(\omega)=\frac{1}{2\pi} 2\pi \left[ \sum_{n=-\infty}^{\infty} D_n \delta(\omega -\omega_0)\right] \ast T_0 sinc{\left( \frac{\omega T_0}{2}\right) }e^{-j\omega T_c}
$$

$$
X(\omega)= \sum_{n=-\infty} D_n T_0 sinc{\left[ \frac{(\omega-n\omega_0)T_0}{2} \right]}e^{-j(\omega -n\omega_0)T_c} \qquad \text{where} \qquad \omega_0=\frac{2\pi}{T_0} \qquad \text{and} \qquad T_0 > \tau
$$

Therefore: 
$$
X(\omega)=\sum_{-\infty} X(n\omega_0)sinc{\left(\frac{\omega T_0}{2}-n\pi \right) }e^{-j(\omega -n\omega_0)T_c}
$$

### Discrete Fourier Transform

Numerical computation of the Fourier Transform requires descrete samples since computers cannot work with contiuous samples.

Furthermore, the Fourier transform can only be calculated at some values of $\omega$.

For a timelimited signal $x(t)$ its spectrum $X(\omega )$ will not be bandlimited. The spectrum $\overline{X}(\omega)$ of the sampled signal $\overline{x}(t)$ consists of $X(\omega)$ repeating every $f_s Hz$ with $f_s=\frac{1}{T_s}$.

If the sampled signal is repeated periodically every $T_0$ samples/$Hz$ then rhe samples are spaced at $f_0=\frac{1}{T_0}$Hz.

Therefore, when a signal is sampled and periodically repeated, it's spectrum si also sampled and periodically repeated.

The number of samples of the discrete signal in one period is $N_0=\frac{T_0}{T}$ whilst the number of samples of the discrete spectrum in one period is $N'_0 =\frac{f_s}{f_0}$. It is seen that: 
$$
N'_0=\frac{f_s}{f_0}=\frac{\frac{1}{T}}{\frac{1}{T_0}}=\frac{T_0}{T}=N_0
$$

*The number of samples in a period of time is identical to the number of samples in a period of frequency.*

#### Aliasing and Leakage

Since $X(\omega)$ isn't bandlimtied, it will experience aliasing.

Furthermore if $x(t)$ is not time limited it'll need to be truncated with a window function. This will lead to a leakage effect similar to the time signal sampling.

#### Formal Definition of Descrete Fourier Transform

If $x(nT)$ and $X(r\omega_0)$ are the $n^{th}$ and $r^{th}$ samples of $x(t)$ and $X(\omega)$ then:
$$
x_n =Tx(nT)=\frac{T_0}{N_0}x(nT)
$$

$$
X_r=X(r\omega_0)\qquad \text{where} \qquad \omega_0=2\pi f_0 = \frac{2/pi}{T_0}
$$

It can be shown that $x_n$ and $X_r$ are related by the following: 
$$
X_r=\sum_{n=0}^{N_0 - 1} x_n e^{-j n r \Omega_0}
$$

$$
x_n=\frac{1}{N_0}\sum_{r=0}^{N_0 - 1} X_r e^{jrn \Omega_0} \qquad \text{where} \qquad \Omega_0=\omega_0 T =\frac{2\pi}{N_0}
$$

There are the Direct and Inverse Descrete Fourier Transforms.

The essential bandwidth $B$ is calculated by finding where the amplitude response drops to $1\%$.

*Note: For proof of DFT rlationships see Appendix of Lecture 14 of Signals and Systems.*



## Z-Transform

The Z transform can be derived from the Laplace transform.

If $x(t)$ is a discrete-time signal that's sampled every $T$ seconds: 
$$
x(t)=x_0 \delta (t) + x_1 \delta (t-T) + x_2 \delta (t-2T) + x_3 \delta (t-3T) + ...
$$

Recalling that in the Laplace domain, $\mathcal{L}\{\delta (t) \}=1$ and $\mathcal{L}\{\delta (t-T) \}=e^{-sT}$ then the Laplace transform of $x(t)$ is: 
$$
X(s)=x_0 + x_1 e^{-sT} + x_2 e^{-s2T} + x_3 e^{-s3T} + ...
$$

Defining $z=e^{sT}=e^{(\sigma + j\omega)T}=e^{\sigma T}\cos{\omega T}+je^{\sigma T}\sin{\omega T}$: 
$$
X[z]=x_0+x_1 z^{-1}+x_2 z^{-2}+x_3 z^{-3}+...
$$
From the Laplace time-shift property, $z=e^{sT}$ is time advance by $T$ seconds, where $T$ is the sampling period.

Therefore $z^{-1}=e^{-sT}$ corresponds to one sampling period delay.

As a result, all sampled data can be expressed in terms of $z$.

More formally, the **unilateral z-transform** of a causal sampled sequence: 
$$
x[n]=\{ x[0],x[1],x[2],x[3],... \}
$$

It is given by:

$$
X[z]=\sum_{n=0}^{\infty} x[n]z^{-n} \qquad where \qquad x_n = x[n]
$$

The **bilateral z-transform** for any sampled sequency is: 
$$
X[z]=\sum_{n=-\infty}^{\infty} x[n] z^{-n}
$$

### Comparison of Laplace, Fourier, and Z-transforms

|                                |                        **Definition**                        |                         **Purpose**                          |                       **Suitable for**                       |
| :----------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|     **Laplace Transform**      |       $X(s)=\int_{-\infty}^{\infty}x(t)e^{-st} \,d t$        | Converts integral differential equations to algebraic equations. | Continuous-time signal systems analysis. Stable or unstable systems analysis. |
|     **Fourier Transform**      | $X(\omega)=\int_{-\infty}^{\infty}x(t)e^{-j\omega t} \,d t$  | Converts finite energy signals to frequency domain representation. | Continuous-time, stable systems. Convergent signals only. Best for steady-state. |
| **Discrete Fourier Transform** | $X[r \omega_0]=\sum_{n=-\infty}^{N_0 -1} Tx[nT]e^{-jnr\Omega_0}$sampling period $\Omega_0=\omega_0 T$, $T=\frac{2\pi}{N_0}$ | Converts discrete time signals to discrete frequency domain. |                    Discrete-time signals.                    |
|        **Z-Transform**         |         $X[z]=\sum_{n=-\infty}^{\infty} x[n]z^{-n}$          |  Converts differential equations into algebraic equations.   |          Discrete-time systems and signal analysis.          |

### Solving Z-Transform questions

To solve z-transform questions, use the equation for the sum of an infinite geometric series:
$$
S=\sum_{i=0}^{\infty} a_i r^i = \frac{a_1}{1-r} 
$$

Where the ratio of convergence $|r|<1$ .

The values that the z-transform exists for are the Region-Of-Convergence, and are found by rearranging $|r|<1$ to $|z|>X$.

The region of convergence is a circle of radius $X$ within the z (complex) plane.

|                       $\mathbf{x[n]}$                        |                       $\mathbf{X[z]}$                        |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
|                        $\delta [n-k]$                        |                           $z^{-k}$                           |
|                           $nu[n]$                            |                     $\frac{z}{(z-1)^2}$                      |
|                            $u[n]$                            |                     $\frac{z}{(z-1)^2}$                      |
|                          $n^2 u[n]$                          |                   $\frac{z(z+1)}{(z-1)^3}$                   |
|                          $n^3 u[n]$                          |               $\frac{z(z^2 +4z _1)}{(z-1)^3}$                |
|                     $\gamma^{n-1}u[n-1]$                     |                     $\frac{1}{z-\gamma}$                     |
|                       $n\gamma^n u[n]$                       |               $\frac{\gamma z}{(z-\gamma)^2}$                |
|   $\frac{n(n-1)(n-2)...(n-m+1)}{\gamma^m m!}\gamma^n u[n]$   |                   $\frac{z}{(z-y)^{m+1}}$                    |
|               $|\gamma |^n \cos{\beta n} u[n]$               | $\frac{z(z-|\gamma|\cos{\beta})}{z^2-(2|\gamma|\cos{\beta})z+|\gamma|^2}$ |
|               $|\gamma |^n \sin{\beta n} u[n]$               | $\frac{z(z-|\gamma|\sin{\beta})}{z^2-(2|\gamma|\cos{\beta})z+|\gamma|^2}$ |
|         $r|\gamma |^n \cos{(\beta n +\theta)} u[n]$          | $\frac{rz(z\cos{\theta}-|\gamma|\cos{\beta-\theta})}{z^2-(2|\gamma|\cos{\beta})z+|\gamma|^2}$ |
| $r|\gamma |^n \cos{(\beta n +\theta)} u[n] \qquad\gamma = |\gamma |e^{j\beta}$ | $\frac{(0.5re^{j\theta)}z}{z-\gamma}+\frac{(0.5re^{-j\theta)}z}{z-\gamma^*}$ |
| $r|\gamma |^n \cos{(\beta n +\theta)} u[n]$$\qquad r=\sqrt{\frac{A^2 \|\gamma\|^2 + B^2 -2AaB}{\|\gamma\|^2-a^2}}$$\qquad \beta=\arccos{\frac{-a}{|\gamma|}}$$ \qquad \theta=\arctan{\frac{Aa-B}{A\sqrt{\|\gamma\|^2-a^2}}}$ |             $\frac{z(Az+B)}{z^2+2az+|\gamma|^2}$             |

The inverse z-transform is: 
$$
x[n]=\frac{1}{2\pi j}\oint X[z] z^{n-1} \,d z
$$

This is difficult to solve so similarly to the Laplace transform partial fractions can be used to work backwards, and then use the z-transform identities.

### Mapping from s-plane to z-plane

Since $z=e^{sT}=e^{(\sigma+j\omega)T}=e^{\sigma T}e^{j\omega T}$ where $T=\frac{2\pi}{\omega_s}$ the s-plane can be mapped to the z-plane.

For $\sigma=0$, $s=j\omega$ and $z=e^{j/omega T}$. Therefore the imaginary axis of the s-plane is mapped to the unit circle on the z-plane.

For $\sigma < 0$, $|z|=e^{\sigma T}<1$. Therefore, the left half of the s-plane is mapped to the inner part of the unit circle on the z-plane.

For $\sigma > 0$, $|z|=e^{\sigma T}>1$. Therefore the right half od the s-plane is mapped to the outer part of the unit circle on the z-plane.

### Finding the inverse z-transform in the case of complex poles

A discrete-time LTI system is stable if and only if the ROC of its system function $H(z)$ includes the unit circle, $|z|=1$.

A causal discrete-time LTI system with rational z-transform $H(z)$ is stable, if and only if all the poles of $H(z)$ lie inside the unit circle. e.g. they must have a magnitude smaller than $1$.
