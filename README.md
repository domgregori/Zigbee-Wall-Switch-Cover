# Zigbee Wall Switch Cover
This is a zigbee button that can go over a standard US wall switch. This can be handy to control smartbulbs (or whatever else) in a place where you are unable to install smart switches, allowing the switch to remain in the on position and activating the bulb with the front buttons.

This is built using [FreePad](https://github.com/diyruz/freepad) firmware for the E18-MS1-PCB zigbee module. For the zigbee coordinator I use [zigbee2mqtt](https://www.zigbee2mqtt.io/)

# Photos

![PCB_Front](https://user-images.githubusercontent.com/12613759/225990714-82f4070e-8f06-425e-b773-d88c17ac61c5.jpg) ![PCB_Back](https://user-images.githubusercontent.com/12613759/225990713-b68e532a-02b2-440a-b12a-4e1ec7ed334e.jpg)

![PCB_On_Wall](https://user-images.githubusercontent.com/12613759/225990718-b320dfeb-5f1c-44e4-844d-b0c2c7245a5a.jpg) ![Case_On_Wall](https://user-images.githubusercontent.com/12613759/225990721-0f84a5b7-3be8-4a63-bc4f-584a9ef7f88f.jpg)

# Programming
This is the wiring diagram between the PCB and CC Debugger

![WiringDiagram](https://user-images.githubusercontent.com/12613759/225987185-fef0e402-405f-4a0a-b338-9e8f65b060e7.png)

To program the module, use [TI SmartRF Flash Programmer](https://www.ti.com/tool/FLASH-PROGRAMMER) **NOT v2** and a CC Debugger

Use the DIYRuZ_FreePad_PM3.hex file from [FreePad](https://github.com/diyruz/freepad/releases) releases for longer battery life.
  
# Ordering
You can use the gerber files in the [PCB folder](PCB/) to order from a PCB manufacturer (I used jlcpcb)

### Part list
Parts can be found in [BOM Folder](BOM/bom.csv)
- 2x 2032 Battery Holder
- 3mm LED
- 5-pin 2.54 (standard) header for programming (if using the 3D printed case that I provided, these headers needed to be removed after programming)
- 2x 1k resistors, 0805
- 10k resistor, 0805
- 2x push buttons, 6x6x4.5mm
- E18-MS1-PCB

# Case
The 3D printed case file can be found in the [Case folder](Case/)

Printed with 20% Infill, Front face on bed with supports for the mounting holes

The PCB has 2mm mounting holes, but I did not use them in this case

![Case (Custom)](https://user-images.githubusercontent.com/12613759/225993588-0e287e40-10d9-466d-a7bb-2e0419b1a7cc.png)

# Notes
- Orient the **"TOP"** part of the PCB towards the direction of the switch (so upside down if your switch in on in the down position)
- Button 1 (SW1) is the pairing button
- Pair using the info at [Freepad: How to join](https://github.com/diyruz/freepad#how-to-join)
- I highly reccomend setting at least on of the buttons to MOMENTARY mode for quicker respose using the [Freedpad: Working modes](https://github.com/diyruz/freepad#work-modes) guide
- Only one battery is required to run but I use 2 so I get a longer run time
- If using zigbee2mqtt, don't use the outdated CC2531 board. It killed my batteries in days and pairing problems. I recomend the Sonoff ZBDongle-P (**Not model ZBDongle-E**)

### How I use mine
- Top button is set to MOMENTARY mode and toggles light on/off
- Bottom button press toggles between scenes from Home Assistant
- Bottom button hold goes into a dimming mode that allows me to brighten with the top button and dim with the bottom button
- Bottom double press sets light to a night light

- I achieve these by using a mix of Home Assistant automations as well as Node Red
