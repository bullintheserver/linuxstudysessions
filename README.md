# linuxstudysessions
Study notes for my Linux Essentials certification journey. Guide follows LPI Essentials Study Guide. See Wiki for important links. 

---
# Topic 1
The Linux Community and a Career in Open Source  

## 1.1
Linux Evolution and Popular Operating Systems  
Weight: 2


### Linux general  
- Based on unix by bell labs
- Common enviros/platforms: smartphone, desktop, server.
- Distro considerations:
    - Cost
    - Performance
    - Scalability
    - Stability 
    - Hardware demand
- AndroidOS can run on:
    - Smartphones
    - Smart TVs
    - Tablets
    - Smartwatches
    - Android Auto

#### Debian  
- Package: dpkg  
- Considered more advanced than Ubuntu  
- More stable than Ubuntu  

#### Ubuntu  
- Mission: easy to use desktop  
    - Cut cost of pro services  
- Recommended for beginners  
- Less stable than Debian  

#### Red Hat  
- Aquired by IBM in 2019  
- Started in 1994  
- Reliable enterprise solution  
- Comes with software aiming to ease Linux use in pro server evironments  
- Some components fee based  
- CentOS uses source code of Red Hat & is free but unsupported  
- RH & Centos optimized for server environments  

#### Fedora  
- Aimed at desktop computers  
- Progressive, aggressive adoption of new tech  
- Test bed for RHEL  
- All RH bases use package: rpm  

#### SUSE
- Known for YaST config tool: allows admins to install and config software and hardware, set up servers and networks
- Commercial ed.: SUSE Linux Enterprise Server 
    - Comes as both a server and desktop enviro
    - Is suitable for enterprise and production deployment 
- openSUSE allows for devs to futher test and develp the system, is free

#### QubesOS  
- Secure desktop enviro

#### Kali  
- Pen-testing 

#### CentOS
- Among most suitable for business
    - As well as Ubuntu LTS
        - Better support
    - Stable vers of Debian GNU/Linux also often used for enterprise
- Incorporates all Red Hat products
- Free to use


### Embedded systems  

- Linux > proprietary: cross vendor platform compatibility, development, support, and no license fees.  
- Most popular embedded software projects are:  
    - Android, mainly mobile phones
    - Raspbian, mainly RaspberryPi

#### Android  
- Base is modified version of Linux kernel with additional open source software  
- Freely available in open source as AOSP, Android Open Source Projects  

#### Raspian  
- RaspberryPi
    - GPIO (general purpose input output) pins
        - Used to attach electronic devices and extension boards  
    - Used for industrial prototyping when developing embedded systems  
    - Uses ARM processors  
    - OS starts from an SD memory card  
    - Compact
    - Low cost
    - Web traffic handling 
    - Can function as a server or firewall
- Prominent distro is Raspbian based on Debian  

#### Linux & Cloud  
- As of 2017, Linux runs 90% of public cloud workload
- Linux usually offered as part of IaaS 
- Benefits of cloud computing
    - Flexibility
    - Easy recovery
    - Low use cost
    - Easy implementation
    - Easy scaling
    - Fast backup and recovery
    - Reduced OpEx
    - Subscription based model
- Amazon & Google Cloud
    - Ubuntu
    - CentOS
    - RHEL (Red Hat Enterprise Linux)
- Amazon
    - Amazon Linux
    - Kali Linux
- Google Cloud
    - FreeBSD
    - Windows Servers


## 1.2
Major Open Sources Applications  
Weight: 2  

### Applications & Software

Install and removal of packages via terminal:  
 - Ordinary users must prepend with `sudo`
    - Followed by entering user password
    - This gives certain `root` user permissions without being in `root` account 

#### Package manager
- Package repo with vast collection of apps available to install
- Debian, Ubuntu, Mint install | uninstall commands
    - `dpkg` (DEB Packages)
    - `apt-get`
    - `apt`
    - `remove`
    - Searching repos
        - `apt-cache search package_name`
            - `apt-cache` used to search for pkgs and list info about available pkgs
    - `apt search package_name`
- Full download and install string example
    - `sudo apt-get install package_name`  
    - `sudo apt install package_name`  

- Red Hat, Fedora, CentOS install | uninstall commands
    - `rpm` (RPM packages)
    - `yum`
    - `dnf`
    - `remove`
    - Searching repos
        - `yum search package_name`
        - `dnf search package_name`
- Full download and install string example
    - `sudo yum install package_name`
    - `sudo dnf install package_name`

#### Office applications
Most popular:  
    - Apache OpenOffice
        - Apache License 2.0
            - Cannot incorporate improvements made by LibreOffice
    - LibreOffice
        - LGPLv3 License
            - Can incorporate improvements made by Apache OpenOffice
            - Reason most distros adopt LibreOffice over OpenOffice
- Both compatible with Microsoft Office
- *Open Document Format* aka *ODF*
    - Preferred
    - Fully open and ISO standardized file format
    - Ensures docs are cross platform, cross application