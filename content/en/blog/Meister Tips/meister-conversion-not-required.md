---
title: "No Meister Conversion required"
date: "2017-05-26"
categories: 
  - "meister-continuous-build"
tags: 
  - "ant"
  - "build-automation"
  - "continuous-integration"
  - "eclipse-builds"
  - "meister"
coverImage: "makechange.jpg"
---

## No Meister Conversion Required to Start Using Meister Build services.

Meister conversion is a myth. To use Meister, our competitors would like you to believe that an Ant to Meister or Maven to [Meister](https://www.openmakesoftware.com/meister-continuous-build/) conversion is required.  We are often asked, "how long does it take to convert my Ant Scripts to Meister?"  The answer is there is really no requirement to "convert" to Meister. Meister will do that for you by referencing the most accurate information found - the [Eclipse](https://www.eclipse.org/) or [Microsoft .Net](https://dotnet.microsoft.com/en-us/) Project files.

<div>
<img src="/images/makechange-300x200.jpg" alt="manage build changes" />
</div>

## Ant and Maven Extras

Ant Scripts can do many steps including calling version control and executing a deployment.  If these kinds of steps are in your Ant scripts, you will need a Meister conversion to your CI workflow.  Meister includes calls to common activities that are included in CI Workflows. For example,  calling version control tools, static testing and automated configuration management.  You will end up creating a CI workflow that performs the same steps as your existing Ant Scripts.

## Meister Generates a New Script

Instead of a Meister conversion, Meister will use your Eclipse Project files to generate the "ant" like process for creating your jars, wars, ears.  An Ant to Meister conversion is a misunderstanding of how Meister is configured.  Meister uses Targets instead of a script of any type. Instead of manually creating _Targets,_ you can automatically generate them using your development IDE.  If you are currently executing builds using  scripts, and you use an IDE, you let Meister generate what you need.   Meister can automatically generate your _Targets_ based on the IDE Project file using the Eclipse plug-in.  This is the preferred method.  Your IDE Project file is the most accurate reflections of how your Java component is built. Therefore automatically generating the Target based on the Project file will provide the most accurate results.

In addition, by automatically generating your Java _Targets_ via your IDE, you can improve your Continuous Integration process.  By auto generating your _Targets_ you can synchronize the builds performed inside of the Eclipse IDE with the builds running outside of the Eclipse IDE.  This synchronization resolves changes made to the source code that has impacted the build scripts running outside of the IDE such as the case with refactoring, adding libraries, or changing compile options.

## The Meister TGT Plug-in

The _Meister TGT Generation Plug-In_ integrates with **Eclipse, IBM Rational Application Developer, IBM Rational Software Architect,** **MyEclipse,** **Weblogic Workshop,** **IBM WebSphere Studio Application Developer,** and **CodeGear**.

When using the Target Generator, _Targets_ are automatically generated and maintained by the Plug-In.  The Plug-In can be configured to automatically create and update .tgt’s when:

A file is added or removed from a referenced Eclipse project

Referenced Eclipse project properties such as Java Build Path are updated

Developers choosing to use the Eclipse plug-in should first setup the configuration of the Eclipse Target Generator.  Once your configuration has been setup you can then define a _Project_ and _Dependency Directory_ and configure their Eclipse projects to use the _Target_ generation and build features.   **Note:**  To validate that you have the Eclipse Target Generator already installed simply view the list of plug-ins available from the Eclipse IDE.  If the Meister Eclipse Target Generator is installed you will see “OpenMake TGT Generator” in the list.
