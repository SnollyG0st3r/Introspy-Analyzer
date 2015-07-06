Introspy-Analyzer
=================

Introspy is a set of iOS and Android tools designed to help understand what an
iOS or Android application is doing at runtime and assist in the identification
of potential security issues.

This is the repository for Introspy-Analyzer, a tool to turn a database
generated by Introspy-iOS or Introspy-Android into an HTML report.

For more information about Introspy-Android see:
https://isecpartners.github.io/Introspy-Android/

For more information about Introspy-iOS see:
https://isecpartners.github.io/Introspy-iOS/


Installation
------------
To install Introspy-Analyzer, you can either install it as a package so it can be executed from anywhere (recommended) or just clone this repo and run it as a script.

As a package:

    pip install git+https://github.com/iSECPartners/Introspy-Analyzer.git
    # (From anywhere)
    python -m introspy <args>

Or locally:

    git clone https://github.com/iSECPartners/Introspy-Analyzer.git
    python Introspy-Analyzer.introspy <args>


Generating HTML Reports
-----------------------

Introspy-Analyzer requires Python 2.6 or 2.7.

Introspy-iOS or Introspy-Android should first be run on the tester's device in
order to collect information about the application to be reviewed. This data
will be stored in a database on the device.


### With Introspy-iOS

For iOS, databases can be fetched directly by Introspy-Analyzer over SSH:

    python -m introspy -p ios -o output -f 192.168.1.12


### With Introspy-Android

For Android, the database will first have to be manually recovered (for example
using adb). Then, a report can be generated using:

    python -m introspy -p android -o output introspy-android.db


Command Line Output
-------------------

While the HTML formatted report is the most digestable format, Introspy-Analyzer
can also be used directly from the command-line to display all recorded function
calls:

    python -m introspy -p ios -l introspy.db


Enumerations - iOS Only
-----------------------

For iOS databases, Introspy-Analyzer also allows users to enumerate various data
from the list of traced calls (via `--info`), inlcuding a list of all of the
unique URLs accessed by the application (urls) and all files accessed (files).

    python -m introspy -p ios -i urls introspy.db


