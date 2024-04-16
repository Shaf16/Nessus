# Vulnerability Management using Nessus

## Overview:
This project utilizes ***Nessus Essentials*** and ***VMware Workstation Player*** to demonstrate the vulnerability management process. A ***virtual machine (VM)*** is set up and scanned using Nessus to identify potential vulnerabilities, which are then remediated accordingly.

## Skills Learned:

- Nessus
- Virtualization
- Vulnerability Management
- Threat Analysis
- Security Assessment
- Remediation Strategies
- Patch Management
- Security Awareness

## Key Tools and Technologies:
- **Nessus**: A leading vulnerability scanner used to detect and assess security issues and vulnerabilities in networks, systems, and applications.
- **VMware Workstation Player**: A desktop virtualization application that allows users to run multiple operating systems on a single physical machine.
- **Virtual Machine**: Set up on VMware Workstation Player to provide a risk-free, controlled and isolated environment for conducting vulnerabilty scanning and security assessments.

## Project Methodology:

- ## Phase One: Setting up the VM on VMware Workstation Player

  We begin by setting up our VM, which serves as a controlled environment for assessing and analyzing vulnerabilities and security issues. Windows is a popular choice for the operating system (OS), so we download a Windows 10 ISO file to create a Windows 10 VM using VMware Workstation Player. Once the VM is set up, we configure it to ensure connectivity with Nessus. This involves disabling the firewall using Windows Defender Firewall. We can verify connectivity by pinging the VM from our host computer. Successful ping indicates that the VM is ready to be scanned by Nessus.

<p align="center">
 <b> Windows 10 set up on VMware Workstation Player</b>
<br />

<img src="https://github.com/Shaf16/Nessus/assets/95363766/6825f8b7-f7c3-487f-bb16-ee2508abccc3" alt="VMware Workstation Player" width="75%" height="75%">
</p>

- ## Phase Two: Inital scans using Nessus

  In this phase, we log in to the Nessus portal using our credentials and create a new scan for our VM. We set up a basic unauthorized (non-credentialed) scan with the target IP address being that of our VM. Once created, we initiate our first non-credentialed scan and inspect the results.

  <p align="center">
   <b> Non-credentialed Scan</b>
  <br />

  <img src="https://github.com/Shaf16/Nessus/assets/95363766/ef09cec6-5b78-49bd-9d14-16fa8a9f9b5e" alt="Non-cred Scan" width="75%" height="75%">
  </p>

  Next, we will proceed with a credentialed scan. To prepare for this, we modify the scan settings to include the Windows credentials (username and password) of the VM. Additionally, we enable the remote registry on the VM, allowing Nessus to connect and identify insecure configurations. To facilitate the scan, we disable User Account Control (UAC) and configure the registry for easier access by the scanner. These steps are essential for conducting a credentialed scan. Upon receiving the results, we observe a noticeable difference.

  <p align="center">
   <b> Credentialed Scan</b>
  <br />

  <img src="https://github.com/Shaf16/Nessus/assets/95363766/f252c605-b93b-40e4-ba4a-b4431662b555" alt="Cred Scan" width="75%" height="75%">
  </p>

  The credentialed scan reveals a higher number of "Critical" and "High" vulnerabilities compared to the non-credentialed scan.

  This disparity arises because a credentialed scan allows Nessus to authenticate and access the target system with elevated privileges, providing comprehensive visibility into the system's configuration, installed software, and detailed security settings. This enables Nessus to perform deeper inspections and identify more vulnerabilities that require privileged access to detect. On the other hand, a non-credentialed scan relies solely on external observations and publicly accessible information, providing a surface-level assessment of vulnerabilities visible from outside the system.

  In summary, a credentialed scan has elevated access and can gather detailed information about the target system, whereas a non-credentialed scan relies on external visibility and is limited to detecting surface-level vulnerabilities accessible without authentication.


- ## Phase Three: Installing Deprecated Software to increase Vulnerabilities

  In this phase, we will download and install a deprecated (outdated) version of Firefox on our VM. We download this version from the [Firefox directory](https://ftp.mozilla.org/pub/firefox/releases/) of old versions, specifically targeting version 3.6.12 for this project. Once downloaded, we proceed to install and set it up on the VM. After installation, we run another credentialed scan. The results of this scan show a significant increase in the number of "Critical" and "High" vulnerabilities compared to the previous scan.

  <p align="center">
   <b> Scan Results After Installing Deprecated Firefox</b>
  <br />

  <img src="https://github.com/Shaf16/Nessus/assets/95363766/b18f9e5b-687e-4e54-b87d-1313d4dde7f3" alt="Dep Scan" width="75%" height="75%">
  </p>

  To further investigate these vulnerabilities, we can navigate to the "Vulnerabilities" tab and view the list of detected issues. Clicking on a specific vulnerability provides more detailed information about it.

  <p align="center">
    <b> Vulnerabilities </b>
   <br /> 
    
    <img src="https://github.com/Shaf16/Nessus/assets/95363766/f75c68db-d2ac-422d-8ccc-8ea12a741000" alt="Vulnerabilities" width="75%" height="75%" />
  </p> 

   <p align="center"> 
    <b> Details of Vulnerability </b>
   <br />
     
  <img src="https://github.com/Shaf16/Nessus/assets/95363766/4b01c75d-e021-4f2f-ab65-499873095518" alt="Details" width="75%" height="75%" />
  </p>

  The noticeable rise in vulnerabilities can be directly attributed to the installation of the deprecated Firefox version, as evidenced by the multiple detected issues and their details. This emphasizes the risks associated with using outdated software and underscores the importance of regularly updating and patching software.


- ## Phase Four: Remediating the Vulnerabilities

  Now that we have detected all the vulnerabilities present in the VM, we need to remediate them to the best of our abilities. Nessus assists us in this task by providing remediation suggestions in the "Remediations" section. We navigate to this section and review the suggestions before implementing them on the VM.

  <p align="center">
    <b> Remediations </b>
  <br />

  <img src="https://github.com/Shaf16/Nessus/assets/95363766/591c78b0-0df6-42b8-9286-b85f1bf3d15b" alt="Remediations" width="75%" height="75%">
  </p>

  Nessus recommends upgrading to the latest version of Firefox and installing "KB5036892". To implement the first suggestion, we uninstall the current version of Firefox and download/install the latest available version. For the second suggestion, we check for updates on our Windows VM and install any available updates. After completing these steps, we run another scan to verify if the existing vulnerabilities have been remediated.

  <p align="center">
    <b> Scan Results After Remediation</b>
  <br />

  <img src="https://github.com/Shaf16/Nessus/assets/95363766/7060e4e5-3e2d-4a40-a2ee-17da883c37ab" alt="Rem Scan" width="75%" height="75%">
  </p>

  As expected, the number of "Critical" and "High" vulnerabilities have significantly decreased. Navigating to the "Vulnerabilities" tab further confirms that the issues related to the deprecated Firefox have been successfully resolved.

  <p align="center">
    <b> Vulnerabilities After Remediation</b>
  <br />

  <img src="https://github.com/Shaf16/Nessus/assets/95363766/e56526f2-7abc-4804-ad03-f467e070fea0" alt="Vul after Rem" width="75%" height="75%">
  </p>


## Conclusion:

This project demonstrated the importance of proactive vulnerability management using Nessus and VMware Workstation Player. By leveraging both non-credentialed and credentialed scans, we identified critical security vulnerabilities within our virtual machine (VM) environment. The scans revealed significant differences in vulnerability detection based on authentication levels, emphasizing the value of comprehensive security assessments.

Furthermore, the impact of installing deprecated software, such as an outdated version of Firefox, underscored the risks associated with running obsolete applications. Remediation efforts guided by Nessus recommendations, including software upgrades and patch installations, effectively mitigated identified vulnerabilities.

Overall, this project highlighted the critical role of continuous monitoring, vulnerability assessment, and prompt remediation in maintaining robust cybersecurity practices. Leveraging Nessus and VMware Workstation Player, we gained insights into security weaknesses, implemented targeted remediation strategies, and enhanced the security posture of our virtualized environment.
