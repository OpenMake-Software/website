---
title: Meister 7.5.1 Installation Guide
description: Installing Meister
summary: Installing Meister with Java 11 or higher
type: contributor
---

## Installation Steps

Meister 7.5.1 now requires the Eclipse IDE to be installed first and then the Meister plugins are added to Eclipse.  This change has been do to support a wider variety of Java runtimes.   Java 11 through Java 22 are supported.

1. Download `Eclipse IDE for Java Developers` from the [Eclipse Download Site](https://www.eclipse.org/downloads/packages/).  

> Note: Older versions can be used but they must be `Eclipse IDE 2022-06 R Packages` or newer.

2. Launch Eclipse and choose `Help -> Install New Software...`

3. Add a new `Update Site` with `Add...`.  Use OpenMake for the name of the update site.  Use `https://www.openmakesoftware.com/eclipse-p2` for the URL.  Save the update site and choose it in the site downdown list.

4. Expand the Group and choose `Meister 7.5.1 - JRE 11`.  Follow the installation prompts and Eclipse restart.

5. Relaunch Eclipse and `Window -> Open Perspective -> Other -> OM Workflow`.  The plugin will determine if further configuration is needed or if it can connect to an existing KB Server.

> Note:  Open the other `OM...` perspectives to access the other Meister Windows.
