# XETK support of VISU 
<p>This page describes the required steps to establish communication between VISU and an ETAS XETK.</p>
<p>In general, an XETK communicates in a proprietary way and therefore can only be used correctly with ETAS tools.</p>

> XCP on Ethernet compatibility has to be activated within the XETK device explicitly. This is done by configuring particular XETK settings.

<p>This configuration should already be done by the ECU supplier for initial XETK usage or it could also be configured later on demand.</p>

### Preconditions
By ETAS (download via ETAS download center):
* HSP Update Tool version 14.0.0 or later
* ETK Tools 4.4.0 or later (includes software XCT)

By ECU supplier:
* A2L file which works successfully for proprietary ETK connection using **INCA**.

### Compatibility to VISU
Please regard the big difference between ETK and XETK devices. ETK devices are not supported in VISU! Those devices work completely ETAS proprietary, except for ETK-S20 and ETK-S21.

XETK and FETK devices are able to communicate via standard XCP on Ethernet. These can be supported by VISU if some circumstances are fulfilled. For details see information listed in the chapters below. The XETK has to be configured in a defined way to work with 3rd party (non-ETAS) tools.

Please regard: For readability and coherence reasons, all ETK devices supported by VISU are called ETK within this document.

## Necessary adjustments and preconditions
### Update XETK via HSP Update Tool (Optional)
Please be sure to use the latest version of the XETK firmware.

Communication (start of Measurement, time correlation…) might not work if firmware is outdated. The XETK Tools package contains the latest firmware of the XETK hardware.

### Use/set fixed IP address for XETK
---Skip this part if XETK already has a fixed IP address.---

Please be aware that the necessary A2L file has to contain a definition for XCP on TCPIP or XCP on UDPIP. The relevant information concerning the IP address has to be listed within those A2L sections. Basically, XETK devices are able to work in two different ways for IP address usage. The IP address can be set fixed or might also be configured dynamically. Please use the tool XCT to configure how the IP address should be used.

> **Fixed IP Address**<br />
> We recommend using a fixed IP address for the XETK. The advantage is a unique way for identification, not depending on any specific tool being required to communicate with the XETK. The IP address of the XETK should also be correctly defined within the A2L file.

However, if dynamic IP addressing is used an ETAS tool called Ethernet System Configuration is responsible to assign the address to the connected XETK. This assignment procedure is done implicitly if starting ETAS products (i.e. INCA). But this automatic assignment does not happen for 3rd party software (i.e. VISU).

Therefore, execution of Ethernet System Configuration is required to assign an IP address (delivered within ETAS ETK Tools package, usually i.e. located at: C:\Program Files\Common Files\ETAS\ETASShared15\IPMServer\IPMClient.exe).

<img width="456" alt="image" src="https://github.com/user-attachments/assets/1f84663a-9f8a-4c2b-bd15-86a659b9bec9" />


Please regard: If the XETK cannot be found execute ETAS Network Manager (i.e. located at C:\Program Files\Common Files\ETAS\ETASShared15\IPMServer\NetworkManager.exe). This software allows the user to define which Ethernet Adapter is used for dynamic IP addresses.

VISU will use the IP address definition in A2L file.

## Configuration of ETK for standard "XCP on Ethernet" usage
---Skip this part if your XETK already configured for your ECU.---

This is a very essential part. The correct configuration of the XETK is the main precondition to enable communication between VISU and the XETK.

By default, an XETK is configured in a proprietary way to establish communication to ETAS tools. However, an XETK can be configured in different ways - e.g. to enable standard XCP on Ethernet communication. After adjusting those relevant settings 3rd party tools (such as VISU, CANape) can communicate with the XETK in a proper standardized way.

> **XCT** is the tool to configure XETK device. If you don't have XCT tool in your PC, you may download from ETAS web site. <a href="https://www.etas.com/ww/en/downloads/software-downloads-overview/etk-tools/">Download ETK Tools</a>.

> ⚠️ You need to apply below static configuration only once. However, when **INCA** tool is used for proprietary ETK connection (not the standard XCP on Ethernet), the static configuration on XETK is reset. So, you need apply below configuration again.

### Option 1: Automatic Configuration (requires VISU v9.1 or later)

<img width="500" alt="image" src="https://github.com/user-attachments/assets/dc423d00-63b2-4ce2-8c6c-3877709d0809" />


VISU finds the path of **XCTConsole.exe** automatically if installed.

Provide the A2L file that supports successful proprietary ETK communication using INCA (contains the valid ETK_XETK configuration block).

Once clicking **Configure XETK**, XCT tool will configure the XETK to be used by XCP on Ethernet.

In addition, the XCP_ON_TCP_IP (or XCP_ON_UDP_IP) block must be added into A2L file, so that VISU can use XCP on Ethernet to communicate XETK device. Check the "Create new A2L file ..." box, so that VISU will add XCP_ON_TCP_IP block for you. If it is already added before, no need to check this box. Tool will create new A2L file into the same folder of source A2L file.

### Option 2: Manual Configuration
* Start XCT tool.
* Refresh the hardware-list, and see the XETK device listed.<br />
  <img width="374" alt="image" src="https://github.com/user-attachments/assets/8cd085d5-142b-4e92-b663-242d40d397bb" />

* Import A2L file (supports successful proprietary ETK communication using INCA). The settings extracted from the A2L will be displayed as temporary XCT project.
* Click "Edit"->"Convert project to fixed configuration" from menu.<br />
  <img width="356" alt="image" src="https://github.com/user-attachments/assets/0c5e782e-fe26-453e-a633-48b7471b6713" />

* Download XCT project to XETK. <br />
  <img width="492" height="464" alt="image" src="https://github.com/user-attachments/assets/10f14f9a-deda-4e20-999b-b42da0f2f3b9" />

* Add "XCP on Ethernet" definition into A2L file.<br />
  ---Skip this part if your A2L file already has XCP on Ethernet (TCP/UDP IP) definition.---<br />
  Your A2L file may have definitions like XCP on CAN, XCP on CAN-FD etc. However, XETK connection is done via XCP on TCP IP or XCP on UDP IP (shortly XCP on Ethernet).<br />
  <img width="600" src="https://github.com/user-attachments/assets/7d490ecd-ba9b-4bae-a329-0a8736bcb105" />

  XCT tool generates a partial A2L. Only XCP on Ethernet definition is necessary for VISU. Find that definition, then insert into the original A2L file.<br>
  <img width="571"  alt="image" src="https://github.com/user-attachments/assets/05ca8e77-e49a-479c-af49-cdb09471c34c" /><br>
  _This is not a valid block. It is shortened._

## XETK connection in VISU
Load the A2L in VISU, and select the appropriate XCP protocol:

<img width="600" alt="image" src="https://github.com/user-attachments/assets/ef81f77b-711a-4244-bce5-c0bf6ab8a4d5" />
  
## Troubleshooting
#### Ethernet connection problem
<img width="350" alt="image" src="https://github.com/user-attachments/assets/44727f06-1e01-431a-923c-ec0494de2699" /> <br>
This problem might occur during initial connection. If VISU v9.1 or greater version is used, use Tools->ETK from menu, and get the list of XETK devices. If older than v9.1 VISU is used, use XCT tool to refresh XETK hardware list.

If the XETK hardware is visible, retry VISU connection attempt.

#### "Optimization type not supported" error
<img width="350" alt="image" src="https://github.com/user-attachments/assets/f977ede3-51ee-4fbb-823d-50ae42e5de5b" /><br>
Use minimum **VISU version 9.0**.

#### XETK connection is successful. However, "DAQ Configuration not valid" seen after starting acquisition. Or, just a single raster works.

<img width="350"  alt="image" src="https://github.com/user-attachments/assets/193a3f3e-0603-4073-9053-b228206b4065" />

This means that XETK is not configured for "fixed configuration". Apply the steps in "Configuration of ETK for standard XCP on Ethernet usage".

