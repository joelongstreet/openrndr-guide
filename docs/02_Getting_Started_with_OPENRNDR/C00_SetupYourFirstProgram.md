# Getting Started with OPENRNDR #

OPENRNDR provides an application framework that allows its users to write applications that run on Microsoft Windows, MacOS platforms and Linux/x64 systems.

## Requirements ##
 * A computer running any of our supported platforms.
 * A graphics adapter and drivers that supports OpenGL 3.3
 * JDK 8, 9, 10, or 11 installed. Both OpenJDK and OracleJDK work.
 * [IntelliJ Idea 2018.3](https://www.jetbrains.com/idea/download/) Community or Enterprise edition
 * A recent version of [Git](https://git-scm.com/)

## Setting up prerequisites
Before you start working with OPENRNDR please follow these instructions.
 * Install a Java Development KIT (JDK) [OracleJDK 10](http://www.oracle.com/technetwork/java/javase/downloads/jdk10-downloads-4416644.html), or if you prefer a guaranteed free version [OpenJDK 10](http://jdk.java.net/10/) and install it.
 * Download [IntelliJ Idea Community Edition](https://www.jetbrains.com/idea/download) and install it.

## Getting OPENRNDR

OPENRNDR is obtained by adding the OPENRNDR dependencies to your Gradle project. You don't have to download anything manually. We offer [ready-to-use artifacts](http://dl.bintray.com/openrndr/openrndr/org/openrndr/) through Bintray.

### Setting up OPENRNDR in IntelliJ Idea

Note: these instructions do not match with how IntelliJ 2018.3 handles the import from version control. IntelliJ will
detect the Gradle project automatically and will not prompt to pick an external model.

Use VCS -> Checkout from Version Control -> Git to open the "Clone Repository" dialog.

<img style="width:auto;" src="media/getting-started-step-01.png"/>

Fill in the url `https://github.com/openrndr/openrndr-gradle-template.git` and pick a target directory.

<img style="width:auto;" src="media/getting-started-step-02.png"/>

Checkout from version control? Yes.

<img style="width:auto;" src="media/getting-started-step-03.png"/>

In the Import Project dialog pick "Import project form external model" and select the "Gradle" model, click the "Next" button.

<img style="width:auto;" src="media/getting-started-step-04.png"/>

In the "Import Project" dialog the default settings should be OK. Make sure the "Use default gradle wrapper" option is selected and Gradle JVM has been picked. If no JVM options are available then create a new JVM option.

<img style="width:auto;" src="media/getting-started-step-05.png"/>

Click the "New Window" option.

<img style="width:auto;" src="media/getting-started-step-06.png"/>

All done. The Gradle project is now imported in IntelliJ Idea and you are ready to run the program.

### Run your first program

In IntelliJ, hover your mouse over the green triangle next to the `main()` function, right click and pick the `Run TemplateProgramKt` option in the pop-up menu. The sketch will now start.

<img style="width:auto;" src="media/getting-started-step-07.png"/>

On MacOS you will find that the program exits immediately with an error. To resolve this edit the run configuration (left of the play button in the main toolbar) and add
`-XstartOnFirstThread` to the VM arguments. The program should now work.

<img style="width:auto;" src="media/getting-started-step-08.png"/>

## Troubleshooting
##### Gradle errors after importing project
If you see something like `Error:No such property: GradleVersion for class: JetGradlePlugin` when importing the project with the directions above, make sure you're using the 2018 version of IntelliJ IDEA. The kotlin plugin that comes with the 2017 version of the IntelliJ IDEA is old and won't match the kotlin version in the build.gradle file.

#### Could not read from remote repository
If you believed you've typed the remote repository correct, but are getting a message from IntelliJ stating `Could not read from remote repository`, try cloning it from the command line. If you see `Error accessing media: gradle/wrapper/gradle-wrapper.jar`, you may have issues with git large file storage config settings. You can remove these settings with the following commands:
```
git config --global --unset filter.lfs.required
git config --global --unset filter.lfs.clean
git config --global --unset filter.lfs.smudge
```