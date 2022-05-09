Application Compatibility Toolkit (ACT) is a set of tools that you can use to perform an inventory of applications, analyze compatibility of applications, and mitigate any compatibility issues. Organizations typically use ACT when planning a new operating system deployment to ensure that all applications function properly.

ACT includes the following features:

 -  **The ACT database**. This tool contains known application compatibility issues and resolutions.
 -  **The Compatibility Administrator Tool**. This tool provides compatibility fixes (previously known as shims) that enable earlier application versions to run on newer Windows operating systems.
 -  **The Setup Analysis Tool (SAT)**. This tool monitors an application’s installation process and identifies issues that relate to installation.
 -  **The Standard User Analyzer**. This tool identifies any issues that relate to running an application as a standard user.
 -  **The Update Compatibility Evaluator (UCE)**. This tool identifies any issues that relate to implementing new Windows operating system updates.

The majority of functionality that ACT provides is currently available in the Upgrade Analytics solution, which is part of Microsoft Operations Management Suite (OMS). After you deploy the OMS agent to the computers on which you want to analyze the applications and enable Windows telemetry, Upgrade Analytics collects data that is necessary to detect any potential compatibility issues and provides recommendations regarding their resolution. It also guides you through the process of applying recommended fixes, provides a searchable inventory of computers and applications, and displays application usage data.
