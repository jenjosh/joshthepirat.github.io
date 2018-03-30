# Complex Variables and Laplace Transforms

[TOC]

## Cauchy-Riemann Equations

### Derivation of Cauchy-Riemann Equations

Functions of the complex variable $z=x+yi$ can be written $w=f(z)$:
$$
f(z)=u(x,y)+v(x,y)
$$
Where $u(x,y)$ is the real part, and $v(x,y)$ is the complex part.

Complex numbers are hard to integrate and differentiate because $z$ varies in a plane instead of a line. This causes $dz$ to be a vector and herefore it's direction needs to be known.

First the limit of integration in the $x$ direction is taken:
$$
\frac{\,d f(z)}{\,d z}=\frac{\partial u}{\partial x}+i \frac{\partial v}{\partial x}=u_x+iv_x
$$
Then in the $y$ direction:
$$
\frac{\,d f(z)}{\,d z}=\frac{\partial u}{\partial (i y)}+i \frac{\partial v}{\partial (i y)}=-i u_y+iv_y
$$
If the limits are equal in both directions:
$$
u_x = v_y \quad \quad \quad u_y = -v_x
$$
These are the Cauchy-Riemann equations. If they both hold at point $z$ then $f(z)$ is differentiable at $z$. If  $f(z)$ is differentiable at all points in a neighbourhood of a point $z_0$ then $f(z)$ is said to be analytic at $z_0$.

If $u_xx + u_yy=0$ and $v_xx + v_yy=0$ then $u$ and $v$ are solutions of Laplace's Equation and are known as **Harmonic**. It is also said that $u(x,y)$ and $v(x,y)$ are conjugate to one another.

### Orthogonality

In regions of analyticity, curves of constant $u$ and curves of constant $v$ are always orthogonal. This can be shown as follows:

From the chain rule:
$$
du=\frac{\partial u}{\partial x} \,d x + \frac{\partial u}{\partial y} \,d y
$$
Since on curves of constant $u$ then $du = 0$, and if constant $v$ then $dv = 0$ the gradients of families of curves like this are:
$$
\left. \frac{dx}{dy}  \right| _{u=const} = -\frac{u_x}{u_y} \qquad \qquad \left. \frac{dx}{dy}  \right| _{v=const} = -\frac{v_x}{v_y}
$$
Thus giving:
$$
\left. \frac{dx}{dy}  \right| _{u=const} \quad  \times \quad \left. \frac{dx}{dy}  \right | _{v=const}    =\frac{v_x u_x}{v_y u_y}
$$
If $f(z)​$ is analytic in a region $R​$ then the Cauchy-Riemann equations hold, $u_x = v_y​$ and $u_y = -v_x​$ and the previous equation becomes:
$$
\left. \frac{dx}{dy}  \right| _{u=const} \quad  \times \quad \left. \frac{dx}{dy}  \right| _{v=const}    = -1
$$
Thus meaning the curves are orthogonal.



## Mappings

### Conformal Mappings

A complex function $w=f(z)$ can be thought of as mapping from the $z$-plane to the $w$-plane. Depending on $f(z)$ the mapping may not be unique e.g. $\pm z_0$ both map to $w_0$ if for example $w=z^2$. 

A mapping is said to be conformal if it preserves both angles in magnitude and sense. Moreover, a mapping has a *fixed point* when $w=f(z)=z$. The following theorem is stated without needing proof:

**The mapping defined by an analytic function $w=f(z)$ is conformal except at points where $f'(z)=0$.**

### Mapping lines to circles and vice versa

The general equation for straight lines and circles in the $z$-plane can be written as: 
$$
\alpha (x^2 + y^2 )+\beta x + \gamma y +\Delta = 0
$$
Where $\alpha$, $\beta$, $\gamma$, and $\Delta$ are constants. If $\alpha = 0$ this represents a straight line but when $\alpha \ne 0$ represents a circle, the previous equation when written in terms of $z$ becomes:
$$
\alpha |z|^2 +\frac{\beta}{2} (z + z^* )+ \frac{\gamma}{2i}(z-z^*)+\Delta
$$
Since:
$$
x^2 + y^2 = |z|^2 \qquad \qquad x = \frac{1}{2}(z + \overline{z}) \qquad \qquad y = \frac{1}{2}(z - \overline{z})
$$
Transforming to an equation $w$ and $w^*$ through $w=\frac{1}{z}$ and $w^*=\frac{1}{z^*}$ becomes:
$$
\frac{\alpha}{ww^*}+\frac{\beta}{2}\left( \frac{1}{w}+\frac{1}{w^*}\right) +\frac{\gamma}{2i} \left( \frac{1}{w}-\frac{1}{w^*}\right)+\Delta
$$
Or:
$$
\alpha+\frac{\beta}{2}(w+w^*)-\frac{i\gamma}{2}(w^*-w)+\Delta ww^*=0
$$
Since $w=u+iv$ we have:
$$
\alpha +\beta u -\gamma v +\Delta (u^2+v^2)=0
$$
This represents a family of circles in the $u  v$ plane when $\Delta \ne 0$ and a family of lines when $\Delta = 0$. Notice, that when $\alpha \ne 0$ and $\Delta \ne 0$ then the mapping maps circles to circles but a family of lines in the $z$-plane $(\alpha =0 )$ also maps to a family of circles in the $w$-plane. However, there is also the case of a family of circles in the $z$-plane for which $\Delta = 0$ which map to a family of lines in the $w$-plane. 

Thus it can be concluded conclude that $w=\frac{1}{z}$ maps lines to circles tand vice versa, but not necessarily lines to lines and circles to circles.

#### Mobius Transformation

The **Mobius** transformation is:
$$
w=\frac{az+b}{cz+d} \qquad \qquad \qquad ad \ne bc
$$
This includes cases such as:

- $w=\frac{1}{z}$ when $a=d=0$, $\frac{b}{c}=1$. 
- $w=\frac{1}{z-1}$  where $a=0$, $b=1$, $c=1$, $d=-1$.

The Mobius transformation can be rewritten as:
$$
w=c^{-1}\left\lbrace a+\frac{bc-ad}{cz+d} \right\rbrace
$$
For various special cases this represents specific transformations:

- $w=z+b; \quad (a=d=1, \; c=0)$ - Translation.
- $w=az; \quad (b=c=0, \; d=1)$ - Contraction/Expansion and Rotation.
- $w=\frac{1}{z}; \quad (a=b=0, \; b=c)$ - Maps Lines/Circles to Lines/Circles.

Thus a Mobius transformation maps lines/circles to lines/circles with contraction/expansion, rotation, and translation on top.

###Mappings of the type $w=\frac{e^z-1}{e^z+1}$

A map $w=\frac{e^z - 1}{e^z + 1}$ which can be re-written as:
$$
e^z = \frac{1+w}{1-w}=\frac{(1+u+iv)(1-u+iv)}{(1-u)^2 +v^2}
$$
Real and Imaginary parts give:
$$
e^x \cos{y} = \frac{1-u^2 -v^2 }{(1-u)^2 + v^2} \qquad \qquad \qquad e^x \sin{y} = \frac{2v}{(1-u)^2 + v^2}
$$
From these it can be concluded that:

1. The family of lines $y = n \pi$ in the $z$-plane map to the line $v =0$ for $n$ integer. Thus an infinite number of horizontal lines in the $z$-plane all map to the $u$-axis in the $w$-plane.
2. The family of lines $y=\frac{1}{2}(2n+1) \pi$ in the $z$-plane map to the unit circle $u^2+v^2=1$ in the $w$-plane.

### Conformal Mapping and Fluid Mechanics



An example of conformal mappings being important is fluid mechanics. In $2D$ fluid incompressible dynamics the velocity field $\mathbf{u}(x,y)$ must satisfy the incompressibility condition $div\mathbf{u} = 0$, in which case $\mathbf{u}$ can be written as $\mathbf{u} = (−\psi_y, \psi_x)$ where $\psi$ is known as a stream function. If the fluid is also irrotational (no vorticity) then $curl\mathbf{u} = 0$. Therefore:
$$
\begin{vmatrix}
\mathbf{\hat{i}} & \mathbf{\hat{j}} & \mathbf{\hat{k}} \\
\partial_x & \partial_y & \partial_z \\
-\psi_y & \psi_x & 0
\end{vmatrix}=0
$$
In which case: 
$$
\psi_{xx}+\psi_{yy}=0
$$
This means that $\psi (x,y)$ satisfies Laplace's equation and is therefore harmonic. It also means that there must be a conjugate function, designated as $\phi (x, y)$, the potential, that satisfies the Cauchy-Riemann equations,  $\phi_x=\psi_y$ and $\phi_y=\psi_x$, and that $\phi$ must also be harmonic. Now the 2D incompressible ideal fluid dynamics can be cast is the language of complex mappings:
$$
w=f(z)=\phi (x,y)+i\psi(x,y)
$$
With $\phi=u$ and $\psi =v$, mappings can be chosen $w=f(z)$ to solve flows around complicated shapes. This provides the following result:

**Harmonic functions remain harmonic under a conformal mapping.**

#### Proof

Let $H$ be a harmonic function in the $z$-plane, therefore satisfying:

$$
H_{xx}+H_{yy}=0
$$
Taking $w=u+iv$ and f(z) being analytic then the Cauchy-Riemann equations hold: 
$$
u_x=v_y \qquad v_x=-u_y \qquad u_{xx}+u_{yy}=0 \qquad v_{xx}+v_{yy}=0
$$
Using the chain rule:
$$
H_x=u_x H_u + v_x H_v \qquad H_y = u_y H_u + v_y H_v 
$$
$$
H_{xx}=u_{xx} H_u + v_{xx} H_v +u_x^2 H_{uu} +v_x^2 H_{vv} +2u_x v_x H_{uv}
$$
$$
H_{yy}=u_{yy} H_u + v_{yy} H_v +u_y^2 H_{uu} +v_y^2 H_{vv} +2u_y v_y H_{uv}
$$
Meaning that:
$$
H_{xx}+H_{yy}=(u_{xx}+u_{yy})H_u+(v_{xx}+v_{yy})H_v +(u_x^2+u_y^2)H_{uu}+(v_x^2+v_y^2)H_{vv}+2(u_xv_x+u_yv_y)H_{uv}
$$
From the Cauchy-Riemann equations, $u_x^2+u_y^2=v_x^2+v_y^2$ and $u_xv_x+u_yv_y=0$, hence:
$$
H_{xx}+H_{yy}=(u_x^2+u_y^2)(H_{uu}+H_{vv})
$$
Thus if $H$ satisfies Laplace's equation in the $z$-plane $H_{xx}+H_{yy}=0$ then in the $w$-plane it must satisfy Laplace's equation:
$$
H_{uu}+H_{vv}=0
$$

The most famous mapping is **Joukowski's** aerofoil transformation:
$$
w=z+\frac{1}{z}
$$
Firstly polar coordinates $$x=r\cos{\theta} \text{ and } y=r\sin{\theta}$$ are used so that $$z=re^{i\theta}$$ and:
$$
u+iv=\left( r+\frac{1}{r} \right) \cos{\theta}+i\left( r-\frac{1}{r} \right) \sin{\theta}
$$
Therefore, with:
$$
a=r+\frac{1}{r}\qquad b=r-\frac{1}{r}
$$
$u$ and $v$ will satisfy the equation for an ellipse:
$$
\frac{u^2}{a^2}+\frac{v^2}{b^2}=1
$$
Conclusions to be drawn are:
- Circles $|z|=t=const$ centered at $z=0$ in the $z$-plane map to ellipses in the $w$-plane.
- The special circle $r=1$ for which $a=2$ and $b=0$ maps to the red segment of the $u$-axis $-2 \leq u \leq 2$.




## Contour Integration

###Cauchy's Theorem
To integrate a complex function, contour equations are used. For a closed contour $C$ enclosing a region $R$ in the $z$-plane around which the line integral is considered in the counter-clockwise direction:
$$
\oint_C F(z)\,d z
$$
With:
$$
F(z)=u+iv \qquad z=x+iy
$$
The equation becomes:
$$
\oint_C F(z) \,d z = \oint_C (u+iv)(\,d x+i \,d y)=\oint_C (u \,d x -v \,d y)+i\oint_C (v \,d x + u \,d y)
$$
Green's Theorem in a plane says that fpr differentiable functions $P(x,y)$ and $Q(x,y)$:
$$
\oint_C(P \,d x +Q \,d y)=\iint_R (Q_x-P_y)\,d x\,d y
$$
For the real part, $P=u$ and $Q=-v$ so that $Q_x-P_y=-v_x-u_y$.
For the imaginary part, $P=v$ and $Q=u$ so that $Q_x-P_y=u_x-v_y$. Therefore:
$$
\oint(u \,d x -v \,d y)=\iint_R(-v_x-u_y)\,d x \,d y
$$
$$
\oint(v \,d x +u \,d y)=\iint_R(u_x-v_y)\,d x \,d y
$$
Which turns the equation into:
$$
\oint_C F(z) \,d z=-\iint_R (v_x +u_y) \,d x \,d y +i \iint_R (u_x-v_y) \,d x \,d y
$$
If $F(z)$ is analytic everywhere within and on $C$ then $u$ and $v$ must satisfy the Cauchy-Riemann equations, in which case both the real and imaginary parts of the uquation must be zero.
This is Cauchy's Theorem:

**If $F(z)$ is analytic everywhere within and on a closed, piecewise smooth contour $C$ then $\oint_C F(z) \,d z = 0$.**

###Poles and Residues
If a complex function fails to be analytic at a point, we cal this point a *singularity*. These can take many forms but the simplest class are called **Simple Poles**. A function $F(z)$ has a simple pole at $z=a$ (which could be real) if it can be written in the form:
$$
F(z)=\frac{g(z)}{z-a}
$$
Where $g(z)$ is analytic at $z=a$. Likewise, $F(z)$ has a pole of multiplicity $m$ at $z=a$ if it can be written in the form:
$$
F(z)=\frac{g(z)}{(z-a)^m}
$$
Where, again, $g(z)$ is analytic at $z=a$, and $m=1, 2, 3, 4, ...$ (when $m=2$ there is a double pole, etc.)
While all poles are singularities, not all singularities are poles. For instance, $\ln{z}$ has a singularity at $z=0$ but this is not a pole. Similarly, $z=a$ is not a pole when $m$ iis not an interger: $f(z)=\frac{z^2}{\sqrt{z-1}}$

**Definition:**  The residue of $F(z)$ at a simple pole $z=a$ is:
$$
\lim_{z \to a} \{(z-a)F(z) \}=\lim_{z \to a} \left\lbrace (z-a)\frac{g(z)}{z-a} \right\rbrace = g(a)
$$
\textbf{Definition: } The residue of $F(z)$ at a pole of multiplicity $m$ at $z=a$ is:
$$
\lim_{z \to a} \left\lbrace \frac{1}{(m-1)!}\frac{\,d^{m-1}}{\,dz^{m-1}}[(z-a)^m F(z)] \right\rbrace =\lim_{z \to a} \left\lbrace \frac{1}{(m-1)!} \frac{\,d^{m-1}}{\,dz^{m-1}} \left[ (z-a)^m \frac{g(z)}{(z-a)^m} \right]   \right\rbrace =\left. \frac{1}{(m-1)!}\frac{\,d^{m-1}g}{\,d z^{m-1}} \right|_{z=a} 
$$
*Note: a funtion may have many poles and each pole has its own residue.*
###The residue of $F(z)=\frac{h(z)}{g(z)}$ when $g(z)$ has a simple zero at $z=a$
Taylor series exist for analytic functions, much as for functions of a single variable. Expanding $g(z)$ about its zero at $z = a$ in a Taylor series:
$$
g(z)=g(a)+(z-a)g'(a)+\frac{1}{2}(z-a)^2g''(a)+...
$$
Noting that $g(a)=0$ there is a residue at $z=a$:
$$
\lim_{z \to a}\left\lbrace \frac{(z-a)h(z)}{g(z)} \right\rbrace 
$$
$$
\lim_{z \to a}\left\lbrace \frac{(z-a)h(z)}{g(a)+(z-a)g'(a)+\frac{1}{2}(z-a)^2g''(a)+...} \right\rbrace 
$$
$$
\lim_{z \to a}\left\lbrace \frac{h(z)}{g'(a)+\frac{1}{2}(z-a)g''(a)+...} \right\rbrace =\frac{h(a)}{g'(a)}
$$
If $z=a$ were a double pole, then $g'(a)=0$ and the method work with the obvious extension, and so on for poles of higher multiplicity.
###The Residue Theorem
Cauchy's Residue Theorem states that:

**If the only singularities of $F(z)$ with $C$ are poles then:**
$$
\mathbf{\oint_C F(z) \,d z = 2\pi i \times \{Sum \; of \;  the \; residues\; of\; F(z)\; at \; its\; poles\; within\; C\} }
$$
###Improper Integrals
Integrals of the type:
$$
\int_{-\infty}^{\infty} f(x) \,d x \qquad \int_{-\infty}^{\infty} f(x) \sin{x} \,d x \qquad \int_{-\infty}^{\infty} f(x) \cos{x} \,d x
$$
Are all instances of real integrals of the type:
$$
\int_{-\infty}^{\infty}e^{i m x }F(x) \,d x \qquad \text{where} \qquad m\geq 0
$$
And the residue theorem can be used to evaluate them provided that $F(z)$ has certain convergence properties: these are called improper integrals because of the infinite nature of their limits. 

Formally they are written as:
$$
\int_{-\infty}^{\infty}e^{i m x}F(x) \,d x = \lim_{R \to \infty} \int_{-R}^{R} e^{i m x} F(x) \,d x
$$
The main idea is to consider a class of complex integrals:
$$
\oint_{C} e^{i m z} F(z) \,d z
$$
Where $C$ consists of the semi-circular arc. The two essential parts are the arc of the semicircle of radius $R$ denoted by $H_R$ and the real axis $[−R, R]$. Hence:
$$
\oint_{C} e^{i m z}F(z) \,d z = \int_{-R}^{R} e^{i m x} F(x) \,d x + \int_{H_R} e^{i m z} F(z) \,d z
$$
Where the left hand side of the right hand side is a real integral and the right hand side of the right hand side is a complex integral.
In principle the closed complex integral over $C$ on the left hand side can be evaluated by the Residue Theorem. The next aim is to evaluate the real integral on the right hand side in the limit as $R \to \infty$. \\This requires a result which is called Jordan’s Lemma.
###Jordans Lemma
####The Lemma
Jordan’s Lemma deals with the problem of how a contour integral behaves on the semi-circular arc ${H^{+}}_{R}$ of a closed contour $C_{}$.

Jordans Lemma states that:

**If the only singularities of $F(z)$ are poles, then:** 
$$
\mathbf{\lim_{R \to \infty}\int_{H_R} e^{i m z}F(z) \,d z = 0}
$$
**Provided that $m>0$ and $|F(z)| \to 0$ as $R \to \infty$. If $m=0$ then a faster convergence to zero is required for $F(z)$.**
####Proof
Since $H_R$ is a semicircle $z=Re^{i\theta}=R(\cos{\theta}+i\sin{theta})$ and $\,d z=iRe^{i\theta} \,d \theta$:
$$
\lim_{R \to \infty}\left| \int_{H_R} e^{i m z} F(z) \,d z \right| \lim_{R \to \infty}\left| \int_{H_R} e^{imR\cos{\theta}-mR\sin{\theta}} F(z)Re^{i \theta} \,d \theta \right| \leq \lim_{R \to \infty} \int_{H_R} e^{-mR\sin{\theta}}|F(z)|R \,d \theta
$$
having recalled that $|e^{iα}| = 1$ for any real $\alpha$ and $\int f(z) \,d z ≤ \int |f(z)| \,d z$. Note: that in the exponential term on the right hand side, $$\sin{\theta} > 0$$ in the upper half plane. Hence, provided $m > 0$, the exponential ensures that the right hand side is zero in the limit $R \to \infty$.
####Remarks
1. When $m > 0$ forms of $F(z)$ such as $F(z) = \frac{1}{z}$, $F(z)=\frac{1}{z+a}$ or rational functions of $z$ such as $F(z) =\frac{z^p ...}{z^q ...}$ (for $0 ≤ p < q$ and $p$ and $q$ integers) will all converge fast enough as these all have simple poles and $|F(z)| \to 0$ as $R\to \infty$.
2.  f however $m=0$ then a modification is needed: e.g. if $F(z)=\frac{1}{z}$ then $|F(z)| \to 0$ but $\lim_{R \to \infty} z|F(z)|=1$. The restriction on integers $p$ and $q$ need altering to $0 \leq p < q-1$ which excludes cases like $F(z)=\frac{1}{z}$, $F(z)=\frac{1}{z+a}$.
	. For $m < 0$ to ensure that the exponential is decreasing for $R \to \infty$ we need $\sin{θ} < 0$. This is	true in the lower half plane. Hence in this case we take our contour in the lower half plane (call this $H^−_R$ as opposed to $H^+_R$ in the upper) but still in an anti-clockwise direction.

A contour in the lower $\frac{1}{2}$-plane with semi-circle $H^−_R$ taken in the counter-clockwise direction which is used for cases when $m < 0$. 
The conclusion is that:

**If $F(z)$ satisfies the conditions for Jordans Lemma then: **
$$
\mathbf{\int_{-\infty}^{\infty}e^{i m x}F(x) \,d x =2 \pi i \times \; Sum \; of \; the \; residues \; of \; the \; poles \; of \;}
$$
$$
\mathbf{ e^{imz}F(z) \; in \ the \; upper \; \frac{1}{2}-plane.} 
$$
###Poles on the Real Axis
When an integrand has a pole on the real axis this causes problems by sitting on the semicircular contour, because Cauchy’s Residue theorem only applies to poles \textit{within} the contour. The trick is to change the contour to include or exclude the pole on the axis. For example:
To calculate an improper integral of the type (e.e where there is a pole at the origin):
$$
\int_{-\infty}^{\infty}\frac{f(x) \,d x}{x} 
$$
The following must be considered:
$$
2 \pi i \times [Sum \; of\; residues\; in\; upper\; half-plane\; and\; at\; the\; origin]=\oint_C \frac{f(z) \,d z}{z} = \mathcal{I} 
$$
And split the contour into four integrals (main semicircle $H^+_R$ radius $R$, small semicircle around the origin $H^+_r$ radius $r$, and lines that were the straight edge of the semicircle$H_r$, and $H_R$)
$$
\mathcal{I}=\int_{-R}^{-r}\frac{f(x)\,d x}{x} +\int_{H_r} \frac{f(z) \,d z}{z} +\int_{r}^{R} \frac{f(x) \,d x}{x}+\int_{H_R} \frac{f(z) \,d z}{z}
$$
For the last of the four integrals, Jordans lemma gives zero as $R \to \infty$. The first and third integral give in the limit:
$$
\lim_{\substack{r\to 0 \\ R\to \infty}}\int_{-R}^{-r}\frac{f(x)\,d x}{x} + \int_{r}^{R}\frac{f(x) \,d x}{x}=\int_{-\infty}^{\infty}\frac{f(x)\,d x}{x}
$$
What’s new here is what happens to the second integral, around the small indented semi-circle $H^+_r$, as $r_{} \to 0$.
###Integrals around the unit circle
Considering integrals of the type:
$$
\int_{0}^{2\pi} f(\cos{\theta},\sin{\theta})\,d \theta
$$
The idea is best illustrated by an example.
For example:
$$
I=\int_{0}^{2\pi}\frac{\,d \theta}{a+\cos {\theta}}
$$
Take $C$ as the unit circle $z=e^{i\theta}$. Therefore, $\,d z=ie^{i\theta} \; \,d \theta=iz\,d \theta\Rightarrow\,d \theta = \frac{\,d z}{iz}$. Recall that:
$$
\cos{\theta}=\frac{e^{i \theta}+e^{-i \theta}}{2}=\frac{1}{2}\left( z+\frac{1}{z} \right) 
$$
with a similar identity available for $\sin{\theta}$, so that:
$$
I=\oint_C \frac{\,d z}{iz(a+\frac{1}{2}(z+\frac{1}{z}))}=-2i \oint_C \frac{\,d z}{z^2 +2az+1}
$$
The next task is to determine the roots of $z^2+2az+1=0$:
$$
z=\frac{-2a \pm \sqrt{4a^2-4}}{2}=-a \pm \sqrt{a^2 - 1}
$$
Note that for $a>1$, whilse $z_1 -a+\sqrt{a^2-1}$ lies within $C$, the other root, $z_2=-a-\sqrt{a^2-1}$ lies outside. Therefore the pole at $z_2$ is excluded and the residue of the integrand at $z_1$ is computed:
$$
\lim_{z \to z_1}(z-z_1)\frac{1}{z^2+2az+1}=\lim_{z \to z_1}(z-z_1)\frac{1}{(z-z_1)(z-z_2)}=\lim_{z \to z_1}\frac{1}{z-z_2}=\frac{1}{z_1-z_2}=\frac{1}{2\sqrt{a^2-1}}
$$
The residue theorem then gives:
$$
I=(2\pi i) \times (-2\pi i) \times (Residue \; at \; z_1)=\frac{2\pi}{\sqrt{a^2 - 1}}
$$
###An application to Fourier Transforms
Applying this to the Fourier Transform of $f(t)=\frac{1}{1+t^2}$ as an example:
$$
\overline{f}(\omega)=\int_{-\infty}^{\infty}\frac{e^{i\omega t}}{1+t^2}\,d t
$$
The need for Jordan’s Lemma arises (with the necessity for upper and lower half-plane contours) because $\omega$ takes both positive and negative values. It obviously plays the role of $−m$ in Jordan’s Lemma so the calculation needs to be split into two halves: take a contour in the upper half-plane $H^+_R$ for $\omega < 0_{}$ and take a contour in the lower half-plane $H^-_R$ for $\omega > 0$. Hence we need to consider the complex plane where the real axis is the $t$-axis with the pair of complex integrals:
$$
\int_{H^+_R}\frac{e^{-i\omega z}}{1+z^2}\,d z \; \; \;(\omega<0)\qquad \qquad \int_{H^-_R}\frac{e^{-i\omega z}}{1+z^2}\,d z \; \; \; (\omega >0)
$$
Using the residue theorem and Jordans Lemma on $H^+_R$ with a simple pole at $z=i$ to obtain, in the limit $R \to \infty$:
$$
2\pi i \left( \frac{e^{\omega}}{2 i} \right)=\int_{-\infty}^{\infty} \frac{e^{-i \omega t}}{1+t^2} \,d t \; \; \; (\omega < 0) 
$$
And on $H^-_R$ with a simple pole at $z=-i$, in the limit $R \to \infty$:
$$
2\pi i \left( -\frac{e^{-\omega}}{2 i} \right)=\int_{\infty}^{-\infty} \frac{e^{-i \omega t}}{1+t^2} \,d t \; \; \; (\omega > 0) 
$$
Note that the integral is reversed because og the contour in the lower half plane. Arriving at the result:
$$
\overline{f}(\omega)=\int_{-\infty}^{\infty}\frac{e^-i\omega t}{1+t^2}\,d t=\pi \left\lbrace \begin{matrix} e^{\omega} & \quad \omega < 0 \\ e^{-\omega} & \quad \omega > 0 \end{matrix}\right. \quad =\pi e^{-|\omega |}
$$

##Laplace Transforms
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
####Important Laplace Transforms:

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

####Time properties

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

####Frequency properties

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

####Other Properties

|            $\mathbf{x(t)}$            |                       $\mathbf{X(s)}$                        |
| :-----------------------------------: | :----------------------------------------------------------: |
| $\int_{-\infty}^{t} x(\tau) \,d \tau$ |  $\frac{X(s)}{s}+\frac{1}{s} \int_{-\infty}^{0^-} x(t) dt$   |
|          $x(t-t_0)u(t-t_0)$           |              $X(s)e^{-st_0} \qquad t_0 \geq 0$               |
|            $x(t)e^{s_0 t}$            |                          $X(s-s_0)$                          |
|              $x(0^{+})$               |          $\lim_{s \to \infty} s X(s) \qquad (n>m)$           |
|              $x(\infty)$              | $\lim_{s \to 0} s X(s) \qquad$ poles of $sX(s)$ in the left hand plane |

###Alternative for type $\mathcal{L}^{-1}\left[ \frac{1}{(s^2+1)^2}\right]$ and $\mathcal{L}^{-1}\left[ \frac{s}{(s^2+1)^2}\right]$
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

###Initial and Final values Theorems
####Initial Value Theorem
So long as the Laplace transforms of $x(t)$ and $\frac{dx(t)}{dt}$ exist, and the power of the numerator of $X(s)$ is less than the power of its denominator:
$$
\lim_{t \to 0}x(t)=x(0^+)=\lim_{s \to \infty} sX(s)
$$
####Final Value Theorem
So long as the Laplace transforms of $x(t)$ and $\frac{dx(t)}{dt}$ exist, and the poles of $sX(s)$ are all on the left plane or origin:
$$
\lim_{t \to \infty}x(t)=x(\infty)=\lim_{s \to 0} sX(s)
$$
###Laplace Transform for solving differential equations
Using the time differentiation property of the Laplace transform:
$$
\mathcal{L}\left\lbrace \frac{d^n x(t)}{dt^n} \right\rbrace =s^n X(s)-s^{n-1} x(0^-)-s^{n-2}x'(0^-)-...-x^{(n-1)}(0^-)
$$
We can solve differential equations by converting them from the time domain into the frequency domain. This means we can solve simple algebraic equations in the frequency domain, and then use the reverse Laplace transform to get the solutions to the original differential equation.
###Laplace Transform and transfer function
The Laplace transform of the impulse response of a system is called the transfer function of the system: 
$$
H(s)=\frac{Y(s)}{X(S)}
$$
Where $H(s)=\mathcal{L}\{h(t) \}$.
Knowing the transfer function of a system, we can fully determine the behaviour of the system.
###Initial Conditions in systems
In circuits, initial conditions may not be zero since components such as capacitors and inductors may contain charge or current.
####Capacitors
For a capacitor $C$ with an initial voltage $v(0^-)$, the equation $i(t)=C\frac{dv(t)}{dt}$ holds.
Taking the Laplace transform on both sides gives: $I(s)=C(sV(s)-v(0^-))$. This can be rearranged to give the voltage across the charged capacitor:
$$
V(s)=\frac{1}{Cs}I(s)+\frac{v(0^-)}{s}
$$
Where the first term is the voltage across the capacitor with no charge, and the second term is the effect of the initial charge = voltage source.
####Inductors
For an inductor $L$ with an initial current $i(0^-)$, the equation $v(t)=L\frac{di(t)}{dt}$ holds.
Taking the Laplace transform on both sides gives: $V(s)=L(sI(s)-i(0^-))$. This can be rearranged to give the voltage across the inductor:
$$
V(s)=LsI(s)-Li(0^-)
$$
Where the first term is the voltage across the inductor with no initial current, and the second term is the effect of the initial current = voltage source.