# System Advisor Model (SAM)

The SAM Open Source Project repository contains the source code, tools, and instructions to build a desktop version of the National Renewable Energy Laboratory's System Advisor Model (SAM). SAM is a simulation program for electricity generation projects. It has models for different kinds of renewable energy systems and financial models for residential, commercial, and utility-scale projects. For more details about SAM's capabilities, see the SAM website at [https://sam.nrel.gov/](https://sam.nrel.gov/).

The desktop version of SAM for Windows, Mac, or Linux builds from the following open source projects:

* [SSC](https://github.com/nrel/ssc) is a set of "compute modules" that simulate different kinds of power systems and financial structures. It can be run directly using the [SAM Sofware Develoment Kit](https://sam.nrel.gov/sdk).

* [LK](https://github.com/nrel/lk) is a scripting language that is integrated into SAM and allows users to add functionality to the program.

* [wxWidgets](https://www.wxwidgets.org/) is a cross-platform graphical user interface platform used for SAM's user interface, and for the development tools included with SSC (SDKtool) and LK (LKscript). The current version of SAM uses wxWidgets 3.1.0.

* [WEX](https://github.com/nrel/wex) is a set of exensions to wxWidgets for custom user-interface elements used by SAM, and by LKscript and DView, which are integrated into SAM.

* **SAM** provides the user interface to assign values to inputs of the SSC compute modules, run the modules in the correct order, and display simulation results. It also includes tools for editing LK scripts, viewing time series results, and generating shade data from a 3-dimenional representation of a photovoltaic array or solar hot water collector and nearby shading objects.

# Quick Steps for Building SAM

For detailed build instructions see the [wiki](https://github.com/NREL/SAM/wiki), with specific instructions for:

  * [Windows](https://github.com/NREL/SAM/wiki/Windows-Build-Instructions)
  * [Mac](https://github.com/NREL/SAM/wiki/Mac-Build-Instructions)
  * [Linux](https://github.com/NREL/SAM/wiki/Linux-Build-Instructions)

These are the general quick steps you need to follow to set up your computer for developing SAM:

1. Set up your development tools:

    * Windows: Visual Studio 2013 Professional or Express edition. Download from list of older versions at https://www.visualstudio.com/vs/older-downloads (requires Microsoft ID and password).
    * Mac: Apple Command Line Tools, available at https://developer.apple.com/download/more/ (requires Apple ID and password).
    * Linux: g++ compiler available at http://www.cprogramming.com/g++.html or as part of the Linux distribution.

2. Download the wxWidgets 3.1.0 source code for your operating system from https://www.wxwidgets.org/downloads/.

3. Build wxWidgets.

5. In Windows, create the WXMSW3 environment variable on your computer to point to the wxWidgets installation folder, or in MacOS and Linux, create the dynamic link `/usr/<USERNAME>/local/bin/wx-config-3` to point to `/path/to/wxWidgets/bin/wx-config`.

6. As you did for wxWidgets, for each of the following projects, clone (download) the repository, build the project, and then (Windows only) create an environment variable pointing to the project folder. Build the projects in the following order, and assign the environment variable for each project before you build the next one:

<table>
<tr><th>Project</th><th>Repository URL</th><th>Windows Environment Variable</th></tr>
<tr><td>LK</td><td>https://github.com/NREL/lk</td><td>LKDIR</td></tr>
<tr><td>WEX</td><td>https://github.com/NREL/wex</td><td>WEXDIR</td></tr>
<tr><td>SSC</td><td>https://github.com/NREL/ssc</td><td>SSCDIR</td></tr>
<tr><td>SAM</td><td>https://github.com/NREL/SAM-private</td><td>SAMNTDIR</td></tr>
</table>

# Contributing

If you would like to report an issue with SAM or make a feature request, please let us know by adding a new issue on the [issues page](https://github.com/NREL/SAM/issues).

If you would like to submit code to fix an issue or add a feature, you can use GitHub to do so. The overall steps are:

1. Install GitHub on your computer.
2. Create a fork on GitHub.com using the link above.
3. Clone your fork to create a local copy on your computer.
4. Create a branch for your changes.
5. Make your changes to the code.
6. Build SAM and test it to make sure your code works as expected (see below).
7. Commit and push the changes to your fork.
8. Create a pull request that we will review and merge into the repository if approved.

We have not yet set up a test framework for the open-source project. We eventually hope to create a framework that will automatically test your commits to ensure that your contribution does not cause any problems with the software. For now, you can help to ensure that your code works with the rest of SAM by:

1. Compile SAM with your contribution for Windows, Mac, and Linux.

3. Fix any compiler warning messages.

3. Run simulations in the compiled program with several configurations.

For example, if you made changes to how the weather file processor works with solar resource data, you might want to run simulations with the different photovoltaic, concentrating solar power, and solar hot water heating model to make sure those models all work with your new code.

# License

SAM is licensed uder a mixed MIT/GPL V3 [license](LICENSE.md).
