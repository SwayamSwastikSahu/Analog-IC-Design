# Summer Internship Report

## MOSFET based Analog Integrated Circuits and Folded Cascode Amplifier

**By**

**Swayam Swastik Sahu**

**Under the Supervision of**

**Prof. Sougata Kumar Kar**

**Department of Electronics and Communication Engineering**

**National Institute of Technology, Rourkela**

**June, 2025**

## Acknowledgement

I would like to express my deepest gratitude to everyone who contributed to the successful completion of this project.

First and foremost, I would like to thank my supervisor, Prof. Sougata Kumar Kar, for his invaluable guidance, continuous support, and encouragement throughout the course of this project. His expertise and insightful feedback were instrumental in shaping the direction and execution of this work.

I would also like to extend my sincere thanks to the National Institute of Technology, Rourkela, for providing the necessary resources, software, and facilities essential for carrying out this project. The access to state-of-the-art technology and a conducive research environment greatly contributed to its success.

Thank you all.

Swayam Swastik Sahu

## Abstract

This report presents the design, analysis, and understanding of various analog integrated circuits. The technology library used is UMC_18_CMOS, based on 180nm CMOS technology. All circuit designs, simulations, and evaluations were carried out using Cadence Virtuoso.

During the internship, the theoretical concepts of different analog circuits were thoroughly studied. For each circuit, certain specifications were provided. Based on these specifications, relevant theoretical equations and concepts were applied to calculate the necessary transistor sizing (W/L ratios) and bias voltages.

Following the calculations, each circuit was implemented using the Cadence Virtuoso Schematic Editor. A variety of simulations—such as DC, AC, and transient analyses—were performed to evaluate the circuit’s performance and compare the results with the initial design specifications.

In cases where simulated results deviated from the target specifications, a tuning process was carried out. This involved modifying certain circuit parameters based on theoretical insights, observed waveforms, and target specifications. The goal of this tuning process was to minimize the gap between simulated and specified values.

Overall, this internship provided valuable hands-on experience with the complete analog IC design flow—from specification and calculation to schematic entry, simulation, and performance tuning.

## Contents

1. **CMOS Inverter Design and MOSFET Characterization**
   - 1.1 Design and Analysis of CMOS Inverter
   - 1.2 Oxide Thickness Calculation
   - 1.3 MOSFET Drain and Transfer Characteristics Analysis and Parameter Extraction
2. **Single-Stage Amplifiers**
   - 2.1 Common Source Amplifier with Resistive Load
   - 2.2 Common Source Amplifier with Ideal Current Source Load
   - 2.3 Common Source Amplifier with Diode-Connected Load
   - 2.4 Common Source Amplifier with Active Current Source Load
   - 2.5 Common Drain Amplifier with Resistive Load
   - 2.6 Common Drain Amplifier with Ideal Current Source Load
   - 2.7 Common Drain Amplifier with Diode-Connected Load
   - 2.8 Common Drain Amplifier with Active Current Source Load
   - 2.9 Common Gate Amplifier with Resistive Load
3. **MOSFET Current Mirrors and Current References**
   - 3.1 Simple Current Mirror
   - 3.2 Cascode Current Mirror
   - 3.3 Wilson Current Mirror
   - 3.4 High Swing Current Mirror
   - 3.5 Improved High Swing Current Mirror
   - 3.6 Simple Current Reference
   - 3.7 Threshold Current Reference
4. **Bandgap References**
   - 4.1 Resistive Bandgap Voltage Reference
   - 4.2 Voltage Reference Circuit Using Current Mirror
   - 4.3 Voltage Reference Circuit Using OPAMP and PMOS
   - 4.4 IZTC Reference Circuit
5. **Differential Amplifiers**
   - 5.1 Differential Amplifier with Resistive Load and Ideal Tail Current Source
   - 5.2 Differential Amplifier with Resistive Load and Current-Mirrored Tail Current Source
   - 5.3 Differential Amplifier with Diode-Connected Load
   - 5.4 Differential Amplifier with Active Current Source Load
   - 5.5 Differential Amplifier with Single-Ended Output
6. **Two-Stage Op-Amp and Folded Cascode Amplifier**
   - 6.1 Two-Stage Operational Amplifier in Open-Loop Configuration
   - 6.2 Inverting Op-Amp
   - 6.3 Non-Inverting Op-Amp
   - 6.4 Differential Op-Amp
   - 6.5 Instrumentation Amplifier
   - 6.6 Folded Cascode Amplifier

## Chapter 1: CMOS Inverter Design and MOSFET Characterization

### 1.1 Design and Analysis of CMOS Inverter

Complementary-Metal-Oxide-Semiconductor (CMOS) is a type of MOSFET fabrication process that employs complementary and symmetrical pairs of p-type and n-type MOSFETs for implementing logic functions. CMOS technology is widely used in the construction of integrated circuit (IC) chips, including microprocessors, microcontrollers, memory units, and other digital logic circuits.

A CMOS inverter is a fundamental device used to generate logic functions and is considered a core component in all integrated circuits. Structurally, a CMOS inverter consists of field-effect transistors (FETs), with a metal gate placed on top of an insulating layer of oxide, which in turn is laid over a semiconductor substrate. These inverters are employed in most electronic systems and play a key role in generating logic levels in small-scale circuits.

An interesting observation made during the study of MOSFET characteristics is that neither NMOS nor PMOS alone is sufficient to produce both logic levels, HIGH and LOW, efficiently. However, they exhibit complementary behavior—where one is strong in pulling the output HIGH and the other is strong in pulling it LOW. This complementary nature led to the idea of combining them. Since a PMOS transistor is efficient at passing a logical '1' (strong 1), it is placed between VDD and the output Vout. Conversely, the NMOS transistor, being efficient at passing a logical '0' (strong 0), is placed between Vout and ground. With this configuration, only one of the transistors conducts at a time, ensuring minimal static power consumption. This arrangement, where the two transistors complement each other to form a reliable switching logic, is known as the CMOS configuration. The simplest implementation of this concept is the CMOS inverter.

![Circuit diagram of CMOS inverter](./media/image2.png)
*Figure: 1.1 Circuit diagram of CMOS inverter*

![Symbolic view of CMOS inverter](./media/image3.png)
*Figure: 1.2 Symbolic view of CMOS inverter*

![Transient analysis of CMOS inverter](./media/image4.png)
*Figure: 1.3 Transient analysis of CMOS inverter*

![Layout of CMOS inverter](./media/image5.png)
*Figure: 1.4 Layout of CMOS inverter*

![Post layout VS pre layout simulation of CMOS inverter](./media/image6.png)
*Figure: 1.5 Post layout VS pre layout simulation of CMOS inverter*

### 1.2 Oxide Thickness Calculation

In MOS, because of its structure, it behaves like a capacitor. In MOS, the Cox is defined as the oxide capacitance per unit area, and its equation is: Cox = εox / tox, εox = ε0 * εSiO2, where tox is the thickness of SiO2 (oxide).

The total oxide capacitance of the entire MOS device is: Ctotal = Cox * W * L, where W = width of the MOS device and L = length of the channel.

Here, in this case, it is also equal to gate capacitance as there is no opposite diffusion region. But in a MOSFET, oxide capacitance and total gate capacitance are different because of opposite diffusion and the depletion region between opposite types of semiconductor.

Here, a simple RC circuit is designed where C is the capacitance of MOS. The NMOS transistor’s source and drain are grounded to use it as a MOS capacitor. A capacitor requires 2.2 * R * C time to charge from 10% to 90% of its supply voltage. So, by doing a transient analysis, the rise time is calculated. From there, using a mathematical equation, the tox is calculated.

![Circuit diagram for calculation of tox](./media/image7.png)
*Figure: 1.6 Circuit diagram for calculation of tox*

![Transient response of the above circuit](./media/image8.png)
*Figure: 1.7 Transient response of the above circuit*

Calculated tox is 4.09nm.

![Device parameters of NMOS transistor](./media/image9.png)
*Figure: 1.8 Device parameters of NMOS transistor*

### 1.3 MOSFET Drain and Transfer Characteristics Analysis and Parameter Extraction

#### Drain Characteristics of MOSFET

The drain characteristics of a MOSFET describe the relationship between the drain current (Id) and the drain-to-source voltage (Vds) for various gate-to-source voltages (Vgs). These characteristics are essential for understanding the different regions of MOSFET operation and are fundamental in analog circuit design.

For an n-channel enhancement-mode MOSFET, the operation can be divided into three regions:

1. **Cut-Off Region (Vgs < Vth)**: No conductive channel is formed as the gate voltage is below the threshold voltage. The MOSFET remains OFF, and the drain current (Id) is essentially zero.
2. **Triode or Linear Region (Vds < Vgs - Vth)**: A conductive channel forms between the drain and source. The MOSFET behaves like a voltage-controlled resistor. The current increases linearly with Vds and is given approximately by: Id = k [(Vgs - Vth)Vds - (1/2)Vds²]. This region is typically used when the MOSFET is acting as a switch or resistor.
3. **Saturation Region (Vds ≥ Vgs - Vth)**: The channel near the drain is pinched off, and the drain current saturates. It becomes independent of Vds and is given by: Id = (1/2)k (Vgs - Vth)². This region is widely used in amplification.

Where:
- k = μn·Cox·(W/L) is the process transconductance parameter,
- Vth is the threshold voltage.

The Id vs. Vds curve for different values of Vgs clearly demonstrates the transition between these operating regions, with the saturation region showing constant current beyond a particular Vds value (pinch-off condition).

![Drain Characteristics of MOSFET](./media/image10.png)
*Figure: 1.9 Drain Characteristics of MOSFET*

#### Transfer Characteristics of MOSFET

The transfer characteristics of a MOSFET illustrate the relationship between the drain current (Id) and the gate-to-source voltage (Vgs) for a fixed drain-to-source voltage (Vds), typically in the saturation region.

For an n-channel enhancement-mode MOSFET:
- When Vgs < Vth: No channel is formed, so Id = 0 and the MOSFET remains OFF.
- When Vgs ≥ Vth: An inversion layer forms a channel, and Id increases quadratically with Vgs: Id = (1/2)k (Vgs - Vth)².

The resulting plot is a parabolic curve beginning at Vgs = Vth. The slope of the curve, known as the transconductance (gm), indicates how effectively the gate voltage controls the drain current.

![Transfer Characteristics of MOSFET](./media/image11.png)
*Figure: 1.10 Transfer Characteristics of MOSFET*

#### μn Cox Calculation

Simply, for a known value of Vgs, Vds, and W/L, the transistor is simulated, and from that, Vth is extracted. Using the saturation region current equation, the μn Cox is calculated. Here μn Cox = 0.259 mA/V².

## Chapter 2: Single-Stage Amplifiers

### Common Source Amplifier

A common source (CS) amplifier is a widely used MOSFET-based amplifier configuration that offers high voltage gain and inverted output. In this topology, the source terminal is common to both the input and output. The input signal is applied at the gate, and the output is taken from the drain.

**Operation:**
- When the input voltage (Vgs) increases, the drain current (Id) increases.
- This increase in Id causes a larger voltage drop across the drain resistor (RD), reducing the drain voltage (Vout).
- As a result, the output signal is inverted with respect to the input (180° phase shift).

The input impedance of a CS amplifier is very high, as the gate terminal is isolated due to the SiO₂ layer. However, it also depends on the type of circuit—that is, where the resistors are connected for biasing the transistor. Output impedance also depends on the type of circuit connections. The voltage gain of a CS amplifier is quite good, but it also depends on the type of circuit. In all three cases, we cannot guarantee a perfect property, but using the CS configuration, if we design a circuit correctly, then we can get high input impedance, high gain, and high output impedance. This high output impedance plays a crucial role in achieving high gain.

#### 2.1 Common Source Amplifier with Resistive Load

A Common Source (CS) amplifier with a resistive load is one of the most basic amplifier configurations. But here the gain depends on the RD, so by increasing the RD we can increase the gain. But the problem is, we cannot increase the RD beyond a certain point as it is also used for biasing and placing the Q-point at the proper location. Increasing the RD beyond a limit results in the transistor possibly coming out of saturation.

![Circuit diagram of common source amplifier with resistive load](./media/image12.jpeg)
*Figure: 2.1 Circuit diagram of common source amplifier with resistive load*

![Transient response of Common source amplifier with resistive load](./media/image13.jpeg)
*Figure: 2.2 Transient response of Common source amplifier with resistive load*

![DC response common source amplifier with resistive load](./media/image14.jpeg)
*Figure: 2.3 DC response common source amplifier with resistive load*

![AC response common source amplifier with resistive load](./media/image15.jpeg)
*Figure: 2.4 AC response common source amplifier with resistive load*

#### 2.2 Common Source Amplifier with Ideal Current Source Load

Here a constant current source is used as a load. This ideal current source has infinite output resistance. Good thing is, here with a constant current source, not only we get a high gain but also better bias point control, since current is set independently. But practically, achieving such high output impedance current source is very complex. So instead of this, active loads like transistors are used as a load.

![Circuit diagram of common source amplifier with Ideal current source load](./media/image16.jpeg)
*Figure: 2.5 Circuit diagram of common source amplifier with Ideal current source load*

![DC Response of common source amplifier with Ideal current source load](./media/image17.jpeg)
*Figure: 2.6 DC Response of common source amplifier with Ideal current source load*

![AC response of common source amplifier with Ideal current source load](./media/image18.jpeg)
*Figure: 2.7 AC response of common source amplifier with Ideal current source load*

![Transient response of common source amplifier with Ideal current source load](./media/image19.png)
*Figure: 2.8 Transient response of common source amplifier with Ideal current source load*

#### 2.3 Common Source Amplifier with Diode-Connected Load

Here a diode-connected NMOS transistor is used as a load. In diode-connected, the gate and drain are shorted. So diode-connected transistor always remains in saturation. But its output impedance is low. Here the overall voltage gain is also low as compared to constant (ideal) current source load. But this diode-connected circuit is easy to design and deciding W/L, and it has better bias point control, since current is set independently from input transistor point.

![Circuit diagram of common source amplifier with diode-connected load](./media/image20.jpeg)
*Figure: 2.9 Circuit diagram of common source amplifier with diode-connected load*

![AC response of common source amplifier with diode-connected load](./media/image21.jpeg)
*Figure: 2.10 AC response of common source amplifier with diode-connected load*

![Transient response of common source amplifier with diode-connected load](./media/image22.png)
*Figure: 2.11 Transient response of common source amplifier with diode-connected load*

![DC response of common source amplifier with diode-connected load](./media/image23.png)
*Figure: 2.12 DC response of common source amplifier with diode-connected load*

#### 2.4 Common Source Amplifier with Active Current Source Load

Here, a PMOS transistor is used as a load. The output is taken at the drain terminal, which is common to both the NMOS and PMOS transistors. At this drain node, the voltage fluctuation is very high. However, since both transistors operate in the saturation region, their drain voltage does not play a significant role in determining the drain current (Id). Therefore, a PMOS is used as a load instead of an NMOS in the NMOS CS configuration. This configuration provides very high voltage gain, high output impedance, and high input impedance.

![Circuit diagram of common source amplifier with active current source load](./media/image24.jpeg)
*Figure: 2.13 Circuit diagram of common source amplifier with active current source load*

![DC response of common source amplifier with active current source load](./media/image25.jpeg)
*Figure: 2.14 DC response of common source amplifier with active current source load*

![AC response of common source amplifier with active current source load](./media/image26.jpeg)
*Figure: 2.15 AC response of common source amplifier with active current source load*

![Transient response of common source amplifier with active current source load](./media/image27.png)
*Figure: 2.16 Transient response of common source amplifier with active current source load*

### Common Drain Amplifier (Source Follower)

In the Common Drain Amplifier configuration, the drain terminal is at AC ground. The input is applied between the gate and drain terminals, while the output is measured between the source and drain terminal. Since the drain terminal is common between the input and output side, it is known as Common Drain Amplifier.

The Common Drain Amplifier has high input impedance, low output impedance, and sub-unity voltage gain. However, these properties still depend on the type of circuit design. If the circuit is designed correctly, then these characteristics can be achieved.

Because of its low output impedance, it is used as a buffer for driving the low output impedance load. Often in multistage amplifiers, while driving low impedance load, the source follower is used as an output stage.

**Operation**

In a Common Drain Amplifier, the input signal is applied at the gate terminal, and the output is taken from the source terminal, while the drain is connected to a constant supply voltage (VDD). When a small input signal is applied, the gate voltage increases, which enhances the channel conductivity of the MOSFET, allowing current to flow from drain to source.

As the current increases, the source voltage rises, reducing the gate-to-source voltage (VGS), which in turn controls the drain current (ID). This feedback mechanism stabilizes the operation and ensures that the source voltage closely follows the input voltage, minus the threshold voltage drop (VGS ≈ constant).

#### 2.5 Common Drain Amplifier with Resistive Load

A Common Drain amplifier with a resistive load is one of the most basic amplifier configurations. But here the gain depends on the RS, so by increasing the RS we can increase the gain (very near to 1). But the problem is, we cannot increase the RS beyond a certain point as it is also used for biasing and placing the Q-point at the proper location. Increasing the RS beyond a limit results in the transistor possibly coming out of saturation.

![Circuit diagram of common drain amplifier with resistive Load](./media/image28.png)
*Figure: 2.17 Circuit diagram of common drain amplifier with resistive Load*

![DC response of common drain amplifier with resistive Load](./media/image29.png)
*Figure: 2.18 DC response of common drain amplifier with resistive Load*

![Transient response of common drain amplifier with resistive Load](./media/image30.png)
*Figure: 2.19 Transient response of common drain amplifier with resistive Load*

![AC response of common drain amplifier with resistive Load](./media/image31.png)
*Figure: 2.20 AC response of common drain amplifier with resistive Load*

![AC gain and phase of common drain amplifier with resistive Load](./media/image32.png)
*Figure: 2.21 AC gain and phase of common drain amplifier with resistive Load*

#### 2.6 Common Drain Amplifier with Ideal Current Source Load

Here a constant current source is used as a load. This ideal current source has infinite output resistance. Good thing is, here with a constant current source, not only we get a nearly unity gain but also better bias point control, since current is set independently. But practically, achieving such high output impedance current source is very complex. So instead of this, active loads like transistors are used as a load.

![Circuit diagram of common drain amplifier with Ideal current source load](./media/image33.png)
*Figure: 2.22 Circuit diagram of common drain amplifier with Ideal current source load*

![DC response of common drain amplifier with Ideal current source load](./media/image34.png)
*Figure: 2.23 DC response of common drain amplifier with Ideal current source load*

![Transient response of common drain amplifier with Ideal current source load](./media/image35.png)
*Figure: 2.24 Transient response of common drain amplifier with Ideal current source load*

![AC response of common drain amplifier with Ideal current source load](./media/image36.png)
*Figure: 2.25 AC response of common drain amplifier with Ideal current source load*

![AC gain and phase of common drain amplifier with Ideal current source load](./media/image37.png)
*Figure: 2.26 AC gain and phase of common drain amplifier with Ideal current source load*

#### 2.7 Common Drain Amplifier with Diode-Connected Load

Here a diode-connected NMOS transistor is used as a load. In diode-connected, the gate and drain are shorted. So diode-connected transistor always remains in saturation. But its output impedance is low. Here the overall voltage gain (unity) is also low. But this diode-connected circuit is easy to design and deciding W/L, and it has better bias point control, since current is set independently from input transistor point.

![Circuit diagram of common drain amplifier with diode-connected load](./media/image38.png)
*Figure: 2.27 Circuit diagram of common drain amplifier with diode-connected load*

![DC response of common drain amplifier with diode-connected load](./media/image39.png)
*Figure: 2.28 DC response of common drain amplifier with diode-connected load*

![Transient response of common drain amplifier with diode-connected load](./media/image40.png)
*Figure: 2.29 Transient response of common drain amplifier with diode-connected load*

![AC response of common drain amplifier with diode-connected load](./media/image41.png)
*Figure: 2.30 AC response of common drain amplifier with diode-connected load*

![AC gain and phase of common drain amplifier with diode-connected load](./media/image42.png)
*Figure: 2.31 AC gain and phase of common drain amplifier with diode-connected load*

#### 2.8 Common Drain Amplifier with Active Current Source Load

Here, an NMOS transistor is used as a load. The active current source provides a constant current and offers a very high output impedance, which improves the amplifier's linearity and performance and gives nearly unity gain.

![Circuit diagram of common drain amplifier with active current source load](./media/image43.png)
*Figure: 2.32 Circuit diagram of common drain amplifier with active current source load*

![DC response of common drain amplifier with active current source load](./media/image44.png)
*Figure: 2.33 DC response of common drain amplifier with active current source load*

![Transient response of common drain amplifier with active current source load](./media/image45.png)
*Figure: 2.34 Transient response of common drain amplifier with active current source load*

![AC response of common drain amplifier with active current source load](./media/image46.png)
*Figure: 2.35 AC response of common drain amplifier with active current source load*

![AC gain and phase of common drain amplifier with active current source load](./media/image47.png)
*Figure: 2.36 AC gain and phase of common drain amplifier with active current source load*

### Common Gate Amplifier

In the Common Gate amplifier, the input and output are in phase. (The voltage gain is positive). The input impedance of the CG amplifier is very low. And typically it is used in high-frequency applications as an amplifier for impedance matching. It has low input impedance, high output impedance, and moderate to high voltage gain. These characteristics also depend on the circuit connection. With a proper circuit design, we can achieve these characteristics.

#### 2.9 Common Gate Amplifier with Resistive Load

A Common Gate amplifier with a resistive load is one of the most basic amplifier configurations. But here the gain depends on the Resistive Load, so by increasing it we can increase the gain. But the problem is, we cannot increase the Resistive Load beyond a certain point as it is also used for biasing and placing the Q-point at the proper location. Increasing the Resistive Load beyond a limit results in the transistor possibly coming out of saturation.

![Circuit diagram of common gate amplifier with resistive load](./media/image48.jpeg)
*Figure: 2.37 Circuit diagram of common gate amplifier with resistive load*

![DC response of common gate amplifier with resistive load](./media/image49.jpeg)
*Figure: 2.38 DC response of common gate amplifier with resistive load*

![DC gain curve of common gate amplifier with resistive load](./media/image50.jpeg)
*Figure: 2.39 DC gain curve of common gate amplifier with resistive load*

![Transient response of common gate amplifier with resistive load](./media/image51.jpeg)
*Figure: 2.40 Transient response of common gate amplifier with resistive load*

![AC response of common gate amplifier with resistive load](./media/image52.jpeg)
*Figure: 2.41 AC response of common gate amplifier with resistive load*

## Chapter 3: MOSFET Current Mirrors and Current References

The current mirror is an analog circuit that senses the reference current and generates the copy or number of copies of the reference current, with the same characteristics. The replicated current is as stable as the reference current source.

The replicated current could be the same as the reference current (Icopy = Iref), or it could be either multiple or fraction of the reference current. (Icopy = N*Iref or Icopy = (1/N)*Iref). Current Mirrors are particularly useful in the integrated circuits, for biasing the amplifiers. In integrated circuits, one stable current source is fabricated within IC, and using the current mirror the multiple copies of the stable current source is generated (which can be used to bias the amplifiers).

### 3.1 Simple Current Mirror

It typically consists of two matched MOSFETs (usually NMOS or PMOS) with the gate and drain of one transistor (M1) connected together to form a diode-connected transistor, and this node is also connected to the gate of the second transistor (M2).

The reference current (I_REF) is applied to the diode-connected transistor (M1), which sets up a gate-to-source voltage (V_GS) common to both transistors. Since M2 has the same V_GS, and assuming both transistors are perfectly matched and operate in saturation, the output current (I_OUT) ≈ I_REF.

![Circuit diagram of simple current mirror](./media/image53.png)
*Figure: 3.1 Circuit diagram of simple current mirror*

![Id vs Vds of simple current mirror](./media/image54.png)
*Figure: 3.2 Id vs Vds of simple current mirror*

### 3.2 Cascode Current Mirror

The Cascode Current Mirror is an advanced version of the simple current mirror designed to improve output resistance and accuracy. Typically it uses four matched transistors arranged in a cascode configuration to reduce the effect of channel-length modulation and increase output impedance. It provides higher output impedance than a simple current mirror, good current matching and reduced channel-length modulation effects. This circuit also has a negative feedback mechanism which reduces the CLM and gives a constant drain voltage irrespective of Vds.

![Circuit diagram of cascode current mirror](./media/image55.png)
*Figure: 3.3 Circuit diagram of cascode current mirror*

![Id vs Vds of cascode current mirror](./media/image56.png)
*Figure: 3.4 Id vs Vds of cascode current mirror*

### 3.3 Wilson Current Mirror

The Wilson Current Mirror is an improved version of the basic current mirror that offers high output resistance and better current matching. It consists of three transistors, typically NMOS or PMOS, arranged in such a way that the feedback from the output controls the gate voltage of the mirroring transistor. In this configuration, one transistor is diode-connected to set the reference current, the second transistor mirrors the current, and the third transistor provides negative feedback by sensing the output current and adjusting the gate voltage accordingly. This feedback mechanism helps maintain a constant current despite changes in output voltage, effectively reducing the effect of channel-length modulation. As a result, the Wilson current mirror achieves better output impedance and accuracy than the simple current mirror, making it suitable for analog integrated circuits where precision current copying is essential.

![Circuit diagram of wilson current mirror](./media/image57.png)
*Figure: 3.5 Circuit diagram of wilson current mirror*

![Id vs Vds of wilson current mirror](./media/image58.png)
*Figure: 3.6 Id vs Vds of wilson current mirror*

### 3.4 High Swing Current Mirror

The High Swing Current Mirror is a modified version of the cascode current mirror designed to allow a larger output voltage swing while maintaining high output resistance. It overcomes the limitation of reduced output swing in traditional cascode mirrors by using an additional level-shifting transistor, which ensures that the output transistor remains in saturation even at lower output voltages. This design provides improved performance in low-voltage applications. Typically it requires one less Vth as compared to cascode current mirror.

![Circuit diagram of high swing current mirror](./media/image59.png)
*Figure: 3.7 Circuit diagram of high swing current mirror*

![Id vs Vds of high swing current mirror](./media/image60.png)
*Figure: 3.8 Id vs Vds of high swing current mirror*

### 3.5 Improved High Swing Current Mirror

The Improved High Swing Current Mirror further enhances the basic high swing current mirror by optimizing the circuit for even greater output voltage swing and better current matching. It typically includes additional transistors or biasing techniques to ensure that the output transistor stays in saturation over a wider range of output voltages. This design improves both the output resistance and voltage headroom, making it highly suitable for low-voltage and high-performance analog applications where precision and dynamic range are critical.

![Circuit diagram of improved high swing current mirror](./media/image61.png)
*Figure: 3.9 Circuit diagram of improved high swing current mirror*

![Id vs Vds of improved high swing current mirror](./media/image62.png)
*Figure: 3.10 Id vs Vds of improved high swing current mirror*

### Current References

#### 3.6 Simple Current Reference

This circuit is a simple MOSFET-based current reference designed using a pair of matched NMOS and PMOS transistors along with a resistor. The core idea is to establish a stable current that remains relatively constant despite variations in power supply. A resistor at the bottom of the circuit develops a voltage drop which sets the gate-to-source voltage of an NMOS transistor, thereby defining the reference current. This current is mirrored through a second NMOS transistor, which in turn controls a pair of PMOS transistors arranged as a current mirror at the top of the circuit. The PMOS mirror feeds back to the initial NMOS, creating a self-biased loop that stabilizes the entire operation. The resulting output current is a copy of the reference current set by the resistor, making this circuit useful for biasing analog blocks in integrated circuits.

![Circuit diagram of simple current reference](./media/image63.png)
*Figure: 3.11 Circuit diagram of simple current reference*

![DC response of simple current reference](./media/image64.png)
*Figure: 3.12 DC response of simple current reference*

![Iout vs temperature of simple current reference](./media/image65.png)
*Figure: 3.13 Iout vs temperature of simple current reference*

![Transient response of simple current reference](./media/image66.png)
*Figure: 3.14 Transient response of simple current reference*

#### 3.7 Threshold Current Reference

This circuit is a threshold voltage-based current reference that generates a stable current by utilizing the threshold voltage of a MOSFET and a resistor. The core idea is to bias a transistor in such a way that the voltage across the resistor is approximately equal to the threshold voltage of the transistor. This results in a reference current defined by the ratio of the threshold voltage to the resistance. The current is then mirrored through a set of matched transistors to replicate the same current at the output. The use of both NMOS and PMOS transistors ensures stability and provides a self-biased loop that maintains the reference current despite variations in supply voltage. This design is simple and power-efficient, making it suitable for use in analog and mixed-signal integrated circuits where a stable current source is needed.

![Circuit diagram of threshold current reference](./media/image67.png)
*Figure: 3.15 Circuit diagram of threshold current reference*

![DC response of threshold current reference](./media/image68.png)
*Figure: 3.16 DC response of threshold current reference*

![Iout vs temperature of threshold current reference](./media/image69.png)
*Figure: 3.17 Iout vs temperature of threshold current reference*

![Transient response of threshold current reference](./media/image70.png)
*Figure: 3.18 Transient response of threshold current reference*

## Chapter 4: Bandgap References

### 4.1 Resistive Bandgap Voltage Reference

This circuit implements a resistive bandgap voltage reference, which generates a stable output voltage that remains nearly constant over temperature variations. It uses two bipolar junction transistors with different emitter areas to create a voltage difference that increases with temperature. This difference, called delta V<sub>BE</sub>, is proportional to absolute temperature and is scaled using resistors. An operational amplifier forces this voltage to appear across another resistor, ensuring a controlled current flow through the transistors. The final output is obtained by summing a voltage that decreases with temperature (base-emitter voltage) and the scaled temperature-dependent voltage, resulting in a reference voltage that is largely temperature-independent. This design is commonly used in analog and mixed-signal integrated circuits for precise voltage referencing.

![Circuit diagram of resistive bandgap voltage reference](./media/image71.png)
*Figure: 4.1 Circuit diagram of resistive bandgap voltage reference*

![Vout vs temperature of resistive bandgap voltage reference](./media/image72.png)
*Figure: 4.2 Vout vs temperature of resistive bandgap voltage reference*

![Vout, Iout vs Vdd of resistive bandgap voltage reference](./media/image73.png)
*Figure: 4.3 Vout, Iout vs Vdd of resistive bandgap voltage reference*

![Transient response of resistive bandgap voltage reference](./media/image74.png)
*Figure: 4.4 Transient response of resistive bandgap voltage reference*

### 4.2 Voltage Reference Circuit Using Current Mirror

This voltage reference circuit utilizes the principle of current mirroring along with bipolar junction transistors to produce a stable reference voltage. It begins by generating a temperature-dependent voltage difference using two transistors with unequal emitter areas, producing a voltage known as ∆VBE, which increases with temperature. This voltage is dropped across a resistor to generate a current that is proportional to absolute temperature. A current mirror replicates this current to a separate branch, where it flows through another resistor to create a voltage drop. This output voltage serves as the reference voltage. By properly choosing resistor values, the temperature dependence of the current can be balanced to produce a voltage that is either temperature-independent or has a predictable temperature behavior, making it highly useful in analog and mixed-signal integrated circuits for reliable voltage referencing.

![Circuit diagram of voltage reference circuit using current mirror](./media/image75.png)
*Figure: 4.5 Circuit diagram of voltage reference circuit using current mirror*

![Vout vs temperature of voltage reference circuit using current mirror](./media/image76.png)
*Figure: 4.6 Vout vs temperature of voltage reference circuit using current mirror*

![Vout vs Vdd of voltage reference circuit using current mirror](./media/image77.png)
*Figure: 4.7 Vout vs Vdd of voltage reference circuit using current mirror*

![Transient response of voltage reference circuit using current mirror](./media/image78.png)
*Figure: 4.8 Transient response of voltage reference circuit using current mirror*

### 4.3 Voltage Reference Circuit Using OPAMP and PMOS

This voltage reference circuit utilizes an operational amplifier, PMOS transistors, and bipolar junction transistors to generate a stable and temperature-independent output voltage. The core idea is to create a current that is proportional to absolute temperature by using US two bipolar transistors with different emitter areas, resulting in a voltage difference that increases with temperature. This difference is converted to current using a resistor, and the operational amplifier ensures that this current is accurately mirrored into another branch using PMOS transistors. The mirrored current flows through a resistor where it combines with the base-emitter voltage of a transistor, which decreases with temperature. By carefully selecting resistor values, the increasing and decreasing temperature effects cancel each other, resulting in a fixed voltage reference at the output. This type of bandgap reference is essential in analog and digital circuits where a constant reference voltage is required regardless of temperature variations.

![Circuit diagram of voltage reference circuit using OPAMP and PMOS](./media/image79.png)
*Figure: 4.9 Circuit diagram of voltage reference circuit using OPAMP and PMOS*

![Vout VS temperature of voltage reference circuit using OPAMP and PMOS](./media/image80.png)
*Figure: 4.10 Vout VS temperature of voltage reference circuit using OPAMP and PMOS*

### 4.4 IZTC Reference Circuit

The IZTC (Intermediate Zero Temperature Coefficient) reference circuit is designed to produce a temperature-independent reference voltage by intelligently combining two opposing temperature-dependent components. It uses a pair of bipolar transistors to generate a voltage difference that increases with temperature, known as a PTAT (Proportional To Absolute Temperature) voltage. This PTAT voltage is converted into a current using a resistor and then mirrored to flow through another resistor, producing a corresponding PTAT voltage drop. Simultaneously, a base-emitter voltage from one of the bipolar transistors, which naturally decreases with temperature (CTAT behavior), is also present in the circuit. By carefully choosing resistor values and scaling the PTAT and CTAT contributions, the circuit balances these opposing effects at a specific temperature where their variations cancel out, resulting in a flat temperature response. An operational amplifier ensures that the proper bias conditions are met by forcing its inputs to the same voltage, stabilizing the operation. As a result, the output voltage remains stable over temperature, making the circuit highly useful in precision analog applications where thermal drift must be minimized.

![Circuit diagram of IZTC](./media/image81.png)
*Figure: 4.11 Circuit diagram of IZTC*

![IZTC, IPTAT, ICTAT, Vref vs temperature](./media/image82.png)
*Figure: 4.12 IZTC, IPTAT, ICTAT, Vref vs temperature*

## Chapter 5: Differential Amplifiers

A differential amplifier amplifies the difference between the two input signals. It is widely used in integrated circuits as an amplifier. The first stage of the op-amp is also a differential amplifier. In a MOS differential pair, two perfectly matched MOSFETs with identical characteristics are used. In the integrated circuits, it is possible to match the characteristics of the two MOSFETs to some extent.

**Advantages of Differential Amplifier**: The ideal differential amplifier eliminates the common-mode signal at the output and only amplifies the differential input. Using the differential amplifier it is possible to eliminate or reduce any noise or interference which is common to both input terminals. When multiple differential amplifier stages are cascaded together, then it also eliminates the use of coupling capacitors between each stage.

### 5.1 Differential Amplifier with Resistive Load and Ideal Tail Current Source

The differential amplifier with a resistive load and an ideal tail current source offers high common-mode rejection ratio (CMRR) and improved bias point stability. The ideal tail current source ensures a constant total current through the differential pair, enhancing symmetry and linearity. Resistive loads convert the differential current into output voltage, but they limit gain due to their relatively low output resistance.

![Circuit diagram of differential amplifier with resistive load and ideal tail current source](./media/image83.png)
*Figure: 5.1 Circuit diagram of differential amplifier with resistive load and ideal tail current source*

![DC response of differential amplifier with resistive load and ideal tail current source](./media/image84.png)
*Figure: 5.2 DC response of differential amplifier with resistive load and ideal tail current source*

![Transient response of differential amplifier with resistive load and ideal tail current source](./media/image85.png)
*Figure: 5.3 Transient response of differential amplifier with resistive load and ideal tail current source*

![AC response of differential amplifier with resistive load and ideal tail current source](./media/image86.png)
*Figure: 5.4 AC response of differential amplifier with resistive load and ideal tail current source*

### 5.2 Differential Amplifier with Resistive Load and Current-Mirrored Tail Current Source

In the differential amplifier with a resistive load and a current-mirrored tail current source, an active current source replaces the ideal tail source, allowing for better integration and bias control in practical circuits. However, the use of resistive loads still limits the voltage gain due to their lower output resistance. Additionally, increasing the resistive load to improve gain is constrained, as it directly affects the quiescent point (Q-point) of the circuit.

![Circuit diagram of differential amplifier with resistive load and current-mirrored tail current source](./media/image87.png)
*Figure: 5.5 Circuit diagram of differential amplifier with resistive load and current-mirrored tail current source*

![DC response of differential amplifier with resistive load and current-mirrored tail current source](./media/image88.png)
*Figure: 5.6 DC response of differential amplifier with resistive load and current-mirrored tail current source*

![Transient response of differential amplifier with resistive load and current-mirrored tail current source](./media/image89.png)
*Figure: 5.7 Transient response of differential amplifier with resistive load and current-mirrored tail current source*

![AC response of differential amplifier with resistive load and current-mirrored tail current source](./media/image90.png)
*Figure: 5.8 AC response of differential amplifier with resistive load and current-mirrored tail current source*

![Common mode AC response of differential amplifier with resistive load and current-mirrored tail current source](./media/image91.png)
*Figure: 5.9 Common mode AC response of differential amplifier with resistive load and current-mirrored tail current source*

### 5.3 Differential Amplifier with Diode-Connected Load

In the differential amplifier with diode-connected load, the output resistance is significantly reduced due to the low impedance of the diode-connected transistors, resulting in a lower voltage gain compared to other load configurations. However, this configuration simplifies biasing and enhances transistor matching, contributing to a more straightforward and reliable design.

![Circuit diagram of differential amplifier with diode-connected load](./media/image92.png)
*Figure: 5.10 Circuit diagram of differential amplifier with diode-connected load*

![DC response of differential amplifier with diode-connected load](./media/image93.png)
*Figure: 5.11 DC response of differential amplifier with diode-connected load*

![Transient response of differential amplifier with diode-connected load](./media/image94.png)
*Figure: 5.12 Transient response of differential amplifier with diode-connected load*

![AC response of differential amplifier with diode-connected load](./media/image95.png)
*Figure: 5.13 AC response of differential amplifier with diode-connected load*

![Common mode AC response of differential amplifier with diode-connected load](./media/image96.png)
*Figure: 5.14 Common mode AC response of differential amplifier with diode-connected load*

### 5.4 Differential Amplifier with Active Current Source Load

In the differential amplifier with an active current source load, the output resistance is significantly increased compared to resistive or diode-connected loads, resulting in a much higher voltage gain. While it enhances gain and performance, precise transistor matching and careful design are critical to ensure proper operation and symmetry between the differential branches.

![Circuit diagram of differential amplifier with active current source load](./media/image97.png)
*Figure: 5.15 Circuit diagram of differential amplifier with active current source load*

![DC response of differential amplifier with active current source load](./media/image98.png)
*Figure: 5.16 DC response of differential amplifier with active current source load*

![Transient response of differential amplifier with active current source load](./media/image99.png)
*Figure: 5.17 Transient response of differential amplifier with active current source load*

![AC response of differential amplifier with active current source load](./media/image100.png)
*Figure: 5.18 AC response of differential amplifier with active current source load*

### 5.5 Differential Amplifier with Single-Ended Output

In this differential amplifier, an active current source load is used, where one transistor is diode-connected and acts as a current mirror for the other load. With this mechanism, we can achieve almost the same gain with single-ended output as in a differential amplifier with differential output. The rest of the operation remains the same. However, if we use a normal differential amplifier and take a single-ended output directly without the current mirror load, the gain becomes half.

![Circuit diagram of differential amplifier with single ended output](./media/image101.png)
*Figure: 5.19 Circuit diagram of differential amplifier with single ended output*

![DC response of differential amplifier with single ended output](./media/image102.png)
*Figure: 5.20 DC response of differential amplifier with single ended output*

![Transient response of differential amplifier with single ended output](./media/image103.png)
*Figure: 5.21 Transient response of differential amplifier with single ended output*

![AC gain and phase of differential amplifier with single ended output](./media/image104.png)
*Figure: 5.22 AC gain and phase of differential amplifier with single ended output*

![ICMR of differential amplifier with single ended output](./media/image105.png)
*Figure: 5.23 ICMR of differential amplifier with single ended output*

![Common mode AC gain and phase of differential amplifier with single ended output](./media/image106.png)
*Figure: 5.24 Common mode AC gain and phase of differential amplifier with single ended output*

![Slew rate of differential amplifier with single ended output](./media/image107.png)
*Figure: 5.25 Slew rate of differential amplifier with single ended output*

## Chapter 6: Two-Stage Op-Amp and Folded Cascode Amplifier

### 6.1 Two-Stage Operational Amplifier in Open-Loop Configuration

Here the Two-Stage Operational Amplifier (Op-Amp) consists of a differential amplifier with single-ended output as the first stage and a PMOS common-source amplifier with NMOS active current source load as the second stage. The first stage provides high input impedance, good common-mode rejection, and gain, while the second stage offers additional voltage gain and good output swing. A compensation capacitor is typically added between the stages to improve frequency stability and ensure sufficient phase margin.

![Circuit diagram of two-Stage operational amplifier in open-loop configuration](./media/image108.png)
*Figure: 6.1 Circuit diagram of two-Stage operational amplifier in open-loop configuration*

**Table 6.1: Transistor W/L Ratios and Drain Currents**

| Sl. No. | Transistor | W/L   | Id       |
|---------|------------|-------|----------|
| 1       | M0         | 7.59  | 23.86µA |
| 2       | M1         | 7.59  | 23.86µA |
| 3       | M2         | 5.28  | 47.72µA |
| 4       | M3         | 36.79 | 347.2µA |
| 5       | M4         | 5.28  | 50µA    |
| 6       | M5         | 3.9   | 23.86µA |
| 7       | M6         | 3.9   | 23.86µA |
| 8       | M7         | 54.42 | 347.2µA |

![DC response of two-Stage operational amplifier in open-loop configuration](./media/image109.png)
*Figure: 6.2 DC response of two-Stage operational amplifier in open-loop configuration*

![Transient response of two-Stage operational amplifier in open-loop configuration](./media/image110.png)
*Figure: 6.3 Transient response of two-Stage operational amplifier in open-loop configuration*

![AC gain and phase of two-Stage operational amplifier in open-loop configuration](./media/image111.png)
*Figure: 6.4 AC gain and phase of two-Stage operational amplifier in open-loop configuration*

![Common mode AC gain and phase of two-Stage operational amplifier in open-loop configuration](./media/image112.png)
*Figure: 6.5 Common mode AC gain and phase of two-Stage operational amplifier in open-loop configuration*

![Slew rate of two-Stage operational amplifier in open-loop configuration](./media/image113.png)
*Figure: 6.6 Slew rate of two-Stage operational amplifier in open-loop configuration*

Op-Amp is a very high gain differential amplifier. So, in open loop configuration, even a small differential input (in micro volts) is applied between the two terminals of the Op-amp, then also the output will get saturated. And we cannot use it as an amplifier. Because in the amplifier the relation between the input and the output is linear. So, to control the gain of the op-amp and to use it as an amplifier, negative feedback is required in op-amp.

**Virtual Ground**: This concept is applicable during the negative feedback only. Because of a very high gain of Op-amp, the differential input voltage signal used to be very small and almost negligible. So, the voltage difference between the inverting and non-inverting input terminal will be approximately equal to zero. Or we can say that both the terminals are at the same potential. It means that there is a virtual short between the two terminals. So, if one terminal is at ground potential then another terminal will appear to be at ground potential (although physically it is not grounded). This concept is known as the virtual Ground Concept.

### 6.2 Inverting Op-Amp

In this configuration, the input is applied at the inverting end of the op-amp and the output voltage is 180 degrees out of phase with the input. That is why it is known as the Inverting Op-amp configuration. The input impedance of this configuration is decided by input resistors and feedback resistor.

![Circuit diagram of inverting Op-Amp](./media/image114.png)
*Figure: 6.7 Circuit diagram of inverting Op-Amp*

![Transient response of inverting Op-Amp](./media/image115.png)
*Figure: 6.8 Transient response of inverting Op-Amp*

![Gain value of inverting Op-Amp](./media/image116.png)
*Figure: 6.9 Gain value of inverting Op-Amp*

### 6.3 Non-Inverting Op-Amp

In non-inverting Op-Amp configuration, the input is applied at the non-inverting terminal of the op-amp and feedback is applied from the output to the inverting end of the op-amp. In this configuration, the input and output voltages are in phase with each other. The input impedance of this configuration is ideally infinite and practically it is very high.

Op-Amp can be used as a buffer in the non-inverting configuration. In this configuration, output voltage follows the input voltage. Or in another way, the gain of the Op-amp is one (Unity). That's why it is also known as a unity gain amplifier. The input impedance of this configuration is very high and that is why it can be used to isolate the different circuit stages.

![Circuit diagram of non-inverting Op-Amp](./media/image117.png)
*Figure: 6.10 Circuit diagram of non-inverting Op-Amp*

![Transient response of non-inverting Op-Amp](./media/image118.png)
*Figure: 6.11 Transient response of non-inverting Op-Amp*

![Gain value of non-inverting Op-Amp](./media/image119.png)
*Figure: 6.12 Gain value of non-inverting Op-Amp*

### 6.4 Differential Op-Amp

The differential amplifier is the op-amp configuration in which the difference between the inputs is amplified by some gain factor. An Op-amp itself is a differential amplifier in open loop configuration but it has very high open loop gain. So, we cannot use the op-amp as the differential amplifier in the true sense in the open-loop configuration. And we require some sort of feedback to use this op-amp as a differential amplifier in the true sense.

The only disadvantage of this differential amplifier is that its input impedance is relatively low and depends on the series resistance used with the inputs. And in some cases, it might affect the source voltage because of the loading effect.

The loading effect of the source can be avoided by using the buffer before applying the input voltages. And this method can be used for general purpose applications. For more sophisticated applications with sensors, an instrumentation amplifier is used instead of the differential amplifier.

![Circuit diagram of differential Op-Amp](./media/image120.png)
*Figure: 6.13 Circuit diagram of differential Op-Amp*

![Transient Response of differential Op-Amp](./media/image121.png)
*Figure: 6.14 Transient Response of differential Op-Amp*

![Gain value of differential Op-Amp](./media/image122.png)
*Figure: 6.15 Gain value of differential Op-Amp*

### 6.5 Instrumentation Amplifier

The instrumentation amplifier is one kind of differential amplifier which provides very high gain, high CMRR, and high input impedance and it is designed for very specific applications. It is used in certain industrial applications (to amplify the output of the transducers) and in test and measurement equipment. Because of its high CMRR and high input impedance, it is preferred in harsh environmental conditions where it is possible to have very large common mode noise or interference signals and very low input differential signals.

![Circuit diagram of instrumentation amplifier](./media/image123.png)
*Figure: 6.16 Circuit diagram of instrumentation amplifier*

![Transient response of instrumentation amplifier](./media/image124.png)
*Figure: 6.17 Transient response of instrumentation amplifier*

![Gain value of instrumentation amplifier](./media/image125.png)
*Figure: 6.18 Gain value of instrumentation amplifier*

### 6.6 Folded Cascode Amplifier

It removes the drawback of limited output swing. It eliminates the difficulty in shorting the input and output of the telescopic cascode op-amp. It does not stack the cascode transistor on top of the input device; instead, it uses two different current paths. It uses an NMOS-PMOS or PMOS-NMOS combination. The output and input can be shorted together. It provides a large output voltage swing.

![Circuit diagram of folded cascode amplifier](./media/image126.png)
*Figure: 6.19 Circuit diagram of folded cascode amplifier*

**Table 6.2: Transistor W/L Ratios and Drain Currents**

| Sl. No. | Transistor | W/L    | Id       |
|---------|------------|--------|----------|
| 1       | M0         | 555.5  | 50.5µA  |
| 2       | M1         | 555.5  | 50.5µA  |
| 3       | M2         | 555.5  | 50.5µA  |
| 4       | M3         | 555.5  | 50.5µA  |
| 5       | M4         | 2.4    | 50.5µA  |
| 6       | M5         | 7.29   | 95.63µA |
| 7       | M6         | 7.29   | 100µA   |
| 8       | M7         | 3.64   | 47.81µA |
| 9       | M8         | 3.64   | 47.81µA |
| 10      | M9         | 2.4    | 50.5µA  |
| 11      | M10        | 120.48 | 98.31µA |
| 12      | M11        | 120.48 | 98.31µA |
| 13      | M12        | 120.48 | 100µA   |

![DC response of folded cascode amplifier](./media/image127.png)
*Figure: 6.20 DC response of folded cascode amplifier*

![DC gain plot of folded cascode amplifier](./media/image128.png)
*Figure: 6.21 DC gain plot of folded cascode amplifier*

![AC gain and phase plot of folded cascode amplifier](./media/image129.png)
*Figure: 6.22 AC gain and phase plot of folded cascode amplifier*

![Transient response of folded cascode amplifier](./media/image130.png)
*Figure: 6.23 Transient response of folded cascode amplifier*

![Slew rate of folded cascode amplifier](./media/image131.png)
*Figure: 6.24 Slew rate of folded cascode amplifier*

![Common mode AC gain and phase plot of folded cascode amplifier](./media/image132.png)
*Figure: 6.25 Common mode AC gain and phase plot of folded cascode amplifier*
