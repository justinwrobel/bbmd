#Developer Setup Tutorial
[StartingBlock]: http://behind.blackboard.com/downloads/details.aspx?d=1669
[DeveloperVMInstall]: https://help.blackboard.com/en-us/Learn/9.1_SP_12_and_SP_13/Administrator/230_Developer_Resources/Developer_Virtual_Machine

1. Download all required files
	* Download [Developer VM](https://behind.blackboard.com/System-Administrator/Learn/Downloads/download.aspx?d=1654) (e.g., devcon-sp14r145_public-license.box)
	* Download [Eclipse](http://www.eclipse.org/downloads/) 
	* Download [Vagrant](http://downloads.vagrantup.com/tags/v1.2.2)
	* Download [VirtualBox](https://www.virtualbox.org/wiki/Download_Old_Builds_4_2)
	* Download [Starting Block][StartingBlock]
1. Install Eclipse
1. Install [VirtualBox & Vagrant][DeveloperVMInstall]
1. Launch Developer VM
	
		vagrant up
		vagrant ssh
	
1. Start blackboard
	
		sudo /usr/local/blackboard/tools/admin/ServiceController.sh services.start

Pat yourself on the back! You've should have a fully functioning Blackboard Instance! 
But if you want to make this VM even easier to use there are some tweaks available in [DeveloperVmTweaks](DeveloperVmTweaks.html)

