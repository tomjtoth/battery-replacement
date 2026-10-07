# 3.9V battery replacement

I'd like to replace Li-ion cells from the battery package of mobile devices
with this DC DC converter, which shall step 5V received from any USB port/charger down to 3.9V.

## Conflict with charging via USB port

The devices USB port should not be used for charging after this integration.
Special cables (with unconnected VBUS) should be used when connecting to computers.

## Design choices

At 5V3A - a type-C DFP can provide without active negotiation - the _ideal_ power budget is 15W.
That should translate to about 3.84A at 3.9V.

As a worst case scenario I picked the largest transient as 3.8A and V_IN as 4.5V.
Using the converter's formulas I got 272.6mV sag and 12.7mV soar on the output.

My calculations and links to datasheets can be found
[here](https://docs.google.com/spreadsheets/d/1-LQr6ypT5iOjkNXZSsbeC3mkMsgCNXlFd2zotSDCdQk/edit?usp=sharing).

I'd like to produce this via JLCPCB, so I'm using only their components. All components are imported via JLCImport.
I minimized extended component usage, but I'm happy to pay extra for the 549k resistor, to keep the footprint smaller.

### RT5788B converter

Has 7V absolute maximum input voltage and 100% maximum duty cycle, can provide 4A continuously.
I'm not using the PGOOD leg of the converter to save space.

I found 2 revisions of its datasheet and proceeded with the earlier one where C_OUT = 2 x 22uF (vs 3 x 22uF on the newer revision).
C_IN is 22uF which exceeds the 10uF allowed by USB standard on Upward Facing Ports.

### Y4203 load switch

The 250us soft-start allows the above mentioned 22uF C_IN to be charged.
Has 6.1V OVP with 50ns response time.

## Schematics

I tried arranging the converter's pins similarly to as seen in the datasheet's Typical Application Circuit.

![schematics](./img/schematics.png)

## PCB

The board is 9 x 25mm sized. The minimum 5 pieces of 100x100mm panels (at JLCPCB) should yield 5x10x4 pieces
(leaving 2x5mm strips on 2 sides for manufacturing holes).
I'm using copper pours for GND on both sides.

![F.Cu](./img/F.Cu.png)
![B.Cu](./img/B.Cu.png)
![No.Cu](./img/No.Cu.png)
![3D-top](./img/3D-top.png)
![3D-bottom](./img/3D-bottom.png)
