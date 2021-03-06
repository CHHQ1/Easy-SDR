# Assembly guide for HF Upconverter (SMD) module

## PCB requirements
In the manufacture of the device, use the material of the FR-4 printed circuit board with a thickness of 1.6 mm (this is not the best material for RF equipment, but it is the most popular and affordable). This is necessary to comply with the wave impedance of the RF line equal to 50 Ohms. If this requirement is not observed, the wave impedance of the RF line will be different from 50 Ohms, which may lead to incorrect operation of the device. Wave resistance calculations were performed for a material with Er = 4.6 (FR-4) using [Saturn PCB Design V7.08](http://www.saturnpcb.com/pcb_toolkit/).

## Components installing 
Due to the use of SMD components and relatively tight mounting, this module has some recommendations on the soldering order of components, this is necessary to facilitate soldering (no hard-to-reach areas for the soldering iron will be formed).
Also, it is strongly recommended that you **use an antistatic wrist strap and do not use soldering irons that are powered directly from the 220V / 110V network**, which can damage some sensitive components when soldering.

Soldering order of components:

- TPS version: C13 -> C14 -> C15 -> L4 -> C17 -> L5 -> C19 -> L6 -> C16 -> C18 -> C20 -> C22 -> L8 -> C24 -> L10 -> C26 -> C21 -> L7 -> C23 -> L9 -> C25 -> L11 -> L12 -> C27 -> L13 -> C28 -> C29 -> R13 -> R14 -> C4 -> C6 -> DNI(R7) -> C7 -> C8 -> C9 -> R10 -> R11 -> R12 -> L2 -> C11 -> L1 -> BLUE LED -> R5 -> RED LED -> R8 -> GREEN LED -> R9 -> D3 -> U2 -> C5 -> DNI(R6) -> MX1 -> DNI(L3) -> DNI(C12) -> U3 -> C10 -> USB1 -> SW1 -> SMA con.

For building this version, you will need a multimeter for measurements the output voltage of the LM317. If you do not have a multimeter, you can use the SMD resistor R3(OR), 412 Ohm **instead** resistor R3.  

- TPS + LM version: C13 -> C14 -> C15 -> L4 -> C17 -> L5 -> C19 -> L6 -> C16 -> C18 -> C20 -> C22 -> L8 -> C24 -> L10 -> C26 -> C21 -> L7 -> C23 -> L9 -> C25 -> L11 -> L12 -> C27 -> L13 -> C28 -> C29 -> R13 -> R5 -> R14 -> C4 -> C6 -> DNI(R7) -> C7 -> C2 -> R2 -> C1 -> R1 -> C3 -> C8 -> R11 -> R12 -> L2 -> C11 -> L1 -> C10 -> BLUE LED -> YELLOW LED -> R4 -> RED LED -> R8 -> GREEN LED -> R9 -> Q1 -> D1 -> Q2 -> D2 -> D3 -> U2 -> C5 -> DNI(R6) -> U1 -> MX1 -> DNI(L3) -> DNI(C12) ->  R3/R3(OR) -> DC1 -> USB1 -> (**Only when using resistor R3**. Connect the power to the DC connector, measure the voltage between the middle switch contact (SW1) and GND. **The value obtained should be between 3.25-3.35 V**. If the voltage does not correspond within the specified range - adjust voltage using resistor R3) -> SW1 -> U3 -> C9 -> R10 -> SMA con. 

## Installation recommendations
If you use HF Upconverter, you will lose the ability to use software selectable Bias Tee (if this is offered by your SDR receiver). Therefore, if you use an active antenna (for example, Mini-Whip), you will definitely need to use a separate Power Feed Unit that is connected between the antenna and the converter.

Also, because of using of a 125 MHz value crystal oscillator, the frequency will be shifted to 125 MHz up (the frequency shift of our received radio station will look like this: 4.625 MHz + 125 MHz = 129.625 MHz). For convenience, you will need to set the value of the backward bias of -125 MHz in the receiving program (Gqrx, SDRSharp, etc.), but this action is not mandatory.

In the event of a large amount of interference at reception, you can independently manufacture a metal case for the upconverter. To do this, you can use any metal box of suitable size. The box is connected to the shield of a coaxial cable (connects to the external part of the SMA connector) or wire can be used, one end of which is soldered to the box and the other to a special "SHIELD" contact on the upconverter PCB.

## Power supply recommendations
When powering the HF Upconverter, **do not use power banks or other power supplies with impulse converters**. These devices create a sufficiently large amount of interference, which can adversely affect reception quality. When working from a laptop it is possible to use power from a free USB connector, or use a battery with a voltage of 5 V (or 6.5 - 36 V, LM317 version). In addition, a good solution will be the use of ferrite filters on power cables.
