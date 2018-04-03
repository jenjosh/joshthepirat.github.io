# Power Electronics Notes

[TOC]

##Introduction to Power Electronics

### Power Transmission and Distribution

#### Voltage source system

A cable or overhead line has a series impedance and a shunt admittance. The series impedance is the resistance of the wire and the inductive reactance of the wire path. The shunt admittance is the conductivity of the insulators and the capacitive susceptance between wires.

Power losses occur in the wire resistance ($I^2 R$) and the insulator conductance ($V^2 G$). In general, insulators are closer to ideal than conductors and the power loss in the insulator is often negligible. Considering only conductor power loss, a voltage source (variable current) system has losses that decrease as the load decreases. A current source system would have constant loss for any load (including no load).

#### Impedance Matching

Amplifiers are used with a load impedance matched to the output impedance in order to maximise
power transfer. Maximum power transfer is not the same as maximum efficiency. In fact, with resistive
impedances, resistance matching gives $50\%$ efficiency. The main consideration with a power system is to maintain the consumer’s voltage within a few percent of its nominal value. For this reason the network is run with low source impedance and high load impedance.

#### Varying voltages

Power, dependent on the $IV$ product, can be transmitted with any value $V$ and a corresponding value of $I$. The loss is related to $I^2$ and so higher voltages reduce power loss and increase efficiency. At very
high voltages the $V^2 G$ losses become a significant factor. 

Voltages of between $500kV$ and $100kV$ are used for transmission. The capital cost of H.V. equipment is prohibitive sometimes so medium voltages of the between 100kV and 10kV are also used. Safety considerations require most users to be supplied at voltages of $250V$ or less.

#### Alternating Currents/Voltages

The only cost effective way of changing voltage levels in a power system is the transformer. Transformers require an AC system because voltage can only be supported by changing flux ($E=N \frac{dF}{dt}$) and AC is the only way of obtaining continuously changing flux.

There are exceptions, DC transmission is used to link AC systems of different characteristics and DC is used in some isolated distribution systems such as on large ships.

#### Sinewave Voltage

The voltages and currents of inductors and capacitors are related by differential equations. A sine wave is the only AC form that will ensure that all voltage drops and leakage currents in the system are the same form as the source waveform.

Considerable design effort is required to achieve sinewave voltages.

#### Frequency

The frequency of an AC power system is directly related to the rotational speed of the generators. When the systems were designed, $3000/3600rpm$ were reasonable choices given the materials available.

Higher frequencies would reduce transformer size but cause larger inductive voltage drops and capacitive leakage currents. Lower frequencies cause noticeable lighting flicker and require larger transformers. Higher frequencies are used where weight and size are an issue such as on ships and aircraft.

#### Three Phases

Generators are best built with a large number of coils distributed around the machine. So that a practicable number of connections can be used outside the machine, the coils are grouped into phases. The choice of three phases is a sensible compromise between number of connections and good utilisation of the machine. More than one phase is essential to facilitate smoothly rotating AC motors.

###Electric Grid Operation

A grid system is expected to provide a secure source of energy whenever a customer demands it. The grid operator must balance the demand with the supply of energy from various generators. There is a daily pattern of load variation that is reasonably predictable. It is different at weekends and different from one season to the next.

The system operator must plan for unusual demand patterns such as "television pick-up". This is the
sudden increase in load when a popular television programme begins. This can provoke a rise of $1000MW$ in demand in a matter of a few minutes. Major television events create even larger changes. The
largest events are over $2000MW$ however, from prior experiences, these changes can be predicted and changes made to the grid appropiately. When generation exceeds demand the excess energy builds up in the inertia of the generators and the frequency rises.

Faults in either generator or the transmission network itself cause system operators the greatest
problems because these are very fast events. The the UK system operators to a $1320MW$ loss-of-in-feed
standard. The large $2000MW$ coal fired plants such as Drax have four $500MW$ turbine-generators which run from two boilers with a double circuit connection to the grid. No single fault can cause all $2000MW$ to be lost in one go. The Sizewell B pressurised water reactor has two $660MW$ turbine generators but only one steam circuit so the whole lot can get shut down in one go if there is a fault in the steam circuit. Therefore National Grid carries enough reserve to deal with this loss if Sizewell B is running. 

A grid system is an efficient means of transporting energy but there are some losses. The local distribution system is less efficient because of the lower voltages used. Of the cost of the electricity to consumers, about $50\%$ is accounted for by costs of generating and the remainder by the losses and operating costs in transmission ($5\%$), losses and operating costs in distribution ($30\%$) and the metering & billing costs ($15\%$).

### AC Power Calculations

Cosine is the standard sinusoidal signal:
$$
v=\hat{V} \cos{(\omega t+\phi )}
$$

$$
e^{j\theta}=\cos{\theta}+j\sin{\theta}
$$

$$
v=Re{\left( \hat{V}e^{j(\omega t + \phi)}\right)} =Re{\left( \hat{V}e^{j\phi}e^{j\omega t}\right) }
$$

In the final representation the signal has three parts:

- $\hat{V}$ is the magnitude of the signal
- $e^{j\phi}$ represents the phase angle of the signal.
- $e^{j\omega t}$ represents the sinusoidal variation at the signal frequency.

Only the magnitude and phase angle need be retained to form the phasor:
$$
\overline{V}=\hat{V}e^{j\phi}=\frac{\hat{V}e^{j(\omega t+ \phi)}}{e^{j\omega t}}
$$
The ratio of voltage and current phasors gives impedance, $Z$, in its complex form. $Re\{Z\}$ is the resisitance and $Im\{Z\}$ is the reactance, both measured in Ohms. Reactance is a feature of energy storage components:

$$
\overline{Z}_L=jX_L=j\omega L
$$
$$
\overline{Z}_C=-jX_C=-j\frac{1}{\omega C}=\frac{1}{j\omega C}
$$

The $j$ term increases/decreases the phase by $90^{\circ}$. Since $\angle{\overline{V}}=\angle{\overline{I}}+\angle{\overline{Z}}$, the expected phase difference is:
$$
\angle{\overline{V}}=\angle{\overline{I}}+90^{\circ} \quad \text{for an inductor.}
$$
$$
\angle{\overline{V}}=\angle{\overline{I}}-90^{\circ} \quad \text{for a capacitor.}
$$

This can also be remembered with the acronym **CIVIL"** which stands for "In a **C**apacitor, current(**I**) leads **V**oltage, whilst **V**oltage leads current(**I**) in an inductor (**L**)".

####Types of Power


Power is energy flow and is measured in watts (joules per second). Intantaneous power is the product of the voltage and current at that instant.

The voltages and currents are defined using the “passive” convention. A positive value of $p$ represents energy flowing into the component and a negative value is energy flowing out.
$$
p(t)=v_{AB}(t)i_{ab}(t)
$$

Energy flow may be occuring if the device is a capacitor or inductor storing energy, or the energy through the comonent being lost as heat etc.

The instananeous power in a resitor is always positive, whilst in a capacitor or inductor, the the instantaneous power oscillates around zero with an average of zero.

![nstpowe](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/instpower.png)

The average or real power is calculated by integrating the instantaneous power over one cycle and dividing by the period.
$$
P=p_{Avg}=\frac{1}{T}\int_{0}^{T}v_{AB}(t)i_{AB}(t) \,d t
$$

Thes stored and returned power is known as reactive power and given the symbol $Q$ and has the units Volt-ampere reactive $VAr$. It isn't dissipative so it doesn't use watts. 

Most electrical equipment has a voltage and current limit. these combine to give an apparent power rating. Apparent power has the unit $VA$. It doesn't specify how much of the power is real, and how much is reactive.

####Average Power

For a resistor, using the previous equation and the knowledge that the voltage and current are cosines the average power can be calculated to be:
$$
\frac{1}{2} \hat{I}\hat{V}_R \quad \text{or} \quad \frac{1}{2}\hat{I}^2 R
$$

The average power of an inductor is zero because all the energy stored in one half of the cycle is released in the other.

The mean of the square is important but since it is inconvenient, the root mean square is used instead.
$$
I_{RMS}=\hat{I}\sqrt{\frac{1}{2\pi}\int_{-\pi}^{\pi}\cos^2{(\omega t)} \,d(\omega t)}=\frac{1}{\sqrt{2}}\hat{I}
$$

The use of RMS is widespread in power engineering so it is assumed that all magnitudes of currents and voltages are in RMS.

####General Case for calculating Power

![omppowe](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/comppower.png)

The real power of general compnents is given by the component of voltage that is in phase with the current.

The real power can be expressed as a dot product:
$$
P=\overline{I}\cdot\overline{V}=IV\cos{\phi}=IV_P
$$

$$
\text{where }\phi =\angle{\overline{V}}-\angle{\overline{I}} \text{ and } V_P=|\overline{V}|\cos{\phi}
$$

Because $V_P=IZ \cos{\phi}$, the real power can also be written as $P=I^2 Re\left( \overline{Z} \right) $.

The reactive power is defined in terms of the component of voltage that is $90^{\circ}$ out of phase with the current.
$$
Q=IV_Q=IV\sin{\phi} \quad \text{or} \quad Q=I^2 Im\left( \overline{Z} \right) 
$$

The reactive power should be minimised.

The apparent power is defined as the product of voltage and current without regard to the angle:
$$
S=IV=I\left( V_P^2+V_Q^2 \right)^{\frac{1}{2}} =\left( P^2+Q^2\right) ^{\frac{1}{2}}
$$

The ratio of real power to apparent power is defined as the Power Factor.
$$
PF=\frac{P}{S}
$$

You can find the real and reactive powers from voltages and currents in phasor form of the complex power:
$$
\overline{S}=\overline{V}\overline{I}*=P+jQ
$$

$$
P=Re\{\overline{V}\overline{I}^*\}
$$

$$
Q=Im\{\overline{V}\overline{I}^*\}
$$

####Generator sign convention

When analysing generators, it may be more useful to use a "generator" sign convention instead of "passive" convention. This is where positive current flows out of a component and positive power is associated with power generation.

####Law of Conservation of Energy

In a closed system energy is conserved and the net power consumption is zero. If all the power from the generators were summend up and all the power from the loads were subtracted and the result should be zero (assuming the impedances of the lines and other imperfections amongst the loads are included).
$$
\sum_{N_G}P_G-\sum_{N_L}P_L=0
$$

There are some devices, such as
energy storage systems or motors, which might just generator or consume. For these a convention arbitrarily and the power will be indicated as positive or negative as appropriate. It might be easier to use only one convention and treat everything as a load and simply note that if any of the devices is a source not a load then its power will be negative. Then it is expected that the sum of all powers to be zero.
$$
\sum_{N}P=0
$$

Because the summation of power to instantaneous power can be applied also, the reactive power in a system should also sum to zero.
$$
\sum_{N}Q=0
$$



##Switch Mode Power Supplies

### Introduction

There are several reasons why electrical power needs to be converted from one voltage to another:

- Various voltages are used in transmission and distribution to optimise costs etc.
- For most loads, the distribution voltage is different to the needs of the the consumer.
- The load may require a variable voltage in order to control it operation.

This cahange in voltage may involve:

- A change of voltage magnitude.
- A change of frequency.
- A change of phase.
- A change between AC and DC.

### Linear vs Switch Mode Conversion

The switch pass linear regulator is a potential divider with a transitor acting as one variable element and the load as the other. The voltage across the load is set by controlling the base voltage.

![inea](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/linear.png)

The load at the base of the transitor is held using a Zener Diode.
If a transistor wasn't used, the non load resistor would have to be chosen is such a way that is extremely difficult and non viable.

The transistor is held in the linear region which results in low efficiency:
$$
P_o=I_o \times V_o =10W
$$

$$
P_i=I_i \times V_i \approx I_o \times V_i =30W
$$

$$
\eta = \frac{P_o}{P_i}=33\%
$$

$$
P_{loss}=20W
$$

The drawback of this curcuit is that the transistor has a controller emitter voltage drop whilst the collector current flows and is thus dissipating energy. This unacceptable where the supply energy is limited or where heat generation must be limited. A further limitation of the circuit is that it can only convert the input voltage to lower voltages.

Instead some circuits such as heaters, incandescent lights and some motors can be controlled by varying the applied voltage. In these particular applications, the form of voltage waveform is not critical so long as the average voltage is correct. 

![puls](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/vpulse.png)

The transistor in the circuit is operated as a switch.

When the transistor is on:

- Transistor is saturated.
- The power loss is small because of the small saturation voltage drop.
- $P_{loss}=I_C \times V_{CE}= \text{small}$.

When the transistor is off:

- The output will fall to zero.
- The transitor will leak a very very small current.
- The power loss is negligible.

Chopping between the states at a high frequency gives an average voltage dependent on the ratio of the on-time to the period. This ratio is known as the duty-cycle of the switch.

Because the power loss is small in both the transistor states, the efficiency is very good ($\approx 100\%$).

### Buck Switch Mode Power Supply

Most electronic equipment needs a ripple-free voltage supply. The addition of an LC filter can produce a good quality supply voltage. The cutoff of the LC filter is chosen to block the switching frequency components of the pulse waveform and only let the DC (or average) component to the output.

![uckswitchmod](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/buckswitchmode.png)

When the transistor is on:

- Input voltage minus output voltage is applied across the inductor.
-  The inductor current rises linearly $\frac{\,d i}{\, d t}=\frac{(V_i-V_o)}{L}$
-  Energy is stored in the inductor $E= \frac{1}{2} Li^2$
-  Capacitor current in the difference between inductorcurrent and load current.

![uckswitchmodeo](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/buckswitchmodeon.png)

When the transistor is off:

- Diode junction capcitance is discharge; voltage at diode cathode drops below anode voltage and diode conducts.
- The minus of the output voltage is applied across the inductor.
- The inductor current falls linearly $\frac{\,d i}{\,d t}=\frac{-V_o}{L}$
- Energy is released from the inductor $E=\frac{1}{2}Li^2$
- The capacitor current is the difference between the inductor current and load current.

![uckswitchmodeof](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/buckswitchmodeoff.png)

The current cannot change quickly because the the energy stored cannot change quickly.

When the transistor is off, the only viable path for the current to flow is through the diode. When the transistor is on the diode is "off" and acts like a capacitor.

There are two operating modes for this circuit. If the average current through the inductor is
large (compared with the ripple caused by the switching) then the inductor current does not reduce to zero during the off time. This is known as continuous conduction. 

If the average current is small then during the off time the current will reduce to zero, the diode will stop conducting and the inductor current will stay at zero until the transistor next turns on. This is known as discontinuous conduction. The boundary condition between these two modes is known as the critical conduction condition.

![omppowe](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/contcond.png)

#### Continuous Conduction Mode

In steady state, any increase in inductor current during thr time that the transistor is on must be balanced by a decrease during the time that the diode conducts.
$$
\Delta I_{on}+ \Delta I_{diode}=0
$$

$$
\Delta I_{on}=t_{on} \times \left. \frac{\, d i}{\,d t} \right|_{on} =t_{on}\frac{V_I-V_{DS}-V_{o}}{L}\approx t_{on} \frac{V_I-V_o}{L}
$$

$$
\Delta I_{diode}=t_{diode} \times \left. \frac{\, d i}{\,d t} \right|_{diode} =t_{diode}\frac{-V_{AK}-V_{o}}{L}\approx t_{diode} \frac{-V_o}{L}
$$

Assumptions about voltages being small and ignorable are not appropiate if the circuit is operated at low input or output voltages. Equating the two temrs for changes in the current in the previous equations reuslts in:
$$
\frac{V_o}{V_i}=\frac{t_{on}}{t_{on}+t_{diode}}
$$

![uckswitchgraph](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/buckswitchgraphs.png)

The average current though L is large and doesn't go to zero whilst the transistor is off.

If the inductor is current is continuous then the diode coducts for all of the time that the transitor is off.
$$
T=t_{on}+t_{diode}
$$

$$
\frac{V_{o}}{V_i}=\frac{t_{on}}{T}=\delta \qquad \qquad \text{where }\delta\text{ is the duty cycle of the switch}
$$

This relationship is very helpful: output voltage is a simple linear function of duty-cycle and duty-cycle is something that can easily be manipulated in a control circuit. 
The assumption that in steady-state the inductor current has no net change over a cycle can be extended to say that the capacitor voltage has no net change over a cycle (the currents into and out of the capacitor integrate to zero).

It can also be assumed that the capacitor value is large and the changes in its voltage are small compared to the DC.

A simple load would draw a constant current since the output voltage is assumed constant.

#### Discontinuous Conduction Mode

![uckswitchgraphs](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/buckswitchgraphs2.png)

The equation relating output voltage to the transistor and diode conduction times still holds but, unlike in continuous mode, the diode conduction time is not equal to (is less than) the off-time of the transistor. In discontinuous mode, there is a period for which neither the transistor nor the diode conducts and the rate of change of inductor current is zero.

The output current and the average inductor current must be equal so $t_{on} + t_{diode}$ can be related to the period. Noting that the inductor current is a triangle wave of amplitude $\Delta I_{on}$:

![riangleio](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/triangleion.png)

$$
I_o=I_L^{AVG}=\frac{1}{2}\Delta I_{on} \frac{t_{on}+t_{diode}}{T}
$$

This yields a relationship between output voltage and input voltage, duty-cycle, and output current:
$$
\frac{V_o}{V_i}=\frac{t_{on}}{t_{on}+t_{diode}}=\frac{t_{on}\Delta I_{on}}{2I_o T}=\frac{\delta \Delta I_{on}}{2I_o}=\frac{(V_i-v_o)\delta^2}{2fLI_o}
$$
$$
=\frac{1}{1+\frac{2fLI_o}{V_i \delta^2}}
$$

The points to note about this equation are that the output voltage is now a non-linear function of duty-cycle (which makes design of a closed loop control system difficult), that the relationship depends on circuit parameters (inductance) and that the relationship is operating point (output current and input voltage) dependent.

Another complication is that the circuit can change between continuous and discontonuous as conditions change.

#### Continuous-Discontinuous Boundary

The boundary between the two modes occurs when the decreasing current during the off-time just reaches zero at the end of the off-time.

The critical value of output current, below which discontinuous conduction occurs can be identified:
$$
I_o^{critical}=I_{L_{avg}}=\frac{1}{T}\int^T  i_L \,d t=\frac{\frac{1}{2}T\Delta I_{on}}{T}=\frac{1}{2}\Delta I_{on}
$$

### Output Voltage Ripple

The capacitor at the output-side of the SMPS is to hold the output voltage as close to constant as possible in the face of a current flow through the inductor that has a ripple component. The capacitor is a good path for high frequency current and the ripple current preferentially takes this path leaving only the average (DC) component of inductor current to flow in the load. Thus, the current flowing through the capacitor in a buck SMPS is the difference between the inductor current and the constant output current. This capacitor causes ripple voltages to appear.

A triangular current can be driven through the capacitor. The positive current cause the output voltage to rise and the negative part causes the voltage to fall. Over a cycle (in steady-state), the two changes sum to zero. The change of voltage within a cycle (the ripple voltage) can be found from charge delivered by the positive portion of capacitor current:
$$
\Delta v_C=\frac{Q^+}{C}=\frac{1}{C}\int^{\frac{1}{2}T}i_C(t)\,d t=\frac{1}{C}\times\frac{1}{2}\times (\frac{1}{2}t_{on}+\frac{1}{2}t_{off})\times \frac{1}{2}\Delta i_C=\frac{\Delta i_C T}{8C}
$$

$$
=\frac{\Delta I_{on}}{8fC}
$$
In a well-designed SMPS, this ripple voltage is very small, helped by the frequency being a denominator term. 

As a worse case, one can calculate the magnitudes of the ripple voltage across C, ESR, and ESL and add them for the total ripple voltage.

### Power Loss in Semiconductors

As for any component, net power dissipated in a semiconductor is found by integrating the voltage current product.
$$
p(t)=v(t)i(t) \qquad E=\int_{0}^{T}p(t)\,d t \qquad P_{avg}=\frac{1}{T}\int_{0}^{T}p(t)\,d t
$$

#### Example of a MOSFET in a buck converter

The action of the diode is crucial: if the diode is conducting it must have a forward voltage of $\approx 0.7V$ and the MOSFET voltage $V_{DS}$ must be almost equal to the input voltage $V_i$ ($V_{DS} = V_i +V_D$).

The diode is known to conduct when the MOSFET is off but the MOSFET takes a finite time to turn on and off so it needs to be established what happens during the turn-on and turn-off processes.

![osonof](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/mosonoff.png)

![owermosexmpl](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/powermosexmple.png)

- **Period 1 Off-state:**
  - Mosfet is off; diode is in conduction.
- **Period 2 Turn-on:**
  - Mosfet begins to turn on and drain current rises; diode must be in conduction to carry whatever inductor current is not carried by the Mosfet.
  - The diode current falls as the drain current rises.
  - The diode must stay in conduction (vD ≈ 0.7) until iDS has risen to equal IL. At this point the diode enters reverse bias and the voltage across the Mosfet can fall.
- **Period 3 On-state:**
  - The Mosfet is on and carries the inductor current with a small drain-source voltage drop.
- **Period 4 Turn-off:**
  - Mosfet begins to turn off.
  - Before the drain current can start to fall, drain-source voltage must rise until the diode is forward biased $(V_i−v_{DS} = −v_{D} \approx −0.7)$. Only as the diode current increases can the drain current fall.

The waveforms can be multiplied to get instantaneous power and integrate to get the cumulative energy and average power:
$$
E_{cond}=V_{DS}I_Lt_{on}=I_{DS}^2R_{DS_{on}}t_{on}
$$

$$
R_{SwOn}=\frac{1}{2}V_iI_L(t_{ri}+t_{fv})
$$

$$
E_{SwOff}=\frac{1}{2}V_iI_L(t_{rv}+t_{fi})
$$

$$
P_{avg}=\frac{1}{T}(E_{cond}+E_{SwOn}+E_{SwOff})=I_{DS}^2 R_{DS_{on}}\delta+(E_{SwOn}+E_{SwOff})f
$$

### Design of an SMPS

The normal chain of decisions when designing a power supply are:
- Choose a transistor able to carry the required current and hold off the applied voltage.
- Choose a switching frequency based on the transistor choice.
- Choose components for the LC filter so that it blocks the switching frequency and passes only the DC (average) term.

There are four principal constraints on the design:
- High current and high voltage transistors cost more than low rated versions so we do not want to over specify.
- It is essential that the transistor’s temperature is kept below its maximum. Although the transistor is operated efficiently, it still has some power loss that is dissipated as heat and raises the transistor’s temperature.
- Large valued L and C components cost more and take up more space; there is pressure to keep them small.
- The filter will not completely stop high frequency voltage appearing at the output but it is necessary to keep this ripple small for quality reasons.

#### Power Transistors

The standard bipolar junction transistors and field effect transistors have structures that are optimised to give high gain and high bandwidth or some other similar criteria that are important in the processing of signals. Power transistors are optimised to give:
- High breakdown voltages: this requires a weakly doped region one side of the diode to keep the field strength below the breakdown level and a deep piece of silicon to allow the depletion region to grow.
- High maximum current: for good thermal design a large cross-sectional area is used to keep the current density.

Power MOSFETS are able to switch more quickly and have lower switching power loss than IGBTS or Thyristors. 

#### Thermal Design

The energy dissipated as heat must be removed to avoid excessive temperature rise. The max temperature of a silicon junction is in the range $125^{\circ}-150^{\circ}C$.

The more power that needs to flow away from the silicon, the higher its temperature will have to rise to force this heat flow:
$$
\frac{\,d E_{Th}}{\,d t}=P_{Th}=\frac{T_1-T_2}{R_{Th}} \qquad \text{where } R_{Th} \text{ is the thermal resistance}
$$

The flow of heat energy due to a temperature difference is analogous to the flow of current due to a potential difference. Therefore an equivalent circuit for heat flow can be created and heat flow and temperature difference calculations can be formed.

#### Passive Design Choices

The cut-off of the filter, $f_C$, needs to be below the switching frequency, $f_{SW}$:
$$
f_C=\frac{1}{2\pi \sqrt{LC}} \qquad f_c << f_{Sw}
$$

The relationship between the component choices and the voltage and current ripple:
$$
\Delta I=\frac{V_i-V_o}{L}\delta T=\frac{V_i-V_o}{fL}\frac{V_o}{V_i}
$$

If there is nothing else to guide the design then L will be chosen to give a reasonable current ripple of about 10% of the max output current. 

### Boost Switch Mode Power Supply

The re-arrangement of components in the Buck SMPS gives the Boost SMPS which has a step-up characteristic:

![oostswitchmod](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/boostswitchmode.png)

If the transistor were left off permanently then a current would flow through the diode to charge the output capacitor to almost the input voltage.

When the transistor is switched on:

- The inductor is connected across the input voltage.
- The inductor current rises and energy is stored in the inductor's magnetic field.
- The load current is served from the output capacitor.

![oostqo](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/boostqon.png)

When the transistor is switched off:

- The diode is brought into conduction.
- The inductor current flows to the output-side capacitor which is at a higher voltage than the input. 
- A negative voltage is imposed across the inductor and the current reduces.
- Energy is released from the inductor to the capacitor.

![oostqof](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/boostqoff.png)

The result of each on and off cycle is that a quantity of charge is delivered to the output capacitor above what would happen without switching and therefore the capacitor voltage is charged above the input voltage. The longer the transistor is held on the more energy is stored in the inductor and the greater the charge delivered to the output capacitor and the higher the voltage rises.

Any increase in inductor current during the time that the transistor is on must be balanced by a decrease during the time that the diode conducts:
$$
\Delta I_{on}+\Delta I_{diode}=0
$$

$$
\Delta I_{on}=\frac{V_I-V_{DS_{on}}}{L}t_{on}\approx\frac{V_I}{L}t_{on}
$$

$$
\Delta I_{diode}=\frac{V_I-V_{diode_{on}}}{L}t_{diode}\approx\frac{V_I-V_O}{L}t_{diode}
$$

$$
\frac{V_o}{V_i}=\frac{t_{on}+t_{diode}}{t_{diode}}
$$

For the continuous inductor current case:
$$
\frac{V_o}{v_i}=\frac{t_{on}+t_{diode}}{t_{diode}}=\frac{T}{t_{diode}}=\frac{1}{1-\delta}
$$

For the discontinuous inductor current case:
$$
I_I=I_{L}^{Avg}=\frac{1}{2}\Delta I_{on}\frac{t_{on}+t_{diode}}{T}
$$

This yields a relationship between output voltage and input voltage, duty cycle & input current:
$$
\frac{V_o}{V_i}=\frac{1}{1-\frac{V_i \delta^2}{2fLI_i}}
$$
In the derivation of the input/output voltage (for both Buck and Boost cases) some assumptions were made that should be stated explicitly:

- The output-side capacitor is considered to be very large such that the voltage across it does not vary significantly during one cycle of transistor switching.
- The voltage drops across the semiconductors are negligible.
- The resistance of the inductor is negligible.

![oostgraph](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/boostgraphs.png)

#### Comparison of Buck and Boost SMPS

|                            |                Buck SMPS                 |                          Boost SMPS                          |
| :------------------------: | :--------------------------------------: | :----------------------------------------------------------: |
|    Output Voltage Range    | $V_O=\delta V_I \quad 0 \le V_O \le V_I$ |        $V_O=\frac{1}{1-\delta}V_I \quad V_I \le V_O$         |
|       Input Current        |                 Chopped                  |                          Continuous                          |
| Capacitor Charging Current |                Continuous                |                           Chopped                            |
|   Output Voltage Ripple    | Small $\Delta V_{ESR}=R_{ESR}\Delta i_L$ | Large $\Delta V_{ESR}=R_{ESR}(I_{L}^{Avg}+\frac{1}{2}\Delta i_L)$ |
| Maximum Transistor Voltage |                  $V_I$                   |                            $V_O$                             |
|   Maximum Diode Voltage    |                  $V_I$                   |                            $V_O$                             |
| Maximum Transistor Current |       $I_O+\frac{1}{2}\Delta i_L$        |                 $I_I+\frac{1}{2}\Delta i_L$                  |
|   Maximum Diode Current    |       $I_O+\frac{1}{2}\Delta i_L$        |                 $I_I+\frac{1}{2}\Delta i_L$                  |

#### Control of Output Voltage
It is almost always necessary to close a feedback loop around the SMPS to regulate the output voltage. 

![sufeedbac](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/psufeedback.png)

Voltage error, via some control law $C(s)$ sets the required $d$.

A pulse-width modulator (PWM) converts the voltage signal representing $d$ into pulses of the correct duration. Normally, the output current is monitored to provide current limiting though disabling the switching. 

The gate-driver translates logic levels to, say $–5V/+15V$ to switch the MOSFET off and on.

### Efficiency of a Switch Mode Power Supply

How close to 100\% the efficiency can reach depends on the quality and size of components. Winding the inductor with thicker wire reduces its resistance and power loss. Similarly, using a large cross-sectional area of silicon will reduce the $R_{DS_{on}}$ value of the MOSFET but it tends to also slow the switching (because of greater capacitance) and therefore increase the switching power loss. 

Increasing the area of the diode does not help much (since it is principally a junction voltage drop not a resistance) but sometimes a second MOSFET is used in place of the diode to reduce its power loss).

It is important to note that efficiency is normally quoted assuming operation at the rated (full) power but efficiency is not a constant. In the transistor, conduction loss proportional to $I^2$ and switching loss propositional to $I$. For the diode, loss is proportional to $I$; for the inductor loss is proportional to $I^2$.

A control circuit which consumes a fixed power regardless of the current in the SMPS. Therefore, the losses are of the form $P_{Loss}=a+bI+cI^2$ where $a$ is the fixed loss of the controller, $b$ determines the linear term of the diode and switching loss and $c$ determines the quadratic term of the resistive losses) and the power output is $P_O=VI$. The efficiency is therefore:
$$
\eta = \frac{VI}{VI+a+bI+cI^2}
$$

![suefficienc](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/psuefficiency.png)

There are two key features. The fixed loss (of the control electronics) means that at low power output the SMPS has a very low efficiency. The quadratic term loss (the resistive loss) increases rapidly at high output power and reduces the efficiency. Somewhere between these two regions the efficiency reaches its maximum value. 

## DC/AC Conversion

Rectification is conversion of AC to DC whilst the opposite is inversion.

### Single Phase Inverter

A basic alternating voltage can be created by using two switches and a split supply.

Anti parallel diodes are required because with an inductive load the current will not reverse polarity until after the voltage and we need a path for the inductor current when the switch is not able to provide one. This is known as a half bridge.

![alfbridg](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/halfbridge.png)

$S_A^T$, connects the output to the positive supply; switching on $S_A^T$, connects the output to the negative supply. The voltage VA is known as a 2 level waveform because it switches between only $V^-_{DC}$ and $V^+_{DC}$.

The circuit can be operated to provide simple square-wave AC but this provides no control over the amplitude and is rich in low-order harmonics which are bad.

The MOSFETs are switched at a high frequency but the duty cycle is modulated so that the average value of the output voltage is a sinusoid. The output voltage contains a low frequency sinewave (which is wanted) and a high frequency carrier (which is ignored or filtered out).

![alfbridgeandmodulato](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/halfbridgeandmodulator.png)

![inusoidmo](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/sinusoidmod.PNG)

These images shows a modulator driving the inverter switch pair. The pulse-width modulator uses a triangular carrier signal $c(t)$ which is much higher in frequency than, $m(t)$. $c(t)$ lies in the range $-1 \le c(t) \le 1$ and $m(t)$ should also stay within this range.

The following images shows, when the modulating signal $m(t)$ exceeds the carrier $c(t)$, the top switch is on, otherwise it is off.  The switching signal follows the shape of modulating signal such that the duty-cycle gradually increases positively then decreases and turns negative.

The relationship between the duty-cycle of the switching signal and the modulating signal is given by:
$$
\delta(t)=\frac{1}{2}(1+m(t))-1 \le m(t)\le 1 \qquad 0 \le \delta(t) \le 1
$$

The cycle-by-cycle average voltage of the PWM signal:
$$
\overline{\overline{v}}_A(t)=\delta(t)V_{DC}-(1-\delta(t))V_{DC}=m(t)V_{DC}
$$
For sine-wave synthesis, the modulating signal is defined as a sinusoid with a frequency and relative amplitude $M$:
$$
m(t)=M\sin{(\omega_M t)} \qquad \text{where }0\le M \le 1
$$
$$
\overline{\overline{v}}_A(t)=MV_{DC}\sin{(\omega_M t)}
$$

The diodes shown are needed since the load is normally an inductive-resistive impedance with a current that follows an approximate sinewave at some phase delay from the modulated voltage.

When the current is in its positive half-cycle and the top switch is on, the current will flow through the MOSFET. When the PWM switches on the bottom switch, the positive load current needs to flow in the reverse direction through that switch therefore the reverse connected diode conducts. Similarly, the top diode conducts if the top switch is turn-on but the load current is in its negative half-cycle. 

Because semiconductor switches take time to turn-on and turn-off, both switches may be conducting at the same time. To avoid this, a dead-time or under-lap (dependent on how fast the semiconductors can switch) time is provided to ensure both switches are off together for a brief period.

![osloadcurrent](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/mosloadcurrents.png)

![odeadtim](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/nodeadtime.png)

The frequency spectrum of the PWM signal $v_A(t)$ can be found using Fourier analysis and this reveals that the voltage contains a low frequency sinusoidal term (the cycle-by-cycle average from $m(t)$) plus some higher frequency terms associated with the switching frequency. The switching frequency is also known as the carrier frequency.
$$
v_{A}=MV_{DC}\sin{(\omega_M t)}+\text{Sidebands at }\omega_c + \text{Sidebands at }2\omega_c+...
$$

It is common for an inverter to be controlled with a microcontroller or digital signal processor. The transistors are switched using the timer channels of the
processor. The sinewave modulation is achieved by regularly updating the timer values with times calculated using a look-up table of sinewave samples. Scaling the sinewave data controls the magnitude of the output voltage. The frequency of the output voltage is set by how rapidly a pointer is advanced through the look-up table. 

### Full Bridge Inverter

The circuit provides a switched waveform at each end of the load and uses four switches in total. The circuit only requires a single supply voltage. The four switches are rated for this supply voltage and this is also the maximum amplitude of the AC waveform that can be synthesised. The half-bridge requires only two switches but these must be rated for the peak-to-peak amplitude of the largest waveform to be synthesised.

![ullbridg](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/fullbridge.png)

The two sides of the bridge are supplied with switching signals from their own pulse-width modulators. The two modulators use the same carrier but apply the modulating signal in the opposite polarity.

In obtaining the cycle-by-cycle average voltage at each side it is important to note that the waveform switches between $0$ and $V_{DC}$ and not $\pm V_{DC}$:
$$
\delta_A(t)=\frac{1}{2}(1+m(t)) \qquad -1 \le m(t) \le 1 \qquad 0 \le \delta_A(t) \le 1
$$

$$
\overline{\overline{v}}_A(t)=\delta_A(t)V_{DC}=\frac{1}{2}V_{DC}+\frac{1}{2}m(t)V_{DC}
$$

$$
\delta_B(t)=\frac{1}{2}(1+m(t)) \qquad -1 \le m(t) \le 1 \qquad 0 \le \delta_B(t) \le 1
$$

$$
\overline{\overline{v}}_B(t)=\delta_B(t)V_{DC}=\frac{1}{2}V_{DC}+\frac{1}{2}m(t)V_{DC}
$$

The output voltage of the bridge, $v_{AB}(t)$ is the difference in voltage between the terminals on the twosides and the DC offset term present in the terminal voltages is absent from the difference because it is a common-mode term.
$$
\overline{\overline{v}}_{AB}(t)=\overline{\overline{v}}_{A}(t)-\overline{\overline{v}}_{B}(t)=m(t)V_{DC}
$$

The voltages $v_A$ and $v_B$ are 2-level switched waveforms but the difference between them, $v_{AB}$ is a 3-level waveform with possible values of $V_{DC}$, $0$, and $-V_{DC}$. The possible combinations of switches are:

- $S_A^T$ and $S_B^B$ are switched on: $V_{AB} = V_{DC}$ (known as a positive voltage loop)
- $S_A^B$ and $S_B^T$ are switched on: $V_{AB} = -V_{DC}$ (known as a negative voltage loop)
- $S_A^T$ and $S_B^T$ are switched on: $V_{AB} = 0$ (known as a zero voltage loop)
- $S_A^B$ and $S_B^B$ are switched on: $V_{AB} = V_{DC}$ (also known as a zero voltage loop)

The full bridge waveforms are shown below:

![ullbridgesignal](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/fullbridgesignals.png)

![oltagewave](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/voltagewaves.png)

This image shows in detail the switching waveforms over one cycle at $m=\frac{1}{2}$ and one cycle at $m=-\frac{1}{2}$. 

In each case the cycle begins with $v_A= V_{DC}$, $v_B= V_{DC}$ and $v_{AB}=0$. In the middle of the cycle $v_A=0$, $v_B=0$ and $v_{AB}=0$. In between the two sides of the bridge switch. 

- For positive m the right side switches first and $v_A=V_{DC}$, $v_B=0$ and $v_{AB}= V_{DC}$. 
- For negative $m$, the left side switched first and $v_A=0$, $v_B= V_{DC}$ and $v_{AB}= -V_{DC}$. 
- The reverse happens in the second half of the switching period. 

Two points arise:although each side of the bridge produces pulses at the rate of the carrier frequency, $f_C$,the output waveform has twice the pulse rate; for positive $m$, the output only switches between $0$ and $V_{DC}$ and for negative $m$, the output only switches between $0$ and -$V_{DC}$.

Because the carrier and sideband terms at $\omega_C$ arise from the same carrier they are also common-mode and are absent from $v_{AB}$. All odd multiples of $\omega_C$ are common-mode and absent from $v_{AB}$ but odd multiples of $\omega_C$ are in phase opposition and so they do appear in the difference term $v_{AB}$.
$$
v_{A0}=\frac{1}{2}V_{DC}+\frac{1}{2}V_{DC}M\sin{(\omega_M t)}+\text{Sidebands at }\omega_c + \text{Sidebands at }2\omega_c+...
$$

$$
v_{B0}=\frac{1}{2}V_{DC}-\frac{1}{2}V_{DC}M\sin{(\omega_M t)}+\text{Sidebands at }\omega_c + \text{Sidebands at }2\omega_c+...
$$

$$
V_{AB}=V_{A0}-V_{B0}=V_{DC}M\sin{(\omega_M t)}+\text{Sidebands at }2\omega_C+...
$$

The remaining sidebands can be removed by a simple passive filter if a sensitive load is being supplied or power quality standards are applied as with grid connected inverters. For the case of supplying inductive loads, such as motors, where it is the quality of the current that counts, the load itself is sufficient filter.

### Three-Phase Inverter

For most three-phase applications, the requirement is to produce a balanced set of voltages for a three-wire system with no neutral connection. This means that the phase voltages produced by the inverter are not directly of concern. What does matter are the line voltages measured between two phases. Three pairs of transistors are used, one for each phase.

![hreephas](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/threephase.png)

Each phase has its own modulator. A common carrier signal is used but the three modulating signals are normally a balanced three-phase set.
$$
m_A(t)=M\sin{(\omega_M t)} \qquad \text{where }0 \le M \le 1
$$

$$
m_A(t)=M\sin{(\omega_M t-\frac{2}{3}\pi)}
$$

$$
m_A(t)=M\sin{(\omega_M t+\frac{2}{3}\pi)}
$$

The cycle-by-cycle average voltages that result are:
$$
\overline{\overline{v}}_{AB}(t)=\overline{\overline{v}}_A(t)-\overline{\overline{v}}_B(t)=\frac{\sqrt{3}}{2}MV_{DC}\sin{(\omega_M t+\frac{1}{6}\pi)}
$$

$$
\overline{\overline{v}}_{BC}(t)=\frac{\sqrt{3}}{2}MV_{DC}\sin{(\omega_M t+\frac{1}{2}\pi)}
$$

$$
\overline{\overline{v}}_{CA}(t)=\frac{\sqrt{3}}{2}MV_{DC}\sin{(\omega_M t+\frac{5}{6}\pi)}
$$

The expressions for voltages including the switching frequency terms are:
$$
v_A=\frac{1}{2}V_{DC}+\frac{1}{2}V_{DC}M\sin{(\omega t)}+\text{carrier and sideband terms}
$$

$$
v_B=\frac{1}{2}V_{DC}+\frac{1}{2}V_{DC}M\sin{(\omega t-\frac{2\pi}{3})}+\text{carrier and sideband terms}
$$

$$
v_C=\frac{1}{2}V_{DC}+\frac{1}{2}V_{DC}M\sin{(\omega t+\frac{2\pi}{3})}+\text{carrier and sideband terms}
$$

$$
v_AB=\frac{\sqrt{3}}{2}V_{DC}M\sin{(\omega t+\frac{\pi}{6})}+\text{some carrier and sideband terms}
$$

$$
v_BC=\frac{\sqrt{3}}{2}V_{DC}M\sin{(\omega t-\frac{\pi}{2})}+\text{some carrier and sideband terms}
$$

$$
v_CA=\frac{\sqrt{3}}{2}V_{DC}M\sin{(\omega t+\frac{5\pi}{6})}+\text{some carrier and sideband terms}
$$

The carrier component in the three output waveforms do not cancel in the same why as they did for the H-bridge and there is no effective frequency doubling. The first carrier term itself is common mode and is not present in the line voltage but the sidebands result from different modulating phase signals and do not cancel.



## Three-Phase Power Systems

A magnetic field of one north-pole and one south-pole rotating at $n\; revs/min$ will induced EMF at a frequency of $\omega = 2\pi \frac{n}{60}$. This forms an elementary generator.

Real generators differ from the elementary generator in a number of ways:

- Both the stator and rotor of the machine are	built from steel to give a good magnetic path.
- Only a very short “air gap” is provided between stator and rotor.
- The magnet on the rotor is often an electromagnet.
- The steel structure is laminated to reduce eddy currents.
- A large number of coils are distributed around the inside surface of the stator (instead of one “concentrated” winding).

![ealgenerato](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/realgenerator.png)

The flux crossing the air-gap between the iron carrying the magnet and the iron carrying the coils does so by the shortest route. The flux lines are radii of a circle. As the magnetic field cuts the coils, it does so at constant rate thereby inducing a quasi-square wave EMF rather than a sine-wave.

When several coils with slight phase displacements are connected in series the result is a staircase waveform which is a good approximation to a sinewave.

Series connecting phase-displaced coils gives a voltage that is the vector sum of the individual voltages. In terms of the magnitude, the sum is less than the sum of the individual magnitudes.

The greater the phase displacement, the greater the cancellation. A series connection of all the coils means that some coils close to $180^{\circ}$ out of phase are series connected, which is wasteful.

A comparison of different number of coils can be seen below:

![oils](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/coils1.png)

![oils](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/coils2.png)

![eriesconnectioncoil](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/seriesconnectioncoils.png)

### A Three-Phase Machine

Connection into three groups or phases is a compromise between avoiding voltage cancellation and keeping the number of external connections low.

![hreephasemachin](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/threephasemachine.png)

![hreephasemachin](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/threephasediagram.png)

A diagram of the generator and it's phase voltages.

The three phase voltages are balanced; they are equal magnitude and are at evenly spaced phase angles of $\frac{2\pi}{3}$. The vector sum of the phase voltages is zero.

$V_A$, $V_B$, $V_C$ are described as a positive phase sequence set. The peaks of the voltage waveforms come in the sequence $A$, $B$, $C$. If the magnet of the generator had been rotating in the opposite direction the sequence would have been $A$, $C$, $B$ and $V_A$, $V_B$, $V_C$ would be known as a negative phase sequence set.

Separate connection of generator phases to loads requires 6 conductors and is unnecessary. A shared return conductor is possible.

![haredconducto](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/sharedconductor.png)

The current in the return conductor is the vector sum of IA, IB and IC. If the load impedances are equal in magnitude and phase (i.e., they are balanced) then they will draw a balanced set of currents from a balance set of voltages.

With balanced phase currents the return, or neutral, conductor carries no current can be dispensed with. Three-phase supplies are described as 3-wire (three "live" phases) or 4-wire (three phases plus neutral).

### Choice of Number of Phases

| Phases | Voltage after Cancellation (% of N $\times$ V) | Conductors Needed to connect Load | Power Transfer |
| :----: | :--------------------------------------------: | :-------------------------------: | :------------: |
|   1    |                     63.66%                     |                 2                 |   Pulsating    |
|   2    |                     90.03%                     |                 3                 |     Smooth     |
|   3    |                     95.49%                     |              3 or 4               |     Smooth     |
|   4    |                     97.44%                     |              4 or 5               |     Smooth     |

An alternating voltage driving and alternating current through a resistor creates an instantaneous power that oscillates at twice the line frequency. Poly-phase systems have an oscillating power in each of their phases. A symmetrically configured poly-phase system has the feature that these oscillating powers are interleaved and sum to a constant value. This is good for motors and rectifiers.

Amongst the poly-phase options, 3-phases strikes such a good compromise between generator utilisation and number of conductors.

### Star Connection

Star connection involves a common point for all three phases and may or may not involve a neutral conductor connected to this point.

![tarconnection](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/starconnection1.png)

The voltage across one winding of the generator is known as the phase voltage: 
$$
V_P=|V_A|=|V_B|=|V_C|
$$

The voltage between a pair of live lines is known as the line-to-line voltage or, more often, the line voltage: 
$$
V_L=|V_{AB}|=|V_{BC}|=|V_{CA}|
$$

The relationship between line and phase voltages for a star system is:
$$
V_L=\sqrt{3}V_P
$$

The current flowing in a live line and the current flowing in the phase of the generator are the same.

A star connected load, whether balanced or unbalanced, with a neutral wire has phase and line voltages defined by the generator / supply system. The neutral current will be zero if the load is balanced. If the load is balanced and the neutral conductor removed the voltages and currents remain unchanged. The neutral is not normally removed if imbalance is expected.

![tarconnection](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/starconnection2.png)

Star connection voltages.

### Phase Connection

The phase components of the load (or generator) are placed between the lines and there is no common point for the phases. There is no role for a neutral conductor. There is no loop current around the delta because the phase voltages sum to zero.

The line voltage is equivalent to the phase voltage for a delta system.

![tarconnection](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/deltaconnection1.png)

![tarconnection](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/deltaconnection2.png)

### Power Calculation

The power consumed by any configuration of load can be found by summing the $V_P I_P \cos(\phi)$ of each phase of the load. Under balanced conditions the expressions simplify.

For an unbalanced star connection:
$$
P_{3\phi}=V_AI_A\cos{\phi_A}+V_BI_B\cos{\phi_B}+V_CI_C\cos{\phi_C}
$$

For an unbalanced star connection:
$$
P_{3\phi}=3V_PI_P\cos{\phi}=\sqrt{3}V_LI_L\cos{\phi}
$$

For an unbalanced delta connection:
$$
P_{3\phi}=V_{AB}I_{AB}\cos{\phi_{AB}}+V_{BC}I_{BC}\cos{\phi_{BC}}+V_{CA}I_{CA}\cos{\phi_{CA}}
$$

For an balanced delta connection:
$$
P_{3\phi}=3V_PI_P\cos{\phi}=\sqrt{3}V_LI_L\cos{\phi}
$$
*Note: The line voltage is chosen over the phase voltage because in a 3-wire system (one with no neutral wire) the phases voltages we cannot be measured and checked and so it is inconvenient to quote phase voltage.*

##Photo-Voltaic Energy

The estimated power reaching the outer edge of Earth’s atmosphere in the form of sunlight is known as the solar constant and is approximately $1,365\; {W}/{m^2}$. Not all this power is available at the Earth’s surface: some is reflected back into space by clouds or absorbed by gasses in the atmosphere.

Some of the sunlight that reaches the earth's surface is scattered and reaches the surface indirectly. The direct component can be focused by lenses or mirrors whilst the indirect component cannot. 

The irradiance or insolation found on the earth’s surface also depends on the Earth’s orbit and the location of the observation point on the surface. A useful way of representing the movement of the Sun relative to the Earth is by use of the Celestial Sphere thar shows the apparent path of the Sun throughout the year. The Earth rotates in a fixed position at the centre of the sphere the change in solar declination $(\delta)$ throughout the year and the significance of the equinoxes and solstices is shown.

![elestialspher](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/celestialsphere.png)

At the equator, the energy passing through an area a illuminates an area a of
the Earth's surface, however, at a latitude $\phi$, the same amount of energy illuminates an area $\frac{a}{\cos(\phi)}$. Therefore, at higher latitudes, the insolation of a flat horizontal surface is less as the same energy is distributed over a greater area. For this reason, in order to maximise the amount of energy collected, it is necessary to reorient a collector to follow the sun.

![attitud](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/lattitude.png)

Latitude also affects how much air is absorbed by the atmosphere because some will travel a longer distance and will therefore be more likely to be absorbed.

- $AM1$ means that light has passed to the Earth’s surface by the shortest route (normal to the Earth’s surface). 
- $AM1.5$ means the light has passed through the atmosphere at an angle to normal that made the path $1.5$ times longer than the normal
path. 

This depends on both latitude and location.

![](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/am.png)

As an approximate guide figure, the radiation that reaches sea level at any location is often taken to be $1,000\; W/m^2$. 
\vspace{5mm}
\\Solar irradiation is the amount of solar energy delivered to a particular location over a particular time. The quantity of sunlight reaching any region is also affected by the time of day, the climate (especially the cloud cover, which scatters the sun's rays), and air pollution. Because of these very variable circumstances, the use of averaged values is a common practice.

- **Total annual irradiation** - This is the energy available per square meter from the sun in a particular location, accumulated over an “average year”. It normally refers to a horizontal surface. A particular example might be $1,200\; kWh/m^2$ per year
- **Daily irradiation** - This is the energy available per square meter from the sun in a particular location across an “average day” in an “average year”. It normally refers to a horizontal surface. It might also be called the annual average irradiance per day. A particular example might be $3\; kWh/m$ per day.
- **Peak power** - This is the power that is available from a particular conversion system (typically a solar panel) in strong sunlight. An irradiance of $1000\; W/m^2$ is usually assumed as the input power. Thus a $1 m^2$ panel with an efficiency of 10\% would be quoted as having a peak power of $100 W_p$ (at $1,000 W/m^2$).

There are significant periods where the power available drops because of cloud cover. The Diffuse and direct components of solar radiation falling on the UK is the same at all seasons, whilst the overall power available decreases in the winter.

### Operating Principle of a PV cell

In a semiconductor, the band gap between the valence and conduction bands is narrow enough that under certain circumstances, electrons can be promoted into the conduction band and become free to move about in the material lattice. This effect can be increased by doping the material to further increase the likelihood of this occurring.

If a photon of light with sufficient energy passes into one side of a pn junction it may be absorbed by an atom and its energy used to promote an electron from the valence band to the conduction band. The hole-electron pair thus created are swept under the electric field in the junctions and constitute a current. This is known as the Photovoltaic Effect.

If a photon of light with sufficient energy passes into one side of a pn junction it may be absorbed by an atom and its energy used to promote an electron from the valence band to the conduction band. The hole-electron pair thus created are swept under the electric field in the junctions and constitute a current. This is known as the Photovoltaic Effect.

The most basic design for a PV cell (and still one of the most widely used) is based on crystalline silicon. A crystalline silicon cell resembles a diode with the lattice doped so that one region becomes p-type semiconductor and the other becomes n-type semiconductor

A PV Cell and it's characteristics:

![](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/pv.png)

![vcha](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/ivchar.png)

The PV cell is represented as a diode with a current source created by the photovoltaic effect in parallel with a diode. The intention is that the photovoltaic current flows through the external circuit not the diode but if the voltage across the external circuit rises much above zero then the diode will begin forward conduction and divert some of the photovoltaic current away from the external circuit. The Current-Voltage curve of the PV cell is similar to a diode except that it is inverted (because of the direction assumed for positive cell current) and offset from zero by the magnitude of the photovoltaic current. The rate at which photons are absorbed (and hole-electron pairs created) determines the current. The I-V characteristic is therefore dependent on the solar irradiance.

For a photon to be absorbed it must have sufficient energy to promote an electron through the energy gap of the semiconductor. The energy of the photon, ER is a function of it frequency, f (or wavelength):
$$
E_R=hf
$$

If a photon has less energy than the energy gap (because the wavelength is large) then the photon is not absorbed and no current is produced. If the photon has more energy than the energy gap then the photon is absorbed with an amount of energy sufficient to promote the electron captured as useful work and the remainder evolved as heat in the crystal.

A high energy gap means that when a photon is absorbed more of its energy is useful and less is lost as heat. However, few photons will have sufficient energy to be absorbed. This is why cell efficiencies are generally low.

The shape of the I-V characteristic is that of a non-ideal current source in which if we attempt to allow a higher and higher voltage to develop across the source then the voltage reduces. 

If a low impedance load is connected then the circuit will draw lot of current but at low voltage and the power yield will be poor. If a high-impedance load is connected then the voltage will be high but little current will flow and the power yield will be low. At some intermediate impedance there will be a current that is reasonably high and a voltage that is also reasonably high and the product of the two is high. The trick is to find the correct impedance match for each and every irradiance condition.

![virra](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/ivirrad.png)

### Construction of PV Cells and Panels

![virra](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/pvcell.png)

This figure shows a transparent “glass” that protects the expensive inner layers without preventing too much of the incident radiation reaching the semiconductor. Silicon layers have a very smooth surface and they reflect a large portion of the light they receive. To reduce this reflection, two approaches are normally followed. Geometric structures (e.g. “pyramids”) are grown on the silicon surface so that light reflected by one structure is mostly received and absorbed by another structure. The second approach is to use an anti-reflective layer over the silicon layers. The cell in Figure 5.8 has an anti-reflective layer.

The contact on the back of a cell is relatively simple, it usually consists of a layer of aluminium or molybdenum. However, the front contact (on the side facing the sun) requires further explanation. When a PV cell is excited by light, hole-electron pairs are is created all over its surface. If the contacts are attached only at the edges of the cell, the large electrical resistance of the top semiconductor layer impedes the flow of current from these regions and reduces the conversion efficiency. To collect as much current as possible, a large number of contacts are fabricated across the entire surface of the PV cell. These contacts are kept relatively thin (compared to their spacing) so that they do not shield too much of the semiconductor from the light which would also reduce the conversion efficiency.

An alternative to metallic grid contacts is a transparent conducting oxide (TCO) layer such as tin oxide (SnO2). The advantage of TCO layers is that they are nearly invisible to incoming light and they form a good bridge from the semiconductor material to the external electrical circuit. Their disadvantage is that they may present a higher contact resistance with the semiconductor material than metallic elements.

#### Crystalline Cells

**Mono-Crystalline Silicon Cells** are made from a silicon base material that is a single crystalline lattice with next to no defects. The crystal is grown and pulled from a molten mass of poly-silicon material. They are expensive to produce but are also the most efficient. They have the disadvantage that the crystals tend to be cylindrical and when cut and mounted on the backplane there are inactive areas between slices.

**Poly-Crystalline Silicon Cells** are made from silicon that is not a single crystal but is cast into ingots. Although cheaper and easier to make, the casting process leads to a less uniform structure and the presence of crystal boundaries leads to additional charge carrier recombination that reduces their efficiency. These problems can be mitigated by casting the ingots in such a way that the crystals are large and also the fact that the ingots can be made square allows them to tessellate more accurately so that there is less inactive area.

#### Thin Film Cells

Thin Film Cells are thinner than crystalline cells. 

**Poly-Crystalline Thin Film Cells** are similar to poly-crystalline cells, but use advanced
light trapping techniques to increase the interaction between the light and the semiconductor. These consist of scattering and reflecting the light inside the cell to increase the path length inside the cell. Because they use less material of a lower grade than crystalline cells, these are cheaper and easier to manufacture, however, they are also lower efficiency. These cells are also known as "thick film" poly-crystalline cells because they are thicker than other thin film cells.

**Amorphous Silicon Thin Film Cells** have a cell structure that is very disordered and generally, they make poor semiconductors as they have a large number of dangling bonds that tend to sweep up any stray carriers. The addition of hydrogen into the amorphous silicon cleans up a lot of these bonds, the material is then referred to as a-Si(H), and the material can be doped to produce n-type and p-type properties. This material is cheap to produce and has a high absorption coefficient, making it very attractive for PV cells. However, the semiconductor properties of the material are such that the cell structure is rather different from a standard crystalline silicon cell.

**Gallium Arsenide Cells** have a similar crystal structure to silicon. GaN
has a high absorption coefficient which makes them highly suitable for use in PV applications and the resulting cells can be quite thin. GaAs also has a wide band-gap that is close to the theoretic optimum for absorbing sunlight, making them very efficient. Unfortunately, the GaN is expensive and the cells are difficult to manufacture so these cells tend to be used in applications where efficiency is more important than cost.

**Dye Sensitised Solar Cells** (also known as "Graetzel cells" after their inventor) are cells where the light is absorbed by a sensitiser layer that injects electrons into a titanium dioxide conduction band which then pass through to the lower contact, through the outer circuit and back to the upper contact. They are returned to the sensitiser layer though a layer of iodine based electrolyte. Whilst these cells are not as efficient as other technologies (about 10\%), they are cheap and easy to produce and can be made as a continuous roll of flexible PV material.

#### Techniques for Improving Solar Panel Efficiency

**Multi-Junction PV Cells** - In this cell, also known as a 'tandem cell', different thin film cells are stacked so that the cell absorbs as much of the incident spectrum as possible. For example, in an amorphous silicon tandem cell, the a-Si is alloyed with different elements at each level to vary the band gap at each layer. The top layer (e.g. alloyed with carbon) absorbs the higher energy photons at the blue end of the spectrum, below this are other thin film cells alloyed with different elements to reduce the band gap so that light from the lower end of the spectrum is absorbed (e.g alloying with germanium reduces the band gap of intrinsic a-Si).

**Concentrating PV Systems** - As the name suggests, these systems use mirrors or lenses to focus the light onto a small PV cell, usually an expensive high efficiency cell is used. They have the advantage that a large amount of energy can be converted by a small PV cell, although the aperture of the concentrator must be large enough the capture the same light as an equivalent flat plate array but at much reduced cost, especially with the use of low cost Fresnel lenses reduces the cost. However, it is usually only the direct component of sunlight that can be concentrated, so the system must track the sun to ensure that the cell is working as efficiently as possible. Also, it is important to ensure that the solar concentration does not raise the temperature of the cell to a point where the efficiency is adversely affect or the cell damaged.

**Fluorescent Concentrators** - The concentrators system in this system is very different from the mirrors or lenses used in classic concentrator systems. In this case, a fluorescent dye in liquid form or contained in a solid plastic absorbs a wide range of wavelengths of light and re-radiates it in a much narrow wavelength. This light is then totally internally reflected to the edges of the panel where it is absorbed by a strip of PV cells. Unlike conventional concentrators, this system can also concentrate diffuse light.

One application for this type of PV module is in windows. The fluorescent dye would be placed into the window glass and the whole window would act as the collector. Although the amount of energy generated would be low, the cells are effectively hidden.

|      Cell Type      |                  Material                  | Typical Efficiency (%) |
| :-----------------: | :----------------------------------------: | :--------------------: |
| Crystalline Silicon |              Mono-crystalline              |        15 - 18         |
|                     |              Poly-crystalline              |        13 - 16         |
|                     | Poly-crystalline produced by ingot casting |           10           |
|                     |           Poly-crystalline band            |        12 - 14         |
|                     |        Poly-crystalline Thin-Layer         |          9.5           |
|     Thin Layer      |             Amorphous Silicon              |         5 - 8          |
|                     |          Copper-Indium Diselenide          |       7.5 - 9.5        |
|                     |             Cadmium-Telluride              |         6 - 9          |
|                     |               Dye sensitised               |           12           |
|                     | Microcrystalline and Micromorphous silicon |        8.5 - 12        |

#### Solar Panels

A single cell gives a voltage that is too low to be useful. In practice, several cells are connected in series in a panel with a more useful voltage. For general purpose energy generation, a typical panel will have 36 cells in series giving a voltage in the region of 20 V when in strong sun light.

#### Modelling PV cell terminal characteristics

The basic conceptual model of a PV cell is a light dependent currebt source in parallel with a diode. A more realistic model adds the parasitic resistances.

![vcellparasite](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/pvcellparasites.png)

The series resistance, $R_s$ is due to resistance of the metallisation and the current paths through the bulk semiconductor and acts to reduce the output voltage. The shunt resistance, $R_{Sh}$ is due to defects in the material lattice creating parallel paths that decrease the available output current.

The inherent photovoltaic current $I_{Ph}$ , scales linearly with solar irradiance and so can be expressed relative to the current found at the nominal irradiance:
$$
I_{ph(G_1)}=I_{ph(G_{nom})}\frac{G_1}{G_{nom}}
$$

Where $G$ is the solar irradiance, $G_{nom}$ is the nominal solar irradiance.

The photovoltaic current also depends on temperature. The variation is taken to be linear so a scaling factor can be used to find current a one temperature given the current at another:

- Form 1:
$$
I_{ph(T_1)}=I_ph(T_{nom})(1+K_{1T}(T_1-T_{nom})) \qquad \text{where }K_{1T}\text{ has units } ^{\circ}C^{-1}
$$

- Form 2:
$$
I_{ph(T_1)}=I_ph(T_{nom})+K_{2T}(T_1-T_{nom}) \qquad \text{where }K_{2T}\text{ has units } A\; ^{\circ}C^{-1}
$$

The teo scaling factors are related by $K_{2T}=I_{ph(T_{nom})}K_{1T}$ and are defined as:
$$
K_{1T}=\frac{I_{SC(T_1)}-I_{SC(T_{nom})}}{I_{ph(T_{nom})}(T_1-T_{nom})}=\frac{I_{SC(T_1)}-I_{SC(T_{nom})}}{I_{SC(T_{nom})}(T_1-T_{nom})} \qquad \text{assuming that }I_{Ph(T_{nom})}\approx I_{SC(T_{nom})}
$$

Where $I_{SC(T_{nom})}$ is the short circuit current produced by the cell at nominal temperature (often $25^{\circ}C$) and nominal irradiance.

For silicon $K_{1T}\approx6\times 10^{-4} \;^{\circ}C^{-1}$
$$
K_{2T}=\frac{I_{SC(T_1)}-I_{SC(T_{nom})}}{(T_1-T_{nom})}
$$
**Form 1 is used in this course!**

The remainder of the model is simply a combination the exponential diode equation with Kirchhoff’s laws:
$$
I_{PV}=I_{ph}-I_{AK}-I_{Sh}
$$

$$
I_{AK}=I_0 \left( e^{\frac{V_{PV}+I_{PV}R_S}{K_Iv_T}}-1 \right)
$$

Where:

- $v_T+\frac{kT}{q}$ and is about $25mV$ at $298K$.
- $I_0$ is the cell reverse saturation current, typically about $1\times10^{-10}A$ at $25^{\circ}C$ but doubles for each $5^{\circ}C$ rise in temperature.
- $K_I$ is the ideality factor of the diode, assumed to be 1 if not stated otherwise.
- $k$ is Boltzmann’s constant $1.38\times10^{-23}J/K$.
- $q$ is the charge on an electron $1.6\times10^{-19}$.

A cold sunny day is the ideal weather for PV systems. Notice that temperature has a larger effect on the junction voltage than on the photovoltaic current and that the variation of junction voltage is mainly due to variation of the reverse saturation current rather than the exponential term. This is shown below.

![vtem](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/pvtemp.png)

### Power Conversion

The power available from a PV panel generally has to be conditioned before it is used. There are multiple objectives for this conditioning. It is important to operate the PV panel at the voltage and current combination that maximises the power yield.

Panel voltages are relatively low and voltage step up is necessary. A first-stage power converter is responsible for these two tasks. The power coditioning is usually done using a Boost SMPS. A second-stage power converter is often added to convert the DC power output to AC.

#### Maximum Power Point Tracking

The correct operating point depends on the characteristic of the particular panel (which is affected by manufacturing tolerances and aging processes), the temperature of the panel and irradiance. Since none of these are easily measured, the construction a feedback system is neccesary.

It is an unusual feedback system in that regulation of the output to make it equal to a reference value isn't the goal, but instead to maximise the value of the output as temperature and irradiance vary.

This is known as a maximum power point tracking problem. The common way to approach is using a trial-and-error iteration known as perturb and observe. A small perturbation to the operating point is made and if the output increases then that perturbation step is accpeted and another step is made in the same direction. If the output decreased then the step is reversed and the next step is made in the reverse direction also.

![ertubetrackin](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/pertubetracking.png)

![ertubei](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/pertubeiv.png)

### Siting and Operation

In equatorial regions of the world, the sun is approximately directly overhead for much of the day and placing a PV panel in a horizontal position captures most of the available energy. At more northerly latitudes, the sun is lower and in the southern sky during the brightest part of the day and the energy yield of a panel inclined slightly and pointing south yields more energy than one that is horizontal. Ideally, the panel would be continuously adjusted to point at the sun but that involves a more complicated and expensive mounting arrangement. There are various rules-of-thumb for choosing a fixed position that yields best results. One is to point the panel due south (in the northern hemisphere) at an angle of inclination equal to the latitude of the site plus about $15^{\circ}$.

In many instances, there are site restrictions. It may be that panels are to be roof mounted and so the inclination angle might be set by the roof pitch and the orientation set by the building’s orientation. There may also be shadows cast by adjacent buildings or trees. One of the panels on the roof of the EEE building has a shadow cast on it by Queen’s Tower in the mid-afternoon. This biases the energy production to the morning and means that that panel should point slightly south-east rather than south.

## Induction Machines

Induction machines are a type of motor. They aren't used much to generate electricity.

In its standard configuration, the induction machine has a three-phase winding on the stator. The stator is made of a stack of steel laminations. Like transformer the stator steel is subject to varying flux that would driv eddy currents so the current paths are broken up by laminations which, because they are slightly oxidised on the surface place insulation barriers in the way of currents in the axial direction.

Each lamination has slots punched in it to carry the windings. The stator is supplied with sinusoidal current. The total flux produced by the stator is found by adding the flux patterns produced by each phase winding.

###Flux Pattern

####Pole-Pair Number

The pole pair number is the number of pole pairs. it determines how many cycles of the sine wave will occur during the $360^{\circ}$ rotation of the magnet.

In general, a machine with p pole-pairs has an electrical frequency p times higher than the angular velocity of the rotor:
$$
\omega_{Elec}=p\omega_{Mech}
$$

A $p$ pole-pair machine has coils that span $\frac{180^{\circ}}{p}$ and produced an alternating pattern of $p$ north poles with $p$ south poles.

#### Total Flux Contributions from Three Phases

The underlying assumptions are that the phase-A winding produces a flux that is
proportional to the current (so long as the steel does not saturate) and that the winding has its coils carefully arranged so that the flux is distributed around the air-gap in a sinusoidal fashion. The flux is greatest along the axis of the winding (in other words, down the centre of the coil) and at points away from this the flux decreases until reaching zero at the off-axis position. In practice, there is some harmonic distortion but this is normally small enough to be neglected.

A magnetic field is produced and is dependednt on the number of pole pairs:
$$
\varphi_A(\theta,i_A)=\frac{L_S}{N_S}i_A\cos{(p\theta)}
$$

Where

- $L_S$ is the self inductance of the wiring.
- $N_S$ is the number of turns.
- $p$ is the number of pole pairs.

The phase-B and phase-C windings produce similar flux distributions but with different spatial
orientation because of the different coil positions.
$$
\varphi_B(\theta,i_B)=\frac{L_S}{N_S}i_B\cos{(p\theta-\theta_B)}
$$

$$
\varphi_C(\theta,i_C)=\frac{L_S}{N_S}i_C\cos{(p\theta-\theta_C)}
$$

If the coils are arranged symmetrically in an anti-clockwise order around the machine then $\theta_A =0$; $\theta_B =\frac{2\pi}{3}$ and $\theta_C =-\frac{2\pi}{3}$

The currents supplied to the machine should be a balanced set and so a positive phase sequence is chosen such that $\varphi_A =0$; $\varphi_B =-\frac{2\pi}{3}$ and $\varphi_C =\frac{2\pi}{3}$:
$$
i_A=I\cos(\omega t+\varphi_A)
$$

$$
i_B=I\cos(\omega t+\varphi_B)
$$

$$
i_C=I\cos(\omega t+\varphi_C)
$$

The total flux found in the air gap is found by superposition:
$$
\varphi=\varphi_A(\theta,i_A)+\varphi_B(\theta,i_B)+\varphi_C(\theta,i_c)
$$

$$
=\frac{IL_S}{N_S}\cos{(\omega t+\phi_A)}\cos{(p\theta-\theta_A)}+\frac{IL_S}{N_S}\cos{(\omega t+\phi_B)}\cos{(p\theta-\theta_B)}+\frac{IL_S}{N_S}\cos{(\omega t+\phi_C)}\cos{(p\theta-\theta_C)}
$$

The product terms can be expanded:
$$
\varphi(\theta,t)=\frac{IL_S}{N_S}\frac{1}{2}\left\lbrace\cos{(\omega t+p\theta)}+\cos{(\omega t-p\theta)}\right\rbrace$$ $$+\frac{IL_S}{N_S}\frac{1}{2}\left\lbrace\cos{(\omega t+p\theta)}-\frac{2\pi}{3}+\cos{(\omega t-p\theta-\frac{2\pi}{3})}\right\rbrace+\frac{IL_S}{N_S}\frac{1}{2}\left\lbrace\cos{(\omega t+p\theta)}+\frac{2\pi}{3}+\cos{(\omega t-p\theta+\frac{2\pi}{3})}\right\rbrace
$$

And now taking the phase B and phase C contributions abd combining them yields:
$$
\varphi(\theta,t)=\frac{IL_S}{N_S}\frac{1}{2}\left\lbrace \cos{(\omega t+p\theta)}+\cos{(\omega-p\theta)}\right\rbrace+\frac{IL_S}{N_S}\frac{1}{2}\left\lbrace \cos{(\omega t+p\theta)}\cos{\left(\frac{4\pi}{3}\right)}+\cos{(\omega-p\theta)}\right\rbrace
$$

$$
\varphi(\theta,t)=\frac{3}{2}\frac{IL_S}{N_S}\cos{(\omega t-p\theta)}
$$

Thus, the total air-gap flux is distributed co-sinusoidally in space and has a co-sinusoidal variation in time. The peak flux occurs at the location, $\theta_p$ that satisfies $\omega t - p\theta =0$. The rate of change of position (the velocity) of the peak flux is thus:
$$
\omega_S=\frac{\,d \theta_P}{\,d t}=\frac{\,d}{\,d t}\left( \frac{\omega t}{p}\right)=\frac{\omega}{p}
$$

This analysis shows that the peak flux rotates (in the positive direction) at an angular velocity equal to the angular frequency of the supply divided by the number of pole-pairs. The speed of rotation of the flux is also known as the synchronous speed, $\omega_S$. The electrical supply frequency is sometimes denoted $\omega_E$:
$$
\omega_S=\frac{\omega_E}{p}
$$

### Rotor Construction

The rotor is made of steel laminations with punched slots. The rotor steel must be able to rotate so a clearance gap, known as the air-gap, is allowed between the stator and rotor. Because flux must cross this air-gap, the gap is kept as short as is practical. A large air-gap would create a high reluctance magnetic path and require a large magnetising current. The slots in the rotor laminations can carry a three-phase winding or, more often, a simple construction of copper or aluminium bars are placed in the slots and connected to shorting rings at either end. This is known as a cage rotor.

![oto](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/rotor.png)

### Principle of Operation

- The supply currents flowing in the stator create a rotating magnetic field.
-  This field is linked to the rotor winding and its movement relative to winding induces voltages in the rotor winding.
-  Theconsequent flow of rotor currents establishes a rotor field that interacts with the stator field to develop torque that opposes the relative motion.

#### Rotor Flux with a stationary Rotor

For a 1 pole pair machine, if the stator is energised with a $50Hz$ voltage whilst the rotor is stationary:

1. Rotor is stationary.
2. The $50Hz$ voltages drive $50Hz$ currents through the stator winding.
3. These currents establish a flux. The flux rotates at $50 rev/s$ or $50\times2\pi rad/s$.
4. The stator flux cuts the rotor bars at $50\times2\pi rad/s$ and induces voltages at this frequency. These voltages drive currents around the rotor at the same frequency.
5. The rotor currents at $50\times2\pi rad/s$ create a rotor field that is also a rotating field. It rotates at $50\times2\pi rad/s$, the same as the stator field.

![tationaryroto](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/stationaryrotor.png)

#### Torque Production

The voltage induced in the rotor drives a rotor current that lags (because the circuit is inductive). The rotor flux therefore lags stator flux and a positive (motoring) torque is developed. Because the two fields rotate at the same speed they maintain a fixed angle difference. Two magnetic fields with an angle between them experience a torque that acts to close the difference. In this case, it acts to make the rotor catch up with the stator field.

#### Rotor Flux with a moving rotor

Once a torque has been applied to the rotor it will start moving. The general case of the rotor bars moving while the stator field rotates also:

1. Rotor is rotating at $40\times2\pi rad/s$ in this example.
2. The $50 Hz$ voltages drive $50 Hz$ currents through the stator winding as before.
3. These currents establish a flux rotating at $50\times2\pi rad/s$.
4. The stator flux rotating at $50\times2\pi rad/s$ cuts the rotor bars rotating at $40\times2\pi rad/s$ with a speed difference of $10\times2\pi rad/s$ and induces voltages at $10\times2\pi rad/s$ in the bars. These voltages drive currents around the rotor at the same frequency.
5. The rotor currents at $10\times2\pi rad/s$ create a rotor field that is also a rotating field. It rotates at $10\times2\pi rad/s$ with respect to the rotor bars, which are themselves rotating at $40\times2\pi rad/s$, which means that the flux rotates at $50\times2\pi rad/s$ (with respect to a stationary frame). This is the same speed as the stator field.

![otatingroto](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/rotatingrotor.png)

In general:

- Angular velocity of rotor: $\omega_R$.
- Stator field velocity relative to stator: $\omega_S=\frac{\omega_E}{p}$.
- Stator field velocity relative to rotor: $\omega_S-\omega_R$
- Rotor field velocity relative to rotor: $\omega_S-\omega_R$
- Rotor field velocity relative to stator: $(\omega_S-\omega_R)+\omega_R=\omega_S$

Whatever the velocity of the rotor structure, the rotor field rotates at the same velocity as the stator field.

#### Rotor Rotating at Synchronous Speed

A special case exists when the physical rotor rotates at the same speed as the stator field.

1. Rotor is rotating at $50\times2\pi rad/s$ in this example.
2. The $50 Hz$ voltages drive $50 Hz$ currents through the stator winding as before.
3. These currents establish a flux rotating at $50\times2\pi rad/s$.
4. The stator flux rotating at $50\times2\pi rad/s$ runs in synchronism with the rotor bars rotating at $50\times2\pi$ rad/s and so the flux does not cut the rotor bars. There is no voltage induced and no rotor currents flow.
5. There is no rotor flux produced and hence no torque either.

![ynchronousroto](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/synchronousrotor.png)

The torque produced by an induction machine is positive if the speed is below synchronous speed but falls to zero at synchronous speed. For speeds above synchronous speed, the torque is negative (i.e. tends to slow not accelerate the machine) and the machine acts as a generator not a motor.

![otoroperatio](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/rotoroperation.png)

### Equivalent Circuit

The equivalent circuit is similar to a tranformer. 

The principle is that if a sinewave voltage is applied to the stator then a sinewave flux is established across the air-gap of the machine that induces an EMF opposing the applied voltage. The flux established by the stator also links the rotor and induces a voltage that depends on the turns-ratio and the speed of the rotor relative to the stator field. This is expressed in terms of a normalised speed difference, known as the slip:
$$
s=\frac{\omega_S-\omega_R}{\omega_S}
$$
If rotor current is allowed to flow, then the stator current must be such that the stator and rotor fluxes together must still induce a sinewave stator EMF equal to the applied voltage. Thus, extra current flows in the stator to compensate for the rotor current.

![otorcircui](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/rotorcircuit.png)

The circuit consists of:

- The voltage and current transformation block
- A magnetising inductance that represents the current that must flow in the stator to set up the flux that cross from the stator to the rotor
- A magnetising resistance (or iron loss resistance) that represents the power lost to hysteresis in the steel and eddy currents in the steel.
- A stator resistance that represents the resistance of the copper wire of the stator coils
- A stator leakage inductance that accounts for the fact that some of the flux produced by the stator flows in local leakage paths not link to the rotor
- A rotor resistance that represents the resistance of the copper wire or aluminium bars of the rotor coils
- A rotor leakage inductance that accounts for the fact that some of the flux produced by the rotor flows in local leakage paths not link to the stator

The transformer-like block is not energy conserving because the voltage and current equations are not reciprocal. Energy is lost from this block and this is the energy that is converted to mechanical form.

A simpler ciruit equivalent circuit is:

![implerotorequi](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/simplerotorequiv.png)

This is formed by referring all components to the stator side of the transform-like transformation block and then removing that block.

#### Important Equivalent Circuit

The final equivalent circuit looks like a transformer except for some differences:

- The rotor is a closed circuit; there is no load impedance attached.
- The rotor currents are dependent on the relative speed of the physical rotor and the stator flux. The rotor impedance is modelled as speed dependent. The real rotor resistance is divided by the slip.
- The dissipation in the rotor resistance is partly normal $I^2 R$ heating loss and partly the electrical power converted to mechanical form (but modelled as $I^2 R$ loss). To emphasise this point, the resistance in the rotor branch is sometimes shown as two separate components.
- The equivalent circuit is known as a "per-phase" model since we show only one phase of the machine. It is assumed that the machine is balance and the other two phases are the same. We apply the phase voltage to this model.

###Power Flow Diagram

![owerlossdiagra](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/powerlossdiagram.png)

The efficiency is found with:

$$
\eta = \frac{P_{out}}{P_{in}} = \frac{P_{in}-\sum{P_{loss}}}{P_{in}}=\frac{P_{out}}{\sum{P_{loss}}}
$$

$$
\eta_{elec}=\frac{P_{conv}}{P_{in}}
$$

The losses in the induction are in the form:
$$
P_{loss}=a+cP_o^2
$$
Things to establish are:

- The current flowing in the induction machine stator and rotor is approximately proportional to the output power. 
- The input power is proportional to current (if the power factor is assumed constant) because of $P_I=3 V_S I_S \cos{(\phi)}$.
-  The output power is also approximately proportional to current if input power and output power are closely matched. 
  - At first it looks like output power is proportional to $I^2 R$ but this isn't true because $s$ is not constant in the equation $P_{EM}=3 I_R^2 R_R \left( \frac{1}{s}-1 \right)$.

The iron losses (eddy current and hysteresis losses) are set by the voltage (or flux) magnitude and frequency and are largely independent of the output power. The friction and windage losses are speed dependent and since the speed variation in normal use is small they are approximately constant. Together these losses make up the $a$-term.

The copper losses (resistive losses in rotor and stator) are proportional to $I^2$ therefore approximately proportional to output power squared. Thus, the copper losses are the $c$-term.

![otorefficienc](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/rotorefficiency.png)

### Torque Characteristic

The electro-magnetic torque, $T_{em}$, the torque produced before the mechanical losses, can be calculated as a function of speed or slip using the equating the converted power to the product or speed and torque:

$$
T_{em}=\frac{3 I'^2_R R'_R \left( \frac{1-s}{s} \right)}{\omega_R}
$$

$$
\omega_R = (1 - s) \omega_S
$$

$$
T_{em} = \frac{3 '^2_R R'_R}{s\omega_S}
$$

This equation includes the referred rotor current which is itself a function of speed. A useful way to proceed is to replace all but the rotor resistance with an equivalent Thévenin source.
$$
\overline{V}_{Thev}=V_S \cdot \frac{R_M || j X_M}{R_s+jX_s +(R_M || j X_M)}
$$

$$
\overline{Z}_{Thev}=j X'_R + ((R_S+jX_s)||R_M||j X_M)
$$

$$
R_{Thev}=Re\{\overline{Z}_{Thev}\} \qquad \qquad X_{Thev}=Im\{\overline{Z}_{Thev}\}
$$

Ths can be used to express referred rotor current as a function of slip:
$$
|\overline{I'}_R|^2=\frac{|\overline{V}_{Thev}|^2}{\left( R_{Thev}+\frac{R'_R}{s} \right)^2 + X^2_{Thev}}
$$

And hence the torque can be expressed as an explicit function of slip:
$$
T_{em}=\frac{3|\overline{V}_{Thev}|^2 R'_R}{\omega_S}\cdot \frac{s}{s^2 | \overline{Z}_{Thev}|^2 + s 2 R_{Thev} R'_R +R'^2_R}
$$

Therefore:
$$
T_{em}\approx \frac{3 | \overline{V}_{Thev}|^2}{\omega_S R'_R}\cdot s \quad \text{for } s \approx 0
$$

$$
T_{em}\approx \frac{3 | \overline{V}_{Thev}|^2 R'_R}{\omega_S X^2_{Thev}}\cdot \frac{1}{s} \quad \text{for } s \approx 1
$$

$$
X_{Thev} > R_{Thev} \qquad \qquad X_{Thev}> R'_R
$$

The induction machine must normally be limited to working close to synchronous speed because the current flow becomes excessive at large slip.

### Direct-on-line Starting

An induction motor can be started by simply connecting it to the three-phase supply. The starting torque, typically 2 or 3 times less than the peak torque but still greater than the rated torque, is sufficient to accelerate the motor to its normal running speed of just below synchronous speed. Starting currents are, however, large, typically ten times greater than rated current. This can be tolerated provided the load accelerates quickly and the circuit-breakers fitted for protection are slow acting.



## Power FLow in Lines and Cables

### Comparison of Transmission and distribution Networks

The transmission system is built to be very secure because loss of a connection to a generator threatens the stability of the system and loss of connection to a load centre affects many millions of customers. There are two important features: 

- The network is “meshed” so that there are multiple routes to each generator and load centre. 
- Each route is a double 3-phase circuit (two sets of 3 conductors). Most faults will affect a single circuit.

Transmission networks are built with Extra High Voltage (EHV) equipment. This reduces power losses. In the UK transmission is at 400 kV.

Once energy has been transported to a load centre it is fed to the individual loads via a distribution network. These operate with lower voltages than transmission networks.

![istributio](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/distribution.png)

Normally a series of decreasing voltages are used. The above image shows a Bulk Supply Point (BSP) which is the interface between a transmission network and a distribution network. It has a pair, or sometimes three, transformers to provide continued supply after a transformer fault. 

The image also shows a set of double-circuit routes to a number of Primary Substations. In the UK, this network is typically at 33 kV.

This network is somewhat less secure than the transmission network because it is radial not meshed. A single fault will not interrupt supply to loads since routes are double circuits and each substation and BSP has two transformers. A double circuit fault would cause an interruption. 

![vdis](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/hvdist.png)

Each primary substation feeds a HV distribution network as shown in above. In the UK this network is normally at 11 kV and consists of single circuits feeding the secondary substations. 

There are switching points that allow the various feeders to be reconfigured after a fault to allow alternative routes from the primary substation to be used.

The final stage of the process is for the secondary substation to transform the voltage (HV) down to the final supply voltage (LV) for domestic and commercial customers, typically 400 V three-phase and 230 V single-phase. 

### Transmission Line Parameters

In general, a transmission line has a quite a complex model because the conductors have series resistance, the wire loops have inductance, the insulators have leakage conductance and the separation of conductors with insulators creates capacitance. The resistance and inductance are in series with the line and the capacitance and insulator conductance are in parallel (or shunt). 

The values of these terms depend on the construction of the line or cable and in particular on its length. A full model of a line or cable should be a “distributed” model with R, L, C and G, throughout the length of the line or cable. For lines of reasonable length and operation at low frequency, we can use a much simpler “lumped parameter” model with R and L as single components and G and C split equally as parallel components at both ends. This is known as the $\pi$-model and is shown below:

![imode](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/pimodel.png)

#### Cable Parameters

Coaxial cables are used. The consist of a central “go” conductor and a metallic outer sheath forming the “return” conductor. The space between the two conductors can be filled with a plastic insulator. This cable will have:

- A resistance which depends on the cross-sectional area of the two conductors, the conductor material and the length of the cable.
- An inductance arising from the magnetic field established around the conductors and depending on the separation of the conductors and the length of the path. The insulator is assumed to have a relative magnetic permeability of approximately 1.
- A capacitance that depends on the outside and inside circumferences of the two conductors, the length of the cable and the permittivity of the insulator.
- A leakage conductance that depends on the separation of the conductors, the length of the cable and the conductance of the insulator.

These are all dependent on length so they are usually expressed as per length quantities. 

The cross-sectional dimensions of a cable are set by its rating: 

- The insulator must be thick enough such that the breakdown electric field strength, $E_{max}$, of the insulator is not exceeded. 
- The conductors must be thick enough so that the maximum current density, $J_{max}, is not exceeded. 
- The maximum current density that can be permitted is essentially set by the thermal design of the cable and thus depends on the $I^2 R$ loss in the conductors, the maximum temperature that the plastic insulator can withstand, the thermal conductivity of the plastic and whether the cable is in air, soil, or water. 

The resistance ignoring the skin effect is:
$$
R'_{LF}=\frac{1}{\sigma_c \pi r^2_c}+\frac{1}{\sigma_c 2 \pi r_o t_o}
$$

At frequencies where the skin effect is significant:
$$
R' = \frac{R_s}{2\pi}\left( \frac{1}{r_c}-\frac{1}{r_o} \right) \qquad \qquad R_s = \sqrt{\frac{\pi f \mu_c }{\sigma_c}}
$$

The skin depth of a conductor is approximately $ \delta = \sqrt{\frac{1}{\pi f \sigma \mu}}$ and if the skin depth is less than the radius or thickness of the conductor then the skin effect corrected equations should be used.

The inductance of per unit length is given by:
$$
L'=\frac{mu_0}{2\pi}\ln{\left(\frac{r_o}{r_C}\right)}
$$

The capacitance per unit length is given by:
$$
C' = \frac{2\pi \epsilon_0 \epsilon_{RI}}{\ln{\left(\frac{r_o}{r_C}\right)}}
$$

The leakage conductance per unit length is given by:
$$
G' = \frac{2\pi \sigma_l}{\ln{\left(\frac{r_o}{r_C}\right)}}
$$

The use of a relatively thin insulator layer (small $r_O$ ) in a cable means that the capacitance of a cable is significant and dominates its characteristic. The thin insulator also means that the magnetic field enclosed by the circuit loop is small and the inductance is not of great significance unless high frequency effects or long cables are considered. For EHV cables the thickness of the insulation is increased and therefore the capacitance per unit length is decreased and the inductance per unit length increased (both dependent on logarithmic functions).

#### Overhead Lines

Overhead lines (OHL) are better than underground lines because they have low capacitance and can easily dissipate $I^2 R$ losses into the surrounding air meaning their temperature isn't limited by a plastic insulator.

The breakdown field strength for dry air is $1 MV/m$ whilst humid air is lower, therefore the cables must be separated by several meters depending on the nominal voltage of the line.

$$
R'_{LF} = \frac{2}{\sigma_C \pi r^2_C} \qquad or \qquad R' = \frac{R_S}{\pi r_c}
$$

$$
L' = \frac{\mu}{\pi} ln{\left( \left( \frac{d}{2r_c}\right)+\sqrt{\left(\frac{d}{2 r_c}\right)^2-1}\right)}
$$

$$
C= \frac{\pi \epsilon_0 \epsilon_R}{ ln{\left( \left( \frac{d}{2r_c}\right)+\sqrt{\left(\frac{d}{2 r_c}\right)^2-1}\right)}}
$$

$$
G' = \frac{\pi \sigma_l}{ ln{\left( \left( \frac{d}{2r_c}\right)+\sqrt{\left(\frac{d}{2 r_c}\right)^2-1}\right)}}
$$

If $d^2 >> (2 r_c)^2$$ which will often be the case ofr power lines then:
$$
L' = \frac{\mu_o}ln{\left( \frac{d}{r_c} \right)} \qquad C' = \frac{2\pi \epsilon_0 \epsilon_{RI}}{\ln{\left(\frac{r_o}{r_C}\right)}} \qquad G' = \frac{2\pi \sigma_l}{\ln{\left(\frac{r_o}{r_C}\right)}}
$$

For most OHL, the separation, $d$ is large enough for the capacitance to be of little importance except for long distance lines or high-frequency transients. 

To achieve a high power rating, we normally keep the current rating fixed and increase the voltage rating. If we increase the conductor separation, $d$, in order to increase the voltage rating then the inductance per unit length increases. With the current rating the same, $r_C$ is unchanged and the resistance per unit length stays constant. 

An important consideration for how a line behaves in a circuit is the $X_L:R$ ratio. 

- EHV has a ratio of 10 or more.
- This decreases for overhead lines to about 3.
- At 11 kV the ratio is 1.
- At 400 V, the resistance dominates and the ratio os less than 1.

This is not a complete picture of the model of a three-phase line on a tower because capacitances to ground are important also.

![hlcapgroun](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/ohlcapground.png)

### Power Flow Equations: $P=P(\delta)$ and $Q =Q(V)$

![hortoh](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/shortohl.png)

A voltage difference between nodes S and R will cause a cuurent to flow:
$$
\overline{I}_{SR}=\frac{\overline{V}_S-\overline{V}_R}{\overline{Z}_{SR}}
$$

For a single-phase system, the complex power $(P+jQ)$ leaving the sending end (generator convention) is:
$$
\overline{S}_S=\overline{V}_S\overline{I}^*_{SR}=\overline{V}_S\frac{\overline{V}^*_S-\overline{V}^*_R}{\overline{Z}^*_{SR}}
$$

For a three-phase systems, we can use phase voltages and include a factor of 3:
$$
\overline{S}_{S3\phi}=3\overline{V}_S\frac{\overline{V}^*_S-\overline{V}^*_R}{\overline{Z}^*_{SR}}
$$

Alternatively using line quantities:
$$
\overline{S}_{S3\phi}=\overline{V}^{line}_{S}\frac{\left(\overline{V}^{line}_S\right)^*-\left(\overline{V}^{line}_R\right)^*}{\overline{Z}^{*}_{SR}}
$$

We can thus use the same equation for single- and three-phase power flow by using line quantities in the three-phase version. 

Now defining $\theta = \angle Z_{SR}$ and $\delta = \angle V_s - \angle V_R $and re-expressing the power flow equation in magnitude and angle form:
$$
\overline{S}_S=\frac{|\overline{V}_S|^2}{|\overline{Z}_{SR}|}e^{j\theta}-\frac{|\overline{V}_S||\overline{V}_R|}{|\overline{Z}_{SR}|}e^{j\theta+\delta}
$$

$$
P_S = \frac{V_s^2}{Z_{SR}}\cos{(\theta)}-\frac{V_S V_R}{Z_{SR}}\cos{(\theta+\delta)}
$$

$$
Q_S = \frac{V_s^2}{Z_{SR}}\sin{(\theta)}-\frac{V_S V_R}{Z_{SR}}\sin{(\theta+\delta)}
$$

A similar but different equation governs the power **arriving** at the receiving end (passive or motor convention):

$$
\overline{S}_R = \overline{V}_R \overline{I}^{*}_{SR}
$$

$$
P_R = \frac{V_s^2}{Z_{SR}}\cos{(\theta-\delta)}-\frac{V_S V_R}{Z_{SR}}\cos{(\theta)}
$$

$$
Q_R = \frac{V_s^2}{Z_{SR}}\sin{(\theta-\delta)}-\frac{V_S V_R}{Z_{SR}}\sin{(\theta)}
$$

#### Power flow in high $X:R$ lines

For EHV overhead lines with $X:R\ge 10, \theta \approx 90^{\circ}$ , the power flow equations then reduce to the following:
$$
P_S \approx \frac{V_S V_R}{X_{SR}}\sin{(\delta)}
$$

$$
Q_S \approx \frac{V_S^2}{X_{SR}}-\frac{V_S V_R}{X_{SR}}\cos{(\delta)}= \frac{V_S}{X_{SR}}(V_S-V_R \cos{(\delta)})
$$

In most normal situations the two voltages will be quite close in value and the angle δ will be small (less than $10^{\circ}$). We can then say that:

- The flow of real power is little influenced by voltage magnitude differences and strongly
influenced by voltage angle differences $P\approx \frac{V^2}{X}\sin{(\delta)} \qquad P \propto \delta$.
- The flow of reactive power is little influenced by voltage angle differences and strongly
influenced by voltage magnitude differences $Q \approx \frac{V}{X} \Delta V \qquad Q \propto \Delta V$.

Remember that this applies to an inductance-dominated line; a resistance-dominated line would have the reverse situation.

The relationship between the real and reactive power flows and the voltage difference appearing across a line is shiwn below:

![hasorpowe](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/phasorpower.png)

#### Approximations for Voltage Drop

When considering just the magnitude of the voltage drop along a line, an approximate expression can be used (provided that the angle difference is small). The approximation is that the in-phase component of voltage-drop causes magnitude change only and the in-quadrature component cause angle change only, as illustrated below:

![hasergfd](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/phasergfda.png)

$$
\Delta V = |V_s| - |V_R|  = R I_{SR} \cos{(\varphi)}+XI_{SR} \sin{(\varphi)}=\frac{R P_R + X Q_R}{|V_R|}
$$

Where $\varphi = \angle V_S - \angle I_{SR}=\arctan{\left( \frac{Q_R}{P_R}\right)}$.

This approximation is showing that for a reactance dominated line it is reactive power that gives rise to voltage drops and for a resistance dominated line it is real power that gives rise to voltage drops. 

This approximation can be difficult to apply. In a feeder with a load at one end, it is normal that the voltage at the source node is known and the voltage at the receiving node is unknown. It is also common that the load power is known rather than its impedance. 

If it is $V_S$, $S_R$ and $Z$ that are known and $V_R$ or $\Delta V$ are to be found, the approximation is not directly useful. We can then use the alternative form of the approximation:
$$
\Delta V = \frac{R P_S + X Q_S}{|V_S|}
$$

We can make a further approximation which is to say that the real and reactive power consumed in the line itself is small and therefore:
$$
P_S \approx P_R \qquad and \qquad Q_s \approx Q_R
$$

If it is felt that this is too approximate, then a correction can be added in an iterative fashion by calculating the current that flows in the line given this first approximation and using this to estimate the power losses in the line and add these to the load power for a fresh approximation of the voltage drop. 

A full solution can be found by stating:
$$
I= \frac{V_S-V_R}{Z} \qquad S_R=V_R I^* = V_R \frac{V_S^*-V_R^*}{Z^*}
$$

And then solving for $V_R$ in:
$$
V_R V_S^* - V_R V_R^* - S_R Z^* = 0
$$

#### Angle Limit on Power Flow

The sin(δ) term in the approximate power flow equation leads to the power transfer characteristic below. This has a clear maximum that occurs at $\delta = 90^{\circ}$.

![owerflowinductivlin](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/powerflowinductivline.png)

In practice, it is rare to run a transmission or distribution line anywhere close to this maximum. A system run close to this point would be susceptible to a collapse of power transfer if a small disturbance pushed the angle beyond $90^{\circ}$.

#### Thermal Limit on Power FLow

Aline is more likely to be limited by its capacity to carry current rather than the angle condition. 
The maximum current an overhead line can carry is limited by how hot the conductors get because of the $I^2 R$ power loss. As the conductors rise in temperature they expand and overhead lines begin to sag. If they sag too far then the insulation distances are compromised and the lines may even sag to the point where they touch treetops or other structures. The extent of $I^2 R$ power loss that can be tolerated before sag is a problem depends on the ambient temperature and so network operators impose different power flow limits for summer and winter conditions. 

### Voltage Control

The second major issue for a transmission system operator is the need to control the voltage to within a narrow band.

#### Voltage Collapse

When current is drawn by a load we expect to see a voltage drop across the supply impedance and therefore the voltage at the load becomes lower than that at the supply point. 

There is some maximum power that can be drawn. If an attempt is made to draw more power than the maximum by decreasing the impedance, the power falls because the increase in current is more than offset by the decrease in load voltage. In a power system, this known as voltage collapse. 

To avoid voltage collapse, a system operator will try to keep the voltage at all nodes in a network close to the nominal value and well away from the “nose” of the voltage collapse curve.

#### Excitation Control

The amount of field current in the field winding of a generator is known as the excitation. 

An important feature of a synchronous machine is that its power factor can be controlled by adjusting the field current. The field current can be adjusted to make the stator current (or line) current lagging or leading as desired.  This shown below:

![yncmachinepowerge](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/syncmachinepowergen.png)

This shows that by decreasing the real component of $E$, the vector $I_G$ is rotated anticlockwise (while keeping $ I_G \cos(\theta)$ constant) and the machine moves from a lagging to a leading condition. 

Thus, we can say that:

- The over-excited condition gives lagging power factor (capacitive) operation. 
- Normal excitation gives (close to) unity power factor operation. 
- Under-excitation gives leading power factor (inductive) operation. 

So, in a similar fashion to power flow in an inductance dominated line, the voltage magnitude change and the flow of reactive power are coupled. A similar equation applies.
$$
Q=\frac{V_{N}}{X_S}(E_S \cos{(\delta)-V_N})
$$

Although in this example the networks voltage $V_N$ was held constant, injecting or removing reactive power from the networks affects the voltages of nearby nodes because of the coupling between reactive power flow and voltage magnitude changes. 

#### Other Reactive Power and Voltage Support Mechanisms

At nodes in the network which do not have generation but where voltage control is needed, it is possible to add some capacitive or inductive reactance so that reactive power is supplied or consumed in order to change the voltage magnitude. The simplest type is *mechanically switched* and is suitable where the quantisation of the capacitance/inductance steps can be coarse, where fast switching is not required and where few operations per day are required. Thyristor switched capacitors/inductors are faster and have a longer service life.

#### Tap-Change Transformers

Voltage control in distribution networks is somewhat different to that in transmission networks. Transmission networks are highly meshed and reactive power injection at a node lifts that node voltage and its surrounding nodes (to some extent). In a distribution network, the structure is different: substations take a power feed from a high voltage, step the voltage down and distribute the power through radial routes to a local area at a lower voltage. 

Because the distribution networks fed by each substation are (largely) independent of each other, the voltage of a group of feeders is set by the transformer of the substation. A very effective way to control the voltage is to use a transformer where the number of turns can be selected by a *tap changer* to give a variable turns-ratio.

#### DC vs AC

There are two places were the argument of AC being better than AC is over-ridden. 

- When making a connection between asynchronous systems. 
- Where very long distance interconnections are required.

Long distance cables and overhead lines have a large capacitance which draws a current even when no real power is being transferred. It can be more cost effective to provide an AC to DC converter at one end of the link, transmit power along the link under DC and reconvert to AC at the other end. Since the capacitors of the cable or line do not draw current under DC, the full current rating is available for power transfer. 

DC wins over AC for overhead lines of about 1,000 km or longer. For cables, with their much higher capacitance per unit length, the distance is more like 60 km or longer. 

A comparison of the costs of AC and DC can be seen below:

![cvsd](https://raw.githubusercontent.com/joshthepirat/joshthepirat.github.io/master/acvsdc.png)

The fixed cost of DC is large because of the cost of the converter stations and the capitalised cost of the power losses of those converter stations (the cost of buying energy over the lifetime of the equipment to make up the losses).

The variable (per unit length) cost of DC is lower because less cable or line material is needed for the same power transfer and the capitalised value of losses in the cables/lines is lower. 