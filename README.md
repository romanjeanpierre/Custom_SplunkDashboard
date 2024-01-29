<h1> Custom Splunk Dashboard for Efficient Security Analysis</h1>

<h2> Executive Summary </h2>
<p> In this project, we delve into the development and enhancement of an operational intelligence dashboard within a Security Information and Event Management (SIEM) system using Splunk. The primary focus is on investigating suspicious activities and integrating new panels into the dashboard for more efficient monitoring and analysis.</p>

 <h2>Utilities Used</h2>
    <ul>
        <li><strong>Splunk Enterprise</strong></li>
        <li><strong>Suricata and Fortigate logs</strong></li>
        <li><strong>Linux Environment</strong></li>
    </ul>
<p align="center">
       <img src="https://imgur.com/KXuOD8X.png" alt="Project Overview Image" style="width:1000px; height:auto;">
   <img src="https://imgur.com/f4viY5R.png" alt="Project Overview Image" style="width:1000px; height:auto;">
    </p>


<h2> Project Walk-Through </h2>
<h3> Generate Suricata Alerts Counter </h3>
<p> Counter for real-time traffic analysis and packet logging. Command: => <code> index=* sourcetype=suricata event_type=alert alert.category!="" | stats count as Total </code> </p>
<p> Display Alert category table in real-time. Command => <code>index=* sourcetype=suricata event_type=alert category!="" | stats count by category | sort count desc </code> </p>
<img src="https://i.imgur.com/onPjtUd.png" height="80%" width="80%" alt="Suricata Alert Count">
<p> Clicking on any of the below events will provide us quick access to Suricata actions and signatures</p> 

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="https://imgur.com/PGPk7If.png" alt="Information_leak" style="width: 49%; height: auto; object-fit: cover;">
 
  <img src="https://imgur.com/pALp7Tz.png" alt="Suricata Action Signature Details" style="width: 49%; height: auto; object-fit: cover;">
</div>

<h3> Generate Fortigate Alerts Counter </h3>
 <p> Counter for Firewall policy violations and network anomalies based on the firewall rules and configurations: </p>
  <p> Command => <code> index=* sourcetype=fortigate_utm level=alert | stats count as Total </code> </p>

 <p> Display Attack vector table in real-time: </p>
   <p> Command => <code> index=* sourcetype=fortigate_utm level=alert | stats count by attack | sort count desc </code></p>
     <img src="https://imgur.com/jY0A3Ko.png" height="80% width="80%" alt="Fortigate Alert Count">
       <p> Clicking on any of the events we can identify the possible exploitation, i.e: "Apache.Roller.OGLN.Injection.Remote.Code.Execution" </p>
         <img src="https://imgur.com/mRP08lZ.png" height="80%" width="80%" alt="Details of Apache Version">
           <p> Conduct OSINT to investigate vulnerability </p>
              <img src="https://imgur.com/lgw7C2j.png" height="80%" width="80%" alt="Details of Apache Version">
               <p> Apache Software Foundation Apache Roller prior to 5.0.2, CVE ID: CVE-2013-4212 </p>

  <h3> Severity Pie Chart - Suricata & Fortigate </h3>
 <p> A Severity Pie Chart in Splunk provides security analysts with a comprehensive visual tool for immediate assessment of alert distributions, enabling prioritization of critical threats and efficient resource allocation. It facilitates trend spotting, accelerates incident response, simplifies compliance reporting, and enhances monitoring efficiency. This visual aid also serves as an effective communication bridge with stakeholders and supports historical analysis to gauge the effectiveness of security measures. </p>
<p> Command Suricata Pie Chart => <code> index=* sourcetype="suricata" event_type=alert| stats count by severity </code></p>
<p> Command Fortigate Pie Chart => <code> index=* sourcetype="fortigate_utm" level=alert | stats count by severity </code></p>
 <img src="https://imgur.com/rNUeZj8.png" alt="Suricate and fortigate pie chart " height="80%" width="80%">
              
