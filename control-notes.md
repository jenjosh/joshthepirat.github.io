# Control Engineering Notes

[TOC]



## Mathematical models of dynamic systems

###Describing dynamic systems

Dynamic systems can be described with:

- **A system of ordinary differential equations**
  - The initial description of the system in terms of its inputs and outputs.
- **A transfer function model**
  - A single input, single output process described by a transfer function,  the ratio of the Laplace transform of output and input.
- **A state variable model**
  - a system of first order ordinary linear differential equations. Differential equation models can be reduced to this form by the introduction of the intermediate variables called states.

###The Laplace Transform

####Introduction to the Laplace transform:

The Laplace Transform for a causal signal $x(t)$ is defined as:
$$
X(s)=\mathcal{L}\{ x(t) \}=\int_{0}^{\infty}x(t) e^{-st} dt
$$
The Laplace transform is a linear transform:
$$
\mathcal{L} \{ k_1 x_1 (t) + k_2 x_2 (t) \} = k_1 \mathcal{L} \{ x_1 (t) \}+ k_2 \mathcal{L} \{ x_2 (t) \} 
$$
Important Laplace Transforms are:
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

#### Inverse Laplace Transform

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

#### Laplace Transform Properties

#####Time properties

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

#####Frequency properties

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

##### Scaling Property

$$
\mathcal{L} \{ x(at) \} = \frac{1}{a}X\left( \frac{s}{a} \right)
$$

The above shows that time compression of a signal by a factor a causes expansion of its Laplace transform in s-scale by the same factor.

#####Other Properties

|            $\mathbf{x(t)}$            |                       $\mathbf{X(s)}$                        |
| :-----------------------------------: | :----------------------------------------------------------: |
| $\int_{-\infty}^{t} x(\tau) \,d \tau$ |  $\frac{X(s)}{s}+\frac{1}{s} \int_{-\infty}^{0^-} x(t) dt$   |
|          $x(t-t_0)u(t-t_0)$           |              $X(s)e^{-st_0} \qquad t_0 \geq 0$               |
|            $x(t)e^{s_0 t}$            |                          $X(s-s_0)$                          |
|              $x(0^{+})$               |          $\lim_{s \to \infty} s X(s) \qquad (n>m)$           |
|              $x(\infty)$              | $\lim_{s \to 0} s X(s) \qquad$ poles of $sX(s)$ in the left hand plane |

#### Models for electric circuit components

- The model for a resistor:

$$
v(t)=R i(t) \Rightarrow V(s)=R I(s)
$$
- The model for a capacitor:

$$
i(t)=C \dot{v}(t) \Rightarrow V(s)=\frac{1}{sC} I(s)
$$
- The model for an inductor:

$$
v(t)=L \frac{\,d i(t)}{\,d t} \Rightarrow V(s)=sL I(s)
$$

##### Impedance

The impedance $Z(s)$ of an electrical component is the ratio of the Laplace transform of the voltage across the component to the Laplace transform of the current through the component, with all initial conditions assumed to be zero.

- For a resistor:

$$
Z(s)=R
$$
- For a capacitor:

$$
Z(s)=sL
$$
- For an Inductor:

$$
Z(s)=\frac{1}{sC}
$$

##### Transfer function

The transfer function $G(s)$ of a linear system is the ratio of the Laplace transform of the output to the Laplace transform of the input, with all initial conditions assumed to be zero.
$$
G(s)=\frac{Y(s)}{X(s)}
$$

##### Block Diagram reduction rules

1. Check for the blocks connected in series and simplify.
2. Check for the blocks connected in parallel and simplify.
3. Check for the blocks connected in feedback loop and simplify.
4. If there is difficulty with take-off point while simplifying, shift it towards right (modify it accordingly).
5. If there is difficulty with summing point while simplifying, shift it towards left (modify it accordingly).
6. Repeat the above steps till you get the simplified form (single block).



## State-variable models

A state variable model is a model where an $nth$ order differential equation is decomposed into a set of $n$ first order differential equations written in matrix vector form.  This is achieved by defining internal variables, called states, whose time evolution completely characterises the behaviour of the system.

### Standard state variable format

State-variable models have the form:
$$
\dot{x}(t)=Ax(t)+Bu(t)
$$

$$
y(t)=Cx(t)+Du(t)
$$

$$
x(0)=x_0
$$

Where $\dot{x}(t)$ is the state equation, $y(t)$ is the output equation, and $x(0)$ is the initial condition. Each of the variables in these equations are matrices of the following sizes:

|   $A:n\times n$   |  $x(t):n\times 1$  |
| :---------------: | :----------------: |
|  $B:n\times n_u$  | $u(t):n_u\times 1$ |
| $C:n_y \times n$  | $y(t):n_y\times 1$ |
| $D:n_y\times n_u$ |                    |

This is a block diagram for the state variable model.

![statevariableblock](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/statevariableblock.png)

#### Advantages of state variable models

-  Time-domain matrix methods lend themselves naturally to computer solution, especially for high order models.
- Matrix methods enable the transient response and system performance to be easily determined.
- They extend straightforwardly to multivariable systems, nonlinear systems, and time varying systems.

#### Simulation Diagrams

Simulation diagrams are block diagrams constructed to have a given transfer function. They have three elements:

- An integrator block. 
- A pure gain block.
- A sum block.

There are simulation diagrams that can be obtained from general transfer functions of the form:
$$
G(s)=\frac{y(s)}{u(s)}=\frac{b_{n-1}s^{n-1}+b_{n-2}s^{n-2}+...+b_0}{s^n+a_{n-1}s^{n-1}+a_{n-2}s^{n-2}+...+a_0}
$$
These are obtained by:

- Dividing the numerator and denominator by $s^n$:

$$
y(s)=\frac{b_{n-1}s^{-1}+b_{n-2}s^{-2}+...+b_0s^{-n}}{1+a_{n-1}s^{-1}+a_{n-2}s^{-2}+...a_0s^{-n}}u(s)
$$

- By setting $e(s)$ to:

$$
e(s)=\frac{u(s)}{1+a_{n-1}s^{-1}+a_{n-2}s^{-2}+...a_0s^{-n}}
$$

- It can be stated:

$$
y(s)=[b_{n-1}s^{-1}+b_{n-2}s^{-2}+...+b_0s^{-n}]e(s)
$$

$$
e(s)=u(s)-[a_{n-1}s^{-1}+a_{n-2}s^{-2}+...a_0s^{-n}]e(s)
$$

- This can then be turned into simulation diagrams by setting:

$$
y(s)=[b_{n-1}s^{-1}+b_{n-2}s^{-2}+...+b_0s^{-n}]e(s)
$$

- The simulation diagram of the transfer function:

![simdiagram1](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/simdiagram1.png)

- A modified simulation diagram of the transfer function:

![simdiagram2](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/simdiagram2.png)

- The state variables then satisfy:

$$
\dot{x}_1=x_2 \qquad \dot{x}_2 =x_3\qquad ... \qquad \dot{x}_{n-1}=x_n
$$

$$
\dot{x}_n=-a_0x_1-a_1x_2-...-a_{n-1}x_{n-1}-a_{n-1}x_n+u
$$

- While the output is:

$$
y=b_0x_1+b_1x_2+...+b_{n-1}x_{n-1}+b_{n-1}x_n
$$

- And in matrix form:

$$
\dot{x}=
\begin{bmatrix}
0 & 1 & 0 & ... & 0 \\
0 & 0 & 1 & ... & 0 \\
\vdots & \vdots & \ddots & \ddots & 0 \\
0 & 0 & ... & 0 & 1 \\
-a_0 & -a_1 & ... & -a_{n-2} & -a_{n-1}  
\end{bmatrix}x+ 
\begin{bmatrix}
0 \\ 0 \\ \vdots \\ 0 \\ 1
\end{bmatrix}u
$$

$$
y=\begin{bmatrix}
b_0 & b_1 & ... & b_{n-2} & b_{n-1}
\end{bmatrix}x
$$



### The matrix exponential function

If $A$ is a square matrix and $t$ denotes the time variable where $(At)^0$ is defined as the identity matrix $I$, then:
$$
e^{(At)}=\sum_{k=0}^{\infty}\frac{1}{k!}(At)^k
$$
The series will converge for any square matrix $A$ and any scalar $t$. Useful properties of the matrix exponential function are:
$$
e^0=I \qquad (1)
$$

$$
e^{T\Lambda T^{-1}}=Te^{\Lambda}T^{-1}\qquad (2)
$$

$$
e^{(\alpha + \beta)A}=e^{\alpha A}e^{\beta A} \qquad (3)
$$

$$
e^{-A}=(e^{A})^{-1} \qquad (4)
$$

$$
\frac{d}{\,d t}e^{At}=Ae^{At}=e^{At}A \qquad (5)
$$

$$
\mathcal{L}(e^{At})=(sI-A)^{-1} \qquad (6)
$$

#### Solving the state variable equations

A method for solving the state variable equations is as follows:

- For the state variable model:

$$
\dot{x}(t)=Ax(t)+Bu(t) \\
y(t)=Cx(t)+Du(t)
$$

- Suppose that $u(t)=0​$ for all $t​$:

$$
\dot{x}(t)=Ax(t) \qquad x(0)=x_0
$$

- Attempt a trial solution $x(t)=e^{At}x_0​$ and check this satisfied the conditions:

$$
\dot{x}(t)=Ae^{At}x_0=Ax(t) \qquad x(0)=e^0 x_0=x_0
$$

- When $u(t) \ne 0$:

$$
e^{-At}\dot{x}(t)=e^{-At}Ax(t)+e^{-At}Bu(t)
$$

- Use the properties of the matrix exponential function to rearrange the initial equation into the form: 

$$
y(t) = initial \; condition \; response \; + \; input \; response
$$

- For the above state variable model:
  - Use $(5)$ to get $\int_{0}^{t}e^{A\tau}Bu(\tau)\,d \tau$
  - Use $(1)$ to get $\int_{0}^{t}e^{-A\tau}Bu(\tau)\,d \tau$
  - Use $(4)$ and $(3)$ to get $x(t)=e^{At}x_0+\int_{0}^{t}e^{A(t-\tau)}Bu(\tau)\,d \tau$
  - This results in:

$$
y(t)=Ce^{At}x_0+\int_{0}^{t}Xe^{A(t-\tau)}Bu(\tau )\,d \tau +Du(t
$$

#### Stability and the matrix exponential

Consider the eigenvalue decomposition of $A=T\Lambda T^{-1}$, then using $(2)$, and then rearranging and simplifying:
$$
e^{At} = T e^{\Lambda t} T^{-1}
$$

- The response of the unforced system is:

$$
\dot{x}(t)=Ax(t)\Rightarrow e^{At}x_0=Te^{\Lambda t}T^{-1}x_0
$$

- It follows that:

$$
\lim_{t\to 0}x(t)=0, \forall x_0 \Leftrightarrow Re[\lambda_i(A)]<0, \forall i
$$

**The unforced system is stable if and only if all the eigenvalues of A lie in the left half of the complex plane.**

### Transfer function from state variable models

$$
\dot{x}(t)=Ax(t)+Bu(t) \\
y(t)=Cx(t)+Du(t)
$$

- Take the Laplace transforms:

$$
sx(s)=Ax(s)+Bu(s) \Rightarrow(sI-A)x(s)=Bu(s) \\
\Rightarrow x(s)=(sI-A)^{-1}Bu(s) \\ 
\Rightarrow y(s)=Cx(s)+Du(s) \\
\Rightarrow y(s)=[D+c(sI-A)^{-1}B]u(s)
$$

The transfer function from $u(s)$ to $y(s)$ is then:
$$
G(S)=[D+C(sI-A)^{-1}B]
$$
$(sI-A)^{-1}$ will exist for all values of $s$ which are not eigenvalues of $A$. The poles of $G(s)$ are $\lambda_i(A)$.



## System Responses

System responses use test signals  to compare the response of different system designs to these signals. The use of test signals is justified since there is a close correlation between the capability of systems to respond to actual input signals and the response characteristics to test signals.

### Test signals

The standard test signals are:

- The unit step function for modelling sudden disturbances:

$$
u(t)=1 \qquad t \ge 0 \Rightarrow \mathcal{L}\{u(t)\}=\frac{1}{s}
$$

- The unit ramp function for modelling gradually changing inputs:

$$
u(t)=t \qquad t \ge0 \Rightarrow \mathcal{L}\{u(t)\}=\frac{1}{s^2}
$$

- The sinusoidal functions are important in frequency response techniques:

$$
\cos{\omega t}=Re\; e^{j\omega t}\Rightarrow \mathcal{L}\{\cos{\omega t}\}=\frac{s}{s^2 +\omega ^2}
$$

$$
\sin{\omega t}=Im\; e^{j\omega t}\Rightarrow \mathcal{L}\{\sin{\omega t}\}=\frac{\omega}{s^2 +\omega ^2}
$$

####Response of first order systems
##### Method

When $G(s)=\frac{y(s)}{u(s)}$ the Laplace transforms of one of the test signal can be substituted into $u(s)$. This can then be rearranged to $y(s)$ and then inverse Laplace transform techniques can be used to find $y(t)$. This can then be analysed to see the effect of the test signal over time. The method can be summarised as follows:

1. Find the transfer function.
2. Multiply the transfer function by $\mathcal{L}\{ u(t)\}$ to get $y(s)$.
3. Use partial fraction expansion to find the inverse Laplace transform.

When the resulting equation is of the form:
$$
y(t)=K-Ke^{-\frac{t}{\tau}}
$$

- The first term is the steady state response and $K$ is called the steady-state value.
- The second term is called the transient response and $\tau$ is called the time constant of the system.
#####Time constant

- The exponential function decays to less than $2\%$ of its initial value within four time constants. 


- The output $y(t)$ reaches about $63\%$ of its final value when $t = \tau$.
- The time constant is the parameter characterizing the response to a step input of a first-order, linear time-invariant system.

#### Steady state response

Steady-state response can be generalized to transfer functions of any order. 
$$
y(s)=G(s)u(s)
$$
For a given transfer function $G(s)$, the DC gain of the system is $G(0)$. It can be found using the final value theorem.

- If the limit $\lim_{t \to \infty}y(t)$ exists then:

$$
\lim_{t \to \infty}y(t)=\lim_{s\to 0}sy(s)=\lim_{s\to 0}sG(s)u(s)
$$

- If $u(t)$ is a unit step:

$$
\lim_{t \to \infty}y(t)=\lim_{s\to 0}sG(s)\frac{1}{s}=\lim_{s\to 0}G(s)=G(0)
$$

#### Response of second order systems

#####Important setup

For a system where the differential equation relating the input $u(t)$ to the output $y (t)$ can be written as:
$$
ky(t)+B\dot{y}(t)+M\ddot{y}(t)=u(t)
$$

- The transfer function $G(s) = \frac{y (s)}{u(s)}$ can be written as:

$$
G(s)=\frac{1}{Ms^{2}+Bs+k}=\frac{\frac{1}{M}}{s^2+\frac{B}{M}s+\frac{k}{M}}=\frac{1}{k}\frac{\frac{k}{M}}{s^2+\frac{B}{M}s+\frac{k}{M}}
$$

- By setting:

$$
K=\frac{1}{k} \qquad \omega_n=\sqrt{\frac{k}{M}} \qquad \zeta=\frac{B}{2\sqrt{kM}}
$$

- $G(s)$ becomes:

$$
G(s)=K\frac{\omega_n^2}{s^2+2\zeta\omega_n s+\omega_n^2}
$$

The standard form for second order equations is:
$$
G(s)=K\frac{\omega_n^2}{s^2+2\zeta\omega_n s+\omega_n^2}
$$
$\zeta$ is the damping ratio,	 $\omega_n$ is the undamped natural frequency, 	$K$ is the DC gain.

Since $K$ only determines the DC magnitude of the response, it can be set to unity and $G(s)$ can be rewritten as:
$$
G(s)=\frac{\omega_n^2}{(s-p_1)(s-p_2)}
$$
Where $p_1, \; p_2=-\zeta \omega_n \pm \omega_n \sqrt{\zeta^2-1}$ and are the poles of $G(s)$.

The system characteristics depend on $p_1$ and $p_2$, since they are the only parameters that appear in the transfer function. The cases are:

- **Overdamped:** $\zeta > 1 \Rightarrow p_1$, $p_2=-\zeta \omega_n \pm \omega_n \sqrt{\zeta^2-1}$ are real, negative, and unequal.
- **Critically damped:** $\zeta = 1 \Rightarrow p_1$, $p_2=-\omega_n$ are real, negative, and equal.
- **Underdamped:** $0 \le \zeta < 1 \Rightarrow p_1$, $p_2=-\zeta \omega_n \pm j\omega_n \sqrt{1-\zeta^2}$ are complex conjugate and have negative real parts (zero real part if $\zeta = 0$).
- **Unstable:**  $\zeta < 0 \Rightarrow p_1$, $p_2=-\zeta \omega_n \pm \omega_n \sqrt{\zeta^2-1}$ have positive real parts.


##### Method

From this point, the method for finding the response is similar to first order systems:

1. Modify the transfer function for the specific case above.
2. Multiply the transfer function by $\mathcal{L}\{ u(t)\}$ to get $y(s)$.
3. Use partial fraction expansion to find the inverse Laplace transform.

##### Analysis

For the first three cases:

- The final value as $t \to \infty$ is $K$ for low pass systems, and $0$ for high and band pass systems. This is known as $H(0)$.
- The initial value as $t \to 0^+​$ is 0 for low pass systems, and $K​$ for high and band pass systems. This is known as $H(\infty)​$.
- Wherever $\omega_n$ occurs, it is multiplied by $t$. This means that if $\omega_n$ is scaled by a scalar $k_0$, the speed of the system is scaled by $k_0$, but the shape remains the same.

![stepresponses](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/stepresponses.png)

The graph above shows the step response as values of $\zeta$ vary. If $\zeta$ becomes negative then the oscillations would increase.

##### Time response specifications

For underdamped second order systems:

- The rise time is $T_r$.
- The peak value is $M_p$.
- The time to first peak is $T_p$.
- The steady state value is $y_{ss}$.
- The percentage overshoot is $\frac{M_p-y_{ss}}{y_{ss}}\times 100$.
- The settling time is $T_s$.
- The time required for the response to enter a $y_{ss}\pm d$ tube is $T_s$.
- The time constant is $\tau = \frac{1}{\zeta \omega_n}$

For over and critically damped systems, $M_p$ and $T_p$ are harder to find. In this case, $y(t)$ must be differentiated and equated to $0$. For the underdamped second order system, this gives:
$$
$T_p=\frac{\pi}{\sqrt{1-\zeta^2}\omega_n} \qquad M_p=1+e^{-\frac{\zeta \pi}{\sqrt{1-\zeta^2}}}
$$
For second order systems, the percentage overshoot only depends on $\zeta$. As $\zeta$ increases from $0$ to $1$:

- $M_p$, $T_s$ and the percentage overshoot decrease.
- $T_p$ and $T_r$ increase.

Therefore, a compromise must be found between:

- Tracking properties (measured by $T_s$ and \% overshoot).
- The speed of response (measured by $T_p$ and $T_r$).

#####Speed of response

For a system such that:
$$
G(s)=\frac{y(s)}{u(s)}=\frac{(s-z_1)(s-z_2)...(s-z_l)}{(s-p_1)(s-p_2)...(s-p_m)}
$$
Assuming that there are no repeated poles, the system response to $u(s)$ can be found by partial expansion and has the form:
$$
y(s)=\frac{r_1}{s-p_1}+\frac{r_2}{s-p_2}+...+\frac{r_m}{s-p_m}+a(s)
$$

$$
y(t)=r_1 e^{p_1 t}+r_2 e^{p_2 t}+...+r_m e^{p_m t}+a(t)
$$

Where $a(t)$ is the forced response.

The numerator and denominator of a transfer function are both real and therefore the poles and zeros must either be real or occur in complex conjugate pairs. A system is predominantly second order if:
$$
G(s)=a(s)+\frac{\alpha s+\beta}{s^2+bs+c}
$$
The poles of $a(s)$ that are located far into the left half plane compared with the roots of $s^2 + bs + c$ are called the dominant poles. The response associated with the poles of $a(s)$ will decay fast, and the response will be largely determined by the dominant poles.



## Stability - the Routh-Hurwitz stability criterion

Stability is important, however issues arise because the benefits of feedback are obtained by increasing the loop gain which usually tends to destabilise the system.

### Bounded-input bounded-output stability and Polynomials

A system is bounded-input bounded-output stable if for every bounded input, the output is bounded for all time. For an LTI system with transfer function:
$$
G(s)=\frac{\beta_m s^m + \beta_{m-1} s^{m-1}+...+\beta_1s+\beta_0}{\alpha_n s^n + \alpha_{n-1}s^{n-1}+...+\alpha_1 s+\alpha_0}
$$

- The denominator polynomial is called the characteristic polynomial.
- The roots of the characteristic equation are called the poles.
- The order of the system is the degree of the characteristic polynomial.

An LTI system is bounded-input bounded-output stable provided all its poles lie in the open left half–plane. If all its poles lie in the closed left half–plane and any poles that lie on the imaginary axis are simple, then it is marginally stable. If neither of these is the case then the system is unstable.

If all the roots are stable, all the coefficients will have the same sign.

### Routh-Hurwitz stability criterion

The Routh-Hurwitz stability criterion is an analytical procedure for determining if all roots of a polynomial lie in the left half-plane, without evaluating them.

- For the $nth$ order polynomial:

$$
P(s)=s^n +\alpha_{n-1}s^{n-1}+...+\alpha_1 s+\alpha_0
$$

- The first 2 rows of the Routh array are formed from the characteristic polynomial coefficients:

$$
P(s)=s^n +\alpha_{n-1}s^{n-1}+\alpha_{n-2}s^{n-2}+\alpha_{n-3}s^{n-3}+\alpha_{n-4}s^{n-4}+...+\alpha_1 s+\alpha_0
$$

$$
\left. \begin{matrix}
s^n \\ s^{n-1} \\ s^{n-2} \\ s^{n-3} \\ \vdots \\ s^2 \\ s^1 \\ s^0
\end{matrix}\right| \begin{matrix}
\alpha_n & \alpha_{n-2} & \alpha_{n-4} & \alpha_{n-6} & \dots \\
\alpha_{n-1} & \alpha_{n-3} & \alpha_{n-5} & \alpha_{n-7} & \dots \\
b_1 & b_2 & b_3 & b_4 & \dots \\
c_1 & c_2 & c_3 & c_4 & \dots \\
\vdots & \vdots & \vdots & \vdots & \ddots \\
k_1 & k_2 & & & \\
l_1 & & & & \\
m_1 & & & & \\
\end{matrix}
$$

- The remaining rows are formed as follows:

$$
b_1=-\frac{1}{\alpha_{n-1}}\left| \begin{matrix}
\alpha_n & \alpha_{n-2} \\ \alpha_{n-1} & \alpha_{n-3} \\ \end{matrix}\right|  \qquad b_2=-\frac{1}{\alpha_{n-1}}\left| \begin{matrix}
\alpha_n & \alpha_{n-4} \\ \alpha_{n-1} & \alpha_{n-5} \\ \end{matrix}\right|
$$

$$
c_1=-\frac{1}{b_1}\left| \begin{matrix}
\alpha_{n-1} & \alpha_{n-3} \\ b_{1} & b_{2} \\ \end{matrix}\right|  \qquad c_2=-\frac{1}{\alpha_{n-1}}\left| \begin{matrix}
\alpha_{n-1} & \alpha_{n-5} \\ b_1 & b_3 \\ \end{matrix}\right|
$$

$$
\vdots
$$

$$
m_1=-\frac{1}{l_1}\left| \begin{matrix}
k_1 & k_2 \\ l_1 & 0 \\
\end{matrix}\right|
$$

Once the Routh array is completed, the Routh-Hurwitz Criterion states:

**The number of unstable roots is equal to the number of sign changes in the first column of the array**

There are two types of problem that require modifications to this method:

- Case 2 Problems are: If the first element of a row is zero, with at least one nonzero element in the same row, the procedure is modified by replacing that first element with a small number $\epsilon$ such that $|\epsilon|<<1$ and proceeding as before.
- Case 3 Problems are: If every entry in a row is zero, the last modification will not give useful information and another modification is needed before proceeding. 

An even polynomial is one in which the powers of $s$ are even integers or zero. The roots of an even polynomial are symmetric with respect to both the real and imaginary axes. At best, an even polynomial has marginally stable roots.

For case 3 problems $P(s)$ is either unstable or marginally stable because: $P_a (s)$ is a factor of $P(s)$ where $P_a (s)$ is either an odd or an even polynomial.

### Stability for first and second order systems

- For a first order system with characteristic polynomial:

$$
P(s)=\alpha_1 s +\alpha_0
$$

​	Stability requires both coefficients to have the same sign.

- For a second order system with characteristic polynomial:

$$
P(s)=\alpha_2 s^2 +\alpha_1 s+\alpha_0
$$

​	The Routh array is:
$$
\left. \begin{matrix}
s^2 \\ s \\ 1
\end{matrix}\right| \begin{matrix}
\alpha_2 & \alpha_0 \\
\alpha_1 & \\
\alpha_0 & \\
\end{matrix}
$$
A necessary and sufficient condition for stability is that all coefficients have the same sign. Therefore for first and second order systems, stability properties can be determined by inspection. For higher order systems, the only conclusion is that a necessary condition  for stability is that all the coefficients have the same sign.




## Nyquist Analysis

Frequency response methods can be used assess stability of a system with feedback. An example of this is Nyquist analysis.

A Nyquist plot of $G(j\omega)$ is a plot of the imaginary part of $G(j\omega)$ against the real part of $G(j\omega)$ as $\omega$ is varied from zero to infinity. 

###Sketching from gain and phase information (from Bode plot)

This method is good when there are no integrator terms.

1. Find the transfer function and rewrite it so that $s=j\omega$.
   - Corner frequencies are the roots of the numerator (zeroes) and denominator (poles).
2. Sketch the magnitude response:
   - Gradient will **decrease after every pole** corner frequency.
   - Gradient will **increase after every zero** corner frequency.
   - Mark and calculate the gain at $\omega = 0$.
   - Ignore dB because it's a sketch.
3. Sketch the phase response:
   - Phase usually starts at zero. 
     - If the transfer function has an integrator term $\frac{1}{s}$ which means an $(s+0)$ term in the denominator then the plot will start at $-90^{\circ}$ instead. 
     - For every $(s-a)$ term in the numerator or denominator, the phase will start $180^{\circ}$ lower, but not vice versa. 
     - Remember that $-360^{\circ}=0^{\circ}$
   - At each **pole corner frequency it will decrease** by $n\times90^{\circ}$ where $n$ is the order of that corner frequency, e.g for $G(s)=\frac{3}{(s+1)^2}$ the phase will decrease by $2\times 90^{\circ}=180^{\circ}$ at the corner frequency $1$.
   - At each **zero corner frequency it will increase** by $n\times90^{\circ}$ where $n$ is the order of that corner frequency.
   - The middle of the plot will be the geometric mean of all the poles in the denominator $\sqrt[n]{p_1 \times p_2 \times ... \times p_n}$. This allows you to plot a smooth curve of the phase response to see how it acts.
4. Sketch the Nyquist plot:
   - Look at the phase plot, see where the phase has been plotted to assess the **quadrants in which the Nyquist plot lies**.
   - Mark the **gain at $\omega = 0$**. 
   - Mark the **gain at the geometric mean**. Plot this on the diagram at it's respective value ($90^{\circ}, 180^{\circ},...$) but make note of the quadrants.
   - See **how the origin is approached**. Does it approach from the negative phase etc. Mark this so the direction of the plot is known.
   - See **what happens to the gain, and phase**. Do they always decrease etc. If they always decrease then make sure this is represented on the graph:
     - Gain is represented by distance from the origin (if it decreases then the plot moves towards the origin and vice versa).
     - Phase is the angle from the origin to any point (if it decreases it the plot is clockwise and vice versa).
   - If there was an **integrator term, the graph will start at infinity in the direction of whatever the starting phase was.** See later section for more information.
   - If it isn't obvious which quadrant the plot starts in, then take the Taylor expansion of the denominator terms, multiply with the numerator and expand out. Then ignore all the higher order $j\omega$ (because only low frequency values matter at the beginning) so that what is left is a complex number in the form $a+bj\omega$. From this it can be seen which quadrant the plot starts in. Alternatively just find the phase for a small value of $\omega$ such as $\omega = 0.1$.
   - The Nyquist plots will **have a mirror image in the real axis** so draw this too. See later section if there are integrator terms. 
   - The direction of change of Nyquist plots is linked directly to bode diagrams.
     - At any point from the bode diagram, it can be seen how the gain and phase are changing.
     - Using knowledge of Nyquist plots, the direction of gain and phase can be plotted for any point.
     - The average between these two directions will be the direction that the Nyquist plot goes through this point.
   - Any extra values such as corner frequencies can be added for more detail.
   - If a delay is added $e^{-sT}$ then the Nyquist plot will never reach the origin and will spiral round it repeatedly. This is exacerbated when $T$ is greater.

### Link between Nyquist diagrams and closed loop behaviour

For good closed loop behaivior the Nyquist diagram needs to stay with $-1+0j$ as far to the left as possible. If it is too close it will oscillate and if it passes with $-1+0j$ to the right then it will beome closed loop unstable. 

###Nyquist Contour

![yquistcontou](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/nyquistcontour.png)

The Nyquist contour is a path travelling from $0-\infty j$ to $0+\infty j$ , followed by a semicircular arc $R$, so that as $R \to \infty$ the contour $\Gamma$ covers the whoole of the right hand plane - the region of instability.

If this contour is mapped thorugh the function $1+G(s)​$ then it yields a plot of $1+G(s)​$ is the complex plane. THis means that the number of clock-wise encirclements of the origin must be the number of zeros of $1+G(s)​$ in the right hand plane minus the number of poles of $1+G(s)​$ in the right hand complex plane.

### Sketching complete Nyquist diagrams with integrator terms

In complete Nyquist diagrams with integrator loops the Nyquist diagram will "start" at infinity. In reality, the nyquist diagram is a loop. This is because using the Nyquist contour, it can be seen that when reaching $|\infty|$ a right turn must be made which will then curve around to reach the other $|\infty|$ term just like in the Nyquist contour. 

Therefore, when sketching nyquist diagrams with integrators, this must be taken into account. when reaching the two $\infty$ points, the diagram must curve round to the right.

For terms with multiple integrators, the diagram must turn $180^{\circ}$ for each one thus meaning that it must make a full loop (or more) before joining back to the other side of the diagram. If it joined back up as soon as it could then it wouldn't make the satisfactory number of right hand turns.

###Nyquist Criterion

#### Encirclement

Reminder that a right half plane zero or pole is in the form $(s-a)$.

- For every right half plane zero, there is clockwise encirclment of the origin by the Nyquist Diagram.
- For every right half plane pole, there is an anticlockwise encirclment of the origin.

These can cancel eachother out.

#### Simple Version

For a simple loop:

![asicfeedback](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/basicfeedbackn.png)

Where $G(s)=\frac{N(s)}{D(s)}$ where $N$ and $D$ are the zero and pole polynomials, the closed loop transfer function is:
$$
H(s)=\frac{G(s)}{1+G(s)} \Rightarrow 1+G(s) = 1+\frac{N(s)}{D(s)}=\frac{N(s)+D(s)}{D(s)}=\frac{p_{c}}{p_{o}}
$$
This shows the open $p_o$ and closed $p_c$ loop poles. Since only right hand plane factors lead to encirclements, let $n$ be an right hand plane hole. This then means $1+G(s)$ must give $n_c - n_o$ clockwise encirclements of the origin meaning that $G(s)$ must give $n_c-n_o$ encirclements of the $-1+0j$ point (or if there is a gain term $K$, then encirclements of $-\frac{1}{K}+0j$. 

The Nyquist Stability Criterion states that if:

- $Z$ is the number of poles of clockwise encirclements of $-1$
- $P$ is the number of right hand plane open loop poles $(n_o)$.
- $N$ is the number of right hand plane closed loop poles$(n_c)$.

$$
Z=N-P
$$

This can be explained more formally as follow.

####The Nyquist Stability Criterion

If the Nyquist contour is mapped though $G(s)$ then the result is the Nyquist plot of $G(s)$. By counting the resulting contour's encirclements of $-1$, we find the difference between the number of poles and zeros in the right half complex plane of $1+G(s)$. Recalling that the zeroes of $1+G(s)$ are the poles of the closed loop system, and noting that the poles of $1+G(s)$ are the same as the poles of $G(s)$, the Nyquist Criterion states:

**Given a Nyquist contour $\Gamma_s$, let $P$ be the number of poles of $G(s)$ encircled by $\Gamma_s$, and $Z$ be the number of zeroes of $1+G(s)$ encircled by $\Gamma_s$.  $Z$ is the number of poles of the closed loop system in the right half plane. The resultant contour in the $G(s)$ plane $\Gamma_{G(s)}$ shall encircle (clockwise) the point $-1+0j$, $N$ times such that $N=Z-P$**

For closed-loop stability of a system, the number of closed-loop roots in the right half of the s-plane must be zero. The right-half-plane poles represent the instability. Hence the number of counter clockwise encirclements around $-1+0j $ must be equal to the number of open loop poles in the right half plane.

##### Nyquist criterion for systems with poles on the imaginary axis (integrators)

For an integrator $\frac{1}{s}$ as $\omega\to 0 $ the gain $|G(s)| \to \infty$. Therefore the Nyquist contour has two right hand right angle turns at $\omega=0^+$ and $\omega=0^-$. The Nyquist diagram must have right hand right angle turns at the corresponding values of $\omega$. Therefore the Nyquist contor must move $180^{\circ}$ anticlockwise around the origin as shown in the above image. This means that sketching the Nyquist diagram is more complicated.

#### Stability requirements

The criterion therefore implies that if a system is stable then $N=0$. Therefore for stability:
$$
Z=-P
$$
Most systems are open loop stbale so $P=0$ whuch means that no encirclements are required, otherwise $Z$ counter clockise encirclements are needed for stability..

### Applying the Nyquist stability criteria

For a system with a gain block $K$, the system may be stable or unstable depedning on the value of $K$.

![asicfeedback](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/anotherbasicfeedback.png)

####Open Loop Stable

If the system is open loop stable (no $(s+a)$ term in the numerator) then no encirclements are required. Therefore to determine whether the system is stable or not, the value for $K$ needs to be found for the point at which the intersection with the real axis is greater than $-1+0j$. 

- This is the point where $\angle(G)=180^{\circ}$.
- Find the argument by summing the arguments of each terms in the numebrator and denominator as needed.

$$
\angle(aj\omega+b)=\arctan{\left(\frac{b}{a}\right)}
$$

- Rearrange this for $\omega$ and substitute this into the equation for $|G|$. The $j$ is gotton rid of by squaring the $j\omega$ term to get $\omega$ and then square-rooting the whole numerator/denominator.
- This will leave an equation in terms of $K$ and this just has to be less than $-1$. This can then be rearranged to find $K$

#### Open Loop Unstable

In this case count the right half plane poles $(s-a)$ to find the value for $P$. The value for $K$ must cause $Z$ to become equal to $-P$. Therefore $K$ must be increased until it intersects the real axis to the left hand side of $-1+0j$. 

The process for finding this value is similar to the open loop stable method.

Sometimes if the Nyquist diagram instersects the real axis at zero and is and is anticlockwise then the system is closed loop unstable for all positive values $K$. Check this by drawing the Nyquist diagram and looking at it's shape.

#### When there are integrators

Integrators are treated as left hand poles so aren't included in the $Z=N-P$ calculation.

For systems with multiple integrators where the Nyquist plot intersects at zero then the gain cannot be changed by to make the system stable.

For systems where the real axis is intercepted in the negative plane, the gain can be changed to make the system stable.

### Gain and Phase Margins

####Gain Margin

- The gain margin is the factor by which the loop gain of a stable closed-loop system must be changed to make the system marginally stable. This is a measure of how much extra gain the loop can tolerate without losing stability. The larger this value, the more extra gain the loop can tolerate and the more robust the design.

- If a Nyquist of $G(s)$ intersects the negative real axis at $-\alpha$ then the gain margin is $\frac{1}{\alpha}$.

- If a Nyquist of $G(s)$ intersects the negative real axis at more than one point then the gain margin is determined by the point that results in the smallest gain margin.

- As a rule of thumb, for many control systems, a gain margin of $2 \;(\approx 6dB) $has been observed to give moderately damped response.

####Phase Margin

- The phase margin of a stable closed-loop system is the minimum angle by which the Nyquist diagram must be rotated to intersect the $−1+0j$ point.
- The phase margin is a measure of how much additional phase-lag the loop can tolerate (without changing the gain) before the onset of instability.
- For many control systems, a phase margin of about $45^{\circ}$ is considered adequate.
- To find this:
  1. Set $|G(s)|=1$ and solve for $\omega$.
  2. Substitute this into $\angle G(s)$ to find the phase margin. If it is negative, then add $180^{\circ}$ to make it positive.
  3. From here it can be decided whether the phase margin is adequate.




## Frequency response design Methods

For a typical feedback system:

![eedbackcomple](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/feedbackcomplex.png)

The components of the feedback system are:

- Open Loop gain: $Q(s)$.
- Reference signal: $r(s)$.
- Output signal: $y(s)$.
- Error signal: $e(s)$.
- Output disturbance: $d(s)$.
- Sensor noise: $n(s)$.

When designing such a system the following objectives must be considered:

- Steady state accuracy.
- Output disturbance rejection.
- Sensor noise attenuation.
- Transient Response and Stability margins.

The importance of these can be found by looking at the relevant parts of the system for each of them.

### System type

The type number of a system is the number of poles at the origin of the s-plane.

If there is an integrator term then the type increases.

###Steady state accuracy

The sensitivity and closed loop transfer functions add up to $1$. Therefore they both cannot be small or large at the same frequency.
$$
H(j\omega)=\frac{Q(j\omega)}{1+Q(j\omega)}\qquad S(j\omega)=\frac{1}{1+Q(j\omega)}\qquad H(j\omega )+S(j\omega)= 1
$$
For good steady state accuracy $|S(j\omega_0)|<<1$ therefore $|Q(j\omega_0)|>>1$.

For good steady state accuracy,:

- **Large open loop gain over a wide range of frequencies is required.**
- **Equivalently, good steady state accuracy requires large closed-loop bandwidth.**

### Output disturbance rejection

Good output disturbance rejection is compatible with good steady-state accuracy, as it too requires:

- **Large open loop gain over a wide range of frequencies is required.**
- **Equivalently, good steady state accuracy requires large closed-loop bandwidth.**

### Sensor noise attenuation

For good sensor noise attenuation:

- **Good sensor noise attenuation requires small closedloop bandwidth.**
- **Small open-loop gain at high frequencies is sufficient for good sensor noise attenuation.**
- **This is in conflict with the previous two requirements.**

####Design trade-offs

For most control systems the references and output disturbances are slow and therefore require low frequency signals, whilst the sensor noise is a fast high frequency signal. This conflict can be resolved by requiring:

- Large gain at low frequencies.
- Small gain at high frequencies.

### Transient response and Stability margins

- Large gain at high frequencies tends to destablise the closed-loop because the gain margin decreases.
- Along with this a large phase lag at high frequencies has the same effect since it reduces the phase margin.
- Therefore stability of the system sets a limit on the closed-loop bandwidth.

As $\zeta\to0$ in the step response:

- The response becomes faster and more oscillatory (smaller $T_r$ and higher percentage overshoot).
- The system bandwidth increases.

To improve a response, the gain $K$ can be decreased to increase the stability margins and rise time and reduce the overshoot and bandwidth. To improve the response further, dynamic compensation is required.

### Dynamic compensation

#### Phase-lead controllers

A phase-lead controller has transfer function:
$$
K_c(s)=K\frac{1+\frac{s}{\omega_0}}{1+\frac{s}{\omega_p}}=K\frac{\omega_p}{\omega_0}\frac{s+\omega_0}{s+\omega_p}\qquad \qquad \mathbf{\omega_0 < \omega_p}
$$

- This increases the gain at frequecies above $\omega_p$ but introduces phase lead between $\omega_0$ and $\omega_p$.
- Since the phase lead is stabilising, $\omega_0$ and $\omega_p$ should be chosen in the crossover frequency range where $|Q(j\omega)| \approx 1$.
- It is difficult to balance the destabilising increase in gain and the stabilising phase-lead.

#### Phase-lag controllers

A phase-lag controller has transfer function:
$$
K_c(s)=K\frac{1+\frac{s}{\omega_0}}{1+\frac{s}{\omega_p}}=K\frac{\omega_p}{\omega_0}\frac{s+\omega_0}{s+\omega_p}\qquad \qquad \mathbf{\omega_p < \omega_0}
$$

- This reduces the gain at frequencies above $\omega_0$ but introduces phase-lag between $\omega_p$ and $\omega_0$.
- Since the phase lead is stabilising, $\omega_0$ and $\omega_p$ should be chosen in the low to middle frequency range where $|Q(j\omega)| >> 1$.
- $K$ is chosen to improve steady-state accuracy by increasing the gain at low frequencies.

#### Lag-lead controllers

A lag-lead controller combines phase-lag and phase-lead features and has the transfer function:
$$
K\frac{1+\frac{s}{\omega_{0_1}}}{1+\frac{s}{\omega_{p_1}}}\frac{1+\frac{s}{\omega_{0_2}}}{1+\frac{s}{\omega_{p_2}}}=K\frac{\omega_{p_1}}{\omega_{0_1}}\frac{\omega_{p_2}}{\omega_{0_2}}\frac{s+\omega_{0_1}}{s+\omega_{p_1}}\frac{s+\omega_{0_2}}{s+\omega_{p_2}}\qquad \qquad \mathbf{\omega_{p_1} < \omega_{0_1}, \;\omega_{0_2} < \omega_{p_2}} 
$$

#### PI controllers

PI controllers are a special form of phase-lag controllers made up of a proportional term and an integrating term. The transfer function is:
$$
K_c(s)=K_p+\frac{K_i}{s}=K_p\frac{s+\frac{K_i}{K_p}}{s}
$$

#### PD controllers

PD controllers are a special form of phase-lead controllers made up of a proprtional term and a derivative term. The transfer function is:
$$
K_c(s)=K_p+K_ds=K_d\left(s+\frac{K_p}{K_d}\right)
$$

#### PID controllers

PID controllers combine PI and PD controllers to create a special form of the lag-lead controller. It will increase the system type by 1. It's transfer function is:
$$
K_c(s)=K_p+\frac{K_i}{s}+K_d{s}
$$

- The **proprtional** term causes the system to change in proportion to the error. 
  - This can be bad if the system has different inputs because the error will be the same but requires a different $K_p$.
  - A proportional controller will reduce the rise time and the steady state error (but never eliminate it)
- The **integral** term increases the action in relation to not only the error but also for the time it has persisted. 
  - This means that if the proprtional term cannot bring the error to zero then the gain will be increased as time passes.
  - A pure I controller could reduce the error to zero but it would react solwly at the start and the end causing oscillations. It would aslso continue to increase even if the error is decreasing.
  - Integral controllers eliminate the steady state error but make the transient response worse.
- The **derivative** term does not consider the error but the rate of change of error.
  - It dampens the response thus inproving the transient response and stability, as well as reducing the overshoot.
  - Since it doesn't consider the error, it cannot bring it to zero.

For more information see Root-Locus design.

### Ziegler-Nicolas tuning rules for practical controller design

For systems that are:

- Stable.
- Type 0 (have no free inteegrators).
- Overdamped (have real poles and zeros).

A simple practical design technique for tuning a compensator can be used that doesn't require a model for the plant. This is called the Ziegler-Nichols tuning rule and is summarised as follows:

1. Apply a proportional compensator and adjust the gain until the closed loop becomes marginally stable (when the closed-loop system just starts to oscillate). Let $K_{po}$ be the value of this gain and $T_o$ be the period of oscillations. These can be found using a Routh-Hurwitz array.
2. The compensator is defined by either:
   - P: $K(s)=0.5K_{po}$.
   - PI: $K(s)=0.45 K_{po}+\frac{0.54\left(\frac{K_{po}}{T_o}\right)}{s}$.
   - PID: $K(s)=0.6K_{po}+\frac{1.2\left(\frac{K_{po}}{T_o}\right)}{s}+0.075K_{po}T_o s$.
   - SInce the plant is assumed to be type 0, intergal action is needed for zero steady state error against a step reference, thus ruling out a PD controller.




## Root-Locus Analysis

For a simple feedback system such as:

![asicfeedback](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/anotherbasicfeedback.png)

The closed loop tranfer function is:
$$
H(s)=\frac{G(s)K(s)}{1+G(s)K(s)}
$$
The closed loop poles are the roots of the characteristic equation (denominator). The response of LTI systems is dependednt on the location of it's poles.

Analysis is concerned with how the loaction of the closed loop poles is determined by $K(s)$.

SUppose the feedback compensator becomes constant $K(s)=K$. The characteristic equation becomes:
$$
1+KG(s)=0
$$
**The root locus of a system  is a plot of the roots of the systems characteristic equation (closed loop poles) as $K$ varies from $0$ to $\infty$.**

Inspection of this allows the possible location of the closed loop poles to be found as a function of $K$, which will allow the determination of the nature of the response of the closed-loop system for all possible values of $K$.

A point $s$ lies of the root loci if $1+KG(s)=0$. This means the:

- Magnitude critereon: $K=\frac{1}{|G(s)|}$.
- The angle criterion: $\angle G(s)=\pm r\pi \qquad r=1,3,5,...$

The angle criterion is independent of $K$ so it can be used to determine whether a point $s$ lies on the root loci and also to plot the root loci. The magnitude criterion can then be used to find the value of $K$ corresponding to a point on the root loci.

By selecting a point along the root locus that coincides with a desired damping ratio and natural frequency, a gain $K$ can be calculated and implemented in the controller. 

In general a point lies on the root loci if:
$$
\sum_i(\text{angles from numerator})-\sum_i(\text{angles from denominator})=\pm r \pi \qquad r=1,3,5,...
$$

### Rules for plotting the Root Loci

1. If $G(s)$ has $n$ poles then there are $n$ root loci.
2. The root loci are symmetric with respect to the real axis.
3. If $G(s)$ has $\alpha$ zeros at infinity, the root loci will approach $\alpha$ assymptotes as $K\to\infty$. THe angles of the assymptotes are:

$$
\phi_A=\pm\frac{r\pi}{\alpha}, \qquad r=1,3,5,...
$$

​	These asymptotes intersect the real axis at:
$$
\sigma_A=\frac{\sum(\text{poles})-\sum(\text{zeros})}{\text{number of poles}-\text{number of zeros}}
$$

4. The root locus includes all points on the real axis to the left of an odd number of poles and zeros.
5. The breakaway points $\sigma_b$ are:

$$
\frac{dG(s)}{ds}=0
$$

​	The root loci plot will go through these points.

6. The root loci departs from a pole $p_j$ at an angle:

$$
\theta_d = \sum_i \theta_{zi}-\sum_{i\ne j}\theta_{pi}+r\pi
$$

​	and arrives at a zero $z_j$ at an angle:
$$
\theta_a = \sum_i \theta_{pi}-\sum_{i\ne j}\theta_{zi}+r\pi
$$

7. For negative $K$ the rules are the same but anything that was odd is even ($r=0,2,4,...$).

### The magnitude criterion

If a point $s_1$ lies on the root locus, there must exist $K>0$ such that one of the closed-loop poles is equal to $s_1$. $K$ can be found using the magnitude criterion:
$$
K=\frac{1}{|G(s_1)|}
$$
The range of $K$ for closed-loop stability is best detemined via the Routh-Hurwitz stability criterion.



## Root Locus Design

If the open-loop response of a system is unsatisfactory, feedback compensation can improve the response. Root locus principles can be used for:

- Closed loop pole placement.
- Improving stability and transient response.
- Improving stead-stae response.

### Compensation

Different compensators have contributions to the angle criterion and can be used to shift the root locus towards the left or right in the complex plane, or improve transient response by improving closed-loop stability.

- Dominant pole specifications can be satisfied by choosing closed loop poles that will adjust the current specifications.
- Other specifications can be filled but must make sure they don't affect other specifications.
- Pole position can be determined by the angle criterion, angle contribution can be changed by moving the poles and zeroes. If a zero is required, but negative angle contribution is not, place that zero near the origin.
- $K$ can be found using the gain criterion.

###Rate Feedback

In systems that are based on the performance the dominant closed loop poles, the introduction of an extra hole by the compensator can cause increases in overshoot. The positive angle contribution comes from the compensator zero, therefore it would be preferable to introduce a zero without introducing a pole.

This can be done using rate feedback as well as output feedback. Ther rate feedback is introduced in between each term:
$$
\frac{1}{s(s+a)} \Rightarrow \frac{1}{s+a} \; \; \left( \frac{FEED}{BACK} \right) \; \; \frac{1}{s}
$$


In other words, the terms are no longer in series, they are in parallel.

This will reduce to a non-unity feedback loop with a different characteristic equation.  

This can be combined with other compensation techniques. $K_v$ can be determined using the location of zeros and the angle criterion. $K$ can be found like before.

This will reduce the overshoot but slow the resonse

### PID controller design

1. Design a PI controller to improvethe steady state properties of the feedback loop.
2. Absorb the PI controller into $G(s)$ and design a PD controller to improve the transient response.
3. The overall controller can then be divided into $K_p$, $K_i$, $K_d$.
4. An additional pole is generall intrdouced to limit high frequency gain.

### Controller realisation

The controllers can all be realised using electronic components.

![IDcircui](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/PIDcircuit.png)

This circuit has the transfer function:
$$
\frac{V_o(s)}{V_i(s)}=-\frac{Z_f(s)}{Z_i(s)}=-\frac{C_i\left(s+\frac{1}{R_iC_i}\right)}{C_f\left(s+\frac{1}{R_fC_f}\right)}=-\frac{C_is+\frac{1}{R_i}}{C_fs+\frac{1}{R_f}}
$$
The various controllers can be realised by using a suitable choice of components:

- **Pure Gain**: Remove $C_f$ and $C_i$ $(C_f=C_i=0)$: $\frac{V_o(s)}{V_i(s)}=-\frac{R_f}{R_i}$.
- **Phase-lead**: Choose $R_iC_i>R_fC_f$.
- **Phase-lag**: Choose $R_iC_i<R_fC_f$.
- **PI**: Remove $R_f$ $(R_f\to \infty)$: $\frac{V_o(s)}{V_i(s)}=-\frac{C_is+\frac{1}{R_i}}{C_fs}$
- **PD**: Remove $C_f$ $(C_f \to 0)$: $\frac{V_o(s)}{V_i(s)}=-R_f\left(C_is+\frac{1}{R_i}\right)$.