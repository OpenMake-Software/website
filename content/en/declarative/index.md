---
title: Declarative Builds
description: Declarative Builds
summary: Moving away from scripted, imperative builds
type: contributor
---

<div class="row">

  <div class="col">
  </div>
  <div class="col-7">
  <div style="margin-bottom:40px">
    <br>
    <h1 class="text-left">Consistent, Repeatable Builds</h1>
    <hr>
    <br>
    <img src="/images/ScriptingNerd-sm.jpg" alt="build manager" style="width"300px;height:400px;"  />
  </div>

One of the most misunderstood steps in the CI/CD pipeline is the software 'build.' Software builds compile and link source code into releasable binaries, and then adds those binaries to a release 'package.' The main reason why it is misunderstood is because an unsung hero, often called the 'build manager,' works quietly, tirelessly and often late to make sure the builds are running. In the early days of continuous integration we talked about the importance of the "10 minute" build, and our build manager made it their goal to accomplish the mission. 

For most, builds are automated. You create a pull request and a subsequent commit triggers the build to run. But the build itself is a scripted process held together by the knowledge of the build manager. They themselves hold the keys to how the build is configured and executed. In other words, it is still a scripted, imperative process regardless of how it is triggered by your CD Pipeline. Sharing information about how the build works, auditing the build and adding more control around the build often does not fit into the culture we have created around managing builds. Project managers often forget to add project time to create the build. As a result, the build itself is ad-hoc, open to security vulnerabilities, and the victim of unintended human errors.

For this reason, it is important to begin moving away from an imperative process to a declarative build process. With a declarative build, your developers declare specific configurations of the build. They declare their target files, the directories from which to pull source code and dependency information and the compile/link flags needed to create the binaries. The logic of the build itself is left to a build engine, or operator, that [insulates](/insulated) the build, controls how the build is executed, reduces risk associated to certain configurations (think a debug flag running in production) and validates the entire process via a [build audit](/insights/) .

## Meister's Declarative Operator

OpenMake Meister is a declarative build system that supports over 200 different languages and development environments. Its core operator is a rules based engine that understands compiler logic, and how to scan and assemble the binaries of these different languages. Instead of one of your key developers stepping up to work late to script the build with the logic, Meister allows your team to declare their objects in a collaborative way, leaving the logic and hard work up to the Meister Operator. The result is a build process that is 100% consistent, accelerated and validated without the need for a single individual to be responsible for the effort. 

## What you Declare in Meister

When defining your project's build to Meister, there are certain elements that must be declared. Meister uses these elements to auto generate a 'build control file' that is then executed by the Meister rules based engine. The following elements are defined by your team.


### Dependency Directories

Dependency Directories are the way in which your source code supply chain is controlled by Meister. Dependency Directories are represented by the VPATH variable in the Build Audit Report. Dependency Directories are passed to the compilers by Meister during the build. Dependency Directories contains a list of approved directories that can be used in the build. If the file is not found in the declared Dependency Directories, Meister displays an error message indicating that the source was not found. Dependency Directories are important because they carefully control how source code gets into the build. Access to defining Dependency Directories can be controlled based on Group privileges. This means that only certain individuals can define the high-level directories that will be used during a build, such as shared libraries or source code. 

### Build Types

Build Types are unique to Meister. Build Types are associated to the compiler/linker or development IDE. Build Types controls the logic of how to call the compiler. Meister includes over 200 pre-defined Build Types. Custom Build Types can be added as needed. Access to updating Build Types can be controlled based on Group privileges. This means that only certain individuals can define build configuration data that will be used during the build.

### Targets

Targets are the objects to be created (.dll, .exe, .lib, .o). Developers define a Target file for each object that needs to be created and checks it into your source repository. A Target includes the name of the binary to be created, the specific source code needed to build the binary, the Build Type and any compile/link flags that are required.

Meister uses the Build Type and the Target to auto-generate the build control file. At build time, the dependency directories are referenced to locate the source and libraries defined in the Target file. Meister runs the build based on the Build Type definition calling the compilers/linkers and development tools as intended. No one needs to create the build logic - it is already done for you. Each developer can create their own Target files. The job of the Build Manager is to simply manage the dependency directories. 

When Meister executes, it can run builds [incrementally](/blog/2017/06/29/incremental-builds-are-critical-for-continuous-builds/) or using a 'clean all' option. In addition, Meister generates the additional work products such as your Software Bill of Material report (Build Auidt) that validates the build. Comparing two Build Audit reports provides you a clear 'difference report.' 

At the end of the build, Meister can package your binaries using the package manager of your choice. When it performs the packaging step, it explicitly defines the files to be included without the use of wildcards ensuring that only the approved binaries are included in your final release package. 


## Conclusion

Moving away from an imperative build process to a declarative method strengthens the security and reliability of the software build process. With a declarative system there is not a single 'go to' individual for executing the builds. Everyone understands the build process and can re-create any build at anytime. A declarative build system can easily achieve the '10 minute' build by using intelligent, incremental build processing. And if you choose to always rebuild everything, Meister can accelerate the build using a distributed, parallelized build logic. These are the additional features a declarative build system can offer once you decide that the imperative method is too risky, historically inconsistent, vulnerable and costly. All true.  

Read more about Meister on our [Blogs](/blog/meister-tips/).

  </div>
  <div class="col">
  </div>
</div>  