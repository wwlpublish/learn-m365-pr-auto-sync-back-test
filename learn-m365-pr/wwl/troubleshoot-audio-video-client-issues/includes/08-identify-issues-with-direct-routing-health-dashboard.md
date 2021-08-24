As an organization, you've rolled out Microsoft Teams with chat, teams, channels, and apps. Maybe you've deployed meetings and conferencing. Now you're ready to add cloud voice workloads. To do so, you've decided to use your own telephony carrier for Public Switched Telephone Network (PSTN) connectivity by using Phone System Direct Routing. With Direct Routing, you can use Teams Phone System with virtually any telephony carrier. Microsoft Phone System Direct Routing enables your organization to connect its on-premises telephony infrastructure to Microsoft Teams. 

Once an organization has configured its Direct Routing environment, there are several components required to make sure everything is running smoothly. For example, you may have a Session Border Controller (SBC), or maybe multiple SBCs connected to Microsoft Teams. You may even have a third-party private branch exchange (PBX) system, as shown in the following diagram:

‎:::image type="content" source="../media/environment-diagram.png" alt-text="Direct routing diagram":::

The following tools can be used to monitor and troubleshoot Direct Routing issues:

* **SBC and private branch exchange (PBX) logs**. Your SBC could also be connected to other environments, giving you access to logs that help you troubleshoot or debug issues. If your SBC communicates with a third-party PBX, you can also collect logs from there.
* **Public switched telephone network (PSTN) provider**. You can also work with your PSTN provider to get more insight into issues that may arise from the PSTN side of your environment.
* **Health Dashboard for Direct Routing**. You can monitor  the connection between your Session Border Controller (SBC) and the Direct Routing interface with Direct Routing Health Dashboard.


## Direct Routing Health Dashboard

The Direct Routing Health Dashboard enables an organization to monitor information about its SBC, the telephony service, and the network parameters between its SBC and the Direct Routing interface.

This information can help identify issues, including the reason for dropped calls. For example, the SBC may stop sending calls if a certificate on the SBC has expired or if there are network issues. 

The Health Dashboard monitors two levels of information:

- Overall health of the connected SBCs
- Detailed information about the connected SBCs

You can view the Health Dashboard in the Microsoft Teams admin center by navigating to **Voice** > **Direct Routing**. 

### Overall health of the connected SBCs

The Health Dashboard provides the following information related to overall health of the connected SBCs:

‎:::image type="content" source="../media/direct-routing-dashboard-stats-1.png" alt-text="Shows Health Dashboard statistics":::

- **Direct Routing summary**. Shows the total number of SBCs registered in the system. Registration means that the tenant administrator added an SBC by using the ```New-CsOnlinePSTNGateway``` command. If the SBC was added in PowerShell but never connected, the Health Dashboard shows it in an unhealthy status.

- **SBC**. The FQDN of the paired SBC.

- **Network Effectiveness Ratio (NER)**. The NER measures the ability of a network to deliver calls by measuring the number of calls sent versus the number of calls delivered to a recipient.  

   The NER measures the ability of networks to deliver calls to the far-end terminal, excluding user actions resulting in call rejections.  If the recipient rejected a call or sent the call to voicemail, the call is counted as a successful delivery. This scenario means that an answer message, a busy signal, or a ring with no answer are all considered successful calls.
  
   For example, assume Direct Routing sent a call to the SBC and the SBC returns SIP code **504 Server Time-out - The server attempted to access another server in attempting to process the request and did not receive a prompt response**. This response indicates there's an issue on the SBC side, which will lower the NER on the Health Dashboard for this SBC.
  
   Because the action you take may depend on the number of calls affected, the Health Dashboard shows how many calls were analyzed to calculate a parameter. If the number of calls is less than 100, the NER may be low, but still be normal.

   The formula used to calculate the NER is:

   NER = 100 x (Answered calls + User Busy + Ring no Answer + Terminal Reject Seizures)/Total Calls

- **Average call duration**. Information about average call duration can help an organization monitor the quality of its calls. The average duration of a 1:1 PSTN call is four to five minutes.  However, for each company, this average can differ. Microsoft recommends establishing a baseline for the average call duration for your company. If this parameter goes significantly below the baseline, it may indicate that your users are having issues with call quality or reliability and are hanging up earlier than usual. If you start seeing low average call duration, for example 15 seconds, callers may be hanging up because your service isn't performing reliably.

   Because the action you take may depend on the number of calls affected, the Health Dashboard shows how many calls were analyzed to calculate a parameter.

- **TLS connectivity status**. TLS (Transport Layer Security) connectivity shows the status of the TLS connections between Direct Routing and the SBC. Health Dashboard also analyzes the certificate expiration date and warns if a certificate is set to expire within 30 days. This notification enables administrators to renew the certificate before service is disrupted.

   By selecting the Warning message, you can see a detailed issue description in a popup window and a recommendation for how to fix the issue.

- **SIP options status**. By default, the SBC sends options messages every minute. This configuration can vary for different SBC vendors. Direct Routing warns if the SIP options aren't sent or aren't configured. 

- **Detailed SIP options status**. Besides showing that there's an issue with SIP options flow, the Health Dashboard also provides detailed descriptions of the errors. You can access the description by selecting the “Warning” message. A pop-up window will show the detailed error description.

   Possible values for SIP options status messages are as follows:

    - **Active**. The SBC is active, which indicates the Microsoft Direct Routing service sees the options flowing on a regular interval.

    - **Warning, no SIP options**. The Session Border Controller exists in the database (your administrator created it using the command New-CsOnlinePSTNGateway). It's configured to send SIP options, but the Direct Routing service never saw the SIP options coming back from this SBC.

    - **Warning, SIP Messages aren't configured**. Trunk monitoring using SIP options isn’t turned on. The Microsoft Calling System uses SIP options and Transport Layer Security (TLS) handshake monitoring to detect the health of the connected Session Border Controllers (SBCs) at the application level. You’ll have problems if this trunk can be reached at the network level (by ping), but the certificate has expired or the SIP stack doesn’t work. To help identify such problems early, Microsoft recommends enabling sending SIP options. Check your SBC manufacturer documentation to configure sending SIP options.

- **Concurrent calls capacity**. You can specify the limit of concurrent calls that an SBC can handle by using the New- or Set-CsOnlinePSTNGateway cmdlet in PowerShell with the -MaxConcurrentSessions parameter. This parameter calculates how many calls were sent or received by Direct Routing using a specific SBC and compares it with the limit set. If the SBC also handles calls to different PBXs, this number won't show the actual concurrent calls.

### Detailed information for each SBC

You can also view the detailed information for a specific SBC as shown in the following screenshot:

‎:::image type="content" source="../media/direct-routing-dashboard-session-border-controller-detail.png" alt-text="Health dashboard SBC details":::

The detailed view shows the following parameters:

- **TLS Connectivity status**. This parameter is the same metric displayed on the **Overall Health** page.

- **TLS Connectivity last status**. This parameter shows time when the SBC made a TLS connection to the Direct Routing service.

- **SIP options status**. This parameter is the same metric displayed on the **Overall Health** page.

- **SIP options last checked**. This parameter is the time when the SIP options were last received.

- **SBC status**. This parameter is the overall status of the SBC, based on all monitored parameters.

- **Concurrent call**. This parameter shows how many concurrent calls the SBC handled. This information is useful to predict the number of concurrent channels you need and see the trend. You can slide the data by number of days and call direction (inbound/outbound/All streams).

- **Network parameters**. All network parameters are measured from the Direct Routing interface to the Session Border Controller. 

   - **Jitter**. This parameter is the millisecond measure of variation in network propagation delay time computed between two endpoints using RTCP (The RTP Control Protocol).

   - **Packet Loss**. This parameter is a measure of packets that failed to arrive; it's computed between two endpoints.

   - **Latency**. Also known as round-trip time, this parameter is the length of time it takes for a signal to be sent plus the length of time it takes for the acknowledgment of that signal to be received. This time delay consists of the propagation times between the two points of a signal.

   You can slide the data by number of days and call direction (inbound/outbound/All streams).

- **Network Effectiveness ratio**. This parameter is the same metric displayed on the **Overall Health** dashboard. However, it provides the option to slice the data by time series or call direction.


## Knowledge check

Choose the best response for the following question. Then select “Check your answers.”