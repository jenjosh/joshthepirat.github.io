

#Communication Systems

[TOC]

## Introduction to Communication Systems

### Introduction

There are four basic elements of communication:

- **Information source** This can be music, picture, video, voice etc.
- **Transmitter** This converts information in the source into a form that is more suitable for transmission over the channel.
- **Channel** This is the physical medium in which the information travels. It introduces distortion noise, interference etc.
- **Receiver** This reconstructs the information back into a recognisable form of the source signal.

![Block diagram of a communication system.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/communicationsystem.png)

#### Communication Channel

The medium through which the information travels is called the communication channel. It can be anything froma cable to optical fibre to air to hard disks etc.

The channel introduces propogation loss, the signal strength decays with distance.

The channel has a bandwidth. The bandwidth is the range of frequencies that can be used for communication. More bandwidth means higher transmission capacity.

The channel can have time variation. This is where the channel characteristics change over time. An example of this is mobile radio channels.

The channel can experience nonlinearity which some elements such as repeaters introduce.

The channel introduces and is prone to noise.

#### Noise in Communications

Unwanted signals present in communication systems are known as noise. Noise can be external or internal.

External noise is usually interference from nearby channels, human made noise, or natural noise.

Internal noise can be caused by thermal noise or the random motion of electrons amongst other things.

Noise limits the performance of communication systems. A widely used metric for this is the signal to noise ratio (SNR): 
$$
SNR=\frac{signal power}{noise power}
$$

#### Transmitter and Receiver

The transmitter modifies the source signal into a form suitable for transmission over the channel. This involves modulation and up conversion.

Modulation is where some parameter of a carrier wave is varied based on the source signal.

- This can be analogue such as AM, FM, and PM.
- It can also be digital such as ASK, FSK, and PSK.

Up conversion is where the modulated signal is converted into the final radio frequency (RF).

The reciever reconstructs the original message by down conversion and demodulation.

- The recovery isn't exact due to noise and distortion.
- The resulting degregation depends upon the type of modulation.

#### Digital vs Analog Communication

Natural signal are analog and are continuous in time and amplitude, whilst digital signals are discrete.

No matter what, the transmitted signal os always analog. Digital vs ANalog refers to how the parameters of these waveforms are formed.

Digital systems convert the source signal into a finite set of source messages and maps them to a set of signals that is tranmitted analogly along a channel. Digital communication is more efficient and reliable than analog, but the design is more sophisticated and complex than analog communication.

### Objectives of System Design

There are two primary resources in communications: the transmitted power and the channel bandwidth (which is very expensive). In certain scenarios, one resource may be more limited than the other. In space, power is more important than bandwidth whilst in a telephone, the opposite is the case.

The objectives of communication design are:

- To deliver the message efficiently and reliably subject to power, bandwidth, and cost cnstraints.
- This efficeiency is usually measured by the number of bits transmitter per unit power, unit time, and unit bandwidth.
- This reliabilty is usually expressed using the signal to noise ratio or the probability of an error having occurred.

#### Communication networks

Todays communication networks are complicated systems with large numbers of users sharing the same medium.


![Diagram of todays complicated communication systems.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/bigsystem.png)

These are made up of hosts which communicate with eachother and provide information to share and routers which route the data from the hosts through the network to other routers.



## Probability and Random Processes

The sample space ($S$) is the set of all possible outcomes.

An event is any subset of the sample space.

The probability of an event in the non negative and non zero value that represents the value for which $P(A) \ge 0$ for any subset $A$ of $S$.

The probability of two events that do not have any common outcome is the sum of the probabilities of the two events separately.
$$
A \cap B= \emptyset \Rightarrow P(A \cup B)=P(A)+P(B)
$$

### Random Variables

A random variable $X(s)$ is a real values function defined on the set of all possible outcomes $S$. $X(s)$ assigns a number to every outcome $s$. $\{X \le x\}$ is the subset of $S$ consisting of all outcomes $s$ such that $X(s) \le x$.

$X(s)$ must satisfy:

- The set $\{X \le x\}$ is an event for every $x$.
- Probabilities of events $\{ X=\infty \}$ and $\{ X=-\infty \}$ are zero.

### CDF and PDF

The cumuative distribution function (CDF) of a random variable is defined as the probability of $X$ being less than $x$: 
$$
F_X(x)=P(X \le x)
$$

The probability density function (PDF) is defined as the derivative of the cumulative distribution function: 
$$
f_X(x)=\frac{\,d F_X(x)}{\,d x}
$$

$$
F_X(x)=\int_{-\infty}^{x}f_X(y)\,d y
$$

$$
P(a<X<b)=F_X(b)-F_X(a)=\int_{a}^{b}f_X(y)\,d y
$$

### Mean and Variance

Mean is also known as the expeced value or the DC level in electronics: 
$$
E[X]=\mu_X=\int_{-\infty}^{\infty}xf_X(x)\,d x
$$

Variance is also known as the power for zero mean signals: 
$$
\sigma_X^2=var[X]=E[(X-E[X])^2]=\int_{-\infty}^{\infty}(x-\mu_X)^2f_X(x)\,d x=E[X^2]-E[X]^2
$$

### Probability Distributions

#### Normal/Gaussian Distribution


![The Normal/Gausian Distribution.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/normal.png)

For the normal distribution (where $E[X]=m$ and $\sigma_X^2=\sigma^2$): 
$$
f_X(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{(x-m)^2}{2\sigma^2}} \qquad \qquad \text{for }-\infty < x < \infty
$$

$$
F_X(x)=\frac{1}{\sqrt{2\pi}\sigma}\int_{-\infty}^{x}e^{-\frac{(y-m)^2}{2\sigma^2}}\,d y
$$

#### Uniform Distribution

![The Uniform Distribution.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/uniform.png)

For the uniform distribution (where $E[X]=\frac{a+b}{2}$ and $\sigma_X^2=\frac{(b-a)^2}{12}$): 
$$
f_X(x)=\left\lbrace \begin{matrix}
\frac{1}{b-a} & \qquad \qquad a \le x \le b \\
0 & \qquad \qquad \text{elsewhere}
\end{matrix}\right.
$$

$$
F_X(x)=\left\lbrace \begin{matrix}
0 & \qquad \qquad x<a \\
\frac{1}{b-a} & \qquad \qquad a \le x \le b \\
1 & \qquad \qquad x>b
\end{matrix}\right.
$$

#### Joint Distribution

The joint distribution function for two random variables $X$ and $Y$ is: 
$$
F_{XY}(x,y)=P(X \le x, Y\le y)
$$

The joint probability density function is: 
$$
f_{XY}(x,y)=\frac{\delta^2 F_{XY}(x,y)}{\delta x \delta y}
$$

The properties of the joint distribution are: 
$$
F_{XY}(\infty, \infty)=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}f_{XY}(u,v)\,d u \,d v =1
$$

$$
f_X(x)=\int_{y=-\infty}^{\infty}f_{XY}(x,y) \,d y
$$

$$
F_Y(x)=\int_{x-\infty}^{\infty} f_{XY}(x,y)\,d x
$$

$$
X,\; Y \text{ are independent} \Leftrightarrow f_{XY}(x,y)=f_X(x)f_Y(y)
$$

$$
X,\; Y \text{ are uncorellated} \Leftrightarrow E[XY]=E[X]E[Y]
$$

Independence implies uncorrelation, however uncorrelation does not imply independence.

Only for the Gaussuian distribution does uncorrelation imply independence.

#### Joint Distribution of $n$ RVs

Joint CDF: 
$$
F_{X_1X_2...X_n}(x_1,x_2,...x_n)\equiv P(X_1 \le x_1, X_2 \le x_2, ... X_n \le x_n)
$$

Joint PDF: 
$$
f_{X_1X_2...X_n}(x_1,x_2,...x_n)\equiv\frac{\delta^nF_{X_1X_2...X_n}(x_1,x_2,...x_n)}{\delta x_1 \delta x_2 ... \delta x_n}
$$

Independent: 
$$
F_{X_1X_2...X_n}(x_1,x_2,...x_n)=F_{X_1}(x_1)F_{X_2}(x_2)...F_{X_n}(x_n)
$$

$$
f_{X_1X_2...X_n}(x_1,x_2,...x_n)=f_{X_1}(x_1)f_{X_2}(x_2)...f_{X_n}(x_n)
$$

Random variables are independent and identically distributed (i.i.d.) if they are independent and have the same distribution.

The central limit theorem states that for i.i.d. random variables: $z=x_1+x_2+...+x_n$ tends to the Gaussian as $n$ tends to infinity.

This is why noise is usually Gaussian.

### Random Processes

A random process is a time-varying function that assigns to each outcome $s$ a function of time $X(t,s)$ for $-T\le t\le T$, where $2T$ is the total observation interval.

For a fixed sample point $s_j$, function $X(t,s_j)$ versus time is called a sample function of the random process.

For fixed $t$, a random process is a random variable.

If one scans all possible outcomes of the underlying random experiment, they shall get an ensemble of signals.

Noise can often be modelled as a Gaussian random process.

The sample of a random process at any point in time is a two function variable.

#### Statistics of a Random Process

For fixed $t$ the random process becomes a random variable: 
$$
\mu_X(t)=E[X(t)]=\int_{-\infty}^{\infty}x f_X (x;t)\,d x
$$

The Autocorrelation founction measures the correlation between two samples: 
$$
R_X(t_1, t_1)=E[X(t_1)X(t_2)]=\int_{-\infty}^{\infty} \int_{-\infty}^{\infty}xy f_X(x,y;t_1,t_2)\,d x \,d y
$$

#### Stationary Random Processes

A process is an $n^{th}$ order Strict Sense Stationary if for any value of $c$: 
$$
f_X(x_1,x_2,...x_n;t_1,t_2,...t_n)\equiv f_X(x_1,x_2,...x_n,t_1+c,t_2+c,...t_n+c)
$$

A process $X(t)$ is strict sense stationary if the above holds true for all $t_i$ where $i=1,2,...,n$ where $n=1,2,..., $ and any $ c$, or if it's $n^{th}$ order stationary for all $n=1,2,...$

The first order set is larger than the second order to $n^{th}$.

The $n^{th}$ order set satisfies the $(n-1)th$ order set (is a subset of).

A random process is stationary to first order if the distribution functio(and hence the density function) of $X(t)$ is invariant over time.

$X(t)$ is stationary to $2^{nd}$ order if $f_{X(t_1)X(t_2)}(x_1,x_2)$ depends only on the difference between $t_2$ and $t_1$

If $X(t)$ is stationary to second order then: 
$$
R_X(t_1,t_2)=R_X(t_2 - t_1), \text{for all }t_1\text{ and }t_2
$$

A random process is wide sense stationary if:

- Its mean does not depend on $t$: 
$$
\mu_X(t)-\mu_X
$$
- Its autocorrelation function depends only on time difference: 
$$
R_X(t, t+\tau)=R_X(\tau)
$$

In communications, noise and message signals are often modelled as stationary random processes.

Strict sense stationarity always implies wide-sense stationarity, however the converse is only true for Gaussian processes.

#### Properties of the Autocorrelation function

For a stationary $X(t)$ with autocorrelation function $R_X (\tau)$:

- $R_X(0)=E[X^2(t)]$
- $R_X(\tau )=R_X(-\tau)$
- $|R_X (\tau)| \le R_X(0)$

$R_X(\tau)$ tells how predictable $X(\tau)$ is based on $X(t-\tau)$.

### Ergodic Processes

Expectations of a stochastic process $X(t)$ are averages "across the process", also referred to as "ensemble averages".

Sometimes it is hard/impossible to observe all sample functions of a random process at a given time, while it may be possible to observe a single sample over a long period of time.

If the time average is equal to the ensembe average, then the process is said to be ergodic. If $E[X(t)]$ is finite for all $t$ and the system is stable and then passed through an impulse response $h(t)$: 
$$
\mu_Y(t)=E[Y(t)]=E\left[ \int_{-\infty}^{\infty}h(\tau)X(t-\tau)\,d \tau \right] =\int_{-\infty}^{\infty}\,d \tau=\mu_X(t)\ast h(t)
$$

If $X(t)$ is wide sense stationary then: 
$$
\mu_Y (t)=\mu_X H(0)
$$

Where $H(0)$ is the zero frequency, DC, response of the system.

If $E[X^2(t)]$ is finite for all $t$ and the system is stable: 
$$
R_Y (t,u)=\int_{-\infty}^{\infty}\,d \tau_1 h(\tau_1)\int_{-\infty}^{\infty}\,d \tau_2 h(\tau_2)E[X(t-\tau_1)X(u-\tau_2)]
$$

$$
=\int_{-\infty}^{\infty}\,d \tau_1 h(\tau_1)\int_{-\infty}^{\infty}\,d \tau_2 h(\tau_2)R_X(t-\tau_1,u-\tau_2)
$$

$$
=\int_{-\infty}^{\infty}\,d \tau_1 h(\tau_1)[h(u)\ast R_X(t-\tau_1, u)]
$$

$$
=h(t) \ast [h(u) \ast R_X (t,u)]
$$

If $X(t)$ is wide sense stationary then letting $\tau=t-u$: 
$$
R_Y(\tau)=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}h(\tau_1)h(\tau_2)R_X(\tau-\tau_1+\tau_2)\,d \tau_1 \,d \tau_2 h(\tau)\ast [h(-\tau) \ast R_X(\tau)]
$$

Both wide and strict sense process goes through an LTI system, they stay the process that the were before.

#### Power Spectral Density (PSD)

PSD is a function that measures the distribution of power of a random process over its spectrum.

PSD is defined only for stationary processes.

The Einstein-Wiener-Khintchine relation states: The PSD of a wide sense stationary process is equal to the Fourier transform of its autocorrelation function: 
$$
S_X(f)=\int_{-\infty}^{\infty}R_X(\tau)e^{-j 2\pi f \tau}\,d \tau \ge 0
$$

The frequency content of a process depends on how rapidly the amplitude changes as a function of time (measured by the autocrrelation function).

The average power is: 
$$
P=E[X^2(t)]=R_X(0)=\int_{-\infty}^{\infty}S_X(f)\,d f
$$

If $X(t)$ is a real WSS process then: 
$$
S_X(f)=\int_{-\infty}^{\infty}R_X(\tau)e^{-j 2\pi f \tau} \,d \tau=\int_{-\infty}^{\infty}R_X (\tau)\cos{2\pi f \tau} \,d \tau
$$

$$
=2\int_{0}^{\infty}R_x(\tau)\cos{2\pi f \tau}\,d \tau=S_X(-f) \ge 0
$$

The power spectrum is an even function.

#### Passing through an linear system

If a WSS process $X(t)$ goes through a linear system of transfer function $h(t)$: 
$$
S_Y(f)=|H(f)|^2S_X(f)
$$

For a complex process $X(t)$ going through a complex valued LTI system, it can be shown that: 
$$
R_Y(\tau)=h(\tau)\ast[h^*(-\tau)\ast R_X(\tau)]
$$

If $X(t)$ is a Gaussian process then $Y(t)$ is also a Gaussian process.



## Baseband and Passband signals

### Energy and Power

Energy of a signal is: 
$$
E=\int_{-\infty}^{+\infty}|s(t)|^2 \,d t=\int_{-\infty}^{+\infty}|S(f)|^2\,d f
$$

Power is the time average of energy, computed over a large interval: 
$$
P=\frac{1}{T}\int_{-\frac{T}{2}}^{+\frac{T}{2}}|s(t)|^2\,d t
$$

For a sinusoid: 
$$
P_s=\frac{A^2}{2}
$$

### Bandwidth

Bandwidth of a signal quantifies its frequency occupancy. One-sided bandwidth is where only positive frequencies are looked when computing bandwidth for physical signals, such as WiFi.

Physical signals are real-valued in the time domain,hence they are conjugate symmetric in the frequency domain, so they can be specified completely by their spectrum over positive frequencies.

Complex exponentials are used because they are eigenfunctions of LTI systems. Physical signals are real-valued in the time domain so they must satisfy conjugate symmetry meaning all the information resides in either positive or negative frequencies. Therefore physical bandwidth is one sided bandwidth.

### Channels

Channels often approximated as LTI systems, signals pass through the channel, and then noise is added. Channels allocated/described typically in terms of frequency bands:

- **Baseband channels/signals**: Energy concentrated in a frequency band around DC.
- **Passband channels/signals**: Energy concentrated in a frequency band away from DC.
- **Unified treatment of baseband and passband systems**: Complex baseband representation of passband systems.

#### Baseband Signals

Baseband signals have energy/power concentrated in a band around DC: 
$$
U(f)\approx 0 \qquad |f|>E
$$

![Baseband signals.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/baseband.png)

Real baseband signal of bandwidth $W$: $U(f)$ has conjugate symmetry. Note that $|U(f)|$ is symmetric for a real baseband signal.

For communication over a physical baseband channel, physical (real-valued) baseband signals are considered. Whilst for communication over a physical passband channel (discussion coming up), complex-valued baseband signals which provide a convenient mathematical representation for the corresponding passband signals are considered.

#### Passband Signals

Passband signals have energy/power concentrated in a band away from DC: 
$$
U(f)\approx0 \qquad |f \pm f_c |>W \qquad \qquad f_c>W>0
$$

![Passband signals.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/passband.png)

Only physical (real-valued) passband signals are considered, hence their spectra always obey conjugate symmetry.

Examples of baseband signals are: Speech and audio; Two-level digital signals.

Often such signals need to be sent over a passband channel (e.g., a 20 MHz WiFi channel at 2.4 GHz) therefore they need to be modulated.

### Modulation: Baseband to Passband

Modulation is to translate to passband by multiplying by a sinusoid. For a real-valued baseband message signal $m(t)$: 
$$
u_p(t)=m(t)\cos{2\pi f_c t} \leftrightarrow U_p(f)=\frac{1}{2}(M(f-f_c)+M(f+f_c))
$$

$$
v_p(t)=m(t)\sin{2\pi f_c t}\leftrightarrow V_p(f)=\frac{1}{2j}(M(f-f_c)-M(f+f_c))
$$

![Baseband to Passband signal modulation.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/pbmodulation.png)

Carrier frequency should be bigger than the message bandwidth to keep away from DC.

The in phase and quadrature components can be modulated separately using cosine and sine of the carrier. The I and Q components are real baseband signals that contain all the information whilst the sinusoids are rapidly varying but predictable so they contain no information: 
$$
u(t)=u_I(t)\cos{(2\pi f_c t)}-u_Q(t)\sin{(2\pi f_c t)}
$$

This all happens at the transmitter.

### Downconversion: Passband to Baseband

To filter out the in phase and Quadrature components the receiver needs to be coherent (phase and frequency of the copy of the carrier at the receiver needs to be the same as that of the incoming signal).

The I and Q channels are orthogonal so information can be sent in parallel on these channels. 
$$
a(t)=u_I(t)\cos{(2\pi f_c t)}
$$

$$
b(t)=u_Q(t)\sin{(2\pi f_c t)}
$$

The passband waveforms $a(t)$ and $b(t)$ are also orthogonal. 
$$
x(t)=a(t)b(t)=u_I(t)u_Q(t)\cos{(2\pi f_c t)}\sin{(2\pi f_c t)}=\frac{1}{2}u_I(t)u_Q(t)\sin{(4\pi f_c t)}
$$

There is a passband at $2f_c$ because: 
$$
p(t)=\frac{1}{2}u_I(t)u_Q(t) \leftrightarrow \frac{1}{2}(U_I \ast U_Q)(f)
$$

The passband signal can be mapped to a pair of real baseband signals meaning passband modulation is two-dimensional.

![Passband modulation plotted on the complex plane.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/passbandir.png)

The three equivalent representations of the passband signal are: Rectangular coordinates (I and Q); Polar coordinates (Envelope and Phase); Complex number (Complex envelope).

Each representation of a complex number corresponds to a time domain expression for the passband signal: 
$$
\tilde{u}(t)=u_I(t)+ju_Q(t)=e(t)e^{j\theta(t)}
$$

$$
e(t)=\sqrt{u_I^2(t)+u_Q^2(t)} \qquad \theta(t)=\arctan{\frac{u_Q(t)}{u_I(t)}}
$$

$$
u_I(t)=e(t)\cos{\theta(t)}\qquad u_Q(t)=e(t)\sin{\theta(t)}
$$

Time Domain Expressions for a Passband Signal:

- In terms of I and Q: $u(t)=u_I(t)\cos{(2\pi f_c t)}-u_Q(t)\sin{(2\pi f_c t)}$
- In terms of envelope and phase: $u(t)=e(t)\cos{(2\pi f_c t+ \theta(t))}$
- In terms of the complex envelope: $u(t)=RE\{\tilde{u}(t)e^{j 2 \pi f_c t}\}$

### Complex Envelope

$$
u(t)=Re\{\tilde{u}(t)e^{j2\pi f_c t}\}
$$

All information in a passband signal is contained in its complex envelope. Complex baseband representation can be defined for arbitrary $f_c$, as long as $f_c>B$. 

If $u(t)=Re\{\tilde{u}_1(t)e^{j2\pi f_1 t}\}$=$u(t)=Re\{\tilde{u}_2(t)e^{j2\pi f_2 t}\}$ then: 
$$
\tilde{u}_2(t)=\tilde{u}_1(t)e^{j2\pi(f_1-f_2)t}
$$

#### Hilbert Transform

Hilbert transform of a signal $g(t)$ is defined as: 
$$
\hat{g}(t)=\frac{1}{\pi}\int_{-\infty}^{\infty}\frac{g(\tau)}{t-\tau}\,d \tau
$$

HT is a linear transformation. Its inverse is given by: 
$$
g(t)=-\frac{1}{\pi}\int_{-\infty}^{\infty}\frac{\hat{g}(\tau)}{t-\tau}\,d \tau
$$

The Hilbert transform of $\hat{g}(t)$ is $-g(t)$.

In the Fourier domain: 
$$
\hat{G}(f)=-j sgn(f)G(f)
$$

$$
sgn(f)=\left\lbrace \begin{matrix}
+1 & f>0 \\
0 & f=0 \\
-1 & f<0
\end{matrix}\right.
$$

#### Pre-Envelope

The pre-envelope of a signal $u(t)$ is: 
$$
u_+(t)=u(t)+j\hat{u}(t)
$$

Its Fourier transform is: 
$$
U_+(f)=U(f)+sgn(f)U(f)=\left\lbrace \begin{matrix}
2U(f) & f>0 \\
U(0) & f=0 \\
0 & f<0
\end{matrix}\right.
$$

Pre-envelope removes the negative frequency components.

Similarly the pre-envelope for negative frequencies: 
$$
u_-(t)=u(t)-j\hat{u}(t)
$$

$$
U_-(f)=U(f)-sgn (f)U(f)=\left\lbrace \begin{matrix}
0 & f>0 \\
U(0) & f=0 \\
2U(f) & f<0
\end{matrix}\right.
$$

#### Complex Envelope

Consider arbitrary complex-valued baseband signal $\tilde{u}(t)$, whose spectrum is limited to $[-B,+B]$: 
$$
U(t)=Re\{\tilde{u}(t)e^{j2\pi f_c t}\}
$$

To show that $u(t)$ is a real-valued passband signal concentrated around $\pm f_c$: 
$$
u_+(t)=\tilde{u}(t)e^{j2\pi f_c t}
$$

Then: 
$$
U_+(f)=\tilde{U}(f-f_c) \qquad \text{in }[f_c+W,f_c-W]
$$

$$
u(t)=Re\{u_+(t)\}=\frac{1}{2}\left( u_+(t)+u_+^*(t) \right) \leftrightarrow U(f)=\frac{1}{2}\left( U_+(f)+U_+^*(-f) \right)
$$

If $u(t)$ is a real valued passband signal:
$$
U(f)=\frac{1}{2}\left( \tilde{U}(f-f_c)+U_+^*(-f-f_c)\right)
$$

$$
u(t) = Re\{\tilde{u}(t)e^{j 2 \pi f_c t} \} = u_I (t)\cos{(2\pi f_c t)} − u_Q (t)\sin{(2\pi f_c t)}
$$



## Noise

Noise is unwanted waves that disturb the transmission of signals.

Noise comes from:

- External sources: e.g. atmospheric, galactic noise, interference.
- Internal sources: generated by communication devices themselves.
    - This type of noise represents a basic limitation on the performance of electronic communication systems.
    - Shot noise: the electrons are discrete and are not moving in a continuous steady flow, so the current is randomly fluctuating.
    - Thermal noise: caused by the rapid and random motion of electrons within a conductor due to thermal agitation.

Both are often stationary and have zero-mean Gaussian distributions.

### White Noise

The power spectral density (PSD) is constant over all frequencies: 
$$
S_N(f)=\frac{N_0}{2} \qquad -\infty < f < \infty
$$

The half factor indicates that half the power is associated with positive frequencies and half with negative.

The term white is analogous to white light which contains equal amounts of all frequencies (within the visible band of EM wave). It is only defined for stationary noise.

An infinite bandwidth is a purely theoretic assumption, it is valid as long as the noise PSD is flat over the bandwidth of interest.

#### White Noise vs Gaussian Noise

White noise $\ne$ Gaussian noise. Gaussian noise is where the distribution at any time instant is Gaussian. The samples at different time instants are uncorrelated. It is typically assumed that noise is additive white Gaussian noise (AWGN).

#### Ideal Low Pass White Noise

Suppose white noise is applied to an ideal low-pass filter of bandwidth $B$ such that: 
$$
S_N(f)=\left\lbrace\begin{matrix}
\frac{N_0}{2} & |f| \le B \\
0 & \text{otherwise}
\end{matrix}\right.
$$

By Einstein-Wiener-Khinchine relation, autocorrelation function: 
$$
R_n(\tau)=E[n(t)n(t+\tau)]=N_0B sinc{(2B\tau)}
$$

Samples at Nyquist frequency $2B$ are uncorrelated: 
$$
R_n(\tau)=0 \qquad \qquad \tau=\frac{k}{2B} \quad k=1,2,...
$$

![Ideal Low-Pass White Noise.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/Rntau.png)

### Band Pass Noise

Any communication system that uses carrier modulation will typically have a band-pass filter of bandwidth $B$ at the receiver front-end.

![Band Pass Noise.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/bandpassnoise.png)

Any noise that enters the receiver will therefore be band-pass in nature. Its spectral magnitude is non-zero only for some band concentrated around the carrier frequency $f_c$ (sometimes called narrowband noise).

![Narrow Band Noise.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/narrowbandnoise.png)

$n(t)$ can be written in canonical form: 
$$
n(t)=n_I(t)\cos{(2\pi f_c t)}-n_Q(t)\sin{(2\pi f_c t)}
$$

$n_I(t)$ and $n_Q(t)$ are fully representative of band-pass noise.

- Given band-pass noise, one may extract in-phase and quadrature components (using LPF of bandwidth B). This is extremely useful in analysis of noise in receivers.
- Given the two components, one may generate band-pass noise. This is useful in computer simulation.

![Band Pass Noise Generation.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/bandpassnoisegen.png)

#### Properties of Baseband Noise

- If noise $n(t)$ has zero mean, then so do $n_I(t)$ and $n_Q(t)$.
- If noise $n(t)$ is Gaussian, then so are $n_I(t)$ and $n_Q(t)$.
- If noise $n(t)$ is stationary, then so are $n_I(t)$ and $n_Q(t)$.
- If noise $n(t)$ is Gaussian and its power spectral density $S(f)$ is symmetric with respect to central frequency $f_c$, then $n_I(t)$ and $n_Q(t)$ are statistically independent.
- $n_I(t)$ and $n_Q(t)$ have the same variance (i.e. same power) as $n(t)$.

### Power Spectral Density

Both in-phase and quadrature components have the same PSD: 
$$
S_{N_I}(f)=S_{N_Q}(f)=\left\lbrace\begin{matrix}
S_N(f-f_c)+S_N(f+f_c) & |f| \le B \\
0 & \text{otherwise}
\end{matrix}\right.
$$

This follows from: 
$$
g(t) \Leftrightarrow G(\omega)
$$

$$
g(t)2\cos{\omega_0t} \Rightarrow [G(\omega-\omega_0)+G(\omega+\omega_0)]
$$

$n_I(t)$ and $n_Q(t)$ have the same PSD.

### Noise Power

For ideally filtered narrowband noise, the PSDs of $n_I(t)$ and $n_Q(t)$ are therefore given by: 
$$
S_I(f)=S_Q(f)=\left\lbrace\begin{matrix}
N_0 & |f| \le B \\
0 & \text{otherwise}
\end{matrix}\right.
$$

![Ideally filtered narrow band noise.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/ideallyfilterednarrowbandnoise.png)

The average power in each of the baseband waveforms $n_I(t)$ and $n_Q(t)$ is identical to the average power in the bandpass noise waveform $n(t)$.

For ideally filtered narrowband noise, the variance of $n_I(t)$ and $n_Q(t)$ is $2N_0B$ each: 
$$
P_{N_I}=P_{N_Q}=2N_0 B
$$

### Phasor Representation

Band-pass noise may be written in the alternative form: 
$$
n(t)=n_I(t)\cos{(2\pi f_c t)}-n_Q(t)\sin{(2\pi f_c t)}=r(t)\cos{[2\pi f_c t+\phi(t)]}
$$

The envelope of the noise is: 
$$
r(t)=\sqrt{n_I(t)^2+n_Q(t)^2}
$$

The phase of the noise is: 
$$
\phi(t)=\arctan{\frac{n_Q(t)}{n_I(t)}}
$$

![Phasor representation.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/phasor.png)

#### Distribution of Envelop and Phase

It can be shown that if $n_I(t)$ and $n_Q(t)$ are Gaussian-distributed, then the magnitude $r(t)$ has a Rayleigh distribution, and the phase $\phi(t)$ is uniformly distributed.

If a sinusoid $A\cos{(2\pi f_ct)}$ is mixed with noise then the magnitude will have a Rice distribution.



## Noise Performance of DSB

### Signal to Noise Ratio

A way to quantify the performance of a modulation scheme is to use the signal to noise ration (SNR) at the output of the receiver: 
$$
SNR_o \equiv \frac{\text{average power of message signal at the reciever output}}{\text{average power of noise at the reveiver output}}=\frac{P_S}{P_N}
$$

This is normally expressed in decibels to manage the wide range of power levels in communication systems.
$$
(\text{SNR}(dB)=10log_{10}\text{(SNR)})
$$

### Transmitted Power

Transmitted power is known as $P_T$. It is limited by equipment and battery cost etc. The higher it is, the greater the received power and SNR.

When comparing various modulation schemes: $P_T$ should remain the same; the baseband signal to noise ratio ($SNR_{baseband}$) as a reference value for comparison.

### Baseband Communication System

This doesn't use modulation and is suitable for transmission over wires. The transmission power is identical to message power. If there is no attenuation, then $P_S=P_T=P$.

![Baseband communication.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/basebandcomms.png)

The baseband SNR is additive white noise with PSD$=\frac{N_0}{2}$. It is the area under the straight line in the triangle. Since the average power at the reciever is $P_N=2W\times \frac{N_0}{2}=WN_0$. Therefore the SNR at the output (assuming no propagation loss) is: 
$$
SNR_{baseband}=\frac{P_T}{N_0 W}
$$

The SNR can be improved by increasing the numerator term and/or decreasing the denominator terms.

### Double Sideband-Suppressed Carrier (DSB-SC) Modulation

The general form of a DSB-SC signal is: 
$$
s(t)=m(t)A\cos{(2\pi f_c t)}
$$

![synchronous detection = product detection = coherent detection.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/dsbsc.png)

The recieved and noisy signal is: 
$$
x(t)=s(t)+n(t)
$$

$$
=s(t)+n_I(t)\cos{(2\pi f_c t)}-n_Q(t)\sin{(2\pi f_c t)}
$$

$$
=Am(t)\cos{(2\pi f_c t)}+n_I(t)\cos{(2\pi f_c t)}-n_Q(t)\sin{(2\pi f_c t)}
$$

$$
=[Am(t)+n_I(t)]\cos{(2\pi f_c t)}-n_Q(t)\sin(2\pi f_c t)
$$

![Coherent detection.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/coherentdetector.png)

#### Synchronous Detection for DSB-SC

Multiply the signal with $2\cos{(2\pi f_c t)}$: 
$$
v(t)=2\cos{(2\pi f_c t)}x(t)
$$

$$
=Am(t)2\cos^2{(2\pi f_c t)}+n_I(t)2\cos^2{(2\pi f_c t)}-n_Q(t)\sin{(4\pi f_c t)}
$$

$$
=Am(t)[1+cos{(4\pi f_c t)}]+n_I(t)[1+\cos{(4\pi f_c t)}]-n_Q(t)\sin{(4\pi f_c t)}
$$

Use a low pass filter to keep: 

$$
y(t)=Am(t)+n_I(t)
$$

Signal power at the receiver output: 
$$
P_S=E\{A^2m^2(t)\}=A^2E\{m^2(t)\}=A^2 P
$$

The power of the noise $n_I(t)$: 
$$
P_N=\int_{-W}^{W}N_0\,d f=2N_0W
$$

The SNR at the receiver output is: 
$$
SNR_o=\frac{A^2 P}{2N_0W}
$$

The DSB-SC system has the same SNR performance as a baseband system.



## Noise Performance of SSB and conventional AM

### Single Sideband Signals

In a single sideband signal, the message can be recovered by moving SSB components left and right by $f_c$, and low pass filtering. This operation recovers the $I$ component. The message is this component.

![Single side band modulation.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/ssbmod.png)

The Q component is the Hilbert transform of the message: 
$$
s(t)_{SSB-U}=\frac{A}{2}m(t)\cos{(2\pi f_c t)}-\frac{A}{2}\hat{m}(t)\sin{(2\pi f_c t)}
$$

$\hat{m}(t)$ and $m(t)$ have the same power $P$.

The average power is: $\frac{A^2P}{4}$

![Side Bands.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/sidebands.png)

#### Noise in SSB

The receiver signal is $x(t)=s(t)+n(t)$. A bandpass filter on the lower sideband (still denote by $n_I(t)$ the lower-sideband noise). Using coherent detection: 
$$
y(t)=x(t)\times 2\cos{(2\pi f_c t)}=\left( \frac{A}{2}m(t)+n_I(t) \right)+\left(\frac{A}{2}m(t)+n_Q(t)\right) \cos{(4\pi f_c t)}+\left(\frac{A}{2}\hat{m}(t)-n_Q(t) \right) \sin{(4\pi f_c t)}
$$

After low pass filtering: 
$$
y(t)=\frac{A}{2}m(t)+n_I(t)
$$

The noise power of the band pass noise $n_I(t)$ is $N_0W$ which is halved compared to DSB.

![Band Pass Noise Power.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/noisepower.png)

#### Output SNR

The signal power is: 
$$
\frac{A^2P}{4}
$$

The SNR at the output is: 
$$
SNR_{SSB}=\frac{A^2 P}{4N_0W}
$$

For a baseband system with the same transmit power $\frac{A^2P}{4}$, $SNR_{baseband}=\frac{A^2P}{4N_0W}$. Therefore the single sideband achieves the same SNR performance as DSB-SC but only requires half the bandwidth.

### Standard AM: Synchronous Detection

Pre detection, the signal is: 
$$
x(t)=[A+m(t)]\cos{(2\pi f_c t)}+n(t)
$$

$$
=[A+m(t)+n_I(t)]\cos{(2\pi f_c t)}+n_I(t)\cos{(2\pi f_c t)}-n_Q(t)\sin{(2\pi f_c t)}
$$

$$
=[A+m(t)+n_I(t)]\cos{(2\pi f_c t)}-n_Q(t)\sin{(2\pi f_c t)}
$$

Multiplying with $2\cos{(2\pi f_c t)}$: 
$$
y(t)=[A+m(t)+n_I(t)][1+\cos{(4\pi f_c t)}]-n_Q(t)\sin{(4\pi f_c t)}
$$

After the lowpass filter:
$$
\tilde{y}=A+m(t)+n_I(t)
$$

#### Output SNR

The signal power at the reciever output is: 
$$
P_S=E\{m^2(t)\}=P
$$

The Noise power is: 
$$
P_N=2N_0W
$$

The SNR at the reciever output is: 
$$
SNR_o=\frac{P}{2N_0W}=SNR_{AM}
$$

The transmitted power is: 
$$
P_T=\frac{A^2}{2}+\frac{P}{2}=\frac{A^2+P}{2}
$$

#### Comparison

Comparison of a baseband signal with the same transmitted power: 
$$
SNR_{baseband}=\frac{A^2+P}{2N_0W}
$$

Thus: 
$$
SNR_{AM}=\frac{P}{A^2+P}SNR_{baseband}
$$

Since $\frac{P}{A^2+P}<1$ the performance of standard AM with synchronous recovery is worse than the baseband system.

#### Non-coherent Receiver and envelope Detection

The envelope (or magnitude of complex envelope) does not depend on carrier phase. If the envelope of a passband signal can be extracted, then carrier sync isn't required.

![AM envelope detector.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/AMdetector.png)

If the signal is DSB modulated but doesn't have a strong carrier compoent, then the envelope only has message magnitude and the envelope detection loses the message sign. If a strong carrier component is used, then an envelope detector and DC block can be used to recover message info.

#### Envelope detection circuit

![AM envelope detector circuit.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/envelopedetectioncircuit.png)

The positive carrier cycle causes the capacitor to charge up and reach the value of the envelope, whilst during the negative carrier cycle the capacitor discharges with the RC time constant.

The circuit shouldn't discharge too fast during negative cycles and should react fast enough to follow variations in envelope which depend on message bandwidth $B$: 
$$
\frac{1}{f_c}<<RC<<\frac{1}{B}
$$

![AM envelope detector circuit operation.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/envelopedetectionoperation.png)

### Envelope Detection for Standard AM

The phase diagram of the signals present at an AM reciever are:

![Phasor of AM signals at reciever.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/AMphasor.png)

The envelope is: 
$$
y(t)=\text{envelope of }x(t)=\sqrt{[A+m(t)+n_I(t)]^2+n_Q^2(t)}
$$

This equation is complicated. Limiting cases can be used to put noise in an additive form.

#### Small Noise Case

The first approximation is the small noise case: 
$$
n(t)<<[A+m(t)]$$ Then: $$n_Q(t)<<[A+m(t)+n_I(t)]
$$

Then: 
$$
y(t)\approx [A+m(t)+n_I(t)]
$$

Thus: 
$$
SNR_o=\frac{P}{2N_0W}\approx SNR_{env}
$$

In terms of the baseband SNR: 
$$
SNR_{env}\approx \frac{P}{A^2+P}SNR_{baseband}
$$

This is valid for small noise only.

#### Large Noise Case

The second approximation is the large noise case: $$n(t)>>[A+m(t)]$$ Isolating the small quantity: $$y^2(t)=[A+m(t)+n_I(t)]^2+n_Q^2$$ $$=(A+m(t))^2n_I^2+2(A+m(t))n_I(t)+n_Q^2(t)$$ $$=[n_I^2(t)+n_Q^2(t)]\left\lbrace 1+\frac{(A+m(t))^2}{n_I^2(t)+n_Q^2(t)}+\frac{2(A+m(t))n_I(t)}{n_I^2(t)+n_Q^2(t)} \right\rbrace$$ $$y^2(t)\approx[n_I^2(t)+n_Q^2(t)]\left( 1+\frac{2[A+m(t)]n_I(t)}{n_I^2(t)+n_Q^2(t)}\right) \qquad E_n(t)\equiv\sqrt{n_I^2(t)+n_Q^2(t)}$$ $$=E_n^2(t)\left( 1+\frac{2[A+m(t)]n_I(t)}{E_n^2(t)} \right)$$

##### Large Noise Case: Threshold Effect

From the phasor diagram: $n_I(t)=E_n(t)\cos{\theta_n(t)}$, then: 
$$
y(t)\approx E_n(t)\sqrt{1+\frac{2[A+m(t)]\cos{\theta_n(t)}}{E_n(t)}}
$$
Using $\sqrt{1+x}\approx 1+\frac{x}{2}$ for $x<<1$: 
$$
y(t)\approx E_n(t)\left( 1+ \frac{[A+m(t)]\cos{\theta_n(t)}}{E_n(t)}\right)=E_n(t)+[a+m(t)]\cos{\theta_n(t)}
$$
The noise is multiplicative meaning $\theta_n(t)$ is uniformly distributed over $[0,2\pi]$.

If there is no term proportional to message, then information is lost.

The **Threshold effect** states that below some carrier-to-noise ratio level (very low A), performance of envelope detector deteriorates very rapidly (not the case in coherent detection).

### Summary

|       (De-) Modulation Format       |      Output SNR       | Transmitted Power | Baseband Reference SNR | Figure of Merit$=\left( \frac{Output\;\; SNR}{Reference\;\; SNR } \right)$ |
| :---------------------------------: | :-------------------: | :---------------: | :--------------------: | :----------------------------------------------------------: |
|        AM Coherent Detection        |   $\frac{P}{2N_0W}$   | $\frac{A^2+P}{2}$ | $\frac{A^2+P}{2N_0W}$  |                     $\frac{P}{A^2+P}<1$                      |
|        AM Coherent Detection        | $\frac{A^2 P}{2N_0W}$ | $\frac{A^2P}{2}$  |  $\frac{A^2P}{2N_0W}$  |                             $1$                              |
|       SSB Coherent Detection        | $\frac{A^2 P}{4N_0W}$ | $\frac{A^2P}{4}$  |  $\frac{A^2P}{4N_0W}$  |                             $1$                              |
| AM Envelope Detection (small noise) |   $\frac{P}{2N_0W}$   | $\frac{A^2+P}{2}$ | $\frac{A^2+P}{2N_0W}$  |                     $\frac{P}{A^2+P}<1$                      |
| AM Envelope Detection (large noise) |         Poor          | $\frac{A^2+P}{2}$ | $\frac{A^2+P}{2N_0W}$  |                             Poor                             |


($A$: carrier amplitude, $P$: power of message signal, $N_0$: single-sided PSD of noise, $W$: message bandwidth.)



## Frequency Modulation

### FM revision

FM additive noise effects the signal by how much it changes the frequency, whereas in AM the noise corrupts the signal directly. Therefore FM is less affected by noise.

FM is made up of a carrier waveform: 
$$
s(t)=A\cos{[\theta_i (t)]}
$$
Where $\theta_i(t)$ is the instantaneous phase angle.

When: 
$$
s(t)=A\cos{(2\pi f t)}\Rightarrow\theta_i(t)=2\pi f t\Rightarrow \frac{\,d \theta_i(t)}{\,d t}=2\pi f \Rightarrow f=\frac{1}{2\pi}\frac{\,d \theta_i(t)}{\,d t}
$$

$$
f_i(t)=\frac{1}{2\pi}\frac{\,d \theta_i(t)}{\,d t}
$$
Since instantaneous frequency is varied linearly with message: 
$$
f_i(t)=f_c+k_f m(t)
$$
Where $k_f$ is the frequency sensitivity.

Hence, assuming that $\theta_i(0)=0$: 
$$
\theta_i(t)=2\pi \int_0^t f_i(\tau)\,d \tau =2\pi f_c t+2\pi k_f \int_0^t m(\tau)\,d \tau
$$
The modulated signal is: 
$$
s(t)=A\cos{\left[ 2\pi f_c t + 2\pi k_f \int_0^t m(\tau) \,d \tau \right]}
$$
The envelope is constant and $s(t)$ is a nonlinear function of the message signal $m(t)$. FM signals are equivalent to PM signals where the modulating signal is: 
$$
\int_0^t m(\tau)\,d \tau
$$


### FM Basics

The peak message amplitude is: 
$$
m_p=max|m(t)|
$$

$$
f_c-k_f m_p < f_i(t)<f_c+k_f m_p
$$
The frequency deviation of $f_i(t)$ from the carrier frequency is: 
$$
\Delta f=k_f m_p
$$
The deviation ratio is: 
$$
\beta=\frac{\Delta f}{W}
$$
Where:

-   $W$ is the message bandwidth.

-   A small $\beta$ means narrow band FM.

-   A large $\beta$ means wide band FM.

Carsons rule states that the transmission bandwidth of FM is: 
$$
B_T=2W(\beta+1)=2(\Delta f+W)
$$


### FM Receiver


![FM receiver block diagram.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/fmreciever.png)

The bandpass filter removes the signals outside of $f_c \pm \frac{B_T}{2}$.

The limiter removes anu amplitude variations becasue an FM signal has a constant envelope.

The discriminator recovers the message signal. It is a device whose instaneous amplitude is proportional to instaneous frequency.

The bandpass lowpass filter removes the out of band noise. It has a bandwidth of $W$.

### High SNR properties

FM is nonlinear so suberposition doesn't hold.

For high SNR the noise and message signals are approximately independent of eachother.

Therefore noise doesn't affect the power of the message signal at the output and vice versa.

### Phase noise in high SNR


$$
x(t)=A\cos{[2\pi f_c t+\phi(t)]}+r(t)\cos{[2\pi f_c t+\psi(t)]}
$$

$$
\phi(t)=2\pi k_f \int_0^t m(\tau) \,d \tau
$$



![Phasor diagram of FM carrier and noise signals.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/FMphasor.png)

The instantaneous phase of the resultant phasor: 
$$
\theta(t)=\phi(t)+\arctan{\left[ \frac{r(t)\sin{(\psi(t)-\phi(t))}}{A+r(t)\cos{(\psi(t)-\phi(t))}}\right]}
$$
For a large carrier power (large A): 
$$
\theta(t)\approx\phi(t)+\frac{r(t)}{A}\sin{(\psi(t)-\phi(t))}
$$
The discriminator output is: 
$$
\frac{1}{2\pi}\frac{\,d \theta(t)}{\,d t}\approx k_f m(t)+n_d(t)
$$
The noise terms are: 
$$
n_d (t)=\frac{1}{2\pi A}\frac{\,d}{\,d t}[r(t)\sin{(\psi(t)-\phi(t))}]
$$
$\psi(t)$ is uniformly distributed over $[0,2\pi ]$. In a high SNR, it can be shown that $\psi(t)-\phi(t)$ is also uniform over $[0,2\pi ]$. This implies that noise is additive and $n_d(t)$ is independent of the message. 
$$
n_d(t)\approx\frac{1}{2\pi A}\frac{\,d }{\,d t} n_Q(t)
$$


### Noise PSD

The output signal power is: $P_S=k^2_f P$ where $P$ is the average power of the message signal.

It follows that: 
$$
S_o(f)=|H(f)|^2S_i(f)
$$
Where:

-   $S_i(f)$: PSD of the input signal.

-   $S_o(f)$: PSD of the output signal.

-   $H(f)$: transfer function of the system.

Therefore: 
$$
\left\lbrace \text{PSD of }n_d (t) \right\rbrace=|j2\pi f|^2\times \left\lbrace \text{PSD of }n_Q(t)\right\rbrace
$$

$$
\left\lbrace \text{PSD of }n_Q (t) \right\rbrace= \left\lbrace  N_0 \text{within band }\pm \frac{B_T}{2} \right\rbrace
$$

$$
\left\lbrace \text{PSD of }n_d (t) \right\rbrace= \left\lbrace  |2\pi f|^2\times N_0 \text{  where  } |f| \le \frac{B_T}{2} \right\rbrace
$$

$$
\left\lbrace \text{PSD of }f_i (t)=\frac{1}{2\pi A}\frac{\,d n_Q(t)}{\,d t} \right\rbrace= \left\lbrace \left( \frac{1}{2\pi A} \right)^2 |2\pi f|^2 \times N_0=\frac{f^2}{A^2}N_0  \right\rbrace
$$
After the low pass filter, the PSD of the noise output $n_o(t)$ is restricted in the band $\pm W$. For wideband FM: $W<<\frac{B_T}{2}$. 
$$
S_{N_O}(f)=\frac{F^2}{A^2}N_0 \qquad |f| \le W
$$



![(a) PSD of $N_Q(t)$ of $n(t)$. (b) PSD of $n_d(t)$ at discriminator output. (c) PSD of $n_o(t)$ at receiver output.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/noisepsdfm.png)

### Noise Power

Average noise power at receiver output: 
$$
P_N=\int_{-W}^{W}S_{N_o}(f)\,d f
$$
Thus: 
$$
P_N=\int_{-W}^{W}\frac{f^2}{A^2}N_0\,d f =\frac{2N_0 W^3}{3A^2}
$$
Average power at the output of an FM receiver: 
$$
\propto \frac{1}{\text{carrier power }A^2}
$$
As $A$ increases, the noise decreases. This is known as the noise quieting effect.

### Output SNR

Since $P_S=k_f^2 P$, the output SNR is: 
$$
SNR_O=\frac{P_S}{P_N}=\frac{3A^2k_f^2 P}{2N_0W^3}=SNR_{FM}
$$
The transmitted power of an FM waveform is $P_T=\frac{A^2}{2}$. 
$$
SNR_{baseband}=\frac{P_T}{N_0 W} \text{  and   }\beta=\frac{k_f m_p}{W}
$$

$$
SNR_{FM}=\frac{3k_f^2P}{W^2}SNR_{baseband}=3\beta^2\frac{P}{m_p^2}SNR_{baseband}\propto \beta^2 SNR_{baseband}
$$
This can be a lot higher than AM and is only valid when the carrier power is large compared to noise power.

#### Bandwidth-SNR tradeoff


$$
SNR_{FM}=3\beta^2 \frac{P}{m_p^2}SNR_{baseband}
$$
In wideband FM, transmission bandwidth $B_T$ is proportional to $\Delta f$. At a high SNR, an increase in $B_T$ provides quadratic increases in the output SNR.



## Pre/de-emphasis for FM and comparison of Analog systems

### Threshold Effect

An FM detector exhibits a more pronounced threshold effect than an AM envelope detector. The threshold point is around when signal power is 10 times noise power:\
Carrier to noise ratio: 
$$
\rho=\frac{A^2}{2N_0B_T}\qquad B_T=2W(\beta+1)
$$
Below the threshold ($\rho<10$) the FM receiver breaks. THis can be seen in the phasor diagram.


![FM phasor diagram.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/fmphasor2.png)

As the oise changes randomly, point $P_1$ wanders around $P_2$.

-   High SNR will have a small change in angle.

-   Low SNR will cause $P_1$ to occasionally sweep around the origin resulting in changes of $2\pi$ in a short time.

### Improving output SNR

PSD of nosie at detector output is proportional to the square f the frequency and the PSD of a message typically decays towards the ends of its band.


![PSD if noise and message at output.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/outputsnrfm.png)

To increase $SNR_{FM}$:

-   Use a low pass filter to cut off high frequencies at the output.

    -   This is bad because the message is attenuated too.

-   Use pre-emphasis and de-emphasis.

    -   The message remains unchaged.

    -   High frequency components of noise are suppressed.

#### Pre-emphasis and de-emphasis


![Pre-emphasis and de-emphasis block diagram.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/predeemp.png)

$H_{pe}(f)$ artificially emphasizes high frequency components of the message before noise is introduced.

$H_{de}(f)$ de-emphasizes high frequency components at the receiver and restores the original PSD of the message. 
$$
H_{pe}(f)\propto f \qquad \qquad H_{de}(f)\propto \frac{1}{f}
$$
This usually improves the output SNR by around $13dB$.

#### Improvement Factor

For an ideal pair of pre/de-emphasis filters: 
$$
H_{de}(f)=\frac{1}{H_{pe}(f)} \qquad |f| \le W
$$
PSD of the noise at the output of the de-emphasis filter: 
$$
\frac{f^2}{A^2}N_)|H_{de}(f)|^2 \qquad |f| \le \frac{B_T}{2}
$$
Average power of noise with de-emphasis: 
$$
P_N=\int_{-W}^{W}\frac{f^2}{A^2}|H_{de}(f)|^2N_0\,d f
$$
The improvement factor is: 
$$
I=\frac{P_N\text{ without pre/de-emphasis}}{P_N\text{ with pre/de-emphasis}}=\frac{\frac{2N_0W^3}{3A^2}}{\int_{-W}^{W}\frac{f^2}{A^2}|H_{de}(f)|^2N_0\,d f}=\frac{2W^3}{3\int_{-W}^{W}f^2|H_{de}(f)|^2\,d f}
$$


### Comparison of Analog Systems

The assumptions that are made:

-   Single tone mpdulation: $m(t)=A_m\cos{(2\pi f_m t)}$.

-   Message bandwidth $W=f_m$.

-   For AM system: $\mu=1$.

-   For FM system: $\beta=5$ (used in commercial FM transmission, with $\Delta f=75kHz$, and $W=15kHz$).

SNR expressions for various modulation schemes without pre/de-emphasis: 
$$
SNR_{DSB-SC}=SNR_{baseband}=SNR_{SSB}
$$

$$
SNR_{AM}=\frac{\mu^2}{2+\mu^2}SNR_{baseband}=\frac{1}{3}SNR_{baseband}
$$

$$
SNR_{FM}=\frac{3}{2}\beta^2 SNR_{baseband}=\frac{75}{2}SNR_{baseband}
$$



![Comparison of analog systems.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/analogs.png)

From this, the following conclusions can be made:

-   Full AM has SNR performance that is $4.8 dB$ worse than a baseband system, transmission bandwidth is $B_T = 2W$.

-   DSB has SNR performance that is identical to a baseband system, transmission bandwidth is $B_T=2W$.

-   SSB also has performance that is identical to a baseband system, but the transmission bandwidth is only $B_T=W$.

-   FM has SNR performance that is $15.7dB$ better than a baseband system with a transmission bandwidth of $B_T=2(\beta+1)W=12W$.

    (with pre- and de-emphasis SNR performance is increased by about $13 dB$ with the same transmission bandwidth.)



## Digital Representation of Signals


![Block diagram of Digital Communication.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/digitalcommsblockdiagram.png)

The advantages of digital are:

-   Digital signals are more immune to channel noise by using channel coding.

-   Repeaters along the transmission path can detect a digital signal and retransmit a new noise-free signal.

-   Digital signals derived from all types of analog sources can be represented using a uniform format.

-   Digital signals are easier to process by using microprocessors and VLSI (e.g., digital signal processors, FPGAs).

-   Digital systems are flexible and allow for implementation of sophisticated functions and control.

### Sampling and Quantization

The Nyquist frequency of a signal is the frequency at which a signal can be reconstructed perfectly from its samples. If a signal is band limited to $W$Hz then it can be reconstructed if the samples are taken at a rate $\ge 2W$Hz.

#### Quantizers

Quantization is the process of transforming the sample amplitude into a discrete amplitude taken from a finite set of possible amplitudes. The more levels, the better the approximation. For memoryless and instantaneous quantization, quantization at time $t$ is independent of other samples.


![A quantizer.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/quantizerblocks.png)

Amplitudes $m_1, ..., m_L$ are decision levels.

The decision region is $\mathcal{I}_k=\{m_k<m\le m_{k+1}\}$, where $k=1, ..., L$.

At the quantizer output, the decision region $k$ is represented by an amplitude $v_k$.

$v_k$, $k=1, ..., L$ are called the representation or reconstruction levels.

Mapping $v=g(m)$ is the quantizer characteristic.


![Graphs of quantization.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/quantgraph.png)


Quantization noise is the error between the input and output signals:


![Quantization Noise.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/quantizationnoise.png)

The variation in the Quantization noise is: 
$$
-\frac{\Delta}{2} \le q \le \frac{\Delta}{2}
$$
Where:

-   $\Delta$ is the gap between quantizing levels (of a uniform quantizer).

-   $q$ is the Quantization error that is any random variable that fits the range.

If $\Delta$ is sufficiently small then it is reasonable to assume that $q$ is uniformly distributed over this range: 
$$
f_Q(q)=\left\lbrace \begin{matrix}
\frac{1}{\Delta}, &  -\frac{\Delta}{2}\le q \le \frac{\Delta}{2} \\
0, &  \text{otherwise}
\end{matrix} \right.
$$
The quantization noise variance is: 
$$
P_N=E[q^2]=\int_{-\infty}^{\infty}q^2 f_Q(q)\,d q=\frac{1}{\Delta}\int_{-\frac{\Delta}{2}}^{\frac{\Delta}{2}}q^2 \,d q=\frac{1}{\Delta}\frac{q^3}{3}\left|_{-\frac{\Delta}{2}}^{\frac{\Delta}{2}} \right.=\frac{1}{\Delta}\left[ \frac{\Delta^3}{24}-\frac{(-\Delta)^3}{24}\right] =\frac{\Delta^2}{12}
$$


### SNR

Assuming that an encoded signal has $n$ bits:

-   The maximum number of quantizing levels is $L=2^n$.

-   THe maximum peak to peak dynamic range of the quantizer is $2^n \Delta$

The power of the signal is $P$ and $m_p=max|m(t)|$ and is the maximum absolute value of the message signal.

Assuming that the message signal fully loads the quantizer: 
$$
m_p=\frac{1}{2}2^n\Delta=2^{n-1}\Delta
$$
The SNR at the quantizer output is: 
$$
SNR_o=\frac{P_S}{P_N}=\frac{P}{\frac{\Delta^2}{12}}=\frac{12P}{\Delta^2}
$$

$$
\Delta=\frac{2m_p}{2^n}\Rightarrow\Delta^2=\frac{4m_p^2}{2^{2n}}
$$

$$
SNR_o=\frac{12P}{\frac{4m_p^2}{2^{2n}}}=\frac{3P}{m_p^2}2^{2n}
$$
In decibels: 
$$
SNR_o(dB)=10log_{10}(2^{2n})+10log_{10}\left( \frac{3P}{m_p^2} \right)=20n log_{10(2)}+10log_{10}\left( \frac{3P}{m_p^2} \right)=6n+10log_{10}\left(\frac{3P}{m_p^2}\right)(dB)
$$
Hence, each extra bit that is added, adds $6dB$ to the output SNR. Therefore there is a tradeoff between the signal to noise ratio and the bandwidth.

### Pulse Coded Modulation (PCM)


![Pulse Coded Modulation.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/PCM.png)

PCM isn't normal modulation, it is actuallt a type of Analog to Digital Converter. In Pulse Coded Modulation, the message is sampled above the Nyquist rate (with a low pass filter applied to avoid aliasing) and each sample is quantized. The discrete amplitudes are then all encoded into a binary codeword.


![Graph of the Pulse Coded Modulation process.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/pcmprocess.png)

### Uniform Quantization Problems

The problem with uniform quantization is that the output SNR is adversely affected by the peak to average power ratio.

Typically the small signal amplitudes occur more often that the large signal amplitudes. This means that the signal doesn't use the entire range of available quantization levels with equal probabilities. Along with this, small amplitudes aren't represented as well as large amplitudes since they are more susceptible to quantization noise.

#### Solution: Nonuniform Quantization

Nonuniform quantization uses quantization levels of varaible spacing which are denser at small signal amplitudes and broader at large amplitudes.


![Comparison of Uniform and Non Uniform Quantization.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/nonuniformquantization.png)

#### Solution: Companding

A practical and equivalent solution to nonuniform quantization is companding. The signal is:

1.  Compressed.

2.  Quantized.

3.  Transmitted.

4.  Expanded.

Companding corresponds to pre- and de-emphasis in FM. The message can be predistorted to achieve better performance in the presence of noise, and then the distortion can be removed at the receiver. The exact SNR gain that is obtained depends on the form of compression used. With proper companding, the output SNR can be made insensitive to peak to average power ratio. Ideally the compression are expansion are exactly the inverse of eachother.

##### Compander Standards: $\mu$-law vs A-law


![(a) $\mu$-law used in North America and Japan, (b) A-law used in most other countries of the world. Typical values in practice: $\mu = 255$, $A = 87.6$.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/companderstandards.png)

### Line Coding

The bits of PCM, DPCM, etc. need to be converted into electrical signals. Line coding encodes the but stream for transmission though a line of cable. Line coding is used for communication between a computer CPU and peripherals or ethernet.

#### Desired Properties of a Line code

-   The transmission bandwidth needs to be as small as possible.

-   The power efficiency needs to be good with as small power as possible for a given bandwidth and target error probability.

-   There needs to be error detection and correction capability.

-   There needs to be favourable power spectral density which should match the channel characteristics.

-   The extraction of timing information needs to be possible.

-   The Data should be transmitted reliably regardless of its binary pattern.

#### Types of Line codes


![(a) Unipolar nonreturn-to-zero signalling. (b) Polar nonreturn-to-zero signalling. (c) Unipolar Return-to-zero signalling. (d) Bipolar return-to-zero signalling. (e) Manchester code.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/linecodes.png)



## Baseband Digital Transmission

Whilst analog communications systems reproduce transmitted waveforms accurately, digital systems are just trying to identify the transmitted signal correctly. Therefore quality of analog is measured with SNR whilst for digital, the probability of error is used instead.

### Matched Fitler

A matched fitler uses a receiver than knows what shape the pulse is but that also minimises the effect of noise.


![Matched Filter](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/matchedfilter.png)


$$
x(t)=g(t)+w(t) \qquad \qquad 0 \le t \le T_b
$$
The filter is linear so: 
$$
y(t)=g(t) \ast h(t) + w(t) \ast h(t)=g_o(t)+n(t)
$$
The instantaneous power of the signal component $g_o(t)$ at $t=T_b$ needs to be as large as possible compared to the noise component $n(t)$. (Peak pulse SNR): 
$$
\eta=\frac{|g_o(T_b)|^2}{E[n^2(t)]}=\frac{instantaneous power}{average power}
$$


#### Derivation

Noise: 
$$
n(t)=w(t)\ast h(t)
$$

$$
S_N(f)=S_W(f) S_H(f)=\frac{N_0}{2}|H(f)|^2
$$

$$
E[n^2(t)]=\int_{-\infty}^{\infty} S_N(f)\,d f=\frac{N_0}{2}\int_{-\infty}^{\infty}|H(f)|^2\,d f
$$
Signal: 
$$
g_o(t)=g(t)\ast h(t) \qquad \qquad G_O(f)=H(f)G(f)
$$

$$
g_o(t)=\int_{-\infty}^{\infty}H(f)G(f)e^{j 2 \pi f t} \,d f
$$

$$
|g_o(T_b)|^2=\left| \int_{-\infty}^{\infty}H(f)G(f)e^{j 2 \pi f T_b}\,d f \right|^2
$$
For the $h(t)$ that maximises $\eta$: 
$$
\eta=\frac{\left| \int_{-\infty}^{\infty}H(f)G(f)e^{j 2 \pi f T_b}\,d f \right|^2}{\frac{N_0}{2}\int_{-\infty}^{\infty}|H(f)|^2\,d f}
$$
Schwartz's Inequality states that for two energy signals $\phi_1(x)$, and $\phi_2(x)$: 
$$
\left| \int_{-\infty}^{\infty}\varphi_1(x)\varphi_2(x)\,d x \right|^2 \le \int_{-\infty}^{\infty}|\varphi_1(x)|^2\,d x \int_{-\infty}^{\infty}|\varphi_2(x)|^2\,d x
$$
Equality only holds if $\varphi_1(x)=k\varphi^*_2(x)$ for an arbitrary constant $k$.

Letting $\varphi_1(f)=H(f)$ and $\varphi_2(f)=G^*(f)e^{-j 2 \pi f T_b}$: 
$$
\left| \int_{-\infty}^{\infty}H(f)G(f)e^{j 2 \pi f T_b}\,d f \right|^2 \le \int_{-\infty}^{\infty}|H(f)|^2 \,d f\int_{-\infty}^{\infty}|G(f)|^2 \,d f
$$

$$
\eta=\frac{\left| \int_{-\infty}^{\infty}H(f)G(f)e^{j 2 \pi f T_b}\,d f \right|^2}{\frac{N_0}{2}\int_{-\infty}^{\infty}|H(f)|^2\,d f}\le \frac{2}{N_0}\int_{-\infty}^{\infty}|G(f)|^2\,d f
$$

$$
\eta_{max}=\frac{2}{N_0} \int_{-\infty}^{\infty} |G(f)|^2 \,d f
$$
This occurs if: 
$$
H_{opt}(f)=kG^*(f)|e^{-j 2\pi f T_b}
$$
Hence: 
$$
h_{opt}(t)=kg^*(T_b - t)=kg(T_b - t)
$$


#### Properties

Impulse response is: 
$$
h_{opt}(t)=kg(T_b-t)
$$
$T_b$ is the symbol period, whilst $g(t)$ is the transmitter pulse shape, and $k$ is the gain. This is a time reversed shifted version of $g(t)$.

The matched filter maximises peak pulse SNR: 
$$
\eta_{max}=\frac{2}{N_0} \int_{-\infty}^{\infty} |G(f)|^2 \,d f=\frac{2}{N_0} \int_{-\infty}^{\infty} |g(t)|^2 \,d t = \frac{2E}{N_0}=SNR
$$


For a matched filter for a rectangular pulse shape, the impulse response will be a rectangular pulse of the same duration. If this input is convolved with a rectangular pulse of duration $T_b$ seconds and it is equivalent to integrating for $T_b$ seconds, then sampling at a symbol period of $T_b$ seconds before resetting the intgration for the enxt pulse. A circuit that does this would consist of an integration block followed by a switch at $t=nT_b$ and is known as an integrate and dump circuit.


![Matched Filter for a Rectangular Pulse](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/matchedrect.png)

### Binary Baseband Communication System

A binary communication system compares a sample of the output of a matched filter with a theshold value and outputs a binary depending upon whether the sample is greater or lesser than the threshold.


![Binary Baseband Communication System circuit.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/binbaseband.png)

It is assumed that it is the AWGN channel with double sided noise PSD of $\frac{N_0}{2}$. and the mathced filter is rectangular. The effect of additive noise needs to be closely monitored since bit errors can occur.

#### Noise Distribution

After the matched filter, the predetection signal is: 
$$
Y=y(T_b)=\frac{1}{T_b}\int_{0}^{T_b} x(t) \,d t = s+\frac{1}{T_b}\int_{0}^{T_b}w(t)\,d t
$$
Where the $s$ term is the binary value, and the none $s$ term is the noise $N$.vTHis is zero mean additive white guassian noise with variance: 
$$
\sigma^2 = E[N^2]=\frac{1}{T_b^2}\int_{0}^{T_b}\int_{0}^{T_b}E[w(t)w(u)]\,d t \,d u=\frac{1}{T_b^2}\int_{0}^{T_b}\int_{0}^{T_b}R_w(t,u)\,d t \,d u = \frac{1}{T_b^2}\int_{0}^{T_b}\int_{0}^{T_b}\frac{N_O}{2}\delta (t-u)\,d t \,d u = \frac{N_O}{2T_b}
$$
$N$ is a guassian rv with pdf: 
$$
p_N(n)=\frac{1}{\sigma \sqrt{2\pi}}exp{\left( -\frac{n^2}{2\sigma^2} \right)}=N(0,\sigma^2)
$$


#### Decision

If a symbol $0$ were transmitted: $Y=N$ with pdf $N(0,\sigma^2)$.

If a symbol $1$ were transmitted: $Y=N+A$ with pdf $N(A,\sigma^2)$.

#### Errors

The probability of $0$ being transmitted but $1$ being decided has probability $P_{e0}$ (case i), whilst the opposite is $P_{e1}$ (case ii).


![Probability density functions for binary data transmission in noise: (a) symbol 0 transmitted, and (b) symbol 1 transmitted. Here $\lambda = \frac{A}{2}$.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/binaryerror.png)

For case i: 
$$
p(i)=P_{e0}\times p_0
$$
Where: 
$$
P_{e0}=\int_{\lambda}^{\infty}\frac{1}{\sigma \sqrt{2\pi}}\exp{\left( -\frac{n^2}{2\sigma^2} \right)}\,d n
$$
For case ii: 
$$
p(ii)=P_{e1}\times p_1
$$
Where 
$$
P_{e0}=\int_{-\infty}^{\lambda}\frac{1}{\sigma \sqrt{2\pi}}\exp{\left( -\frac{(n-A)^2}{2\sigma^2} \right)}\,d n
$$
The total error probability is: 
$$
P_e(\lambda)=P(i)+p(ii)=p_1P_{e1}+(1-p_1)P_{e0}=p_1 \int_{-\infty}^{\lambda}\frac{1}{\sigma \sqrt{2\pi}}\exp{\left( -\frac{(n-A)^2}{2\sigma^2} \right)}\,d n+(1-p_1)\int_{\lambda}^{\infty}\frac{1}{\sigma \sqrt{2\pi}}\exp{\left( -\frac{n^2}{2\sigma^2} \right)}\,d n
$$
Then $\lambda$ must be schose so that $P_e(\lambda)$ is at a minimum: 
$$
\frac{\,d P_e (\lambda)}{\,d \lambda}=0
$$


#### Derivation

Use leibnitz rule: 
$$
I(\lambda)=\int_{A(\lambda)}^{b(\lambda)}f(x;\lambda)\,d x
$$

$$
\frac{\,d I(\lambda)}{\,d \lambda}=\frac{\,d b(\lambda)}{\,d \lambda}f(b(\lambda);\lambda)-\frac{\,d a(\lambda)}{\,d \lambda}f(a(\lambda);\lambda)+\int_{A(\lambda)}^{b(\lambda)}\frac{\partial f(x;\lambda)}{\partial \lambda}\,d x
$$
 Therefore: 
$$
\frac{\,d P_e (\lambda)}{\,d \lambda}=p_1 \frac{1}{\sigma \sqrt{2\pi}}\exp{\left( -\frac{(n-A)^2}{2\sigma^2} \right)}-(1-p_1)\frac{1}{\sigma \sqrt{2\pi}}\exp{\left( -\frac{n^2}{2\sigma^2} \right)}=0
$$

$$
\frac{p_1}{1-p_1}=\exp{\left(-\frac{\lambda^2-(\lambda-A)^2}{2\sigma^2}\right)}=\exp{\left(-\frac{\lambda^2-\lambda^2-A^2+2\lambda A}{2\sigma^2}\right)}=\exp{\left( -\frac{A(2\lambda-A)}{2\sigma^2} \right)}
$$


#### Optimum Threshold

This would be where $p_1=p_0=(1-p_1)$ which when subbed into: 
$$
\frac{p_1}{1-p_1}=\exp{\left( -\frac{A(2\lambda-A)}{2\sigma^2} \right)}\Rightarrow \lambda = -\frac{\sigma^2}{A}\ln{\left(\frac{p_1}{1-p_1}\right)}+\frac{A}{2}\Rightarrow\lambda=0+\frac{A}{2}=\frac{A}{2}
$$


#### Calculation of $P_e$

A new variable of integration is defined: 
$$
z \equiv \frac{n}{\sigma}\Rightarrow\,d z=\frac{1}{\sigma}\,d n \Rightarrow \,d n = \sigma \,d z
$$
Then: 
$$
P_{e0}=\frac{1}{\sigma\sqrt{2\pi}}\int_{\frac{A}{2\sigma}}^{\infty}e^{-\frac{z^2}{2}}\sigma \,d z = \frac{1}{\sqrt{2\pi}}\int_{\frac{A}{2\sigma}}^{\infty}e^{-\frac{z^2}{2}}\,d z
$$
$P_{e0}$ can then be expressed in terms of the Q-function: 
$$
Q(x)=\frac{1}{\sqrt{2\pi}}\int_{x}^{\infty}\exp{\left( -\frac{t^2}{2} \right)}\,d t
$$
Then: 
$$
P_e=Q\left(\frac{A}{2\sigma}\right)
$$
If the energy of a pulse is $E=A^2 T_b$ and a pulse is only transmitted half the time (on average) then the average energy per bit $E_{b}$vis: 
$$
E_b=\frac{A^2 T_b}{2}
$$
And the noise variance is: 
$$
\frac{N_O}{2T_b}
$$
The probability of error in terms of energy per bit and noise PSD is: 
$$
p_e=Q\left(\sqrt{\frac{E_b}{N_O}}\right)
$$


#### Q-function boundaries

For large $x$: 
$$
Q(x) \le \frac{1}{\sqrt{2\pi}x}e^{-\frac{x^2}{2}}, x \ge 0
$$
For small $x$: 
$$
Q(x) \le \frac{1}{2}e^{-\frac{x^2}{2}}, x \ge 0
$$



## Digital Modulation

### Digital Passband Modulation

In baseband, a linearly modulated waveform is given by: 
$$
u(t)=\sigma_n b[n]p(t-nT)
$$
Where $b[n]$ is the sequence of symbols to be transmitted, and $p(t)$ is the modulating pulse. In digital passband modulation:

-   Assume symbols take values from $\{-1, +1\}$, and modulating pulse is rectangular time-limited pulse.

-   In passband, $s(t) = u(t)\cos{(2 \pi f_c t)}$ can be transimtted simply.

-   For the $nth$ symbol interval, $nT\le t \le(n+1)T$: $s(t)=\cos{(2\pi f_c t)}$ if $b[n]=+1$ and $s(t)=\cos{(2\pi f_c t+\pi)}$ if $b[n]=-1$.

-   Binary antipodal modulation switches the phase of the carrier between $0$ and $\pi$, hence it is called binary phase-shift keying (BPSK)

The passband signal can be written as: 
$$
s(t)=u_I (t) \cos{(2\pi f_c t)}-u_Q (t) \cos{(2\pi f_c t)}
$$
Both the I and Q components can be modulated. If only the I component is modulated, then it is BSPK, if both are modulated then it is QPSK (quadrature phase shift keying).


![$s(t)$ for different values of $b_I[n]$ and $b_Q[n]$](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/qpsk.png)


![(a) Amplitude-shift keying (ASK), (b) Phase-shift keying (PSK), (c) Frequency-shift keying](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/digitalmodulation.png)


![Signal constellations.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/signalconstellations.png)

### Demodulation


![Digital signal transmission.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/digidemod.png)

To demodulate a digital signal, coherent detection can be used:

-   Use a BPF to reject out-of-band noise.

-   Multiply the incoming waveform with a cosine of the carrier frequency.

-   Use a LPF.

-   Requires carrier regeneration (both frequency and phase synchronization using a phase-locked loop).

Or noncoherent demodulation such as envelope detection can be used. This however will make no explicit effor to estimate the phase.

### ASK Coherent Demodulation

In an ASK signal: 
$$
s_0(t)=0
$$

$$
s_1(t)=A\cos{(2\pi f_c t)}
$$
Pre-detection signal is: 
$$
x(t)=s(t)+n(t)=A(t)\cos{(2\pi f_c t)}+n_I(t)\cos{(2 \pi f_c t)}-n_Q(t)\sin{(2\pi f_c t)}
$$

$$
=[a(t)+n_I(t)]\cos{2\pi f_c t)}-n_q(t)\sin{(2 \pi f_c t)}
$$
After multiplication with $2\cos{(2\pi f_c t)}$: 
$$
y(t)=[A(t)+n_I(t)]2\cos^2{(2\pi f_c t)}-n_Q(t)2\sin{(2\pi f_c t)}\cos{(2\pi f_c t)}=[A(t)+n_I(t)](1+\cos{(4\pi f_c t)})-n_Q(t)\sin{(4\pi f_c t)}
$$
After the low pass filtering: 
$$
\tilde{y}(t)=A(t)+n_I(t)
$$


#### Bit Error Rate (BER)

The PSD of in-phase noise component $n_I (t)$ is $N_o$, double the PSD of the original band-pass noise $n(t)$. Assuming equi-probable transmission of 0s and 1s, then the decision threshold must be $\frac{A}{2}$ and the probability of error is given by: 
$$
P_{e,ASK}=Q\left(\frac{A}{2\sigma}\right)
$$
Transmission energy for a pulse is: 
$$
E=\frac{a^2 T_b}{2}
$$
The average energy per bit is: 
$$
E_b=\frac{A^2 T_b}{4}
$$
The noise variance is: 
$$
\frac{N_o}{T_b}
$$
The probability of error in terms of energy per bit and noise PSD is therefore: 
$$
P_{e,ASK}=Q\left( \sqrt{\frac{E_b}{N_o}} \right)
$$


### PSK Analysis

In an PSK signal: 
$$
s(t)=A(t)\cos{(2\pi f_c t)}, \qquad \qquad A(t) \in \{-A,A\}
$$
Coherent detection is used to get the detection signal: 
$$
\tilde{y}(t)=A(t)+n_I(t)
$$



![The pdfs for PSK for equiporbable 0s and 1s in noise.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/pskpdfs.png)

The conditional error probalities are are: 
$$
P_{e0}=\int_{0}^{\infty}\frac{1}{\sigma \sqrt{2\pi}}\exp{\left(-\frac{(n+A)^2}{2\sigma^2}\right)}\,d n
$$

$$
P_{e1}=\int_{-\infty}^{0}\frac{1}{\sigma \sqrt{2\pi}}\exp{\left(-\frac{(n-A)^2}{2\sigma^2}\right)}\,d n
$$
In the first, setting $\tilde{n}\equiv n+A \Rightarrow \,d n = \,d \tilde{n}$ and when $n=0$, $\tilde{n}=A$: 
$$
P_{e0}=\frac{1}{\sigma\sqrt{2\pi}}\int_{A}^{\infty}\exp{\left(-\frac{\tilde{n}^2}{2\sigma^2}\right)}\,d \tilde{n}
$$
In the second, setting $\tilde{n}\equiv -(n+A)=-n+A \Rightarrow \,d n = -\,d \tilde{n}$ and when $n=0$, $\tilde{n}=A$: 
$$
P_{e1}=\frac{1}{\sigma\sqrt{2\pi}}\int_{\infty}^{A}\exp{\left(-\frac{\tilde{n}^2}{2\sigma^2}\right)}(-1)\,d \tilde{n}=\frac{1}{\sigma\sqrt{2\pi}}\int_{A}^{\infty}\exp{\left(-\frac{\tilde{n}^2}{2\sigma^2}\right)}(-1)\,d \tilde{n}
$$


#### Bit Error Rate

$$
P_{e0}=P_{e1}=P_{e,PSK}=\int_{A}^{\infty}\frac{1}{\sigma\sqrt{2\pi}}\exp{\left(-\frac{n^2}{2\sigma^2}\right)}\,d n
$$
Changing the variable of integration to $z\equiv\frac{n}{\sigma}\Rightarrow\,d n = \sigma \,d z$ and when $n=A$, $z=\frac{A}{\sigma}$ Then: 
$$
P_{e,PSK}=\frac{1}{\sqrt{2\pi}}\int_{\frac{A}{\sigma}}^{\infty}e^{-\frac{z^2}{2}}\,d z = Q\left(\frac{A}{\sigma}\right)
$$
The average energy per bit is: 
$$
E_b=\frac{A^2 T_b}{2}
$$
The noise variance is: 
$$
\frac{N_o}{T_b}
$$
The probability of error in terms of energy per bit and noise PSD: 
$$
P_{e,PSK}=Q\left(\sqrt{\frac{2E_b}{N_o}}\right)
$$


### Frequency Shift Keying

For FSK: 
$$
s_0(t)=A\cos{(2\pi f_0 t)}
$$

$$
s_1(t)=A\cos{(2\pi f_1 t)}
$$
To recover this signal, two sets of coherent detectors are used operating at frequencies $f_0$ and $f_1$.


![Coherent FSK demodulation. The two BPF's are non-overlapping in frequency spectrum.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/fskdemod.png)

In each branch of the ASK detector, the output of the LPF has $A+noise$ if symbol is present, and just $noise$ if the signal is not present. Each noise term has identical statistics to $n_I(t)$.

The output if a symbol 1 was transmitted: 
$$
y=y_1(t)=A+[n_1(t)-n_0(t)]
$$

The output if a symbol 0 was transmitted: 
$$
y=y_1(t)=-A+[n_1(t)-n_0(t)]
$$


#### Bit Error Rate for FSK

The detection threshold should be 0. THe difference from PSK is that the noise term is now $n_1(t)-n_0(t)$. The noises in the two channels are independent because their spectra are non-overlapping. THe variances add meaning the noise variance doubles. 
$$
P_{e,FSK}=Q\left(\frac{A}{\sqrt{2}\sigma}\right)
$$
The average energy per bit is: 
$$
E_b=\frac{A^2T_b}{2}
$$
The noise variance is: 
$$
2\sigma^2=\frac{2N_o}{T_b}
$$
The probability of error in terms of energy per bit and noise PSD is: 
$$
P_{e,FSK}=Q\left(\sqrt{\frac{E_b}{N_o}}\right)
$$


#### Sum of two RVs

The variance for $Y\equiv X_1 \pm X_2$ where $X_i$ is a random variable with variance $\sigma_i^2$: 
$$
\sigma_Y^2=E[Y^2]-E[Y]^2=E[(X_1 \pm X_2)^2]=E[X_1^2 \pm 2X_1X_2+X_2^2]=E[X_1^2] \pm E[X_1 X_2]+E[X_2^2]
$$
For independent variables: 
$$
E[X_1X_2]=X[X_1]E[X_2]
$$

For zero-mean random variables: 
$$
E[X_1]=E[X_2]=0 \Rightarrow E[X_1 X_2] = 0
$$
So: 
$$
\sigma_Y^2=X[X_1^2]+E[X_2^2]=\sigma_1^2+\sigma_2^2
$$

![Comparison of PSK, ASK, and FSK.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/schemecomp.png)



## Non coherent Demodulation

Coherent demodulation assumes perfect synchronization, however accurate phase synchronization may be difficult in a dynamic channel due to varying propagation delays, frequency drift, oscillator instability, and noise. In this case non coherent demodulation must be used. The phase is assumed to be uniformly distributed on $[0,2\pi]$.

### ASK non coherent demodulation


![Non coherent demodulation of ASK.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/ncdask.png)

Output of the BPF: 
$$
\text{When }0\text{ is sent}: \quad y(t)=n(t)
$$

$$
\text{When }1\text{ is sent}: \quad y(t)=n(t)+A\cos{(2\pi f_c t)}
$$
Since: 
$$
n(t)=n_I(t)\cos{(2\pi f_c t)}-n_Q(t)\sin{(2\pi f_c t)}
$$
The envelope is: 
$$
R=\sqrt{n_I^2(t)+n_Q^2(t)}\quad \text{when }0\text{ is sent}
$$

$$
R=\sqrt{(A+n_I(t))^2+n_Q^2(t)}\quad \text{when }1\text{ is sent}
$$
When $0$ is sent the envelope (just bandpass noise) has Rayleigh distribution: 
$$
f(r)=\frac{r}{\sigma^2}e^{-\frac{r^2}{2\sigma^2}}, \quad r \ge 0
$$
When $1$ is sent the envelope (signal and bandpass noise) has Rician distribution: 
$$
f(r)=\frac{r}{\sigma^2}e^{-\frac{r^2+A^2}{2\sigma^2}}I_0\left(\frac{Ar}{\sigma^2}\right), \quad r \ge 0
$$


#### Rayleigh Distribution

$R$ has a rayleigh distribution if $X$ and $Y$ are independent gaussians in the form $R=\sqrt{X^2+Y^2}$: 
$$
f_R(r)=\frac{r}{\sigma^2}e^{-\frac{r^2}{2\sigma^2}}, \quad r \ge 0
$$



![Rayleigh Distribution.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/rayleigh.png)

##### Derivation

Change it to polar form: 
$$
R=\sqrt{X^2+Y^2} \qquad \Theta= \arctan{\frac{Y}{X}}
$$
 Consider a small area $\,d x \,d y=r \,d r \,d \theta$: 
$$
f_{R,\Theta}(r,\theta) \,d r \,d \theta =f_{X,Y} (x,y) \,d x \,d y=f_{X,Y}(x,y)r \,d r \,d \theta=\frac{1}{2\pi \sigma^2}e^{-\frac{x^2+y^2}{2\sigma^2}}r\,d r \,d \theta
$$
 Hence: 
$$
f_{R,\Theta}(r,\theta)=\frac{r}{2\pi \sigma^2}e^{-\frac{x^2+y^2}{2\sigma^2}}=\frac{r}{2\pi \sigma^2}e^{-\frac{r}{2\sigma^2}}
$$
 The pdf of $R$ is: 
$$
f_R(r)=\int_{0}^{2\pi} f_{R,\Theta}(r,\theta)\,d \theta =\frac{r}{\sigma^2}e^{-\frac{r^2}{2\sigma^2}} \quad r>0
$$
 The pdf of $\Theta$ is: 
$$
f_\Theta(\theta)=\int_{0}^{2\pi} f_{R,\Theta}(r,\theta)\,d r =\frac{1}{2\pi} \quad \theta \in [0,2\pi]
$$


#### Rician Distribution

If $X$ has nonzero mean $A$, $R$ has Rician distribution: 
$$
f_R(r)=\frac{r}{\sigma^2}e^{-\frac{r^2+A^2}{2\sigma^2}}I_0\left(\frac{Ar}{\sigma^2}\right)\quad r \ge 0
$$
 Where: 
$$
I_0(x)=\frac{1}{2\pi}\int_0^{2\pi}e^{x\cos{\theta}}\,d \theta
$$
 This is the modified zero order Bessel function of the first kind.


![Rician Distribution.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/rician.png)

##### Derivation


$$
f_{R,\Theta}(r,\theta) \,d r \,d \theta =f_{X,Y}(x,y)r \,d r \,d \theta = \frac{1}{2\pi \sigma^2}e^{-\frac{(x-A^2)+y^2}{2\sigma^2}} r\,d r\,d \theta= \frac{1}{2\pi \sigma^2}e^{-\frac{r^2-A^2-2Ar\cos{\theta}}{2\sigma^2}} r\,d r\,d \theta
$$
 Hence: 
$$
f_{R,\Theta}(r,\theta)=\frac{r}{2\pi \sigma^2}e^{-\frac{r^2-A^2-2Ar\cos{\theta}}{2\sigma^2}} r\,d r\,d \theta
$$
 The pdf of R is: 
$$
f_R(r)=\int_{0}^{2\pi}f_{R,\Theta}(r,\theta)\,d \theta =\frac{r}{\sigma^2}e^{-\frac{r^2+A^2}{2\sigma^2}}\frac{1}{2\pi}\int_{0}^{2\pi}e^{\frac{Ar\cos{\theta}}{\sigma^2}}\,d \theta \quad r>0
$$


#### Error Probability

The threshold is $\frac{A}{2}$, the error probability is dominated by symbol $0$ and is given by: 
$$
P_e \approx \frac{1}{2}\int_{\frac{A}{2}}^{\infty}\frac{r}{\sigma^2}e^{-\frac{r^2}{2\sigma^2}}\,d r
$$
The final expression is: 
$$
P_{e,ASK,noncoherent}\approx\frac{1}{2}e^{-\frac{A^2}{8\sigma^2}}
$$
Non coherent demodulation results in some performance degradation as coherent demodulation. Yet, for large SNR, performances are similar.

### Non coherent demodulation of FSK


![Non coherent demodulation of FSK.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/ncdfsk.png)

When a symbol $1$ is sent the BPF outputs are: 
$$
y_1(t)=m_1(t)
$$

$$
y_2(t)=n_2(t)+A\cos{(2\pi f_2 t)}
$$
The first has a Rayleigh distribution and the second has a Rice distribution: 
$$
f_{R_1}(r_1)=\frac{r_1}{\sigma^2}e^{-\frac{r_1^2}{2\sigma^2}} \quad r_1 \ge 0
$$

$$
f_{R_2}(r_2)=\frac{r_2}{\sigma^2}e^{-\frac{r_2^2+A^2}{2\sigma^2}}I_0 \left(\frac{Ar_2}{\sigma^2}\right) \quad r_2 \ge 0
$$
$R_1$ and $R_2$ are independent.

Error occurs if Rice \< Rayleigh. 
$$
P_e=P(R_2 < R_1)
$$

$$
\int_{0}^{\infty}\int_{r_2}^{\infty}\frac{r_2}{\sigma^2}e^{-\frac{r_2^2+A^2}{2\sigma^2}}I_0 \left(\frac{Ar_2}{\sigma^2}\right)\frac{r_1}{\sigma^2}e^{-\frac{r_1^2}{2\sigma^2}} \,d r_1 \,d r_2=\int_{0}^{\infty}\frac{r_2}{\sigma^2}e^{-\frac{r_2^2+A^2}{2\sigma^2}}I_0 \left(\frac{Ar_2}{\sigma^2}\right)\int_{r_2}^{\infty}\frac{r_1}{\sigma^2}e^{-\frac{r_1^2}{2\sigma^2}} \,d r_1 \,d r_2
$$

$$
\int_{0}^{\infty}\frac{r_2}{\sigma^2}e^{-\frac{r_2^2+A^2}{2\sigma^2}}I_0 \left(\frac{Ar_2}{\sigma^2}\right)\,d r_2=\frac{1}{2}e^{\frac{A^2}{4\sigma^2}}\int_{0}^{\infty}\frac{x}{\sigma^2}e^{-\frac{x^2+\alpha^2}{2\sigma^2}}I_0 \left( \frac{\alpha x}{\sigma^2} \right) \,d x
$$

$$
\text{Where }x=\sqrt{2}r_2, \; \alpha = \frac{A}{\sqrt{2}}
$$
 The integrand is Rician density: 
$$
P_{e,FSK, non coherent}=\frac{1}{2}e^{-\frac{A^2}{4\sigma^2}}
$$


### Differential PSK

It is impossible to demodulate PSK with an envelop detector, since PSK signals have the same frequency and amplitude. Demodulation of PSK occurs differentially, where phase reference is provided by a delayed version of the signal in the previous interval.


![Differential encoding for DPSK.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/dpsk.png)

#### Differential Demodulation


![Differential demodulation.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/diffdemod.png)

The error probability is: 
$$
P_{e,DPSK}=\frac{1}{2}e^{-\frac{A^2}{2\sigma^2}}
$$



![Illustration of DPSK.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/dpsktable.png)

### Summary and Comparison

|      Scheme      |               Bit Error Rate                |
| :--------------: | :-----------------------------------------: |
|   Coherent ASK   |     $Q\left( \frac{A}{2\sigma} \right)$     |
|   Coherent FSK   | $Q\left( \frac{A}{\sqrt{2}\sigma} \right)$  |
|   Coherent PSK   |     $Q\left( \frac{A}{\sigma} \right)$      |
| Non Coherent ASK | $\frac{1}{2}\exp{(-\frac{A^2}{8\sigma^2})}$ |
| Non Coherent FSK | $\frac{1}{2}\exp{(-\frac{A^2}{4\sigma^2})}$ |
|       DPSK       | $\frac{1}{2}\exp{(-\frac{A^2}{2\sigma^2})}$ |

![Comparison of demodulation types.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/snrgraph.png)



## Entropy and Data Compression


![Digital communication systems model.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/digicomms.png)

Amount of information in a symbol $s$ with probability $p$: 
$$
I(s)=log \left( \frac{1}{p} \right)
$$
Properties:

-   $p=1 \Rightarrow I(s)=0$ a deterministic symbol contains no information.

-   $0 \le p \le 1 \Rightarrow 0 \le I(p) \le \infty$ information measure is monotonic and non- negative.

-   $p=p_1 \times p_2 \Rightarrow I(s)=I(p_1)+I(p_2)$ information from statistically independent events is additive.

Log base 2 is used to represent bits $p_1=p_2=0.5$.

Suppose there is an information source emitting a sequence of symbols from a finite alphabet: 
$$
S=\{ s_1, s_2, ... s_K \}
$$
This is a discrete memoryless source: The successive symbols are statistically independent and identically distributed. It is assumed that each symbol has a probability: 
$$
p_k \text{ where } k=1,...,K, \text{ such that }\sum_{k=1}^{K}p_k=1
$$
If a symbol $s_k$ has occurred this corresponds to $I(s_k)$ bits of information: 
$$
I(S_k)=\log_2{\left(\frac{1}{p_k}\right)}=-\log_2{(p_k)}
$$
The expected value of $I(s_k)$ over the source alphabet is: 
$$
E \{I(s_k)\}=\sum_{k=1}^{K}p_k I(s_k)=-\sum_{k=1}^{K}p_k \log_2{(p_k)}
$$
Source entropy is the average amount of information per source symbol with units, bits/symbol: 
$$
H(S)=-\sum_{k=1}^{K} p_k \log_2{(p_k)}
$$
Entropy is the amount of uncertainty before the source is received. It shows how many bits of information per symbol there are on the average by learning the source realization. In general, entropy is maximized when the source is uniformly distributed over its alphabet. Bits are wasted if more that 1 symbol is required per symbol.

### Source Coding Theory

Source encoding: concerned with minimizing the actual number of source bits that are transmitted to the user.

Channel encoding: concerned with introducing redundant bits to enable the receiver to detect and possibly correct errors that are introduced by the channel.

#### Average Codeword Length

The average codeword length is: 
$$
\overline{L}=\sum_{k=1}^K p_k l_k
$$
Where:

-   $l_k$ is the number of bits used to code the $k_{th}$ symbol.

-   $K$ is the total number of symbols.

-   $p_k$ is the probability of occurrence of symbol $k$.

To reduce the average codeword length, symbols that occur often should be encoded with shorter codewords, whilst symbols that occur rarely may be encoded using longer codewords.

### Minimum Codeword Length

In a system with $n$ symbols that are equally likely, the probability of each symbol to occur is: 
$$
p=\frac{1}{n}
$$
One needs $L=\log_2{n}=\log_2{\frac{1}{p}}=-\log_2{p}$ bits to represent the symbols.

#### The general case

-   $S=\{s_1,...,s_K\}$ is an alphabet.

-   $p_k$ is the probability of symbol $s_k$ to occur.

-   $N$ is the number of symbols generated.

-   $N p_k$ occurrences of $s_k$ are expected.

-   It is assumed that:

    -   The source is memoryless.

    -   All symbols are independent.

    -   Probability of occurrence of a typical sequence $S_N$ is: 
$$
p(S_N)=p_1^{Np_1}\times p_2^{Np_2}\times ... \times p_K^{Np_K}
$$


-   All such typical sequences of $N$ symbols are equally likely.

-   All other compositions are extremely unlikely to occur as $N \to \infty$

#### Source Coding Theorem

The number of bits required to represent a typical sequence $S_N$: 
$$
L_N=\log_2 \left(\frac{1}{p(S_N)}\right)=-\log_2{(p_1^{Np_1}\times p_2^{Np_2}\times ... \times p_K^{Np_K})}
$$

$$
=-Np_1 \log_2 {p_1}-Np_2 \log_2 {p_2}-...-Np_K \log_2 {p_K}=-N\sum_{k=1}^{K}p_k \log_2{p_k}=NH(S)
$$
The average length for one symbol is: 
$$
\overline{L}=\frac{L_N}{N}=H(S) bits/symbol
$$
**Given a discrete memoryless source of entropy $H(S)$, average codeword length for any source coding scheme is bounded by $H(S)$:** 
$$
\overline{L} \ge H(S)
$$


### Huffman Coding

Huffman coding is an efficient source coding algorithm. It yields the shortest average codeword length. The basic idea is to choose codeword lengths so that more-probable sequences have shorter codewords.

Huffman Code construction:

-   Sort source symbols in order of decreasing probability.

-   Take two smallest $p(x_i)$ and assign each a different bit (i.e., $0$ or $1$). Then merge into a single symbol.

-   Repeat until only one symbol remains.


![An example of Huffman Coding.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/huffmanexample.png)

The average codeword length in this example is: 
$$
\overline{L}=(2\times 0.4)+(2\times 0.2)+(2\times 0.2)+(3 \times 0.1)+(3 \times 0.1)=2.2
$$
Huffman code is not unique (equal probabilities can be reordered) and is the most efficient prefix code.


![A clearer example of Huffman Coding using a tree.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/huffmantree.png)

A drawback of Huffman coding is that it requires knowledge of a probabilistic model, which is not always available.



## Channel Capacity

### Introduction

In a discrete memoryless channel, the channel output $Y$ is a noisy version of channel input $X$.

The input alphabet is: 
$$
X=\{x_0, x_1,...x_{J-1}\}
$$
The output alphabet is: 
$$
Y=\{y_0, y_1,...y_{K-1}\}
$$
Transition probabilities are: 
$$
p(y_k|x_j)=P(Y=y_k|X=x_j)
$$
Assume that the input is selected based on: 
$$
p(x_j)=P(X=x_j)\quad \forall \quad j
$$
The joint probability distribution is given by: 
$$
p(x_j, y_k)=p(y_k|x_j)p(x_j)
$$
Marginal distribution of the channel output is found as: 
$$
p(y_k)=P(Y=y_k)=\sum_{j=0}^{J-1}p(y_k|x_j)p(x_j)
$$


#### Conditional Entropy

$$
H(X|Y=y_k)=\sum_{j=0}^{J-1}p(x_j|y_k)\log_2 \left[\frac{1}{p(x_j|y_k)}\right]
$$
This is a random variable that takes values on: 
$$
H(X|Y=y_0), \; H(X|Y=y_1),...,H(X|Y=y_{K-1})
$$

Where the probabilities are $p(y_0),p(y_1),...,p(y_{K-1})$. The mean entropy is given by: 
$$
H(X|Y)=\sum_{k=0}^{K-1}H(X|Y=y_k)p(y_k)=\sum_{k=0}^{K-1}\sum_{j=0}^{J-1}p(x_j|y_k)p(y_k)\log_2{\left[\frac{1}{p(x_j|y_k)}\right]}=\sum_{k=0}^{K-1}\sum_{j=0}^{J-1}p(x_j,y_k)\log_2{\left[\frac{1}{p(x_j|y_k)}\right]}
$$
This is the amount of uncertainty after observing the channel output.

#### Mutual Information

Difference $H (X) − H (X | Y )$ is the uncertainty resolved by observing channel output. Define the mutual information as: 
$$
I(X;Y ) = H (X) − H (X | Y )
$$
Which results in: 
$$
I(X;Y)=\sum_{k=0}^{K-1}\sum_{j=0}^{J-1}p(x_j,y_k)\log_2{\left[\frac{p(y_k|x_j)}{p(y_k)}\right]}
$$
Mutual information is:

-   Non-negative: 
$$
I(X;Y) \ge 0
$$


-   Symmetric: 
$$
I(X;Y)=I(Y;X)
$$


### Channel Coding Theorem

Capacity of a discrete memoryless channel is the maximum mutual information between the input and output, where the maximization is over all possible input probability distributions. 
$$
C=max_{p(x_j)}I(X;Y)
$$
If the transmission rate $R \le C$, then there exists a coding scheme such that $R$ bits per channel use can be transmitted over the channel with an arbitrarily small probability of error.

Conversely, error probability is always bounded above zero when the transmission rate is above the capacity.

#### Binary Symmetric Channel


![Binary Symmetric Channel.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/binsymchan.png)


$$
C=max_{p(x_j)}I(X;Y)
$$
Where: 
$$
I(X;Y)=H(Y)-H(Y|X)
$$

$$
H(Y|X)=p_0 H(Y|X=0)+p_1H(Y|X=1)=p_0 h(p)+p_1 h(p)=h(p)
$$
Where $h(p) = p log_2 p + (1− p)log_2 (1− p)$. Then: 
$$
I(X;Y)\le1-h(p)
$$
It is easy to see that this can be achieved by setting: 
$$
p_0=p_1=\frac{1}{2}
$$



![Binary Symmetric Channel graph.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/binsym2.png)

### Additive White Gaussian Noise (AWGN) channel

Capacity of an additive white Gaussian noise (AWGN) channel: 
$$
C=B \log_2(1+SNR)=B \log_2 \left(1+\frac{P}{N_0 B}\right)
$$
Where:

-   $B$ is the bandwidth of the channel.

-   $P$ is the average signal power at the receiver.

-   $N_0$ is the single-sided PSD of noise.

This rate can be achieved by:

-   Designing powerful error correcting codes to correct as many errors as possible.

-   Using ideal modulation schemes that do not lose information in the detection process.

### Shannon Limit

There is a trade off between power and bandwidth. To get the same target capacity $C$, one may increase power, decreasing bandwidth; or decrease power. increasing bandwidth.

The minimum power to send 1 bps (where C = 1): 
$$
\frac{P}{N_0}=B(2^{\frac{1}{B}}-1)=\frac{2^{\frac{1}{B}}-1}{\left(\frac{1}{B}\right)}\Rightarrow \lim_{B\to\infty}\frac{P}{N_0}=\lim_{B\to\infty}\frac{2^{\frac{1}{B}}\ln{2(-B^{-2})}}{-B^{-2}}=\ln{2}=0.693=-1.6dB
$$



![Shannon Limit.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/shannonlimit.png)

### Noise and Errors

Noise can corrupt the information we wish to transmit. This is a bad thing that should be avoided, if possible. Different systems will generally require different levels of protection against errors. Consequently, a number of different techniques have been developed to detect and correct different types and number of errors.

### Channel Model

The effect of noise can be measured in different ways. The most common is to specify an error probability, $p$. If the error probability is small and information is fairly fault tolerant, it is possible to use simple methods to detect errors.

-   Repetition -- Repeating each bit in the message:

    -   If two symbols in an adjacent pair are different, it is likely that an error has occurred.

    -   However, this is not very efficient (bit rate is halved).

    -   One repetition provides a means for error detection, but not for error correction. More repetitions are needed for error correction.

-   Parity bit -- Use of a 'parity bit' at the end of the message:

    -   A parity bit is a single bit that corresponds to the sum of the other message bits (modulo 2).

    -   This allows any odd number of errors to be detected, but not even numbers.

    -   A single parity bit only allows error detection, not error correction.

    -   More efficient than simple repetition.

### Block Codes

An important class of codes that can detect and correct some errors are block codes:

-   Encode a series of symbols from the source, a 'block', into a longer string: codeword or code block.

-   Error detection: if the received coded block is not a valid code word.

-   Error correction: "decode" and associate a corrupted block to a valid coded block by its proximity (as measured by the "Hamming distance").

#### Linear Block Codes

An $(n, k)$ binary linear block code takes a block of $k$ bits of source data and encodes them using $n$ bits.

-   Ratio between the number of source bits and the number of bits used in the code, $R=\frac{k}{n}$, is referred to as the code rate.

-   Linearity: the Boolean sum of any two codewords must be another codeword.

-   This means that the set of code words forms a vector space, within which mathematical operations can be defined and performed.

#### Generator Matrix

To construct a linear block code we define a matrix, the generator matrix $G$, that converts blocks of source symbols into longer blocks corresponding to code words.

$G$ is a $k\times n$ matrix ($k$ rows, $n$ columns), that takes a source block $u$ (a binary vector of length $k$), to a code word $x$ (a binary vector of length $n$): 
$$
x=u\cdot G
$$



![How the generator matrix works.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/generatormatrix.png)

#### Hamming Distance

Hamming weight of a binary vector $a$ (written as $w_H(a)$), is the number of non-zero elements it contains.

Hamming Distance between two binary vectors, $a$ and $b$, is written $d_H(a,b)$, and is equal to the Hamming weight of their (Boolean) sum.

### Error Detection and Correction

#### Error Detection

To determine the number of errors a particular code can detect and correct, the minimum Hamming distance between any two code words needs to be analysed. From linearity the zero vector must be a code word.

If the minimum distance between any two code words is defined as: 
$$
d_{min} = min \{d_H(a,b), \; a,b \in C\} = min \{ d_H (0,a+b),a,b \in C \} = min \{ w_H(c), \; c \in C, \; c \ne 0 \}
$$
Where $C$ is the set of code words.

The number of errors that can be detected is then $(d_{min}–1)$, since $d_{min}$ errors can turn an input code word into a different valid code word. Less than $d_{min}$ errors will turn an input code word into a vector that is not a valid code word.

#### Error Correction

Number t of errors that can be corrected is simply the number of errors that can be detected divided by two and rounded down to the nearest integer, since any output vector with less than this number of errors will be 'nearer' to the input code word.

(7,4) Hamming code has $d_{min} = 3$. It can detect one or two bit errors, and correct any single bit error.


![Error Correction.](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/errorcorrection.png)
