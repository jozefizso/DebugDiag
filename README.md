# Debug Diagnostic Tool (DebugDiag)

> The Debug Diagnostic Tool (DebugDiag) is designed to assist in troubleshooting issues such as hangs,
> slow performance, memory leaks or fragmentation, and crashes in any user-mode process.


## Introduction

The Debug Diagnostic Tool (DebugDiag) is designed to assist in troubleshooting issues such as hangs,
slow performance, memory leaks or fragmentation, and crashes in any user-mode process.
The tool includes additional debugging scripts focused on Internet Information Services (IIS) applications,
web data access components, COM+ and related Microsoft technologies.

| Version:         | Date Published: |
|------------------|-----------------|
| 1.2              | 7/14/2011       |

| File Name:       | File Size:      |
|------------------|-----------------|
| DebugDiagx86.msi | 11.7 MB         |
| DebugDiagx64.msi | 16.1 MB         |

* DebugDiag 1.0 was released as part of the IIS Diagnostic Toolkit and as a standalone tool (x86 only).
* DebugDiag 1.1 was released as a standalone tool only (x86 and limited x64 support).
* DebugDiag 1.2 is currently available as a standalone tool only (x86 and full x64 support).

## Overview

DebugDiag provides an extensible object model in the form of COM objects and provides a script host with a built-in reporting framework.

It is composed of the following 3 components: a debugging service, a debugger host, and the user interface.


## The Debugging Service

The Debugging Service The debugger service (DbgSvc.exe) performs the following tasks:

* Attach/Detach the host to processes
* Collect performance monitor data
* Implement HTTP ping to detect hangs
* Inject leak monitor into running processes
* Collect debugging session state information
* Shows the state of each rule defined


## The Debugger Host

The Debugger Host (DbgHost.exe) hosts the Windows Symbolic Debugger Engine (dbgeng.dll) to attach to processes
and generate memory dumps. It also hosts the main analyzer module to analyze memory dumps.
Dbghost.exe has no dependency on the service "DbgSvc.exe" and can be used separately.


## The User Interface

The user interfaces (DebugDiag.exe and DebugDiagAnalysisOnly.exe) present an interface to analyze memory dumps,
automate the creation of control scripts and show the status of running processes, including services.

It is composed of 3 views:

* **Rules**: Creates control script for the debugger host through a wizard. The script is located under `\scripts`.
* **Advanced Analysis**: Runs a selected **Analysis Script** against one or more memory dumps.
* **Processes**: Shows status of running processes/services.

> **Note:** DebugDiagAnalysisOnly.exe does not require elevation on operating systems beginning with Windows Vista, so it only contains the Advanced Analysis view.
