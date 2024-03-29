# Opportunistic security (OS)

Most of the time the internet service provider send the data through their network as they have to meet the Service Level Agreements with the customers. The SLA are mainly with respect to the throughput and latency. If they take the responsibility of encryption and decryption hop-by-hop, for sure they won’t be able to meet the SLAs. Hence they provide these security requirements end to end instead of hop-by-hop and users has to trust the service provider. At times even the Service Provider will compromise on the security of data when meeting the SLA is challenge, example peak traffic time. Service Providers has to implement many tools to assure the data security and administrating various features and protocols and its maintenance such as Key validation, procuring license etc are a challenge and that is another reason why the Service Providers often offload these responsibility to the end user systems. 


Nowadays most of the web services use VPN devices Public Key Infrastructure (PKI) for authenticating peers.  IPSec, SSL, and TLS is widely relied on PKI. In order to do so, one has to maintain a licensed Certificate Authority and it’s a challenge. Trusting a certificate authority is again a challenge. Many service provider will have issues on trust with the Certificate Authority and this might lead to the disagreement between users who are trying to connect and sometimes the service has to compromise on peer authentication and when the authentication is an optional service, then the traffic will be either send in plain text without any security or in cipher text with some security and most of the case the security provided are either ‘NULL’ or minimum and rarely with complete.

In Opportunistic Security, the baseline communication is in plain text and with encryption and authentication by negotiation between peers when available and the negotiated algorithms and techniques are used for encryption and authentication. If authentication is not available, then at least encrypt the data and if both are not available, send the data in plain text. Opportunistic Security is not an alternative for authenticated, encrypted data transfer when tools for such operation is already in place. It is only used when encrypted and authenticated data communication is needed otherwise go for plain text.

# OS in MPLS

As we discussed above the basic requirement of MPLS Opportunistic Security is encrypt the data between MPLS Routers with the a key both the routers are negotiated with. The has to be derived by a diffie-hellman key exchange. The generated session key after the Diffie-Hellmans key exchange is used for the packet encryption. The Algorithm to be used for encryption should be any flavours of AES and it should use in GCM mode for the payload authentication. The key derived should be according to the algorithm going to use which should be negotiated by exchanging TLVs.  The key length will change from 128 bit to 256 bits

# Implementation

OpenVswitch, Mininet, OpenFlow, Linux Crypto APIs, Kernel forwarding are the important technologies used in the project.

Step 1 : Install openvswitch

    In my project, i used ubuntu 16.04 as the OS and 2.9.2 is the openvswitch version.
    The prerequisites for installing openviswitch is given in the prerequisites.sh script. Install that in the ubuntu.
    
    copy the openvswitch to the ubuntu. we can use git clone https://github.com/openvswitch/ovs.git for copying openvswitch.
    makesure to use linux kernel 4.13 for installation.
    installation steps are given in the install.sh script. run the install.sh script from the directory where you copied the          
    openvswitch (ovs). 
    
    replace the ovs/datapath/action.c with the action.c file given in this repository 
    
    add files tlv.h,ach.h,achtlv.h,gap.h,adb.h,tlvo.h to the folder ovs/datapath/linux/compat/include/net/
    
    run once again the install.sh script from the directory where you copied the          
    openvswitch (ovs). 
   
   
    
    
