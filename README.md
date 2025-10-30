# VISU
VISU tool is the Phinia product for calibration of ECU function parameters. VISU supports online and offline adjustments of characterictic values, curves and tables. Simultaneously to the parameter optimization, VISU allows to acquire measurement signals from ECUs as well as from their vehicle environment.

In addition to the measurement and calibration core system, VISU includes tools for reading faults, writing Injector parameters and for reprogramming ECU software into flash memory. VISU uses Flasher tool for running diagnostic commands (e.g. flashing HEX file to ECU). If Flasher is installed, VISU will find it automatically. VISU runs "plugin" function on the Flasher. "Plugin" is the DLL file which describes the diagnostic routines for Flasher tool.

<img alt="VISU and Flasher access to ECU" src="https://github.com/user-attachments/assets/5599bc26-3429-4a4f-b6eb-034ca28bd894">

## Applications
**Calibration:** Online/offline calibration, 2 page (work / reference page) / 1 page concept, support of dependent and adaptive parameters, editors for scalars and multidimensional parameters (1D and 2D).

**Calibration data management:** Listing, comparing and copying calibration data, functional view, support of maturity levels, version management of calibration data sets.

**Measurement data acquisition:** Acquisition and online display of measurement values, calibration parameters (scalars, characteristic curves/maps), numerous trigger options, XT/XY-oscilloscope and table display, simultaneous acquisition of parallel measurements, cold start acquisition.
+ Multi ECU measurement.
+ Bus signals or raw CAN frame recording parallel to CCP/XCP measurement.
+ Recording GPS data from [PhyPhox mobile app](https://phyphox.org/), or any GPS device with CAN support.
+ Polling DAQ support when the ECU rasters are not sufficient.
+ XCP stimulation support.
+ Recording of unlimited large measurement file using ASAM MDF v4. Compression is supported.
+ Add text or voice markers to the recording.
+ ECU reconnection when the measurement fails.

![meas](https://github.com/user-attachments/assets/06440f60-91b6-4104-9d38-3c445924f755)


**Measurement data analysis:** XT/XY-oscilloscope, table display, samples display, cursor, offline trigger, signal calculation, statistical analysis, calculated signals (equation) on the fly, various export features.

![Measure-analysis](https://github.com/user-attachments/assets/16602f20-78c8-4a1b-abc2-f5f080774565)


**Flash programming:** ECU-specific flash programming via [Flasher](https://github.com/PHINIA-FS-Tools/Flasher/) tool.

**Experiment environment:** Numerous user-friendly display and control elements, interface for integrating customer-specific elements.

**Hardware configuration:** Configuration of ECU and bus interfaces, and measurement modules, hardware auto-scan.

**Bus monitoring:** Advanced bus monitoring features for CAN/FlexRay/LIN buses, grouped or chronological view of traces, J1939 (/21 and /22) transmission and monitoring.
![bus_monitor](https://github.com/user-attachments/assets/c990a3a6-18c0-4e26-8ee9-114f9d6cd99a)


**ECU diagnostics:** via [Flasher](https://github.com/PHINIA-FS-Tools/Flasher/) tool, Error memory reading and clearing, validation of services of diagnostic services, Automation of service sequences, support of ODX into diagnostic script.

**Test automation:** Remote control via ASAP3 and iLinkRT.

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

