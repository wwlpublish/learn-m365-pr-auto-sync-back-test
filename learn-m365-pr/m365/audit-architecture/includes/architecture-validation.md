Secure system architectures must be implemented and operated correctly to provide the level of security and resilience they were designed for. Microsoft 365 architecture is validated regularly, automatically, and using cloud-based tools to verify alignment with our security principles and to continuously test isolation and resiliency features. We use two primary forms of architecture validation:

- **Architectural and configuration assessment:** verifying that promises we make about our service architecture (for example, that specific networks are correctly segmented or that machines are up to date with required patches) hold and do not regress.
- **Post-exploitation validation:** simulating attacks directly against our infrastructure, with the goal of verifying that our monitoring and response systems work as expected in the production environment.

Both forms of validation result in analytics and reports that allow us to quickly identify and remediate failures. The tools we use for validation are configured to run continuously and to target the entire service, or a representative sample when completeness is not feasible. Like our monitoring and response systems, our validation systems take a service-wide view. For example, our attack simulation tools are designed to intelligently navigate throughout the service infrastructure by using a cloud-based command and control system to coordinate actions.

As part of our Assume Breach mentality, we design our service architecture to minimize the damage that an attack could cause. Network isolation is a great example of this. But it's possible for network isolation to degrade over time. Our architectural validation works to automatically identify instances where the current state of the service has drifted from the desired state. For example, if a new service is introduced that listens on a previously unused port, an entire section of the service may be at risk of lateral movement through compromise of the new service. Architectural validation helps to detect changes to the architecture that might degrade its security posture and flag these changes for review and mitigation.

The goal of architecture validation is to ensure the security capabilities of our service infrastructure function as expected. Implementing a security control is simply not enough. For this reason, our systems regularly validate our controls to ensure that they work to protect our systems and customers.

## Learn more

- [Behind the Scenes: Securing the Infrastructure Powering the Microsoft 365 Service](https://download.microsoft.com/download/c/4/5/c45b197e-f0d9-4f40-bd5f-ed8fc7d0cd8c/M365DCSecurityIntro_Whitepaper.pdf)
