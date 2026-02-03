Active Directory (AD) is a centralized directory service used to manage users, computers, and resources across a networked environment. It allows administrators to control access, enforce security policies, and organize systems from a single, consistent framework. By providing authentication, authorization, and structured management at scale, Active Directory simplifies administration, improves security, and ensures consistency across an organization. Its ability to integrate seamlessly with Windows environments and support large, complex infrastructures makes it a reliable and widely adopted solution for identity and access management.

Below, I will document my personal adventure in learning Active Directory, walking through the process of installing and setting up Windows Server 2022, creating a Domain controller, Organization Units, Users, Groups, and some example Group Policy Objects. Hopefully this can act as a reference guide, or give some background information on how Active Directory functions at a high level.

Installing Windows Server 2022:
The first step of setting up an Active Directory for a Windows environment is installing a Domain Controller, typically through Windows Server for a local directory. Alternatives include a virtual domain controller, or cloud based domain controller, such as those offered by Microsoft Azure.

I personally set it up on a virtual machine through VirtualBox, starting from a Windows Server 2022 ISO. The installation process is similar to installing a regular Windows operating system.

I picked to install the version with the desktop, as I am more comfortable with a desktop graphical interface. There are alternative options for those more comfortable with the Windows Server to leave out the desktop, opting for a system controlled mainly through command prompt. Once I pick the initial setup options and the operating system is finished installing, I’ll be asked to pick a password for the built-in administrator:
Generally, I’ll want to disable this default administrator account as soon as possible, but for the purposes of this learning adventure, I’ll continue to use it for convenience. Leaving default administrator accounts active can be huge security liabilities in the production environment, as I’ll want to ensure only authorized personnel have access to my Domain Controller.


Once I’ve finalized the account, I’m greeted with a login screen similar to a regular Windows operating system (because I choose the version with the desktop). Once I log in and the system finishes initial setup, I’m greeted with the Server Manager Dashboard.
Domain Controller Setup:

From the dashboard, select the option to “Add roles and features”. I’m taken through a set up wizard, selecting the option for “Role-based or feature-based installation”, and selecting the current system as the location to install my new service. Since I am also going to use this server as the DNS in order to point other clients on this Domain to this server as the Domain Controller, I’ll also enable that role here. I could host DNS separately on a different server, but for this exercise, I am opting to host it all on one VM.


Once the Domain Controller role is designated, I am given a notification that I need to promote this server to a Domain Controller in order to use it. Following the notification, I am led through another setup wizard to begin configuration of my Domain.
 

I’ll be setting this server up as the sole Domain Controller on my newly created domain, creatively named “Corp.CalvinCom”. Note that the domain name is two parts, separated by a period. Just CalvinCom is not a valid root domain name. I am given additional options to configure the controller, such as recovery password or save location for system logs. I left most of those options default for now. After a final review of the settings, I finalize the installation process of this Domain Controller. After a reboot and logging back in, I am finally ready to start configuring my new domain through the Domain Controller.

A quick indication that the domain has been set up and the active directory environment is live is that at log in, I am asked to login not as the local administrator, but the administrator of Corp, the new domain I just created.
