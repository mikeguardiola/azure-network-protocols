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
Once Wireshark opens, click once on "Ethernet", then click on the small blue fin under File. This will start the packet capturing process and you will be able to see the live network traffic on our virtual machine.
</p>
<br />

<p>
  Step 19:
<img src="https://i.imgur.com/miQ0PRl.jpg"/>
</p>
<p>
You can now see the live traffic on our virtual machine's network.
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
  Step 16:
<img src="https://i.imgur.com/gVh2m25.png"/>
</p>
<p>
You can install Wireshark with all the default settings, so just go ahead and click through the installation process. Once you get to the end, click on the "Finish" button.
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
  Step 16:
<img src="https://i.imgur.com/gVh2m25.png"/>
</p>
<p>
You can install Wireshark with all the default settings, so just go ahead and click through the installation process. Once you get to the end, click on the "Finish" button.
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
  Step 16:
<img src="https://i.imgur.com/gVh2m25.png"/>
</p>
<p>
You can install Wireshark with all the default settings, so just go ahead and click through the installation process. Once you get to the end, click on the "Finish" button.
</p>
<br />

<p>
  Step 17:
<img src="https://i.imgur.com/6bbJACJ.png"/>
</p>
<p>
After you click on "Topology", you will need to make sure you have the correct "Resource Group" and correct "Virtual Network" selected. Once you have those selected, Azure will now visually display a model of what your network topology looks like, which is an excellent feature that allows you to visualize everything that you just created. This also serves as a nice verification tool to ensure that your network topology is set up correctly.
</p>
<br />
This concludes your tutorial on how to create virtual machines in Azure, as well as observe network topology. Well done and thank you for following along!
