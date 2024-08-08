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
    - Searching repos
        - `yum search package_name`
        - `dnf search package_name`
- Full download and install string example
    - `sudo yum install package_name`
    - `sudo dnf install package_name`
- Remove vs. purge
    - Configuration files are not removed when updating software for seamless login
    - apt-remove
        - Doesn't remove configuration files
    - apt-purge
        - Removes configuration files
#### Office applications
- Most popular  
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

#### Web browsers
- Main web browsers in Linux enviro
    - Google Chrome
        - Maintained by Google
        - Based on open source browser *Chromium*
    - Mozilla Firefox
        - Maintained by Mozilla
            - Non-profit org
            - Foundation deeply involved with open standards development underlying the modern web
            - Develops other apps 
                - E-mail client *Thunderbird* 
                    - Offers extra features and integrates with other desktop apps
        - Origins linked to Netscape
            - First popular web browser to adopt open source model

#### Multimedia
- Popular FLOSS applications
    - Blender
        - 3d animations and objects rendering
    - GIMP
        - Full-featured image editor
        - Comparable with Adobe Photoshop
    - Inkscape
        - Vector graphics editor
        - Comparable to Corel Draw or Adobe Illustrator08_05_2024_10_53_00
        - Default open standard format: SVG
    - Audacity
        - Audio editor
        - Limited compared to GarageBand or ProTools
    - ImageMagick
        - Command line tool
            - Converts / edits image file types
            - Can create PDFs from image files
    - Playback applications
        - Video playback
            - VLC
            - smplayer
        - Audio playback
            - Audacious
            - Banshee
            - Amarok
                - Can also manage local sound files

#### Server programs
- Web page servers
    - Web browser: client
        - Common script: JavaScript
    - Remote computer: server
        - Common script: PHP
        - Can request info from other servers
            - Such as a database server
    - most deploy open source server programs
    - Known as an *HTTP server*
        - Collects and sends requested data back to browser
        - Arranges content defined by HTML document
    - Most popular
        - Apache
        - Nginx
        - lighttpd
- Database servers
    - Database
        - Orgnaized set of information
    - Stores contents in formatted fashion
    - Most common type
        - Relational database
            - Data organized in predefined tables
            - Most popular open source
                - MariaDB
                    - Originated from MySQL
                - PostgreSQL

#### Data sharing
- *Network File System* aka *NFS*
    - NSF protocol
    - Standard way to share file systems in Unix/Linux-only networks
    - Shares directories for r/w (read/write) purposes
    - Can share entire directory tree to boot from
        - Used by *thin clients* in large networks 
            - Avoids individual OS maintenance
- *Samba*
    - Compatible with all major OSs
        - As of version 4
    - Can share files and printers
    - Used in mixed OS network settings
- *Domain controller*
    - Central server
    - Authorizes logins on workstations 
    - Manages access to local and remote resources 
    - Domain controller service provided by Microsoft's *Active Directory*
    - Workstations
        - Can associate with DC using
            - Samba
            - Auth subsystem *SSSD* 
- Cloud computing
    - ownCloud
        - More focused on
            - File sharing
            - Thrid-party integration
        - Supports plugins
    - Nextcloud
        - *Fork* (aka spin-off) of ownCloud
        - All features of ownCloud
            - Plus private audio/video conferencing
        - Supports plugins
    - Both
        - Offer paid version
            - Extra features
            - Extended support
        - Can be installed on private server
        - Free of charge
        - Must be installed on previously configured web server
            - Such as Apache
            - Because services depend on HTTP, and are written in PHP
        - Make sure to enable HTTPS
            - Encrypts all connections to your cloud

#### Network administration
- Netowrk configuration
    - Set of programs running on router
        - Responsible for setting up and checking network availability
    - *Dynamic Host Configuration Protocol* (*DHCP*)
        - Responsible for assigning IP addresses to hosts
        - ISP's DHCP server provides external network address
        - Local DHCP server provides internal network address
        - Most routers come with pre-configured DHCP server
    - *Domain Name System* (*DNS*)
        - Translates IP addresses into human readable URLs, aka *domains*
            - *Uniform Resource Locators*
        - IP address of DNS server is provided by ISP's DHCP server
    - Both DHCP and DNS settings can be modified via web interface
    - Google DNS & OpenDNS
        - Sometimes faster
        - Provides extra features

#### Programming languages
- Programs
    - Single file or complex system of files
        - OS treats these files as instruction sequence
        - Performed by processor and other devices
    - Begin as text file known as *source code* 
        - Uses various human readable languages that describe program actions

- Compiled languages
    - Source code converted to binary file
        - Computer executes binary file
    - *Compiler* program responsible for conversion
        - Compiled binary specific to kind of processor
    - Not computer readable and executable 
            - Processor can not directly execute these human readable languages
   
- Interpreted languages
    - Program does not need to be compiled
    - *Interpreter* reads source code and executes every time program is run
    - Pro
        - Development is easier and faster
    - Con
        - Programs tend to be slower than compiled programs 
    - Aka *scripting languages*

- JavaScript
    - Mostly used in web pages
    - Used to create complex apps for web, servers, and mobile
- C
    - Compiled language
    - Closely related with OSs
        - Particularly Unix
    - Used to write any kind of program to almost any device
    - Advantages
        - Flexibility
        - Speed
        - Can be compiled to run in different platforms and OSs with little or no modification
        - After compiling program will only run on targeted system
- Java
    - Compiled language
        - Converted to *bytecode*
        - Executed in *Java Virtual Machine* software environment
    - Main aspects
        - Portability
        - Same program can be executed in different OSs
        - Not related to JavaScript
- Perl
    - Most used to process text content
    - Strong regular expressions emphasis
        - Makes Perl suited for text filtering and parsing
- Shell
    - Not just a programming language
        - Interactive interface to run other programs
    - Shell programs
        - aka *shell scripts*
        - Can automate complex or repetitive tasks on command line enviro 
- Python
    - Good way to start learning programming
    - Easy to use approach
- PHP
    - Most used as server side scripting language 
        - Used for generating content for web
    - Used to generate dynamic content from various sources such as databases
    - LAMP
        - Popular server solution for running web servers
        - Made up of
            - Linux OS
            - Apache HTTP server
            - MySQL or Maria DB database
            - PHP programming
        - All of the programming languages described can also be used to implement these applications

### 1.3
Open source software and licensing  
Weight: 1  

#### The four essential freedoms
- Freedom 0
    - Freedom to run the program as you wish, for any purpose.
- Freedom 1
    - Freedom to study how the program works, and change it so it does your computing as you wish.
    - Access to source code is a precondition.
- Freedom 2
    - Freedom to redistribute copies so you can help others.
- Freedom 3
    - Freedom to distribute copies of your modified versions to others.
    - Gives whole community chance to benefit from changes.
    - Access to source code is a precondition.

#### FOSS & FLOSS
- FOSS
    - Free & open source software
- FLOSS
    - Free/libre & open source software
- Proprietary
    - For profit, controlled, limited 

#### Copyleft
- *Free Software Foundation* created licenses
    - *GNU General Public License* (GPL)
        - One of the most important license for free software
        - Used for the Linux kernel
    - *GNU Lesser General Public License* (LGPL)
        - Combination free software with modifications made to code where source code for mods do not have to be released to public
    - *GNU Affero General Public License* (AGPL)
        - Covers selling access to hosted software
    - *GNU Free documentation License* (FDL)
        - Extends freedom principles to software documentation
    - Also makes recommendations for or against:
        - Third party license
        - Affiliated projects

- *Copyleft*
    - FSF term meant to contrast principle of restrictive copyright
    - Transfers the liberal principles of a software license as unrestrictedly as possible to future variants of the software in order to prevent subsequent restrictions. 
    - Critics call copyleft "viral" since it's transmitted to subsequent versions
    - LGPL is a concession to be able to connect free software with "non-free" components
    - *Dual licensing*
        - Licensing under multiple licenses
        - e.g. a free license and a proprietary license

#### Open source & licenses 
- *Open Source Initiative* (OSI)
    - Has standardized procedure for checking OS software license compliance
    - Has more than 80 recognized OS licenses on the OSI website
    - *Berkeley Software Distribution*
        - Contradictory to copyleft
        - "OSI approved," especially the BSD licenses group
        - Varient of Unix OS originally deveoped at UC Berkeley
        - Gave rise to
            - NetBSD
            - FreeBSD
            - OpenBSD
        - Underlying licenses "permissive" 
            - Do not have aim of establishing terms of use of modified variants
            - Maximum freedom should help sofware decide how to edit
            - Developers have control over open or closed source
        - *2-Clause BSD License*, aka *Simplified BSD License*, or *FreeBSD License*
            - Consists of a standardized liability clause and the following:
                - Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:
                   - 1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer. 
                   - 2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

#### Creative commons 
