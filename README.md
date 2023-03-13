# TSMSI-SRV-FI-POC

## Description

The default service titled 'SessionEnv' contains a DLL hijack.
A user with admin privileges can utilize this service for lateral movement to a remote machine using the Execute Method below.

This POC in C# leverages the called functions of the TSMSISrv.dll by including malicious instructions within StartComponent.

The result of the script: creates a new Windows user called 'RedUser'

## Build Process

Please ensure you have the UnmanagedExports Package installed and are building for your target architecture e.g Framework 4.0.

Other NuGet Packages that are required are: 

Costura.Fody 3.3.3 - https://www.nuget.org/packages/Costura.Fody/3.3.3
Fody 4.0.2 - https://nuget.info/packages/Costura.Fody/3.3.3
Unmanaged Exports 1.2.7 - https://www.nuget.org/packages/Costura.Fody/3.3.3

## Execution Instructions

1. `sc.exe \\REMOTECOMPUTER stop SessionEnv`
2. `copy TSMSISrv.dll to C:\Windows\System32\TSMSISrv.dll`
3. `sc.exe \\REMOTECOMPUTER start SessionEnv`

Execution should have occurred on the remote machine and added a new user called "RedUser"

Suggestion: Run the project through offensive pipeline to obfuscate the DLL.
