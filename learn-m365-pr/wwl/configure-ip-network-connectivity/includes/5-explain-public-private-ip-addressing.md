Devices and hosts that connect directly to the Internet require a public IPv4 address. However, hosts and devices that do not connect directly to the Internet do not require a public IPv4 address.

#### Public IPv4 addresses

Public IPv4 addresses, which IANA assigns, must be unique. Usually, your ISP allocates to you one or more public addresses from its address pool. The number of addresses that your ISP allocates to you depends upon how many devices and hosts that you have to connect to the Internet.

#### Private IPv4 addresses

The pool of IPv4 addresses is becoming smaller, so IANA is reluctant to allocate superfluous IPv4 addresses. Technologies such as network address translation (NAT) enable administrators to use a relatively small number of public IPv4 addresses, and at the same time, enable local hosts to connect to remote hosts and services on the Internet. IANA defines the following address ranges as private. Internet-based routers do not forward packets originating from, or destined to, these ranges.

:::row:::
  :::column:::
    **Class**
  :::column-end:::
  :::column:::
    **Mask**
  :::column-end:::
  :::column:::
    **Range**
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    A
  :::column-end:::
  :::column:::
    10.0.0.0/8
  :::column-end:::
  :::column:::
    10.0.0.0 - 10.255.255.255
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    B
  :::column-end:::
  :::column:::
    172.16.0.0/12
  :::column-end:::
  :::column:::
    172.16.0.0 - 172.31.255.255
  :::column-end:::
:::row-end:::
:::row:::
  :::column:::
    C
  :::column-end:::
  :::column:::
    192.168.0.0/16
  :::column-end:::
  :::column:::
    192.168.0.0 - 192.168.255.255
  :::column-end:::
:::row-end:::


In today’s network environments, it is most common for organizations to have one or more public, routable IP addresses from an ISP assigned to the external interfaces of their firewall appliances. Additionally, they use the designated private IP subnets internally.
