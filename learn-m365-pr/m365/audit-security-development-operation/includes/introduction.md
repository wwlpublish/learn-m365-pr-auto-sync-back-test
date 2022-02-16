>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4xdb1]

Microsoft's Security Development Lifecycle (SDL) is a security assurance process focused on developing and operating secure software. The SDL provides detailed, measurable security requirements for developers and engineers at Microsoft to reduce the number and severity of vulnerabilities in our products and services. All Microsoft 365 Services must follow SDL requirements, and we continuously update the SDL to reflect the changing threat landscape, industry best practices, and regulatory standards for compliance.

## Phases of Microsoft's SDL

Microsoft 365 has built SDL practices into the DevOps model to ensure that security and privacy remains a core focus of our products and services. To safeguard customers and Microsoft 365's data, all development at Microsoft takes place in development environments completely segregated from production environments without any access to customer tenants. In addition, access to production environments is limited to engineers operating the services, and these environments are segregated from the Microsoft corporate network.

The SDL process at Microsoft can be thought of in terms of five phases of development. It begins by defining software requirements with security in mind. To do this, we ask security-relevant questions about what the application must accomplish. Does the application need to collect sensitive data? Will the application perform sensitive or important tasks? Does the application need to accept input from untrusted sources? Once relevant security requirements have been identified, we design our software to incorporate security features that meet these requirements. Our developers implement SDL and design requirements in the code, which we verify through manual code review, automated security tooling, and penetration testing. Finally, before code can be released, it undergoes final security and privacy review to ensure all requirements are met.

:::image type="content" source="../media/process-flow-diagram.png" alt-text="A process flow of SDL starting with training, requirements, design, implementation, verification, release, and response." border="false":::
  
Any changes, whether they are new or updated software builds, are made according to this SDL process. Once a build is approved for release, our systems gradually roll out the change, beginning with internal test environments and followed by deployment for Microsoft internal use. After internal release, changes are pushed to production environments in a staggered manner, limiting exposure in the event of a problem. At each stage of release, we actively monitor services for potential anomalies before proceeding to the next stage. Release monitoring includes automated test scenarios to confirm changes have been successfully applied without impacting existing functionality. By pausing and listening between each release stage, we can quickly detect and roll back any changes that cause unexpected problems without impacting the availability of Microsoft 365 Services.

In addition to the five core development phases, the SDL includes security activities before code is developed and after it is released. Microsoft personnel who develop our products and services are required to complete security-oriented training to cultivate a defensive mindset. After release, new production services are added for security monitoring.

In the units that follow, we will explore how Microsoft implements SDL requirements by:

- Requiring training for security awareness and secure development practices.
- Defining security and privacy requirements, maintaining up-to-date threat models, and requiring manual code review.
- Running SDL tools automatically to detect security issues in the code as part of the build process.
- Enforcing and testing operational security requirements to maintain security best practices.
- Performing security and privacy reviews prior to release.
- Using Component Governance (CG) to manage open-source software.

## Learn more

- [Microsoft Security Development Lifecycle (SDL)](https://www.microsoft.com/securityengineering/sdl?azure-portal=true)
- [Secure DevOps](https://www.microsoft.com/securityengineering/devsecops?azure-portal=true)
