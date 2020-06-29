>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4xdb2]

To support our developers in implementing security requirements during code development and after release, Microsoft provides a suite of secure development tools to automatically check source code for security flaws and vulnerabilities. Microsoft defines and publishes a list of approved tools for our developers to use, such as compilers and development environments, along with their built-in security checks. Our developers use the latest versions of approved tools to take advantage of new security features.

In addition to providing secure development tools, Microsoft implements and enforces SDL code analysis requirements using automated security tooling. Many of these tools are built into the commit pipeline and automatically analyze code for security flaws as it is checked in and as new builds are compiled and tested. Issues uncovered by our automated security tools must be fixed before new builds can pass security review and be approved for release.

Our automated security tooling falls into several broad categories for testing code at different stages of development, from the time code is committed to when it is released for operation in production environments. The table below summarizes the types of tools we use at Microsoft for SDL code analysis.

| SECURITY TOOL | Description |
|-|-|
| STATIC CODE ANALYSIS | Analyzes source code for potential security flaws, including the presence of credentials in code. |
| BINARY ANALYSIS | Assesses vulnerabilities at the binary code level to confirm code is production ready. |
| ENCRYPTION SCANNING | Validates encryption best practices in source code and code execution. |
| FUZZ TESTING | Uses malformed and unexpected data to find defects in code and validate proper error handling. |
| CONFIGURATION VALIDATION | Analyzes the configuration of production systems against security standards and best practices. |

## Static code analysis and binary analysis

Analyzing source code prior to compilation provides a highly scalable method of security code review and helps ensure that secure coding policies are followed. Our static code analysis tools, such as Roslyn, scan source code for common vulnerabilities and security flaws, such as unsafe functions. We also use CredScan to detect credentials and other secrets embedded in source code. Flaws discovered by these tools are flagged as bugs for our developers to fix.

Most of our static code analysis tools are integrated into the commit pipeline to identify vulnerabilities each time the software is built and prevent insecure code from being checked in. We also integrate static code analysis tools into the developer environment to spot certain flaws, such as the presence of unsafe functions, and replace insecure code with safer alternatives while the developer is actively coding.

In addition to static analysis of source code, we use automated tooling like BinSkim to scan compiled code for security flaws at the binary level, such as compiler/linker settings and other security relevant binary characteristics. Our binary analysis tools are executed on each build to detect binary security flaws and flag them for remediation before a build can be released.

## Encryption scanning

Microsoft takes care to ensure all data, including security-sensitive information and management and control data, is protected from unintended disclosure or alteration when it is being transmitted or stored using strong encryption. The SDL limits developers to approved encryption modules that implement encryption reliably and securely. To enforce this policy, our tools scan and validate cryptography implementations in source code and during code execution. Insecure use of cryptography is flagged for remediation and validated during security review.

## Fuzz testing

Fuzzing is a form of dynamic testing used to systematically find defects in code that account for many of the most severe security bugs. Fuzzing is capable of finding remote code execution (buffer overruns), permanent denial-of-service (unhandled exceptions, read AVs, thread hangs), and temporary denial-of-service (leaks, memory spikes) vulnerabilities.

Microsoft’s SDL requires fuzz testing to validate all inputs from untrusted sources, including user inputs, inputs received from networks, and file uploads. Our build pipelines incorporate automated fuzz testing tools that run parallel to the build process. Separate dynamic code testing tools are configured to automatically scan and fuzz web APIs for potential security flaws. Security flaws detected by our fuzz tooling are flagged for remediation and validated during security review.

## Configuration validation

At Microsoft, our operations teams are integrated with development teams using the DevOps model. As part of DevOps, we continue to validate the secure operation of our code after a build is a released to production environments. Operations teams use secure deployment checklists, baseline configuration scanning, vulnerability scanning, and host-based intrusion detection systems to validate that software is configured and operated according to security best practices. Configuration flaws detected by the operations teams are flagged for remediation, while any bugs discovered by the operations team are assigned to the appropriate development team to be fixed at the code level. By integrating operational security into our SDL requirements, we help to ensure the ongoing security of our products and services even after release.

## Learn more

- [What are Microsoft SDL practices?](https://www.microsoft.com/securityengineering/sdl/practices?azure-portal=true)
- [DevOps at Microsoft](https://docs.microsoft.com/azure/devops/learn/devops-at-microsoft/?azure-portal=true)
