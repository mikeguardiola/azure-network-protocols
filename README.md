<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, you will learn how to observe various types of network traffic to and from Azure Virtual Machines with Wireshark (a protocol analyzer), as well as experiment with Network Security Groups. <br />

<h2>Prerequisites</h2>

- [Creating Virtual Machines in Azure and Observing Network Topology](https://github.com/mikeguardiola/azure-vm-and-network)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 Pro (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Use Remote Desktop to connect to your Windows 10 Virtual Machine
- Within your Windows 10 Virtual Machine, Install Wireshark
- Open Wireshark and filter for ICMP traffic only
- Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM
- From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website and observe the traffic in WireShark
- Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
- Observe SSH traffic
- Observe DHCP traffic
- Observe DNS traffic
- Observe RDP traffic

<h2>Step-By-Step Instructions:</h2>

<p>
  Step 1:
<img src="https://i.imgur.com/socu9go.png"/>
</p>
<p>
Within the Azure Portal, navigate to the search bar at the top. Within the search bar, type "Virtual machines" and select it.
</p>
<br />

<p>
  Step 2:
<img src="https://i.imgur.com/XnmiN9P.png"/>
</p>
<p>
After you click "Virtual machines", you will be taken to this screen. Once there, click on "VM1".
</p>
<br />

<p>
  Step 3:
<img src="https://i.imgur.com/2cUyVa0.png"/>
</p>
<p>
You are going to connect to your Windows VM via Remote Desktop Connection, so you will need to do a few things to set that up. First, you will need to copy your Windows VM Public IP Address.
</p>
<br />

<p>
  Step 4:
<img src="https://i.imgur.com/xTN92Dm.png"/>
</p>
<p>
After that, you will need to press the Windows Key on your keyboard to open the Start Menu or you can click on the Windows icon to open the Start Menu.
</p>
<br />

<p>
  Step 5:
<img src="https://i.imgur.com/chuWbfh.png"/>
</p>
<p>
Once you have the Start Menu open, type "Remote Desktop Connection" and select it.
</p>
<br />

<p>
  Step 6:
<img src="https://i.imgur.com/MQFhF9A.png"/>
</p>
<p>
After the Remote Desktop Connection application opens, paste your Windows VM Public IP Address from earlier into the "Computer" section. Next, click on the "Connect" button.
</p>
<br />

<p>
  Step 7:
<img src="https://i.imgur.com/oe2cBpD.png"/>
</p>
<p>
The Remote Desktop Connection app will now ask for your log in credentials to your Windows VM, which you created while configuring your VM in Azure. (Note: the Remote Desktop app may default to asking for your personal Windows account log in credentials. If this happens, just select the "More choices" option and the select "Use a different account")
</p>
<br />

<p>
  Step 8:
<img src="https://i.imgur.com/XGUddc6.png"/>
</p>
<p>
Go ahead and enter your Windows VM log in credentials. Click on the "OK" button.
</p>

<p>
  Step 9:
<img src="https://i.imgur.com/mLcYDTJ.png"/>
</p>
<p>
You will get this warning notice saying that it is unsafe to proceed. However, you can go ahead and click "Yes". The explanation for why you can do this is beyond the scope of this tutorial, but just know that it is in fact okay to proceed in this example.
</p>
<br />

<p>
  Step 10:
<img src="https://i.imgur.com/sMHinQJ.png"/>
</p>
<p>
The Remote Desktop app will now establish a connection to your Windows VM, and you be taken to this screen. Once here, go ahead and set all the privacy settings to "No". Then click on "Accept".
</p>
<br />

<p>
  Step 11:
<img src="https://i.imgur.com/j4VLjFq.png"/>
</p>
<p>
Now you are officially remotely connected to the Windows VM that you previously created in Azure in the previous tutorial. You will see a Network notice pop up on the right side of your screen, go ahead and click "Yes".
</p>
<br />

<p>
  Step 12:
<img src="https://i.imgur.com/Zobvi9F.png"/>
</p>
<p>
Next, you will need to open up the Microsoft Edge Browser and navigate to Google.com. Once there, type "download wireshark" into the search bar and hit enter.
</p>
<br />

<p>
  Step 13:
<img src="https://i.imgur.com/7WmTanN.png"/>
</p>
<p>
You can click on the first result "Download Wireshark".
</p>
<br />

<p>
  Step 14:
<img src="https://i.imgur.com/stEwFnU.png"/>
</p>
<p>
Click on the "Windows Installer (64-bit)" option.
</p>
<br />

<p>
  Step 15:
<img src="https://i.imgur.com/5LSjQbp.png"/>
</p>
<p>
Go ahead and open the file from your Downloads. Once opened, click "Next" to begin the installation process.
</p>
<br />

<p>
  Step 16:
<img src="https://i.imgur.com/gVh2m25.png"/>
</p>
<p>
You can install Wireshark with all the default settings, so just go ahead and click through the installation process. Once you get to the end, click on the "Finish" button.
</p>
<br />

<p>
  Step 17:
<img src="https://i.imgur.com/y3yJqb1.jpg"/>
</p>
<p>
After Wireshark has installed, you can minimize or close the web browser. Next, click on the Start Menu button. Type "Wireshark" and select it.
</p>
<br />

<p>
  Step 18:
<img src="https://i.imgur.com/1ngmXv3.png"/>
</p>
<p>
Once Wireshark opens, click once on "Ethernet", then click on the small blue fin under File. This will start the packet capturing process and you will be able to see the live network traffic on your virtual machine.
</p>
<br />

<p>
  Step 19:
<img src="https://i.imgur.com/miQ0PRl.jpg"/>
</p>
<p>
You can now see the live traffic on your virtual machine's network.
</p>
<br />

<p>
  Step 20:
<img src="https://i.imgur.com/WmehizG.png"/>
</p>
<p>
Next, go to the search bar within Wireshark and type "icmp" and hit enter on your keyboard. ICMP stands for Internet Control Messaging Protocol.
</p>
<br />

<p>
  Step 21:
<img src="https://i.imgur.com/h1yB7TY.png"/>
</p>
<p>
Next, minimize your Remote Desktop Connection window and navigate back to the Azure Portal on your main desktop window. Navigate to VM2 and find VM2's Private IP Address.
</p>
<br />

<p>
  Step 22:
<img src="https://i.imgur.com/znwJJ9z.png"/>
</p>
<p>
Re-open your Remote Desktop Connection window. Click on the Start Menu button and type "Powershell" and select it.
</p>
<br />

<p>
  Step 23:
<img src="https://i.imgur.com/gIlK40O.png"/>
</p>
<p>
Once Powershell is open, you are going to ping your Linux Virtual Machine, VM2. You will need the Private IP Address from earlier. In Powershell, type "ping 10.0.0.5" and hit enter. You can see now that Wireshark is picking up the ICMP traffic between your virtual machines.
</p>
<br />

<p>
  Step 24:
<img src="https://i.imgur.com/qEXVB0Y.png"/>
</p>
<p>
Next, you are going to try pinging a public website and then observe the traffic in Wireshark. In Powershell, type "www.google.com -4" and hit enter. You can now see that Wireshark has captured the ICMP traffic between your Windows Virtual Machine (VM1) and Google.
</p>
<br />

<p>
  Step 25:
<img src="https://imgur.com/YTCMudt.png"/>
</p>
<p>
Next, we are going to initiate a perpetual ping from VM1 to VM2. In Powershell, type "ping 10.0.0.5 -t" and hit enter. You can now observe that this will cause VM1 to ping VM2 nonstop.
</p>
<br />

<p>
  Step 26:
<img src="https://imgur.com/S3P2hsw.png"/>
</p>
<p>
While VM1 is continuously pinging VM2, we are going to change the firewall on VM2 to not allow ICMP traffic to come through. Essentially, we are going to block ICMP traffic on VM2's firewall. This will allow us to gain a better understanding of how firewalls work. To begin this process, head back over to the Azure Portal. In the search bar, type "Network Security Group" and click on it. Once there, click on "VM2-nsg".
</p>
<br />

<p>
  Step 27:
<img src="https://imgur.com/lAW1Y9i.png"/>
</p>
<p>
Once you are in the VM2-nsg portal, click on "Inbound security rules".
</p>
<br />

<p>
  Step 28:
<img src="https://imgur.com/sYG3qp4.png"/>
</p>
<p>
Once you are at this screen, click on "+ Add". Fill out the sections accordingly. When finished, click on the blue button at the bottom of the screen. Doing this creates a security rule within Azure that will effectively stop ICMP traffic from VM1 to VM2.
</p>
<br />

<p>
  Step 29:
<img src="https://imgur.com/hvAhsdN.png"/>
</p>
<p>
Head back over to your VM1 Remote Desktop. You will now see in Powershell that the ping request has timed out as a result of blocking ICMP traffic. VM2's firewall is blocking the traffic.
</p>
<br />

<p>
  Step 30:
<img src="https://imgur.com/trgjBhy.png"/>
</p>
<p>
Go back to VM2-nsg Inbound Security Rules in Azure. Click on "DENY_ICMP_PING_FROM_ANYWHERE" to edit the rule. Under "Action", change from "Deny" to "Allow". Click on the blue "Save" button at the bottom of the screen.
</p>
<br />

<p>
  Step 31:
<img src="https://imgur.com/TA8dqFS.png"/>
</p>
<p>
Go back to your VM1 Remote Desktop. You can observe that ICMP traffic has resumed.
</p>
<br />

<p>
  Step 32:
<img src="https://imgur.com/SXCzS5h.png"/>
</p>
<p>
Now we are going to explore SSH (Secure Shell) Traffic on the network. Within Wireshark, type "ssh" into the search bar and hit enter. Also, click on the green fin to restart the capturing process. 
</p>
<br />

<p>
  Step 33:
<img src="https://imgur.com/kfm8Xnt.png"/>
</p>
<p>
In Powershell, we are going to establish a secure connection from VM1 to VM2. Type "ssh labuser@10.0.0.5" and hit enter. You will see that the connection is not able to be established at first. Powershell will prompt you with a yes/no question - type yes and press enter. Powershell should then prompt you to enter in the password for VM2. If it does not automatically prompt you, then go ahead and retype "ssh labuser@10.0.0.5" and hit enter. Now you should be prompted to enter the password. (Note: when you are typing in the password, it won't actually show the text to indicate you are typing. That's normal. Just go ahead and type the full password anyway and hit enter.) You are now securely connected to VM2 remotely.
</p>
<br />

<p>
  Step 34:
<img src="https://imgur.com/ITomFvU.png"/>
</p>
<p>
To end the remote connection, type "exit" and hit enter. This will take you back to VM1's command line.
</p>
<br />

<p>
  Step 35:
<img src="https://imgur.com/GB3oQTD.png"/>
</p>
<p>
Next, you are going to observe DHCP traffic. Remember that DHCP is used to automatically assign an IP address. You are going to force the renewal of an IP address in Powershell. First, go to Wireshark and type "dhcp" into the search bar - hit enter. This wil filter for dhcp traffic. In Powershell, type "ipconfig /renew" and press enter. VM1 will now broadcast over the network that it needs a new IP address. Azure's DHCP server inside the virtual network will then re-issue the IP address. You should then be able to observe some DHCP traffic inside Wireshark.
</p>
<br />

<p>
  Step 36:
<img src="https://imgur.com/zHJWkhl.png"/>
</p>
<p>
Next, you are going to observe DNS traffic. In Wireshark, go ahead and filter for DNS by typing "dns" into the search bar - press enter. To observe some DNS traffic, you are going to type "nslookup www.google.com" - press enter. Now you can see the DNS traffic coming through in Wireshark.
</p>
<br />

<p>
  Step 37:
<img src="https://imgur.com/rrFochy.png"/>
</p>
<p>
Finally, you are going to observe RDP traffic. In Wireshark, filter for RDP by typing "rdp" into the search bar - press enter. You will immediately see RDP traffic coming through nonstop in Wireshark. This is due to the fact that we have a live remote session going.
</p>
<br />
This concludes your tutorial on how to observe various types of network traffic to and from Azure Virtual Machines with Wireshark, as well as experiment with Network Security Groups. Well done and thank you for following along!
