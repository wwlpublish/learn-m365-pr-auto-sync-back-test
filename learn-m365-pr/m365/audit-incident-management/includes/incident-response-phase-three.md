>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wzgz]

Based on the analysis coordinated by the Microsoft 365 Security Response team, an appropriate containment, and recovery plan is developed to minimize the impact of the security incident and remove the threat from the environment. Relevant service teams implement the plan with support from the Microsoft 365 Security Response team to ensure the threat is successfully eliminated and the impacted services undergo a complete recovery.

## Containment

The primary goal of containment is to limit harm to Microsoft systems, applications, customers, and customer data. During this phase, the Microsoft 365 Security Response team works with affected service teams to limit the impact of the security incident and prevent further damage. Various automated responses within Microsoft 365 aid the team in containing the incident.

Data collection and analysis continue through the containment phase to ensure that the root cause of the incident has been correctly identified and that all impacted services and tenants are included in the eradication and recovery plan. Successfully tracing all impacted services makes full eradication and recovery possible.

## Eradication

Eradication is the process of eliminating the root cause of the security incident with a high degree of confidence. The goal of eradication is twofold: to evict the adversary completely from the environment, and to mitigate any vulnerabilities that contributed to the incident or could enable the adversary to reenter the environment.

Eradication steps to evict the adversary and mitigate vulnerabilities are based on the analysis performed in the previous incident response phases. The Microsoft 365 Security Response team coordinates with affected service teams to ensure the threat is successfully removed from the environment. Recovery is not possible until the threat has been removed and its underlying causes have been resolved.

## Recovery

When the Microsoft 365 Security Response team is confident the adversary has been evicted from the environment and known vulnerabilities have been remediated, they work with affected service teams to initiate recovery. Recovery brings affected services to a known secure configuration. The recovery process includes identifying the last known good state of the service, restoring from backups to this state, and confirming the restored state mitigates the vulnerabilities that contributed to the incident.

A key aspect to the recovery process is enhanced detection controls to validate that the recovery plan has been successfully executed and that no signs of breach remain within the environment. Examples of additional detection controls include increased network-level monitoring, targeted alerting for attack vectors identified during the incident response process, and additional security team vigilance for critical resources. Enhanced monitoring helps to ensure that eradication was successful, and that the adversary is unable to reenter the environment.

## Learn more

- [Microsoft 365 security incident management: Containment, eradication, and recovery](/compliance/assurance/assurance-sim-containment-eradication-recovery?azure-portal=true)
