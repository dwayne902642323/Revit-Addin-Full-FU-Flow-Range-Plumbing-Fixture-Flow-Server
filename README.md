👨‍💻 About This Repository

This repository contains the complete source code for a custom C# Revit API add-in that overrides Revit’s default plumbing fixture flow calculation logic for domestic water systems. Developed by Derek Eubanks, PE, HFDP, CHD, HBDP — a licensed mechanical engineer and Georgia Tech MSCS candidate — the add-in is purpose-built to resolve critical inaccuracies in low-demand fixture unit (FU) flow modeling.

🔧 Problem It Solves

Revit’s built-in logic assigns a fixed 15 GPM flow rate to any branch under 5 Fixture Units when the system is marked as predominantly flush valve. This creates oversized pipes, unrealistic velocities, and inflated pressure drops — violating the intent of IPC Table 103.3(3) and leading to overdesigned systems.

✅ What This Add-In Does

This tool registers a custom Plumbing Fixture Flow Server using the IPipePlumbingFixtureFlowServer interface. It overrides Revit’s default calculations by:
	•	Interpolating flush tank values for fixture groups below 5 FU, even in flush valve systems.
	•	Maintaining IPC/ASPE accuracy across the full FU range.
	•	Producing corrected GPM values, pipe diameters, and pressure drop reports.
	•	Enabling seamless adoption via Revit’s Mechanical Settings > Pipe Settings > Calculation interface.

## 📁 Repository Contents

| File Name                     | Description                                                                   |
|-------------------------------|-------------------------------------------------------------------------------|
| `PlumbingFixtureFlowServer.cs`| Core logic for converting Fixture Units (FUs) to GPM based on IPC tables      |
| `StraightSegmentCalculationServersApp.cs` | Registers custom flow server w/ Revit's external service framework|
| `UserStraightSegmentCalculationServers.dll` | Compiled add-in DLL (to be placed in Revit add-ins folder)      |
| `UserStraightSegmentCalculationServers.addin` | Manifest file to register the DLL with Revit                  | 
| `README.md`                   | Documentation and setup instructions                                          |

🧠 Author Background

This tool was developed as part of an ongoing effort to bring real engineering logic into Revit. I’m a licensed Mechanical PE with 12+ years of HVAC and plumbing design experience, certified by ASHRAE (HFDP, CHD, HBDP), and currently completing my MS in Computer Science at Georgia Tech, specializing in machine learning.

My goal is to bridge the gap between mechanical engineering standards and software automation — creating tools that are technically rigorous, code-compliant, and field-tested.
