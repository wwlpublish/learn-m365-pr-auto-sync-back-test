While well-funded and highly organized security operations teams often have the most sophisticated detection mechanisms in place, these teams still need experts that can run guided investigations to locate and stop certain threats. For example, sophisticated attackers often take advantage of normal system functionality that leaves almost no identifiable traces. Yes, behavior-based detection algorithms powered by machine learning and AI can learn and respond quickly. But human experts still play the most valuable role in threat hunting. Their role is especially important if they know the network and are familiar with how attacks might play out.

### What is threat hunting?

Cyberthreat hunting, or simply threat hunting, is a proactive cybersecurity activity. Its goal is to find threats that are either buried under massive quantities of security signals and alert data, or aren't flagged by security products. It's generally a manual process, although as we'll discuss in a moment, Microsoft Threat Protection can make the process much less tedious and time-consuming.

During threat hunting, security operations practitioners apply threat intelligence takeaways, whether from their own internal research or external research. With this information in hand, they then devise ingenious ways to determine the existence of an otherwise undetected threat. To do that, they need efficient access to comprehensive data about events and entities in their network. They also need a good, quantifiable understanding of normal states or baselines.

Threat hunting lets analysts work with established baselines and highlight behavior that might be interesting. Given the right tools, analysts can tailor their threat hunting activities to their environments and the threats that they'll likely meet. For instance, they can hunt for unusual behavior—like unexpected network connections—that might indicate that an in-house app or an account has been compromised.

The process of establishing the baselines themselves can also be part of threat hunting. To establish baselines, analysts need tools that can quickly look backwards and forwards in time. These tools must provide data that's sufficiently granular for defining normal states.

Effective threat hunting relies on:

 -  Comprehensive, well-structured, and retrievable event and system data.
 -  Threat intelligence: knowledge about threat actors or actor infrastructure, methodologies, and indicators.
 -  Granular baseline information that represents normal activity and states.

### Threat hunting example

Let’s look at what Jessica, Contoso's Security Operations admin, might go through:

1.  Jessica learns about a new vulnerability that affects one of the product suites in Contoso's environment. In this case, the attacks are against a known web content management system (CMS).
2.  After doing some more research, Jessica is unable to determine how attackers will use this vulnerability. Because the release of this vulnerability is so recent, there's no historical data Jessica can analyze to determine how attackers may use this threat in Contoso's environment. Contoso's situation is made even more arduous by the fact that a patch to remedy the issue isn't yet available.
3.  Jessica creates a query for behaviors tied to the processes involved in this vulnerability. This query determines an existing baseline and normal behavior. Jessica then modifies existing queries to only return what's not expected.
4.  Jessica also creates rules so that the queries run regularly and send notifications to the security operations team whenever there are matches.
5.  Because Jessica completed extensive research and constructed excellent queries—carefully considering the possibility that some unaffected machines might display threat-like behavior—each match to one of the queries is a valuable threat-hunting find. These matches include unusual process activities that may actually be attempts to abuse Contoso's vulnerable CMS.

### Threat hunting in Microsoft Threat Protection

With cloud-based storage and compute solutions, organizations can now easily collect massive quantities of data. But as larger data sets get stored, there's a growing need to efficiently manipulate and make sense of them. It's at this point where Microsoft Threat Protection shines.

The threat hunting capabilities in Microsoft Threat Protection enable you to find threats across your users, endpoints, email, productivity tools, and apps. After Microsoft Threat Protection finds these threats, it automatically flags and remediates them.

Microsoft Threat Protection itself is made possible by the power of the Azure cloud coupled with insights from the Microsoft Intelligent Security Graph. At the most basic level, the Intelligent Security Graph collects all the security-related data from every Microsoft application. It then crunches this massive amount of threat intelligence and security data from across Microsoft’s portfolio against indicators, expert human rules, and machine learning (ML) algorithms in Microsoft AI. Intelligent Security Graph then generates meaningful alerts, identifying threat components and activities that automated investigation and response (AIR) capabilities can remediate.

For example, Microsoft Threat Protection distinguishes between malicious and normal attempts to write to the system registry. It does so by looking at millions of examples of registry writes and their contexts. These contexts include the files or processes involved, file pedigrees, whatever was written to the registry, the time the writes were completed, and so on. With this much baseline information, Microsoft AI can confidently raise alerts and start conducting remediation activities, rapidly placing harmful registry modifications and associated files in quarantine.

Microsoft AI and other automated systems are effective at finding threats. However, human intuition and flexibility can still beat them when dealing with highly specialized or unusual scenarios. Microsoft Threat Protection's threat hunting capabilities provide the tools needed by human analysts to let them:

 -  **Effectively access and handle large sets of data.** Microsoft Threat Protection's interface is easy-to-use, and it's responsive and labels and organizes data well. At the same time, log storage is as straightforward as any competitive cloud-based storage and compute solution that can be deployed and scaled without professional system integrators and other specialists.
 -  **Automate monitoring of interesting matches to new data**. Microsoft Threat Protection monitors new activities for matches to the attack activities that analysts have modeled. Without this automation, analysts will be manually looking for matches as new data comes in.

## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”