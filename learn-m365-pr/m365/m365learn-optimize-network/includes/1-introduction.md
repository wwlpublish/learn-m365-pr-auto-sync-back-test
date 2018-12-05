# Introduction

Prior to cloud-based services, IT departments optimized network traffic between users and the on-premises datacenters where the server-based resources were located. Internet traffic was typically not vital to the productivity of the organization and was routed to an Internet connection in a central or regional office.

For cloud-based services, traffic for key productivity services is now Internet traffic that must be optimized for performance. Furthermore, Microsoft 365 services are hosted through a globally distributed Software-as-a-Service (SaaS) infrastructure, with Microsoft Global Network locations all over the world.

Network performance optimization for Microsoft 365 traffic requires a new approach that includes:

- Using Internet connections at each office, not just regional or central offices, to reach the Microsoft Global Network location nearest to the office.
- Removing unnecessary intermediate destinations.
- Bypassing edge devices for specific types of traffic to Microsoft 365 services.

View this video for an overview of the steps you take to optimize your network for connectivity and performance to Microsoft 365.

[A conceptual video that describes and shows:

- The three categories of Office 365 traffic (Optimize, Allow, and Default), highlighting the Optimize and Allow categories as the ones that need to be addressed for networking traffic optimization and onboarding.
- How non-local Internet connections and non-local DNS servers introduce delay and route traffic to non-local Microsoft network front ends for Optimize and Allow traffic.
- A typical network hairpin configuration and how it can be modified to eliminate hairpin paths.
- How to configure edge devices for traffic bypass and the resulting impact on performance.
]
 
## Learning objectives

In this module you’ll be able to: 

- State the three categories of Office 365 endpoints and name which ones must be bypassed for the best network performance.
- Describe the attributes of local Internet connections for all offices of an organization.
- Explain the impact of network hairpins on performance.
- Explain how edge devices must be configured for Microsoft 365 traffic bypass for the best performance.

## Prerequisites:

- Knowledge of Internet connections and typical network edge devices.

Next: Microsoft 365 endpoint categories
