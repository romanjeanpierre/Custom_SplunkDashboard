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
    </p>
<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="https://i.imgur.com/3fz6j8i.png" alt="Fortigate Alert Count" style="width: 49%; height: auto; object-fit: cover;">
 
  <img src="https://i.imgur.com/onPjtUd.png" alt="Suricata Alert Count" style="width: 49%; height: auto; object-fit: cover;">
</div>

<h2> Project Walk-Through </h2>
<h3> Generate Suricata Alerts Counter </h3>
<p> Counter for real-time traffic analysis and packet logging. Command: => <code> index=* sourcetype=suricata event_type=alert alert.category!="" | stats count as Total </code> </p>
<img src="https://i.imgur.com/onPjtUd.png" height="80%" width="80%" alt="Suricata Alert Count">
<p> Clicking on any of the below events will provide us quick access to Suricata actions and signatures</p> 

<div style="display: flex; justify-content: space-between; align-items: center;">
  <img src="https://imgur.com/PGPk7If.png" alt="Information_leak" style="width: 49%; height: auto; object-fit: cover;">
 
  <img src="https://imgur.com/pALp7Tz.png" alt="Suricata Action Signature Details" style="width: 49%; height: auto; object-fit: cover;">
</div>

<h3> Generate Fortigate </h3>
<p> Counter for Firewall policy violations and network anomalies based on the firewall rules and configurations</p>
<p> Command => <code> index=* sourcetype=fortigate_utm level=alert attack</code></p>

