# VISU
Measurement and Calibration tool
VISU tool is the Phinia product for calibration of ECU function parameters. VISU supports online and offline adjustments of characterictic values, curves and tables. Simultaneously to the parameter optimization, VISU allows to acquire measurement signals from ECUs as well as from their vehicle environment.

In addition to the measurement and calibration core system, VISU includes tools for reading faults, writing Injector parameters and for reprogramming ECU software into flash memory. VISU uses Flasher tool for running diagnostic commands (e.g. flashing HEX file to ECU). If Flasher is installed, VISU will find it automatically. VISU runs "plugin" function on the Flasher. "Plugin" is the DLL file which describes the diagnostic routines for Flasher tool.

<img alt="VISU and Flasher access to ECU" src="https://github.com/user-attachments/assets/5599bc26-3429-4a4f-b6eb-034ca28bd894">

## Technical Data

### Interfaces
**ECU calibration:** CAN (CCP, XCP, UDS), CAN FD (XCP, UDS), Ethernet (XCP, UDS), FlexRay (XCP), Serial port (XCP), X-ETK Interface (board)
ETK and F-ETK interfaces are not supported.

**Bus monitoring:** CAN, CAN FD, FlexRay, LIN

**Measurement devices:** CAN (Vector, Peak, Softing, Kvazer, any SAE J2534 compliant device), CAN-FD (Vector, Peak), Flexray (Vector), LIN (Vector, Intrepid, Peak)

**Test bench / automation:** ASAM ASAP3 (v2.0, v2.1.1, v3.0), iLinkRT v2.0

| Bus/Protocol  | CCP  | XCP | UDS | Monitoring |
| :------------ |:---------------:| :-----:| :-----:| :-----:|
| CAN      | y | y | y | y |
| FlexRay  |   | y |   | y |
| LIN      |   |   |   | y |
| Ethernet |   | y | y |   |
| Serial   |   | y |   |   |

### Data exchange
**ECU description:** ASAM MCD-2 MC (A2L) up to 1.7.1

**CAN Bus description:** DBC, FIBEX (From v3.0.0 to v4.1.2), ARXML (AUTOSAR 4.2.2 schema)

**FlexRay Bus description:** FIBEX (From v3.0.0 to v4.1.2), ARXML (AUTOSAR 4.2.2 schema)

**LIN Bus description:** LDF (in conformity with LIN 2.2 Rev A)

**Calibration data:** Intel HEX, Motorola S19, S28, S37

**Calibration data(physical representation):** DCM, CVX, PaCo, ASAM CDF (v2.0, v2.1)

**Measurement file data:** ASAM MDF (v3, v3.3, v4.0, v4.1), ASCII

**Bus trace file:** BLF, ASC

### Applications
**Calibration:** Online/offline calibration, 2 page (work / reference page) / 1 page concept, support of dependent and adaptive parameters, editors for scalars and multidimensional parameters (1D to 3D)

**Calibration data management:** Listing, comparing and copying calibration data, functional view, support of maturity levels, version management of calibration data sets

**Measurement data acquisition:** Acquisition and online display of measurement values, calibration parameters (scalars, characteristic curves/diagrams), numerous trigger options, online signal calculation, XT/XY-oscilloscope and table display, simultaneous acquisition of parallel measurements (multi-recorder)

**Measurement data analysis:** XT/XY-oscilloscope, table display, cursor, offline trigger, signal calculation, statistical analysis

**Flash programming:** ECU-specific flash programming via Flasher application

**Experiment environment:** Numerous user-friendly display and control elements, interface for integrating customer-specific elements

**Hardware configuration:** Configuration of ECU and bus interfaces, and measurement modules, automatic search for connected hardware, sending of CAN messages

**ECU diagnostics:** via Flasher application Error memory reading and clearing, validation of services of diagnostic services, Automation of service sequences Support of ODX into diagnostic script
