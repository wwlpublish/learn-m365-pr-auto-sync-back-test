In a computing sense, an identity can be a user, device, or application. The first step in a successful Zero Trust framework is being able to secure these identities.

Knowing who is making a request to access resources in your digital estate is essential to controlling access to sensitive data. When a user or device has been authenticated, they're given appropriate authorization, which grants them access to resources, assets, and data.

Securing identities with a Zero Trust framework, also referred to as identity management, applies the principle of continually verifying users. Before allowing access, organizations must validate the identity of the user and other properties, such as their location, the health of their device, their role in the organization, and the type of data they're attempting to access. To achieve this end state, a Zero Trust strategy relies heavily on automated technologies and enforcement of policies to ensure security and provide a great user experience.

A Zero Trust approach focuses on _authenticating_ and _authorizing_ every connection, device, user, or network flow.

## Authentication and authorization

As part of a Zero Trust strategy, users, applications, and devices should be strongly authenticated and evaluated before being granted authorization to access your resources.

- **Authentication** is a process that requires users to confirm that they are who they claim to be.
- **Authorization** is an automated process where the system determines which level of access each user is granted.

## Authentication methods

It's important for organizations to establish the identity of users, devices, and applications. The process of authentication involves determining a user's initial identity and binding them to it using various techniques. Below are some of the common authentication methods practiced by organizations:

- **Passwords**: Using passwords is the most basic form of authentication based on something that the user knows, for example, a string of letters, numbers, or special characters. There are limitations to this type of authentication because credentials can be stolen or guessed by attackers.
- **Multifactor authentication (MFA)**: This technique requires more than one distinct factor to prove the user is who they say they are. Multifactor authentication typically uses one or more of:

  - Something a user knows, such as a username or password.
  - Something the user has, like a security token.
  - Something the user is, such as fingerprints, retina, or voice.

One or more of these can be used to confirm the request is genuine.

- **Biometric**: This technique uses biological characteristics, such as fingerprints, face, voice, or retina recognition to verify a user's identity. Using biometrics removes the burden of typing the password and reduces the chances of shoulder surfing by an attacker.
- **Passwordless**: This authentication is the latest technology that eliminates using passwords. It combines biometric, multifactor authentication, and mobile apps to remove the need for a password.

## Difference between strong and weak authentication

Strong authentication is when the method combines two or more factors to verify the identity of a user or device. For example, multifactor authentication combines two or more independent factors to confirm the user's identity. This adds an extra layer of security as it evaluates the identity of a user based on given details, such as their device or location. In case of compromised credentials, unauthorized users won't be able to meet the second or third level of authentication required.

Weak authentication is when the strength of the method being used is flawed and uncertain. It might lead to scenarios where passwords can be easily cracked, or the attackers could effortlessly bypass authentication to gain access.
