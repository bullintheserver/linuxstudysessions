# Topic 4
The Linux Operating System  

## 4.1
Choosing an Operating System
Weight: 1  

### Operating Systems
- Linux-based OSs
    - Enterprise
    - Consumer grade
- UNIX
- MacOS
- Windows-based OSs
    - Windows Servers
    - Windows Desktops

### Kernel and Distros
- Kernel
    - At the core of every distro
    - Manages system resources
    - Facilitates hardware <> software communication

**! Check your version and kernel with `uname -r`!**

- Key functions of the kernel incl:
    - Process management
    - Memory management 
    - Device management
    - File system management
    - System calls and interrupts
- Distributions aka "distros"
    - Packaged version of Linux OS
    - Includes
        - Installer
        - Linux kernel
        - Selection of software apps 
        - Libraries
        - Desktop environment. such as:
            - Gnome
            - KDE
        - Utilities
        - Additional tools for functionality
        - Version of linux kernel
    - Each distro tailored for:
        - Different use cases
        - User preferences
        - Hardware configurations

### Types of Distros

#### Enterprise Grade Linux Distros 
- Designed for large org/enterprise hardware
- Meets higher requirements for stability
- Distros tend to incl. older reliable releases of kernel/software
- Distros port important updates, security fixes back to stable versions
- May lack support for most recent consumer hardware

Includes:  
- Red Hat Enterprise Linux
- CentOS
    - *Community ENTerprise*
- SUSE Linux Enterprise Server
- Debian GNU/Linux
- Ubuntu LTS
    - Long term support versions suited for enterprise

#### Consumer Grade Linux Distros  
- Meant for SOHO, hobbyist users
- Likely to be using latest hardware
- Will need and have latest drivers 
- Will not meet needs of large orgs/enterprise
- Usually the latest kernel 
    - May be under-tested, that's alright

Includes:  
- Fedora
- Ubuntu non-LTS
- openSUSE

#### Experimental/Hacker Linux Distributions  
- Live on cutting edge of technology
- Contain recent versions
    - Even if they have bugs or untested features
- Use a rolling release model
    - Allows for update delivery at any time
- Use by advanced users

Includes:  
- Arch
- Gentoo

#### Conclusion
- Check https://distrowatch.com/ for more distro options
- Enterprise hardware
    - Can use both enterprise or consumer distros
- Consumer hardware
    - Must use consumer distros

### Linux Support Lifecycle