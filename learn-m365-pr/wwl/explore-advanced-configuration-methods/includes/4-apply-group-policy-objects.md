GPOs apply in a consistent order that allows you to predict which settings are effective when there are conflicting settings in GPOs that apply to a user or computer. GPOs that apply later in the process overwrite any conflicting policy settings that applied earlier.

:::image type="content" source="../media/gpmc1-a828502e-754f30f4.png" alt-text="Screenshot of Group Policy Management Console":::


GPOs apply in the following order:

1.  **Local GPOs**. Each operating system that is running Windows Vista or newer potentially has a local GPO configured already.
2.  **Site GPOs**. Policies that link to sites process next.
3.  **Domain GPOs**. Policies that link to the domain process next. There often are multiple policies at the domain level. These policies process in order of preference.
4.  **OU GPOs**. Policies linked to OUs process next. These policies contain settings that are unique to the objects in that OU. For example, Sales users might have special required settings. You can link a policy to the Sales OU to deliver those settings.
5.  **Child OU policies**. Any policies that link to child OUs process last.

AD DS objects in the containers receive the cumulative effect of all policies in their processing order. In the case of a conflict between settings, the last policy applied takes effect. For example, a domain-level policy might restrict access to registry editing tools, but you could configure an OU-level policy and link it to the Information Technology (IT) OU to reverse that policy. Because the OU-level policy applies later in the process, access to registry tools would be available to users in the IT OU.

If multiple policies apply at the same level, an administrator can assign a preference value to control the order of processing. The default preference order is the order in which the policies were linked. You also can disable the user or computer configuration of a GPO.

## Local GPOs

Each Windows-based computer has one local GPO that contains default computer and user settings, regardless of whether the computer is part of an AD DS environment. In addition to this default local GPO, you can create custom local user GPOs.

A local GPO is the least influential object in an AD DS environment because its settings can be overwritten by GPOs that are associated with sites, domains, and OUs. In a non-networked environment, or in a networked environment that does not have a domain controller, local GPO settings are important because other GPOs do not overwrite them. Stand-alone computers only use local GPOs to control the environment.

Windows Vista and newer Windows client operating systems, and Windows Server 2008 and newer Windows Server operating systems, have an added feature: multiple local GPOs. Since Windows 8 and Windows Server 2012, you also can have different user settings for different local users, but this is only available for users' configurations that are in Group Policy. In fact, there is only one set of computer configurations available that affects all users of the computer.

Computers that run Windows 7 and newer versions provide this ability with the following three layers of local GPOs:

 -  Local Group Policy (contains the computer configuration settings)
 -  Administrators and Non‑Administrators Local Group Policy
 -  User-specific Local Group Policy

## Domain GPOs

You can use Group Policy in an AD DS environment to provide centralized configuration management. Domain GPOs are created and linked to objects within an AD DS infrastructure. The settings in the GPO then affect the computers and users that are within those objects, depending on how you configure the application of the GPO.

## Options for modifying Group Policy processing

You can modify the default processing of GPOs by using:

 -  **Security filtering**. You can use security filtering to specify users, computers, or groups that are able or not able to process a GPO. For example, you could specify that members of the Technical Support group have special security settings.
 -  **Enforcement**. You can use enforcement to ensure that settings in a specific GPO apply regardless of any lower-level GPOs that would normally override this GPO. For example, you could specify standardized security settings at the domain level.
 -  **Block inheritance**. You can use block inheritance to prevent a lower-level OU from inheriting settings from a higher-level OU. For example, you could block settings applied at the domain level from affecting users in the IT OU.

> [!NOTE]
> When a link is enforced and a lower-level OU blocks inheritance, the settings in the enforced GPO apply.
