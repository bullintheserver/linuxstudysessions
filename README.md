 _ _                      _             _                         _         
| (_)_ __  _   ___  _____| |_ _   _  __| |_   _ ___  ___  ___ ___(_) ___   _ __  ___   
| | | '_ \| | | \ \/ / __| __| | | |/ _` | | | / __|/ _ \/ __/ __| |/ _ \ | '_ \/ __|  
| | | | | | |_| |>  <\__ \ |_| |_| | (_| | |_| \__ \  __/\__ \__ \ | (_) || | | \__ \  
|_|_|_| |_|\__,_/_/\_\___/\__|\__,_|\__,_|\__, |___/\___||___/___/_|\___/ |_| |_|___/  
                                          |___/                             


# linuxstudysessions
Study notes for my Linux Essentials certification journey. Guide follows LPI Essentials Study Guide. See Wiki for important links. 

---
# TOPIC 1
The Linux Community and a Career in Open Source  

## 1.1
Linux Evolution and Popular Operating Systems  
Weight: 2


### LINUX GENERAL  
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


### EMBEDDED SYSTEMS  

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

#### package manager
- Package repo with vast collection of apps available to install
- Debian, Ubuntu, Mint
    - `dpkg` (DEB Packages)
    - `apt-get`
    - `apt`
    - Searching repos
        - `apt-cache search package_name`
            - `apt-cache` used to search for pkgs and list info about available pkgs
    - `apt search package_name`

- Red Hat, Fedora, CentOS
    - `rpm` (RPM packages)
    - `yum`
    - `dnf`
