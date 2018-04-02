# Digital Electronics Notes

[TOC]

## Field Programmable Gate Arrays

Field Programmable Gate Arrays are semiconductor devices that are based around a matrix of configurable logic blocks connected via programmable interconnects. 

FPGAs can be reprogrammed to desired application or functionality requirements after manufacturing. This feature distinguishes FPGAs from Application Specific Integrated Circuits, which are custom manufactured for specific design tasks. 

###How FPGAs work

A logic block contains a four input look-up table and a D-flipflip. They can beprogrammed to implement any 4-input Boolean function.

The Logic blocks are surrounded by lots of routing wires and interconnection switches. Typically a signal wire to the Logic Block or Logic Element can be connected to any of these wiring channels through a programmable connection (essentially a digital switch).

###Configuring FPGAs

In FPGAs, you only need to configure the chip ONCE on power-up. You download to the chip a BITSTREAM (also bits in ‘1’s and ‘0’s), which determines the logic functions performed by the Logic Elements, and the interconnecting switches in order to connect the different LEs together to make up your circuit. Once the bitstream is received, the FPGA no longer needs to read the 1’s and 0’s again, very unlike a microprocessor which has to continually decoding the machine instructions.

For an FPGA with that uses 4-input LUTs circuits, the truth table is typically implemented using a tree of four layers of 2-input to 1-output multiplexers. The entire circuit is behaving like a 16-to-1 multiplexer using the 4 inputs ABCD as the control of the MUX tree. For example, if ABCD = 0000, then the top-most input of the MUX is routed to Y output. In this way, ABCD forms the input columns of a truth table.

The routing between blocks is done by setting a register to high or low to set the switch.



## Verilog

Verilog is a hardware design language. The most important advantages of a hardware design language are:

- The design can be made to take on specific parameters (such as number of bits in an adder).
- It is much easier to use compilation and synthesis tools with a text file than with schematics.
- It is very difficult to express an algorithm in diagram form, but it is very easy with a computer language.
- Can be easily edited and a can be saved as a text file.



Verilog can be used at three levels:

- Behavioural Level is where you describe the hardware without reference to digital hardware.
- Register transfer level assumes the existence of registers that are clocked by a clock signal.
- Gate level is where each gate and it’s interconnections are explicitly specified.



Verilog contains interconnected modules. The process of making a design is as follows:

1. Specify a module (make sure to give it a good name).
2. Specify a port as an input, output, or a wire (nodes that aren’t inputs or outputs).
3. Afterwards express modules behaviour with each statement executing in parallel.



|     Code      |        Meaning        |
| :-----------: | :-------------------: |
| ```+ - * /``` |      Arithmetic       |
|      `%`      |        Modulus        |
|  `> >= < <=`  |      Relational       |
|      `!`      |       Negation        |
|     `&&`      |      Logical And      |
|     `||`      |      Logical Or       |
|     `==`      |   Logical Equality    |
|     `!=`      |  Logical Inequality   |
|     `===`     |     Case Equality     |
|     `!==`     |    Case Inequality    |
|      `~`      |   Bit-wise Negation   |
|      `&`      |     Bit-wise And      |
|      `|`      | Bit-wise Inclusive Or |
|      `^`      | Bit-wise Exclusive Or |
|    `^~ ~^`    | Bit-wise Equivalence  |
|   `{},{{}}`   |     Concatination     |
|     `<<`      |      Left Shift       |
|     `>>`      |      Right Shift      |
|     `?:`      |       Condition       |
|     `or`      |       Event or        |
|      `&`      |     Reduction AND     |
|     `~&`      |    Reduction NAND     |
|      `|`      |     Reduction OR      |
|      `^`      |     Reduction XOR     |
|     `~|`      |     Reduction NOR     |
|    `~^ ^~`    |    Reduction XNOR     |

###Boolean Operators

There are three typs of Boolean operators:

- Bitwise operators perform bit-sliced operations on vectors, bit by bit.
- Logical operators return true or false 1 bit results.
- Reduction operators act on each bit of a single input vector.

###Always Blocks 

An `always` block runs whenever a signal in the sensitivity list changes. This allows you to create more sequential circuits. If a `∗` appears in the block it will run anytime a value that appears inside the block has a value change. For example, the following code will run when `a`, `b`, or `sel` changes:

```verilog
always @ (a or b or sel)
    begin
        if (sel) out = a;
        else out = b;
        
        outbar = ~out;
    end
```

###Other verilog rules

- In Verilog `reg` is not a digital register, it is only used to declare a variable that holds a value. In this sense it is similar to `int`, and `float` etc. from C. It is a rule that any variable inside an always block must be declared `reg` and NOT a wire.


- The notation for numbers in verilog is <size> ' <base><number>. For inputs of n bits, you specify when creating the inputs in the way: `input[7:0] a, b;`


- Continuous assignments are where you map the boolean equation to a single verilog statement.
- A case statement is where you directly map the truth table onto the case statemen. It replaces`if-else` statements
- In verilog, If something is not completely specified, the output must retain its previous value when the unspecified condition occurs. If every possibility isn't specified then the risk of creating a completely different circuit occurs.
  - To solve this, either precede all conditionals with a default assignment for all signals, or fully specify all branches of the if-else construct, or include a default statement in case construct:

```verilog
always @ (a or b or c or sel)
  	begin
        out = 1'bx;		//Fully specifying branches
        case (sel)
            2'b00: out = a;
            2'b01: out = b;
            2'b10: out = c;
        endcase
    end
endmodule
```

```verilog
always @ (a or b or c or sel)
  	begin        
        case (sel)
            2'b00: out = a;
            2'b01: out = b;
            2'b10: out = c;
            default: out = 1'bx;	//Including a default
        endcase
    end
endmodule
```

- To specify a sequential edge-triggered flip flop use: `always @ (posedge clk)`. `posedge` and `negedge` makes and always block sequential and edge triggered.

### Blocking vs Non-blocking assignments

Verilog has two types of assignments: blocking and non-blocking. Blocking assignments are executed in the order in which they appear. Therefore the first statement blocks the second until it is done. The `=` is used operator to execute a blocking command.

```verilog
a = b;
b = a;
// Blocking means that both a and b = b.
```

Non-blocking assignments are executed in parallel. An earlier statement doesn’t block the later statement. This can cause a different effect when compared to a blocking assignment.

```verilog
a <= b;
b <= a;
// Non-Blocking means that a and b will swap.
```

**Non-Blocking assignments should always be used for sequential logic.**



## Counters and Shift Registers

Counters and Shift registers are used for some operations because they are fast, cheap, and easy to design. However, they are only good very simple systems. They are a special type of synchronous state machine.

D flipflops in a counter can be easily implemented by using the `always @ (posedge clk)` command.

```verilog
module counter (count clk);	//Synchronous Counter
    output [3:0] count;
    input clk;
    
    reg [3:0]		count;
    always @ (posedge clk)
        count <= count + 1'b1;
endmodule
```

```verilog
module counter (count clk);	//Asynchronous Counter
    output [3:0] count;
    input clk, rst;
    
    reg [3:0]		count;
    always @ (posedge clk)
        if (rst == 0)
        	count <= count + 1'b0;
    	else
            count <= count + 1'b1;
endmodule
```

```verilog
module counter_div10 (count clk);	//Counts to 10 then goes to 0
    output [3:0] count;
    input clk;
    
    reg [3:0]		count;
    always @ (posedge clk)
        if (count == 4'd9)
            count <= 4'b0;
    	else
     	   count <= count + 1'b1;
endmodule
```

### Output glitches

If $k$ counter bits change simultaneously, other logic circuits using them may briefly see any of $2^k$ possible values. Glitches are possible at the logic circuit output if both:

- These $2^k$ values include any that would cause the logic circuit output to change.
- The logic circuit output is meant to remain at a constant value.

Glitches can be caused as the outputs in the circuit won’t change exactly on the gate edge due to propagation delays. These delays may be different for different outputs. 

Anything dependent on these outputs will not change at the correct times due to the misalignments of the outputs. To eliminate output glitches delay all of the outputs with a flip flop. This will make sure that any circuits using the outputs will receive them at the same time. However, a delay of one cycle is needed to implement this. 

Alternatively, a gray code counter can be used if a one-cycle delay isn't wanted.

```verilog
module graycode_counter(count, clk);
    output [3:0] count;
    input clk;
    
    reg [3:0] count;
    
    initial
        count = 4'b0;
    
    reg d_in
    
    always @ (posedge clk)
        count <= d_in;
    
    always @ (count)
        case (count)
            4'd0: d_in = 4'd1;
            4'd1: d_in = 4'd3;
            4'd2: d_in = 4'd6;
            4'd3: d_in = 4'd2;
            4'd4: d_in = 4'd12;
            4'd5: d_in = 4'd4;
            4'd6: d_in = 4'd7;
            4'd7: d_in = 4'd5;
            4'd8: d_in = 4'd0;
            4'd9: d_in = 4'd8;
            4'd10: d_in = 4'd11;
            4'd11: d_in = 4'd9;
            4'd12: d_in = 4'd13;
            4'd13: d_in = 4'd15;
            4'd14: d_in = 4'd10;
            4'd15: d_in = 4'd14;
        endcase
endmodule
```



### Timers

Instead of having a timer that counts events, often one that measures time is wanted. To do a clock input is used to decrement a counter so that a circuit that outputs a tick after a certain number of clock inputs.

An example of one of these circuits is clktick.v it produces a tick pulse every $N+1$ cycles of the clock. 

```verilog
module clktick (clkin, enable, N, tick);
    parameter N_BIT = 16;
    
    input clkin;
    input enable;
    input [N_BIT-1:0] N;
    
    output tick;
    
    reg [N_BIT-1:0] count;
    reg tick;
    
    initial tick = 1'b0;
    
    always @ (posedge clkin)
        if (enable == 1'b1)
            if (count ==0) 
                begin
                    tick <= 1'b1;
                    count <= N;
                end
    		else
        		begin
            		tick <= 1'b0;
                	count <= count - 1'b1;
            	end
endmodule
```

By cascading counters a counter that counts the number of milliseconds elapsed can be made. Look at the clock frequency and cascade the required number of counters.

A clock divider produces a symetric clock output at a frequency that is the input clock frequency divided by $2 \times (K + 1)$. 

```verilog
module clktick (clkin, enable, K, clkout);
    parameter N_BIT = 16;
    
    input clkin;
    input enable;
    input [K_BIT-1:0] K;
    
    output clkout;
    
    reg [K_BIT-1:0] count;
    reg clckout;
    
    initial clkout = 1'b0;
    
    always @ (posedge clkin)
        if (enable == 1'b1)
            if (count == 10'b0) 
                begin
                    clkout <= ~clkout;
                    count <= K;
                end
    		else
				count <= count - 1'b1;
endmodule
```

### Shift registers as control circuits

Instead of producing binary signals using a counter, one could use a shift register to produce a sequence of pulses delayed relative to each other, and use gates to merge these together and produce different binary signals.

A D-input to a shift register could be used to produce a P Q R and S output, delayed from the previous signal by one clock cycle. 

Using AND, NOT, OR or XOR gates, various digital signals can be produced with different delays and pulse widths. Beware that producing control signals this way may generate glitches.

```verilog
module sreg4 (data_out, data_in, clk);
    output data_out;
    input data_in;
    input clk;
    
    reg [4:1] sreg;
    initial sreg = 4'b0;
    
    always @ (posedge clk)
        begin
            sreg[4] <= sreg[3];
            sreg[3] <= sreg[2];
            sreg[2] <= sreg[1];
            sreg[1] <= data_in;
        end
    
    wire data_out;
    assign data_out = sreg[4];
endmodule
```

Alternatively, concatination can be used instead of specifying each `sreg` individually:

```verilog
always @ (posedge clk)
sreg <= {sreg[3:1],	data_in}
```

### Linear Feedback shift registers

A shift register can count in psuedo random binary by using linear feedback. These are called linear feedback shift registers.

They use a XOR gate in parallel to a series of D flipflops to form primitive polynomial such as:
$$
1+X^3+X^{4}
$$
The term $1$ specifies the input to the left-most D-FF. This signal is derived as an XOR function (which is the finite field ‘+’) of two signals “tapped” from stage 3 (i.e. $X^3$) and stage 4 (i.e. $X^{4}$) of the shift register.

For a m-stage LFSR, where m is an integer, one could always find a polynomial (i.e. tap configuration) that will provide maximal length. This means that the sequence will only repeat after $2^m-1$ cycles. Such a polynomial is known as a **primitive polynomial**.

```verilog
module lsfr4 (data_out, clk);
    output [4:1] data_out;
    input clk;
    
    reg [4:1] sreg;
    initial sreg = 4'b1;
    
    always @ (posedge clk)
		sreg < {sreg[3:0], sreg[4] ^ sreg[3]};
    
    assign data_out = sreg[4];
endmodule
```



## Finite State Machines

###Synchronous state machines

A synchronous state machine is made up of a set of D-flipflips that are used to store the current state value. The current state together with external inputs are the fed to a combinational logic circuit to evaluate two things: the next state and the current outputs.

![enericfs](/home/josh/Documents/Digital Notes/genericfsm.png)

This is a synchronous state machine because the transition to the next state is synchronous with the rising edge of the clock signal. Therefore all output signals are synchronized.

There are two basic rules in designing a FSM that operates reliably:

- Do not put logic in front of the clock signal. Doing so is likely to cause timing issues when the FSM is used in conjunction with the rest of the system.
- Do not use asynchronous SET or RESET signals. Doing so would make the rest of the system NOT synchronous to the CLOCK signal.

####Combinational Logic Block

The combinational logic circuit in a FSM performs two separate tasks:

- It determines what the output signals should be. This derived by the current state value STATE and the current inputs. Therefore such output signals could change in the middle of a clock cycle if input signals are NOT synchronized with the CLOCK.
- It determines what the next state value should be, i.e. the state transition of the FSM.

It contains no memory circuit.

### Analysing a finite state machine

#### State Table

- Each row in a table represents one state (If an FSM has 2 state bits, there are 4 possible states).
- There is one column devoted to each input combination (There would be four columns if there were two inputs).
- The contents of the table shows the next state transition, followed by the output signal(s) during the current state. A ‘/’ character is used to separate the two.

#### Drawing a state diagram

1. Split the state transition table into two tables: one for next state, and another for the output signal.
2. Now draw a bubble for each state and label this with the state name (which happens in this case to be the same as the state value). Transition arrows are draw between the states with a Boolean expression as a label to indicate the condition required for the transition to occur **ON THE ACTIVE CLOCK EDGE**. The transitions are derived direclty from the next state table.
3. Inside the bubble, now indicate the value of Y as another Boolean expression.

In order to make the state diagram less cluttered, the self transition arrows can be omitted. Therefore the rule is that a state machine stays in its current state unless the conditions of an exiting arrow is satisfied.

Output expressions can also be put on arrows.

#### TIming Diagram

It is important to note that the behaviour of a FSM is determined by the initial state. This is specified with the `initial` statement in verilog.

Given the state diagram and the initial state, and a waveform of the input A, the subsequent states and the output can easily be traced.

There are two types of state machines:

- **Moore machine** – the outputs are constant 0 or 1 while inside a state even if input changes. The output only changes on the active clock edge. An example of a Moore machine is a counter. For our designs with Verilog, our FSMs are usually a Moore machine.
- **Mealy machine** – the outputs could changes if input changes even without an active clock edge.

#### Output Glitches

In general, a glitch can be produced if:

- Two or more state bits change values when transiting states.
- The output has the same value in both states.

The source of glitches can be seen by analysing the timing diagrams. Components like gates introduce delay which can affect the rest of the circuit. These aren't usually important unless they are used as clock signals for other circuits.

D flipflops can be used to avoid glitches but intriduce one cycle delays.

###Designing a finite state machine

#### General design procedure

1. Construct a sequence of input waveforms that includes all relevant situations.
2. Go through the sequence from the beginning. Each time an input changes, decide whether to:
   - Branch back to a revious state if the current sutuation is materially identical to a previous one.
   - Create a new state.
3. For each new state, ensure that the following are specified:
   - Which state to branch to for each possible input pattern.
   - What signals to output for every possible input pattern.

Alternatively, the FSM can be designed by approaching it like an algorithm.

#### Implementing the FSM

1. Before mapping the FSM to hardware, **state encoding** needs to be performes. This gives each state a unique binary value.
2. Fill in the state transition table for the FSM.
   - For each state and input put the next state/output
3. From this, the Boolean expression can be derived for the combinational logic block.

### One-hot encoding

In implementing FSMs using FPGAs, a form of state encoding different from simple binary encoding is used. It is known as one-hot encoding. With one-hot encoding, only one-bit in the state value is “hot” (i.e. set to ‘1’), and all the other bits are “cold” (i.e. reset to ‘0’).

Using one-hot encoding requires more state registers, as for $N$ states, $N$ registers are needed. The advantage is that the state transition table and utput logic can be much simpler than binary encoding as there is no need to decode the binary number.

FPGA is a register-rich architecture. Therefore using one-hot encoding matches the FPGA architecture well. Each FPGA logic element contains a combinational logic module and one or more registers.

### Implementation in verilog

![smexampl](/home/josh/Documents/Digital Notes/fsmexample.png)

First declare the inputs outputs and parameters. The parameters assign the binary value to each state to make it clearer (in this case one hot encoding is used).

```verilog
//Declarations
module eliminator (out, in, clk, rst);

input in, clk, rst;
output out;

parameter S_A = 4'b0001; S_B = 4'b0010;
parameter S_C = 4'b0100; S_D = 4'b1000;
parameter NSTATE = 4;
    
reg [NSTATE-1:0] state;
```

Specify the state machine transition logic (in this case the FSM is detecting whether there is a single pulse and getting rid of it).

```verilog
//State transition
always @ (posedge clk)
    if (rst == 1'b1)
        state <= S_A;
else
    case (state)
        S_A: if (in == 1'b1) state <= S_B;
        S_B: if (in == 1'b1) state <= S_C;
        		else state <= S_A;
        S_C: if (in == 1'b0) state <= S_D;
        S_D: if (in == 1'b1) state <= S_C;
        		else state <= S_A;
        default: ; //Do nothing
    endcase
```

Specify the Output logic.

```verilog
always @ (*)
    case (state)
        S_A: out = 1'b0;
        S_B: out = 1'b0;
        S_C: out = 1'b1;
        S_D: out = 1'b1;
    endcase

endmodule
```

Using parameter block to give a name to each of the states has many benefits: the Verilog design is much easier to read; the state assignment values can be modified without needing to change any code. In general, parameter blocks allow the use of symbols (names) to replace numbers. This makes the code easier to read and easier to maintain, and it is a good habit to get into.

The state variable declaration reg `[NSTATE-1:0]` is used here to show that there are 4 states (S_A to S_D).

When specifying FSM in Verilog, you should following the following convention:

- Use `always @ (posedge clk)` block to specify the state transition. Note that the `<=` assignments (non-blocking) are used in this always block because the FSM is responding to clock edges.
- Use a separate `always @ (*)` block to specify the the output logic. Normal assignments (blocking) are used here because this is actually a combinational logic block, not sequential circuit.

It is a good idea to include `initial` statements for the initial state of output waves.

Make sure to include the `default: ; \\Do nothing` statement.



## Timing Constraints and Analysis

Typical digital signals will have overshoots and undershoots. Fortunately, digital signals are characterised as low (‘0’) or high (‘1’) by threshold voltages:

- **Voh = output high threshold voltage** – all logic circuits with a high output will drive a circuit node at Voh or higher.
- **Vih = input high threshold voltage** – all logic circuits will regard an input voltage as high (‘1’) if it is 2V or higher.

The difference Voh - Vih is the margin of eror between the driving circuit and the input circuit. It is called the noise margin. It is the amount of overshoot, undershoot or noise that could be tolerated on a digital signal wire without it being interpreted wrongly by the circuit.

### Setup and Hold times

Registers (D flipflops) are used everywhere in digital circuits. Using registers has the advantage of: 

1. They synchronising all activities to a clock signal.
2. They solate different part of the digital systems between registers (because the registers block the signal until the next active edge of the clock. 
3. It makes timing consideration much easier to handle.

For reliable operations, data must be stable for some time before the rising edge of CLOCK. This time is known as setup time $t_s$. This time is needed because there is internal propagation of the DATA signal which must be taken into account. As a result, for the D-flipflop to work, such internal delay is specified as the flipflop setup time requirement.

Similarly, data must be stable and holds its value some time after the rising edge of CLOCK. This time is known as hold time $t_H$.

If data changes within the setup or hold time then the flipflop becomes metastable. The Q value becomes unknown. It will eventually go to high or low but it teill take a random time.

To avoid the metastable signal causing error in the digital system, one could use a synchronization chain that contains a chain of D flipflops so that the output register is synchronised to the clock until the first flipflop goes stable.

### Transmission delays

For a given wire, there is a characteristic inductance $L_o$ and characteristic capacitance $C_o$ per unit length. The speed of propagation of a digital signal along such a wire is roughly $\sqrt{L_oC_o}$.

A digital signal takes around 1 nanosecond to travel a distance of 15 cm on a PCB.

### Synchrous Bit-serial transmission

Serial transmission sends one bit at a time. It is very simple and requires few wires linking the systems.

If the communication is governed by a clock signal, it is a synchronous bit-serial transmission system. A clock signal and a data signal are needed. 

Since in most cases, the data has more than one bit (for example a block of data occupying, say, 134 bits). This block of data is known as a “frame”. To identify when a frame of data starts, Another signal FRAME is needed to indicate where the first bit starts. 

The sender is triggered on the falling edge of the clock, and the receiver is triggered on the rising edge of the clock.

In timing diagrams remember to include propogation and transmission delays.

#### Timing constraints

In order to guarantee reliable working of the serial interface circuit, the rising edge of receiver clock must become stable outside the setup time window.

**To see whether a system is stable consider what causes it to change and see how long it takes to propogate, then add the set up time.**

**The do the same to work out whether the value will be held for long enough.**

To write the timing inequalities:

- For a device "B" look at when the data input changes in terms of propogation delays etc.
- Look at the rising (or falling) edge of the clock. 
- For reliable operation:
  - Setup requrement: The time for the data to change + the setup time < The time the clock changes.
  - Hold requirement: The time the clock changes + hold time < time the data next changes.
- Always look at maximum propogation delays and minimum changing times.
- $t_H$ and $t_s$ are never in the same inequality.
- Remember that D flipflops will not change till they get a clock signal etc.



##Digital to Analogue Conversion

### DAC specific jargon

- **Resolution** – the voltage step equivalent to one least significant bit (1 LSB) of the digital input. Assuming that the input is an N-bit number, then resolution of the DAC is the same as:

$$
\frac{\text{full scale voltage}}{2^N-1}
$$

- **Accuracy** – maximum error as compared to the perfect reference line (red).
- **Linearity** – Instead of using the reference line, we can join to max-point with the minpoint to form another straight line. Linearity is the maximum deviation from this new line.
- **Differential Linearity** – Worse case error as you step from X to X+1 for all values of X.
- **Monotonic DAC** – One that always goes up as the input number X[3:0] increases.
- **Settling time** – Time taken to reach final value within ±1 LSB as input changes.

### Simple DAC

The simplest DAC can be constructed using a number of resistors with binary weighted values. `X[3:0]` is the 4-bit digital value to be converter to an analogue voltage Vout. The 4-bit number is used as input to buffer circuits (the rectangular blocks labelled ‘1’). The outputs of the four buffers are `V[3:0]` respectively.
$$
V_{out}=\frac{V_nG_n+V_{n-1}G_{n-1}+...+V_{0}G_0}{G_n+G_{n-1}+...+G_0}
$$

$$
R_{Thev}=\frac{1}{G_n+G_{n-1}+...+G_0}
$$

Using Kirchhoff current law, the current at node Vout sums to zero, and this gives the first equation. Rearranging the equation produces the equation for $V_{out}$. The digital value `X[3:0]` can therefore be converted to an analogue voltage in the correct binary weighting if `G3:G2:G1:G0` have the ratio of `8:4:2:1`. 

Since the digital buffer is very fast and the resistor network has no (or negligible) capacitance or inductance, this DAC can be very fast. However, this DAC has two problems: 

1. The output impedance of the DAC is the Thevenin equivalent circuit resistance. Choosing too high a resistance value results in the DAC having a high output impedance; choosing too low a resistance value draws lots of current from the buffers and is inefficient on power. 
2. It requires very large resistance ratio if the number of bits of X is large. For example, for a 10-bit DAC, the ratio is `1024:1`. Such a DAC is difficult and expensive to manufacture. 

Instead of only using binary weighting, it is possible for you to choose five arbitrary Vout values. If you add another resistor R4 connecting from Vout to the power supply, and set `X[3:0]` to `0000`, `0001`, `0010`, `0100` and `1000`, you can easily work out the required value of the resistances in order to give you the five arbitrary voltages.

### Improved Simple DAC

By adding an inverting summing op amp amplifier to the simple DAC the circuit can be improved.
$$
V_{out}=\frac{-R_f}{R_{Thev}}\times V_{Thev}=-R_f(V_nG_n+V_{n-1}{G_{n-1}}+...+V_0G_0)
$$
The high output impedance of the previous circuit can be circumvented using an operational amplifier. Shown here is a summing amplifier. $V_{out}$ is given by this simple linear equation. The output impedance is that of the op amp and is very low.

Unfortunately the output voltage of this circuit cannot change very fast. It is limited by the slew rate of the op amp.

Making binary weighted resistors is still difficult and expensive of the number of bits in the DAC is high.

#### Further Improvement with a reference voltage source

Instead of driving the resistor network directly from the digital output, which is not very accurate, most DAC actually use the digital signal to control electronic switches which switch in or out a reference voltage Vref. This reference voltage can be made very accurate, thus providing accurate output voltage values.

### Thermometer DAC using Resistor String

Instead of using binary weighted resistor network, a series string of identical resistors can be used. With this architecture, $V_{ref}$ to 0 is divided into 8 equal steps (including 0 value). The 3-bit digital input is decoded into 8 possible binary one-hot codes. For example, 000 results in the lowest switch being connected and 111 will switch the upper most switch on.

This DAC has the advantages listed here:

- It is simple, uses only one resistor value R everywhere, therefore easy to manufacture using semiconductor process.
- Only operating two switches at anyone time, so the glitches are smaller.
- It is low power and inherently monotonic.

However, it uses a lot of resistors meaning it has a large resistance and higher noise. Therefore it is only useful for low to medium resolution dacs.

#### Resistor String DAC with op amp output

Instead of using a large number of switches, switches can also be arranged into a tree structure. Decoding is implicitly performed via the control of the switches using the three digital bits. The output op amp provides buffering of the DAC voltage.

### DAC using R-2R Ladder

A string resistor network is good for small numbers of resistors with a low number of bits, but for 16 bit DAC, over 65000 resistors would be needed. A better solution is to use R-2R Ladder network. 

The basic idea is to produce current $I_o$, $2I_o$, $4I_o$ etc, using only identical resistors connected in a special way.

The best way to understand the working of this R-2R network is to consider just two resistors both with values 2R. If the current flowing through each resistor is Io, then the total current at node $V_o$ must be $I_1 = 2I_o$. The Thevenin equivalent resistance of these two resistor is $2R || 2R = R$. Now we add an extra resistor $R$ in series with these two $2R$ network. Together they form a resistance 2R. If we add the next step of the ladder as shown here, the total current at $V_1$ is $2I_1 = 4 I_o$. As you can see, adding each extra step of the ladder doubles the current. If the voltage drop across the horizontal resistors therefore also increases in ratios of 2 for each step.

For a practical DAC circuit, the R-2R ladder network is connected to the virtual earth of an op amp. The current is either sent to the virtual earth node if the digital value is $1$, or switched to earth if it is $0$. In that way , the output voltage Vout is a converter analogue value of `X[3:0]`.

Note that we switch current from one branch to another branch. It is known as current steering. Current steering is much faster than turning the current on and off.

###Digital Attenuator (Amplifier)

Instead of using $V_{ref}$, a fixed reference voltage, we could use an analogue input $V_{in}$ (such as an audio signal), and then use the DAC as a digitally control amplifier or attenuator. This is also known as a multiplying DAC. The output is $X$ multiplied by $V_{in}$.

###Bipolar DAC

A bipolar DAC is one that can give out both positive and negative voltages according to the sign of its input. There are two aspects of the circuit that need to be changed.

- **Number representation** - Usually two's complement is used, but in converters it's better to use offset-binary notation. What it means is that you use zero to represent the most negative value instead of a negative number. For example, for a range from -512 to 511, use the range 0 to 1023 by adding to your number an offset of 512.
- **Positive and negative currents** - If you need to produce a DAC with negative voltage or current for bipolar digital input values, you need an analogue component known as a current mirror. A current mirror simply mirrors the current on one branch of the circuit to a second branch of the circuit.

### Signed Number DAC

A current mirror can be attached to the bottom of the R-2R ladder so that unused currents are reversed in direction. These are then added to the original current to give $2(X3:0-8)I_0$.

### PWM DAC

Instead of using analogue resistor network, it is possible to build a simple DAC using only digital components.

A counter is used to produce a count value A that ramps up linearly in a sawtooth manner. The digital value we want to convert to analogue value is stored in the input register. A digital comparator circuit compares this input data with the counter value (which is ramping up). While the counter is less than this value, the output of the comparator is high. As soon as the counter value exceeds the input data, the output goes low. In this way, the pulse width is proportional to the value of the input data.

```verilog
module pwm (clk, data_in, load, pwm_out);
    input clk;
    input [9:0] data_in;
    input load'
    output pwm_out;
    
    reg [9:0] d;
    reg [9:0] count;
    reg pwm_out;
    
    always @ (posedge clk)
        if (load == 1'b1) d <= data_in;
    
    initial count = 10'b0;
    
    always @(posedge clk)
        begin
            count <= count + 1'b0;
            if (count > d)
                pwm_out <= 1'b0;
            else
                pwm_out <= 1'b1;
        end
endmodule
```



## Analogue to digitial conversion

ADCs are more complicated circuits that DACs. 

They take an analogue input and round it to nearest integer. Therefore information is destroyed since a range of voltages is converted to a single voltage.

The ADC does this using sampling. An analogue signal is quantised in time and in amplitude. 

- Quantizing in time does not loose information as long as the sampling frequency is at least twice the maximum frequency component of the signal you are sampling. 
- Quantising in amplitude is achieved through a ADC and information is lost. The difference between the original analogue signal and the digitized signal is the quantisation noise.

$V_{out}$ is resitricted to discrete levels so it cannot follow $V_{in}$ exactly. The quantization nise can be found by first quantizing the signal then converting this back to analogue and subtracting $V_{out}-V_{in}$. It has the amplitude of $\pm \frac{1}{2} LSB$. The RMS value can be found using:
$$
\sqrt{\int_{-0.5}^{0.5}x^2 dx}=\frac{1}{\sqrt{12}}=0.3LSB
$$
The signal to noise ratio SNR is the ratio of the maximum sine wave level to the noise level.

For a sinewave of amplitude $\pm 2^{n-1}$ the RMS value is $0.35\times 2^n$.

The SNR is:
$$
20\log_10{\left(\frac{0.35\times 2^n}{0.3}\right)}=1.8+6n\times LSB
$$
Therefore for every extra bit of ADC/DAC resolution, an extra $6dB$ is added to the SNR.

### Threshold voltages

Every ADC contains a DAC converter, which provides many threshold voltages. The ADC compares the input voltage to be converter $V_{in}$ to these threshold voltages and determine what the converter digital value should be. Each converter value $X$ therefore corresponds to a range of values of $V_{in}$. This range defines the threshold voltages which is $X \pm \frac{1}{2} LSB$.

### Flash ADC

For an n-bit converter, there are $2^n-1$ threshold voltages. Therefore there are an equal number of comparators. A string of resitors is then used to provide the threshold voltages. This part is called a DAC circuit. This then gets encoded into the digital value using a priority encoder.

#### Priority encoder

The decoder that maps the thermometer code to binary code is a very simple truth table, which can be implemented in Verilog as a case statement.

### ADC using a counter

A simple ADC can be implemented using a counter and a DAC. 

A START signal is a short pulse that is used to asynchronously reset the counter to zero. This starts the ADC conversion. If $V_{in}$ is above the lowest value from DAC, the counter is enabled. The counter then counts up until $V_{in}$ is now lower than the DAC output, and counter is disabled, a DONE signal goes high. The output shows the value of the counter that makes the DAC just over the $V_{in}$ value. 

The disadvantage of this converter is that the time it takes to perform a conversion is dependent on the value of $V_{in}$. Furthermore, if this is a 16-bit converter, it could take over 65,000 clock cycles – therefore the conversion time can be very long.

### Successive Approximation ADC

1. A successive approximation DAC splits up the output values into two. It then sets the output value of the DAC to `4b'1000` (for a 4 but DAC). It sets the MSB to $1$.
2. It compares $V_{in}$ to this value and then if it is greater than or equal and if that it the case, the MSB stays as $1$, otherwise it gets set to $0$ because setting the MSB to $1$ would be too high.
3. It then repeats this except only using the half that the $V_{in}$ values was determined to be a part of. $0$ or $1$ is set as the second MSB.
4. This is repeated until the required value of precision is reached (e.g. 4 times for a 4 bit converter).

![uccessiveAD](/home/josh/Documents/Digital Notes/successiveADC.png)

A DAC is used to generate the threshold voltages, and then a state machine is used to implement the algorithm.

![uccessiveADCfs](/home/josh/Documents/Digital Notes/successiveADCfsm.png)

This just acts like a binary tree.

### ADC with sample/hold

So far we assume that while the ADC is performing conversion, the input signal is held at a fixed voltage level. If the input signal is in fact changing, the converted digital value will not be an accurate measure of $V_{in}$ at the time of sampling. To ensure that the ADC input is held at a fixed voltage, we usually include follow and hold circuit. An analogue switch is normally turn ON, so that $V_{in}$ is continuously charging the capacitor C. When the START pulse activates the ADC to take a sample, the DONE signal immediately goes low. This should open the switch and hold the $V_{in}$ value at the time the conversion started.

![ampleandhol](/home/josh/Documents/Digital Notes/sampleandhold.png)

A practical sample/hold or follow/hold circuit is shown here using two operation amplifier. This has the advantage that the leakage current from the capacitor can be made very low. During the sampling or following mode, the right most op amp provides strong charging current to charge the capcitor.

The time taked to charge the capacitor is limited by the maximum op amp current. Thus detemines the *acquisition time* to acquire the signal to withing $\frac{1}{2} LSB$. 

The value of C is a compromise.

- High C gives slow acquisition.
- Small C gives too much drift.

An ADC with a sample/hold in them is called a sampling DAC.

### Other ADC types

There is another class of converters known as oversampling converters. These use a sigma-delta modulator circuit which sample the input signal at a much high frequency than the Nyquist frequency demands. 

Normally it produces a 1-bit digital signal which is than down sampled and filtered to produce an accurate analogue output for a DAC, and a multi-bit digital value for a ADC. 

For example, CD players use an oversample DAC with sampling rate of 6.4MHz. This is then down sampled to produce an output sample rate of 50KHz – a oversampling ratio of 128 times.



## Memory Interfacing

Memory cells are usually organised in the form of a 2-D array of RAM cells. An N bit address bus defines $2^N$ memory locations.

These are accessed first in a row, then in a column. The address bus is divided into two components, the row address and the column address. There is a decoder to translate the 8-bit row address into one-hot outputs in order to specify which row is being accessed. Only ONE ROW will be enable at any one time (hence one-hot). 

The second part of the address (normally the less significant bits) is used as select signal into the output mux. This is because when memory is accessed, they are normally read or written in a sequence. Using LSB for column decoding means that one stays on the same row of memory as much as possible. Staying in the same row uses significantly lower energy than switching between rows in memory accesses. 

The column address is used to select from a N-to-1 mux to provide the correct location in memory to access. There are N identical blocks, each providing one-bit of the data output. The output enable signal OE allows the selected data value be driven on the data bus.

### Random Access Memory (RAM)

In static RAM, data is stored in bistable latches, whilst in dynamic RAM data is stored in charged capacitors.

![k8RA](/home/josh/Documents/Digital Notes/8k8RAM.png)

Here is a 8K x 8 static RAM chip and its associated digital signals. The 13-bit address bus A12:0, the 8-bit data bus D7:0 are mandatory. There are three more control signals: Output Enable OE which we have seen before, Chip Enable CE which is used to address or select this particular memory chip (hence the name), and finally the WRITE ENABLE signal WE, which, when set high, indicates that you are writing to the RAM chip, and is normally low (i.e. reading).

Note that the data bus has an inverted triangle sign, indicating that this is a tri-state bus. This means that the pin could be an input pin, output pin, or an open-circuit pin (i.e. not connected to anything – we call the signal floating). The truth table shown here specifies the behaviour of the data bus in one of the three possible states.

#### Static RAM

For a 8k x 8 RAM, there are 8 data bits, and therefore 8 separate 1-bit arrays. Let us assume that each data bit array is organised as a 256 rows x 32 column (=8192) of memory cells. Eight such array are placed next to each other to form the 8 data bits required. This makes the memory chip roughly square (which is generally desirable). 

You can think of the row decoder and the column selector driven by the 13-bit address as a 8192 way multiplexer, selecting one of 8192 cells organised as 256 x 32, to be accessed. 

The simplified circuit of each memory cell consists of two inverters and two switches is a schematic of the read-write circuit. When reading from the cell, A12:0 select one of 8192 cells to route its signal via the right inverter to Dn. Now Dn is an output pin. This only happens if CE*OE* !WR = 1 (i.e. asserting CE and OE, but not asserting WR). 

When writing to the memory cell, the right switch is open, Dn is an input pin driving the left hand inverter and the output switch from that inverter is closed because both CE and WR are asserted.

### Microprocessor to Memory Interface

During each memory cycle:

- The address bus selects one of the $2^N$ possible memory locations.
- The data connections transfer one word of memory to either the memory (write), or the mocroprosser (read).
- The control signals go between the two to control the transfer of information, and is in general governed by the microprocessor which acts as the **master**.

### Mircroprocessor Memory Map

The memory map of a microprossor is split intot three sections:

- Input/outpus.
- ROM.
- RAM.

For example:

|      | A15:A12 |             |
| :--: | :-----: | :---------: |
|  F   |  1111   | Inut/Output |
|  E   |  1110   |     ROM     |
|  D   |  1101   |     ROM     |
|  C   |  1100   |     ROM     |
|  B   |  1011   |     ROM     |
|  A   |  1010   |             |
|  9   |  1001   |             |
|  8   |  1000   |             |
|  7   |  0111   |     RAM     |
|  6   |  0110   |     RAM     |
|  5   |  0101   |     RAM     |
|  4   |  0100   |     RAM     |
|  3   |  0011   |     RAM     |
|  2   |  0010   |     RAM     |
|  1   |  0001   |     RAM     |
|  0   |  0000   |     RAM     |

By looking at this memory map, it can be seen that:

- RAM = $!A15$
- ROM = $A15 \& A14 \& !(A13 \& A12) + (A15 \& !A14 \& A13 \& A12)$
- INOUT = $A15\&A14\&A13\&A12$

A design needs to take the upper bits of the address bus and decode these bits into enable signals for the three different partitions. In this case, we can see that we only need to decode A15:12 according to the Boolean equations shown here. What about A11:0? These are the address bits used inside the RAM, ROM and input/output modules to select particular locations

Selecting which memory sub-system and therefore which memory chip to enable is the job of the address decoder circuit. This circuit takes the upper bits of the address bus, and produce enable signals for RAM, ROM and INOUTx for a particular I/O device.

### Memory Control Interface Signals

- **Output enable** - $OE=MCLOCK \& !WRITE$ from microporcessor. This turns on the data output from the memory.
- **Write enable** - $WE=MCLOCK\&WRITE$ from  microprocessor. This writes new information into the selected memory location with data coming from the microprocessor.
- **Chip enable** - COmes from the decoder and makes sure the memory only responds to the correct addresses.

### Memory Read Cycle

![eadcycl](/home/josh/Documents/Digital Notes/readcycle.png)

A read cycle happens when $CE\&OE\&!WR$ is true.

1. If A12:0 changes, D7:0 remains for at least 2ns and goes to a new value withon 8ns. The value in between is unknown even if old and new locations contain the same value. This is address to data **access time** for this RAM.
2. If a read cycle ends due to $OE$ going low then the outputs go Hi-Z within 2ns.
3. If a read cycle starts due to $OE$ going high, D7:0 stays Hi-Z for at least another 2ns and the selected word appears within 4ns.

The most important delay here is that from address or OE to data. They are called address access time and output enable access time. Usually address access timing is longer (here it is 8ns) than OE access time (4ns) because output enable simply enable the output multiplex stage, which is close to the data output pin. Address access involves decoding the address values to produce the one-hot row select signal (known as the WORD line), and then the row of memory cells needs to present its data to the column multiplexer. Selecting which row to access is generally a much slower process than the column multiplexer.

### Memory Write Cycle

![ritecycl](/home/josh/Documents/Digital Notes/writecycle.png)

Write Cycle timing is particularly important – any timing error here could result in corrupting the contents store in RAM.

1. The write pulse is signified by CE and WR both being asserted (i.e. TRUE). There is usually a minimum period specified – here 10ns. Also as soon as the WR is asserted, WR = 1 and D7:0 must go high-impedance within 2ns (i.e. memory no longer driving the data bus).
2. The address A12:0 must be stable at least 2ns before the write pulse, and it must hold for another 2ns after the write pulse.
3. The data is written to memory on the falling edge of the write pulse. The setup and hold time is 4ns and 1ns respectively.
4. This is when the Write Cycle finishes, and we go back to Read Cycle. Expect D7:0 stays high impedance for at least 2ns.

### Microprocessor Timing

Assuming that the falling edge of MCLOCK starts a memory transaction cycle. Gates are assumed to have a 1ns delay. Therefore WR and OE signals are delayed by 1ns. A15:0 is assumed to hold its previous value for at least Ans, but will go to the new vale by Bns. The same is true with the WRITE signal.

####Microprocessor Read Setup Timing

The three timing inequalities are:

1. **Address to Data setup time** – RAM must provide the data to the micro early enough for the micro to read it properly. If the setup time of the data input to micro is 4ns, the address access time of the RAM is 8ns, and the address is only stable 8ns after the falling edge of MCLOCK, then we obtain the left side of the inequality.
2. **WRITE to Data setup time** – We need to check the WRITE signal to data setup. If the WRITE signal goes low (indicating a read cycle) at 8ns and the worst case path is to OE is through two gates, this adds another 2ns delay. Then if RAM access time from OE is 4ns and the data setup time is 4ns. The total of this must be less than or equal to 20ns.
3. **MCLOCK to Data setup time** – MCLOCK also controls OE and WR, so we need to check that it does not violate any timing requirement. If MCLOCK goes high at 10ns, and there is a 1ns delay with the AND gate, adding the 4ns OE setup time and 4ns micro data setup time, the total must be earlier than 20ns.

From these inequalities, it can be determined whether the timing constraints for the read setup time are satisfied.

####Microprocessor Read Hold Timing

The minimum hold time can be found by summung, the MCLOCK falling edge time, the gate delays, and the microprocessor hold timing.

This must hold for longer than the OE to tristate delay summed with the MCLOCK falling edge time.

####Microprocessor Write to Memory Timing

![ritetome](/home/josh/Documents/Digital Notes/writetomem.png)

There are 4 separate timing specifications to consider:

1. Address to WR setup time – this timing constraint is imposed by RAM that address must be stable (set up time) 2ns before WR pulse goes high. Since the WR pulse goes high at 11ns (relative to falling edge of MCLOCK which is the reference 0ns), and that the address A12:0 are stable no later than 8ns, the constraint is satisfied.
2. Data to !WR setup time – writing to memory occurs on the falling edge of WR. Data must be stable 4ns before that. WR goes low at 21ns. Data is stable at 12ns or earlier. Therefore this constraint is also satisfied.
3. WR pulse width – this must be at least 10ns. Since the write pulse starts at 11ns and finishes at 21ns, the minimum WR pulse width is just met (with no margin).
4. Address hold time – The address must be held 2ns after WR signal is deasserted. Therefore this hold time is also just met (with no margin).
5. Data hold time – Data is held for 1ns. Therefore data hold time is also met.



## FPGA Embedded Memory

Microprocessors contain register files. Register files are the simplest forms of storage. These are the registers of microprocessors.

On the FPGA, register files are often implemented with the D-flipflops in the Adaptive Logic Modules (ALMs). Each ALM has two D flip flops. Therefore a 32-bit register will take up 16 ALMs. Alternatively one could also use the static memory blocks for this purpose.

The inportant parts of a register file are:

- **regid** - Register identifier, the address of a word in memory.
- **sizeof(regid)** - This is $log_2{(\# \; of \; reg)}$.
- **WE** - Write enable.

The circuit of a register file consists of arrays of D flipflops, which can be disable (and output becomes high impedance). The register select signals sel_reg0, sel_reg1 etc. enable the correct register to put the data on the data line. The read/write control signal WE is used to determine if you are reading or writing to the register.

The register identification (regid) determines which register you are trying to access. This is achieved through a decoder, which generates a onehot code word to select the appropriate register to access.



### FIFOs

Internally there typically two counters, one keeping track of the read address (or read pointer) and another counter keeping track of the write address (write pointer). There needs to be status signals such as FULL, which is asserted if the FIFO is completely filled and writing any more words to it will destroy stored data, or EMPTY, which signifies that there are no data left to read.



## Adders and DSP blocks

### Full Adder

The building block for an n-bit adder is a one-bit full adder. This is essentially a component that adds THREE one-bit values together: P Q and CI. It produces two outputs: Sum S, and Carry C.

The output is a 2-bit number counting how many inputs are high.

|  P   |  Q   |  CI  |  C   |  S   |
| :--: | :--: | :--: | :--: | :--: |
|  0   |  0   |  0   |  0   |  0   |
|  0   |  0   |  1   |  0   |  1   |
|  0   |  1   |  0   |  0   |  1   |
|  0   |  1   |  1   |  1   |  0   |
|  1   |  0   |  0   |  0   |  1   |
|  1   |  0   |  1   |  1   |  0   |
|  1   |  1   |  0   |  1   |  0   |
|  1   |  1   |  1   |  1   |  1   |

###N-bit adders

An N-bit adder can be made by cascading full adder sections.

The advantage of using 2s complement for signed numbers is shown by this circuit; it allows signed and unsigned numbers to use identical circuitry for identical circuits for addition and subtraction.

The output of an N-bit adder can be:

- **Unsigned:** $0 \le x \le 2(2^N-1)$.
- **Signed**: $-2^N \le x \le 2(2^{(N-1)-1})$

If you are adding two N-bit numbers together you should use an (N+1)-bit adder to avoid overflow issues. This causes issues for signed addition and subtraction.

###Expanding and Shrinking Binary Numbers

#### Expanding Binary Numbers

For unsigned numbers, exampling a 4-bit number to an 8-bit number simply requires adding 4 extra ‘0’ to the MSB part of the number.

For signed numbers, the left most digit of the number must be added 4 times to the MSB of the number to make a 4 bit number into an 8 bit number.
$$
5 \Rightarrow \mathbf{0}101 \Rightarrow \mathbf{0000}0101
$$

$$
-3 \Rightarrow \mathbf{1}101 \Rightarrow \mathbf{1111}1101
$$

####Shrinking Binary Numbers

To shrink a binary number to smaller number of bits, it is easy for unsigned numbers – simply delete all leading ‘0’s for MSB. The value of the unsigned number will not change.

For signed numbers, if the MSB is 0, you can delete all ‘0’ from MSB down except the last ‘0’. If the MSB is ‘1’, you can delete all ‘1’s from MSB down except the last ‘1’. In that way, you preserve the correct sign of the number.

Numbers can also be trncated. This involved cutting off the LSBs you don't want.

Rounding is harder, and there are various method of rounding that can be used. The simplest method in the case of 8-bit rounded to 4-bits is to add $8’b00001000$ to the number, than truncate the bottom 4-bit. Basically, you add half of the LSB of the final number to the original number before chopping off the lower bits. This is the same as how we round with decimal numbers.

### Adder Propagation Delay

When considering the propagation delay through a 4-bit adder. 

The worst case path is from P0 or Q0 input, then passing through the carry chain to the MSB sum output. Assuming the gate delay to C is 2 and to S is 3, then the worst case delay is 9. 

This is called a ripple carry adder because the carry signal has to propagate all the way from the LSB stage to the MSB stage. 

An example scenario for the worst case propagation delay is shown here. If initially $P=4’b0000$ and $Q=4’b1111$, the $S=5’b10000$. Now if $P$ changes to $4’b0001$, then this ‘1’ in the LSB is propagated all the way to $S4$. The worst-case path is exercised.

The delays are data-dependent.

To determine the delay of a circuit, three things **MUST** be specified:

- The circuit.
- The initial value of all the inputs.
- Which of the inputs change.

After these are specified, the input can be changed, and the effect on the gates can be seen and calculated.

#### Worst Case Delays

The worst case delay is what determines the maximum clock speed of a synchronous circuit.

Since the clock speed must be chosen to ensure that the circuit always works, it is only the worst case logic delay that maters.
$$
\text{Max Clock Frequency} = \frac{1}{\text{Worst Case Delay}}
$$


###Adaptive Logic Modules

The Altera Cyclone V FPGA uses Adaptive Logic Modules or ALMs instead of 4-input LUTs.

An ALM can take up to 8 Boolean input signals and produces four outputs with or without a register. Additionally, each ALM also can perform the function of a 2-bit binary full adder.

#### ALM Arithmetic Mode

The ALM in arithmetic mode uses two sets of two 4-inputs and two dedicated 1-bit full adders.

The full adder can add the output of the two 4-input LUTs (which can also do other logic functions).

There is also a dedicated carry chain that allows for fast ripple carrying. 

The adders add delays of only 57ps and the clock to Q delay + setup time is 1.8ns.

### DSP Blocks

The DSP blocks on the Cyclone V can be used for a combination of different functions. It can do multiplication of different precision and also to perform multiply-accumulate function.

Each DSP block can be configured as three 9 x 9 multipliers. This is particularly useful for real-time video processing since each pixel values are often represented as an 8-bit unsigned value (or 3 x 8 bit unsigned number if we are using colour). 

Alternatively, each block can provide TWO 18 x 18 bit, or one 27 x27 bit multiplier(s). Of course if you need lower number of bits (say 14 x 14), you can always either zero-extend, or sign-extend the operands to fit and use the 18 x 18 multiplier. 

Each multiplier can also be configured to operate with the adder or the accumulator at the output. 

It is important to understand that when you multiply two N x M bits unsigned numbers together, you get a product which is N+M bits. The same also applies if you multiply one signed and one unsigned number together.

However, if you multiply two signed 2’s complement numbers together, you get a product that is only N+M-1 bits. The top two-bits are always the same and they both provide the sign of the product value (i.e. you get two identical sign bits in the product).

###Specifying Adders

Given that the FPGA has special adder mode, you should never specify your adder as individual full adder circuits connected together. The synthesis system WILL NOT be able to exploit the dedicated adder mode configuration.

Instead use the `+` operator in Verilog as shown here. It is simpler and will produce a very fast adder.

```verilog
//What you SHOULD NOT do
module full_adder(a ,b ,cin ,s , cout)
    input a, b cin;
    output s, cout;
    
    assign s =  a^b^cin;
    assign cout = a&b | cin&(a^b);
endmodule
```

```verilog
//What you SHOULD do
module add32v (a, b ,sum , clk)
    parameter SIZE=32;
    
    input [SIZE-1:0] a,b;
    input clk;
    output [SIZE-1:0] sum;
    
    reg [SIZE-1:0] reg_a, reg_b;
    reg [SIZE-1:0] sum;
    
    always @ (posedge clk)
        begin
            reg_a <= a;
            reg_b <= b;
            sum <= reg_a + reg_b;
        end
endmodule
```

