<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

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
<img src="https://i.imgur.com/pr8xnDL.png"/>
</p>
<p>
After you click "Virtual machines", you will be taken to this screen. Once there, click on "Create" and select "Azure virtual machine".
</p>
<br />

<p>
  Step 3:
<img src="https://i.imgur.com/OEs2drO.png"/>
</p>
<p>
Once you are at this screen, you can begin configuring your virtual machine. Under "Project Details", make sure that you have the correct subscription and resource group selected from the drop down menus. Since you are building off the previous tutorial, you can go ahead and select "Azure subsciption 1" and "resource-group-lab-01". Under "Instance Details", you will need to give your virtual machine a name. I went with "VM1". Next, select the correct region that most closely matches where you live. Next, for "Image" you will want to select "Windows 10 Pro, version 21H2 - x64 Gen2 (free services eligible)".
</p>
<br />

<p>
  Step 4:
<img src="https://i.imgur.com/ZUBCPI5.png"/>
</p>
<p>
After that, you will need to scroll down until you see this portion of the screen. For the virtual machine size, select "Standard_E2s_v3-2 vcpus, 16 GiB memory" from the drop down menu. Under "Administrator account", create a username and password. Next, check the box under "Licensing". After that, go ahead and click on the "Next:Disks >" button.
</p>
<br />

<p>
  Step 5:
<img src="https://i.imgur.com/3umaVjc.png"/>
</p>
<p>
You do not need to change any of these settings, so just click on the "Next: Networking >" button.
</p>
<br />

<p>
  Step 6:
<img src="https://i.imgur.com/jMFjgEc.png"/>
</p>
<p>
Once you are at this screen, you do not need to change any settings. However, you will want to make some observations. Under " Network interface", you can see how Azure automatically creates a Virtual Network or Vnet whenever you are setting up a virtual machine. This Vnet is what will connect multiple virtual machines and allow you to facilitate data communication. When ready, go ahead and click on the "Review + create" button.
</p>
<br />

<p>
  Step 7:
<img src="https://i.imgur.com/jKQU4KZ.png"/>
</p>
<p>
Azure will now go through a quick validation process. Once the validation process is complete, click on the "Create" button.
</p>
<br />

<p>
  Step 8:
<img src="https://i.imgur.com/sTtHUUU.png"/>
</p>
<p>
Azure will go through its deployment process to create all of the resources connected to your virtual machine. Once deployment is complete, you will be able to see all the various resources that were created under "Deployment details". When ready, click on the "Create another VM" button.
</p>

<p>
  Step 9:
<img src="https://i.imgur.com/kEXy51l.png"/>
</p>
<p>
You will now repeat the process from earlier for creating a virtual machine. Under "Project Details", make sure that you have the correct subscription and resource group selected from the drop down menus. Since you are building off the previous tutorial, you can go ahead and select "Azure subsciption 1" and "resource-group-lab-01". Under "Instance Details", you will need to give your virtual machine a name. I went with "VM2". Next, select the correct region that most closely matches where you live. Next, for "Image" you will want to select "Ubuntu Server 20.04 - x64 Gen2 (free services eligible)".
</p>
<br />

<p>
  Step 10:
<img src="https://i.imgur.com/rV9W2PV.png"/>
</p>
<p>
After that, you will need to scroll down until you see this portion of the screen. For the virtual machine size, select "Standard_E2s_v3-2 vcpus, 16 GiB memory" from the drop down menu. Next, you will need to select "Password" instead of "SSH public key". Then go ahead and create a username and password. After that, go ahead and click on the "Next:Disks >" button.
</p>
<br />

<p>
  Step 11:
<img src="https://i.imgur.com/ZygXPDw.png"/>
</p>
<p>
You do not need to change any of these settings, so just click on the "Next: Networking >" button.
</p>
<br />

<p>
  Step 12:
<img src="https://i.imgur.com/4Ya5yOd.png"/>
</p>
<p>
Once you are at this screen, you do not need to change any settings since Azure already pre-selected the correct settings. Under "Network interface", double check to make sure that you have the virtual network that you created earlier selected, which is "VM1-vnet". This will ensure that both of your virtual machines are able to communicate with each other. After that, go ahead and click on the "Review + create" button.
</p>
<br />

<p>
  Step 13:
<img src="https://i.imgur.com/J3uBAq0.png"/>
</p>
<p>
Azure will now go through a quick validation process. Once the validation process is complete, click on the "Create" button.
</p>
<br />

<p>
  Step 14:
<img src="https://i.imgur.com/7hI695A.png"/>
</p>
<p>
Azure will go through its deployment process to create all of the resources connected to your virtual machine. Once deployment is complete, you will be able to see all the various resources that were created under "Deployment details".
</p>
<br />

<p>
  Step 15:
<img src="https://i.imgur.com/luHUUPH.png"/>
</p>
<p>
Next, you will want to navigate back to the Azure Portal home screen. Once there, click on the search bar and type "Network Watcher" and select it.
</p>
<br />

<p>
  Step 16:
<img src="https://i.imgur.com/Ddxkcil.png"/>
</p>
<p>
Once you are at this screen, go ahead and click on "Topology".
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
