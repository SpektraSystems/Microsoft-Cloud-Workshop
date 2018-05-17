# Overview
Due to recent change, you might get the following issue in rdp connection.
* An authentication error has occurred.
  The function requested is not supported.  
  This could be due to CredSSP encryption oracle remediation.
  For more information, see https://go.microsoft.com/fwlink/?linkid=866660
  
  <kbd>![](Images/RDP%20credSSP.jpg)</kbd>
  
## Following is fix for this: 
* You can run the following dos command to make change in in registry setting
    > REG  ADD HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System\CredSSP\Parameters\ /v AllowEncryptionOracle /t REG_DWORD /d 2
    
* You can read more about this at https://blogs.technet.microsoft.com/mckittrick/unable-to-rdp-to-virtual-machine-credssp-encryption-oracle-remediation/
