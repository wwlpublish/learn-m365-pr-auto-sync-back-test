Now that you understand various tools and technologies Microsoft 365 uses to enforce access control, let's discuss how service team accounts are created. The environment for Microsoft 365 Services is segregated from the Microsoft Corporate environment. This means Microsoft Corporate environment user accounts do not provide any access to the Microsoft 365 Services environment. Service team accounts are only created for personnel whose job responsibilities require access to the production environment to manage Microsoft 365 Services. In addition, service team accounts cannot be created without first meeting the eligibility requirements outlined in this unit.

When an engineer is assigned to a service team to support production services, they request eligibility for a service team account through the Identity Management Tool (IDM). The request for eligibility triggers a series of personnel checks to ensure the engineer has passed all screening requirements, completed necessary training, and received appropriate management approval prior to account creation. Only after meeting all eligibility requirements can a service team account be created for the requested environment.

![A workflow diagram, starting with Microsoft Service Engineer joining the service team. They must go through personnel screening and role-based training in order to be eligible to request for service team Account. After authorized manager's approval, the account is created.](../media/personnel-screening-diagram.png)

## Personnel screening

Microsoft 365 screening practices align with Microsoft's Corporate Standards and National Institute of Standards and Technology (NIST) 800-53 for personnel screening.

To the extent permissible by local law, pre-employment screening checks include the following:

- Confirmation of identity
- Criminal history check
- Confirmation of highest level of academic achievement
- Employment history
- Global sanctions and enforcement check

Staff involved in the development, operation, or delivery of online services to government or commercial cloud customers may be subject to additional checks to comply with relevant privacy laws. In addition, rescreening every two years is required to maintain eligibility for a service team account. Access is automatically revoked for personnel who do not pass rescreening or fail to complete rescreening requirements.

IDM enforces personnel screening requirements and denies service team account eligibility to anyone who does not meet relevant screening requirements. In addition, IDM automatically disables service team accounts for users who do not pass required rescreening.

## Training

Each engineer working on Microsoft 365 service teams is provided with training appropriate to their role. Initial training occurs when a new employee begins working at Microsoft, and annual refresher training takes place every year thereafter. The training is designed to provide the employee with an understanding of Microsoft's fundamental approach to security.

Training requirements are enforced by IDM. Failure to complete required training prevents eligibility for new service team accounts and automatically disables existing service team accounts.

## Management approval and account creation

After IDM has confirmed all eligibility requirements are met, the service team account request is sent to authorized managers for review and approval. Only after the request is approved can a service team account be created.

Baseline service team accounts are limited to broad system metadata read access used for regular troubleshooting. This default access is read-only, with no administrative privileges or access to customer content. Moreover, baseline service team accounts cannot request elevated access through Lockbox without specific role assignments allowing elevation requests for specific tasks and operations. These limitations are the foundation of Microsoft 365's privileged access management strategy, which is built on the principle of Zero Standing Access.

## Learn more

- [Microsoft cloud background check](/compliance/assurance/assurance-cloud-background-check?azure-portal=true)
