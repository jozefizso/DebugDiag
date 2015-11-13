# Debug Diagnostic Tool (DebugDiag)

> The Debug Diagnostic Tool (DebugDiag) is designed to assist in troubleshooting issues such as hangs,
> slow performance, memory leaks or fragmentation, and crashes in any user-mode process.


## Introduction

The Debug Diagnostic Tool (DebugDiag) is designed to assist in troubleshooting issues such as hangs,
slow performance, memory leaks or fragmentation, and crashes in any user-mode process.
The tool includes additional debugging scripts focused on Internet Information Services (IIS) applications,
web data access components, COM+ and related Microsoft technologies.
Debugdiag 2.0 introduces a new analysis engine host with built-in reporting framework that can be accessed from .NET.
This new analysis engine simplifies analysis rule development in .NET.
Starting with Debugdiag 2.0, the analysis engine relies on Microsoft.Diagnostics.Runtime for .NET analysis.

| Version:         | Date Published: |
|------------------|-----------------|
| 2.2.0.14         | 11/13/2015      |

| File Name:       | File Size:      |
|------------------|-----------------|
| DebugDiagx86.msi | 17.3 MB         |
| DebugDiagx64.msi | 22.1 MB         |

* DebugDiag 1.0 was released as part of the IIS Diagnostic Toolkit and as a standalone tool (x86 only).
* DebugDiag 1.1 was released as a standalone tool only (x86 and limited x64 support).
* DebugDiag 1.2 is currently available as a standalone tool only (x86 and full x64 support).
* DebugDiag 2.0 is currently available as a standalone tool only (x86 and full x64 support).
* DebugDiag 2.1 is currently available as a standalone tool only (x86 and full x64 support).
* DebugDiag 2.2 is currently available as a standalone tool only (x86 and full x64 support).

## Overview

DebugDiag is composed of two main modules: Collection and Analysis.


## Collection Module

The collection module is composed of three main components: The Debugging service, the debugger host and the user interface.
It is the base install component of the tool.


### The Debugging Service

The Debugging Service The debugger service (DbgSvc.exe) performs the following tasks:

* Attach/Detach the host to processes
* Collect performance monitor data
* Implement HTTP ping to detect hangs
* Inject leak monitor into running processes
* Collect debugging session state information
* Shows the state of each rule defined


### The Debugger Host

The Debugger Host (DbgHost.exe) hosts the Windows Symbolic Debugger Engine (dbgeng.dll) to attach to processes
and generate memory dumps. It also hosts the main analyzer module to analyze memory dumps.
Dbghost.exe has no dependency on the service "DbgSvc.exe" and can be used separately.


### The User Interface

The User Interface (DebugDiag.Collection.exe) allows generation of control scripts, manual dump generation, displaying of rules status, etc.

It is composed of two views:

* **Rules**: Creates control script for the debugger host through a wizard. The scripts are located under the directory `DebugDiag\scripts`.
* **Processes**: Shows status of running processes/services. Selecting a process provides you with a context menu to start monitoring for memory leaks, collect single dumps or series of dumps, etc.

> **Note:** DebugDiagAnalysisOnly.exe does not require elevation on operating systems beginning with Windows Vista, so it only contains the Advanced Analysis view.

## Analysis Module

The analysis module is selected by default in a typical install; however, you can deselect the feature if not needed.
The analysis module requires .NET 4.0 installed on the system.

### Analysis Engine: dbglib.dll, DebugDiag.DotNet.dll
The analysis engine loads in the Analysis UI. It uses the Windows Symbolic Debugger Engine (dbgeng.dll) to access userdump data. It exposes this data via a rich API set that you can call from .NET code.

### Analysis UI: DebugDiag.Analysis.exe
The analysis UI is a .NET 4.0 executable that allows you to runs selected "Analysis Rules" against one or more memory dumps. Once the analysis is complete, the analysis report will open in the browser.

There are 5 built-in Analysis rules that are shipped with the product. These analysis rules are converted to .NET from the old "Analysis Scripts". They are all loaded from the assembly "Debugdiag.AnalysisRules.dll"

Debugdiag 2.0 ships 16 C# sample analysis rules and 10 XAML analysis rules along with a Visual Studio solution and project to get you started fast in analysis rules development!

### Rule Builder: DebugDiag.RuleBuilder.exe
The Rule builder UI is a .net 4.0 Workflow application that allows you to create simple workflow analysis rules. The resulting file is a XAML file that is loaded by either the RuleBuilder or the Analysis UI to run against selected Userdumps.
