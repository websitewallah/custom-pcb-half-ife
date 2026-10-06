# How to Design Your Own Custom PCB (Half-IFE Project)

Welcome to your custom PCB design journey! This guide will walk you through creating a professional PCB from start to finish.

## Project Overview

In this guide, we'll design a custom PCB with:
- A microcontroller (XIAO ESP32-C3)
- Multiple input sensors or switches
- Display/output components
- Power management

This process will be divided into **3 main phases**:

1. **PCB Design**
   - Drawing the schematic
   - PCB Layout and routing
   - Design verification
   - Export (Gerber files)
2. **Fabrication**
3. **Firmware & Testing**

## Tools You'll Need

- [KiCad](https://www.kicad.org/) - Open source PCB design tool (free!)
- Component datasheets (Google is your friend)
- A PCB manufacturer (JLCPCB, PCBWay, etc.)
- Arduino IDE or PlatformIO for firmware

---

## Phase 1: PCB Design

### Step 1: Gather Your Component Footprints & Symbols

Before you start designing, you need to collect the symbol libraries (schematic symbols) and footprint libraries (physical component layouts) for every component you plan to use.

**Recommended resources:**
- KiCad's built-in libraries
- Component manufacturer websites (often provide KiCad libraries)
- Online repositories like [KiCad Libraries](https://kicad.github.io/libraries/)

YouTube tutorials on installing libraries are incredibly helpful—search for "KiCad install custom libraries" if you get stuck.

### Step 2: Schematic Design

The schematic defines all electrical connections on your PCB.

#### Open KiCad Schematic Editor
1. Launch KiCad
2. Create a new project
3. Click the "Schematic Editor" button

#### Add Your Components

Press **A** to open the component selector. Add:

- **Microcontroller** (XIAO ESP32-C3 recommended)
- **Power management** (voltage regulator if needed, capacitors)
- **Input components** (buttons, sensors, potentiometers—your choice!)
- **Output components** (LED, buzzer, OLED display, etc.)
- **Decoupling capacitors** (essential for stable operation)

#### Wiring Tips

- **Press P** to add power symbols (+3.3V, +5V, GND)
- **Press L** to create net labels—these connect wires without drawing lines everywhere
- Group related connections with net labels for a cleaner schematic
- Ensure all power pins are connected
- Don't forget decoupling capacitors near each IC's power pins

**Example basic connections:**
- All GND pins → connected to GND net
- All 3.3V pins → connected to 3.3V net
- Component data pins → GPIO pins on microcontroller with labels

#### Assign Footprints

Once your schematic is complete:
1. Click the "Run Footprint Assignment Tool" (usually top right)
2. For each component, assign a realistic footprint (match the component's actual package)
3. Common footprints:
   - Buttons: `SW_SPST_EVQP` or `SW_Push_1P1T_NO_6MM`
   - LEDs: `LED_0805` or `LED_1206`
   - Resistors/Capacitors: `R_0805`, `C_0805`
   - Microcontroller: `XIAO_ESP32C3`

4. Click **Apply & Save**

---

### Step 3: PCB Layout & Routing

#### Import Netlist into PCB Editor

1. Return to the KiCad project window
2. Click "PCB Editor"
3. Click **"Update PCB from Schematic"** (top right)

Your components will appear in a chaotic pile—this is normal!

#### Arrange Components

1. Move components inside a defined board boundary (use the Edge Cuts layer)
2. Consider signal flow: inputs on one side, outputs on the other
3. Keep high-speed signal components close to the microcontroller
4. Leave room for traces between components

#### Route the Traces (Connect Pads)

Press **X** and click on an unrouted pad (shown as a thin blue line). The screen will dim, showing you where to connect.

**Routing tips:**
- Use both sides of the board (F.Cu for front, B.Cu for back)
- Keep traces away from edges
- Minimize sharp 90° angles (prefer 45° corners)
- Keep high-speed signals short
- Use a GND pour (fill) for better stability and easier routing

**YouTube is your best friend here**—search for "KiCad PCB routing tutorial"

#### Design Checks

Run **DRC (Design Rules Check)**:
1. Click the DRC button (top right)
2. Check for errors
3. Common issues:
   - Unrouted connections
   - Trace width violations
   - Clearance problems

Fix any errors before proceeding. Some warnings can be ignored (ask an instructor if unsure).

---

### Step 4: PCB Customization

Add personality to your board!

- **Silkscreen text**: Add your name, version number, date
- **Design elements**: Use the Image Converter tool to add logos or patterns
- **Color**: Some manufacturers support colored PCBs

---

### Step 5: Export Gerber Files

Your PCB manufacturer needs Gerber files (manufacturing format):

1. In KiCad PCB Editor: **File → Plot**
2. Select "Gerber" as format
3. Check: `F.Cu`, `B.Cu`, `F.SilkS`, `B.SilkS`, `F.Mask`, `B.Mask`, `Edge.Cuts`
4. Generate the files
5. **Also export the drill file** separately
6. Create a ZIP file with all Gerber files
7. Upload to your chosen PCB manufacturer

---

## Phase 2: Component Selection Guide

**Recommended starter components:**

| Component | Notes |
|-----------|-------|
| XIAO ESP32-C3 | Microcontroller, easy to program |
| AMS1117-3.3 | Voltage regulator (if using higher voltage) |
| Tactile buttons | SW_SPST_EVQP, 6mm height |
| LEDs | Red, green, or blue—choose your color |
| Resistors (10k, 1k, 220Ω) | Current limiting, pull-ups/pull-downs |
| Capacitors (10µF, 0.1µF) | Power filtering, decoupling |
| OLED display | 0.96" I2C interface, easy to use |
| DHT11/DHT22 | Temperature/humidity sensor (optional) |

---

## Phase 3: Firmware

Once your PCB arrives and is assembled, you'll program it using Arduino IDE.

### Setup
1. Install Arduino IDE
2. Add ESP32 board support
3. Install necessary libraries (Adafruit, sensor libs, etc.)
4. Write code to test each component
5. Upload via USB

### Testing Checklist
- [ ] Microcontroller boots (LED blink test)
- [ ] All buttons register
- [ ] Display shows output
- [ ] Sensors read correctly
- [ ] Power consumption is reasonable

---

## Troubleshooting

**"Component not found in libraries?"**
- Check spelling, search the manufacturer's name
- Create a simple placeholder symbol if needed

**"Routing is impossible"**
- You may need to use both PCB layers (front and back)
- Consider moving components for better signal flow

**"DRC errors everywhere"**
- Check trace widths match design rules
- Increase spacing between traces if needed
- Consult the KiCad manual or YouTube

---

## Final Checklist Before Ordering

- [ ] All components have footprints assigned
- [ ] Schematic is complete and reviewed
- [ ] PCB is fully routed (no blue lines remaining)
- [ ] DRC has no errors
- [ ] Gerber files are generated and verified
- [ ] Component values are correct on silkscreen
- [ ] Board dimensions are reasonable for your use case
- [ ] You've ordered components from suppliers

---

## Next Steps

1. **Order your PCB** from JLCPCB, PCBWay, or similar
2. **Order components** from Digi-Key, Mouser, or Aliexpress
3. **Wait for delivery** (usually 1-3 weeks)
4. **Solder components** onto your PCB
5. **Write and upload firmware**
6. **Test and debug**
7. **Document your project** in this repository

---

## Useful Resources

- [KiCad Official Documentation](https://docs.kicad.org/)
- [Adafruit Learning System](https://learn.adafruit.com/)
- [Electronics tutorials](https://www.electronics-tutorials.ws/)
- Your instructor and peers—don't be shy about asking for help!

Good luck with your project! 🚀
