When you troubleshoot name resolution, you must understand which name resolution methods the computer is using, and in what order. As you know, the operating system resolves host names either by using a local text file named Hosts, or by using DNS.

> [!NOTE]
> Windows appends the primary and connection-specific suffixes to all names that it is resolving. If the name resolution is unsuccessful initially, Windows applies parent suffixes of the primary DNS suffix. For example, if the DNS resolver attempts to resolve the name **LON-CL1**, Windows appends the .adatum.com suffix to attempt resolution. If that is unsuccessful, the operating system appends .com to the name, and attempts to resolve it once again. You can configure this behavior from the **Advanced TCP/IP Settings** page.

The primary tools for troubleshooting host name resolution are **IPConfig** and **NSLookup**, and their Windows PowerShell equivalents **Get-NetIPAddress**, **Get-NetIPv4Protocol**, and **Resolve-dnsname.**

> [!TIP]
> Be sure to clear the DNS resolver cache between resolution attempts.

### The process for troubleshooting name resolution

If you can't connect to a remote host, and if you suspect a name resolution problem, you can troubleshoot name resolution by using the following procedure:

1.  Open an elevated command prompt, and then clear the DNS resolver cache by typing the following command:
    
    ```
    IPConfig /flushdns
    
    ```
    
    > [!NOTE]
    > Alternately, you can use the Windows PowerShell cmdlet **Clear-DnsClientCache**.
2.  Attempt to verify connectivity to a remote host by using its IP address. This helps you identify whether the issue is due to name resolution. You can use the **Ping** command or the **test-connection** Windows PowerShell cmdlet. If the **Ping** command succeeds with the IP address but fails by the host name, the problem is with name resolution. **Note:** Remember that the remote host must allow inbound ICMP echo packets through its firewall for this test to be viable.
3.  Attempt to verify connectivity to the remote host by its host name, by using the FQDN followed by a period. For example, type the following command at the command prompt:
    
    ```
    Test-connection LON-cl1.adatum.com
    
    ```
    
    > [!NOTE]
    > You also can use the **ping** command.
4.  If the test is successful, the problem is likely unrelated to name resolution.
5.  If the test is unsuccessful, edit the **C:\\windows\\system32\\drivers\\etc\\hosts** text file, and then add the appropriate entry to the end of the file. For example, add this line, and then save the file:
    
    ```
    172.16.0.51 LON-cl1.adatum.com
    
    ```
6.  Perform the test-by-host-name procedure again. Name resolution should now be successful.
7.  Examine the DNS resolver cache to verify that the name resolved correctly. To examine the DNS resolver cache, type the following command at a command prompt:
    
    ```
    IPConfig /displaydns
    
    ```
    
    > [!NOTE]
    > You also can use the Windows PowerShell cmdlet **Get-DnsClientCache**.
8.  Remove the entry that you added to the Hosts file, and then clear the resolver cache once more. At the command prompt, type the following command, and then examine the contents of the filename.txt file to identify the failed stage in name resolution:
    
    ```
    NSLookup.exe –d2 LON-cl1.adatum.com. \> filename.txt
    
    ```
    
    The Windows PowerShell equivalent command is:
    
    ```
    Resolve-dnsname lon-cl1.adatum.com. \> filename.txt
    
    ```

### Interpreting NSLookup output

The NSLookup command line tool displays information that you can use to diagnose your Domain Name System (DNS) infrastructure. Before using this tool, you should be familiar with how DNS works. The nslookup command-line tool is available only if you have installed the TCP/IP protocol. The nslookup command-line tool has two modes: interactive and noninteractive.

 -  **Interactive**. If you need to look up only a single piece of data, we recommend using the non-interactive mode. For the first parameter, type the name or IP address of the computer that you want to look up. For the second parameter, type the name or IP address of a DNS name server. If you omit the second argument, nslookup uses the default DNS name server.
 -  **Noninteractive**. If you need to look up more than one piece of data, you can use interactive mode. Type a hyphen (-) for the first parameter and the name or IP address of a DNS name server for the second parameter. If you omit both parameters, the tool uses the default DNS name server.

You should understand how to interpret the **NSLookup** command output so that you can identify whether the name resolution problem exists with the client computer’s configuration, the name server, or the configuration of records within the name server-zone database. In the first section of the following output sample, the client resolver performs a reverse lookup to determine the DNS server host name. You can view the query **10.0.16.172.in-addr.arpa, type = PTR, class = IN** in the **QUESTIONS** section. The returned result, **name = LON-dc1.adatum.com**, identifies the host name of the petitioned DNS server:

```

\------------

SendRequest(), len 41

HEADER:

opcode = QUERY, id = 1, rcode = NOERROR

header flags: query, want recursion

questions = 1, answers = 0, authority records = 0, additional = 0

QUESTIONS:

10.0.16.172.in-addr.arpa, type = PTR, class = IN

\------------

\------------

Got answer (73 bytes):

HEADER:

opcode = QUERY, id = 1, rcode = NOERROR

header flags: response, auth. answer, want recursion, recursion avail.

questions = 1, answers = 1, authority records = 0, additional = 0

QUESTIONS:

10.0.16.172.in-addr.arpa, type = PTR, class = IN

ANSWERS:

\-\> 10.0.16.172.in-addr.arpa

type = PTR, class = IN, dlen = 20

name = LON-dc1.adatum.com

ttl = 1200 (20 mins)

\------------

Server: LON-dc1.adatum.com

Address: 172.16.0.10


```
