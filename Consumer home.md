## Consumer Home

### Description

  A domestic residential (home) environment, from which there is typically one ISP chosen by the adult(s) residing
  in the household. This single ISP may provide redundant connectivity over multiple paths, although it is more usually non-redundant.
  This ISP connection is made available over WiFi within the home. 
  
  In the home there can be multiple smartphones (or tablets) that connect both to the WiFi and (if they contain a SIM/eSIM)
  independently over the mobile network. Each smartphone could be attached to a different mobile provider, which may or may not be
  from the same company providing the household ISP service.
  
  The home is populated with a growing number of "smart" devices that independently perform a particular function, such as temperature
  control or remote observation. These devices are connected to the WiFi but their OS is generally managed by the manufacturer rather than
  any of the people in the home. In some cases, no OS updates occur and the software will be dated.
  
  There is generally one central router for the home, and this router announces the DNS resolver IPs it recommends.
  While it is usually provided by the chosen household ISP, and uses configuration managed by that ISP, variations do exist.
  The router may come from another source, and could use different settings out of the box. Or an adult could have configured
  the router to announce a different DNS server such as a local Pi-hole, or an alternative public DNS provider.

### Specific cases

1. WiFi user is happy to use any DNS recommended by the WiFi network to which they have chosen to attach

    The user of the WiFi device, such as a smartphone, has instructed it to connect to a WiFi network with a certain SSID, that communicates
    in some way the party operating the WiFi network. In the consumer home this is dependent on the configuration of the central router,
    and in the most common case the SSID will be associated with the name of the household ISP.
    
    In accepting this connection, the user is expecting that the SSID will deliver a certain set of behaviours regarding performance,
    privacy, protection, etc.
    
    Once attached to the SSID, the central router announces the DNS resolver IPs it recommends for this network. The user wishes the device
    to follow those recommendations, in order to obtain the expected behaviours.
    
1. WiFi user prefers to use DNS directly to a provider they are happy with

    The user would like a different set of performance/privacy/protection behaviours than those associated with the local SSID.
    Perhaps they are looking for greater privacy, a stronger set of malware protections, or a more customized service.
    
    They may already have a DNS provider in mind that can meet those requirements, in which case they configure the device to use this
    provider. In order to avoid degrading properties such as privacy, this configuration should mandate the use of encrypted DNS.
        
    If they do not have a pre-chosen DNS provider, the user would like the device to offer the means to choose a provider. This will
    involve:
      * Discovery of reachable DNS resolvers
      * Learning about the properties offered by those resolvers, and the trust model behind it (company reputation, legal regime, etc)
      * Selection of the preferred resolver
      
    To avoid becoming onerous this process should be automated as much as possible, because selection may need to be repeated every time
    there is a change to the list of attached networks. Of course it cannot be entirely automated, because it is necessary for a
    human decision to be made. Ideally there will be a means for the user's preferences to be stated at the beginning, and for these
    to be automatically followed during subsequent network events.
    
    Regardless of selected resolver, the user would usually wish to obtain access to locally-scoped resources such as printers or smart home
    devices. In addition if the home router imposes a captive portal, e.g. because the ISP link is down, the user would like to be able to
    access the portal.
    
1. WiFi user wishes to tunnel through a VPN to a provider they are happy with

    The user has previously selected and configured a VPN to a provider. They wish to use this VPN for all internet-bound traffic.
    
    VPN client configuration will state the DNS resolver to be used when the VPN is up. This is often the same provider as the VPN server,
    but could be another public DNS service.
    
    During the time period between WiFi attach and the VPN interface coming up, the user wishes to minimise the amount of cleartext network
    communication on the local WiFi. For example, they may need to use the DNS resolver recommended by the home router in order to
    look up the address of the VPN server, but would prefer to avoid sharing privacy-sensitive queries with this resolver.
    
    After the VPN is up, the user would usually wish to retain access to locally-scoped resources such as printers or smart home
    devices. In addition if the home router imposes a captive portal, e.g. because the ISP link is down, the user would like to be able to
    access the portal.
    
1. Parent of young children

    If the home contains children under the age of 10 who are given devices with WiFi access, the parent (IL-Parent-9) will often
    wish to allow them access to some parts of the internet but not others. In particular they will want to avoid them being exposed
    to inappropriate content.
    
    For devices for which they have administrative control, this can often be achieved with device-based settings.
    
    If the parent requires a more general solution, including coverage of heterogeneous devices and devices brought into the home
    by friends (IL-Parent-Byod), then they may need the home router or upstream ISP to implement such controls.

1. Smart device

    "Smart" devices (DD-Homedev) that independently perform a particular function, can be considered to have at least three stakeholders concerned
    with their operation.
  
    The first is the manufacturer (OL-Thingco) who created the hardware and software, and may or may not wish to ensure its
    continued operation, safely and effectively, possibly with an ongoing revenue stream.
  
    The second is the resident adult (IL-Adult) who placed it in the home, who certainly wishes it to work and be secure from attack.
    They may also wish to apply controls on the communication between the device and the internet, to limit data exfiltration or its
    potential for remote compromise. This will be even more important if the embedded software is old and contains known CVEs.
  
    A third stakeholder can be another resident or a visitor to the home (also IL-Adult), who may not wish to be observed by the device
    without their consent. On the other hand they may wish to engage with the device, e.g. to use their smartphone to play music
    through a smart speaker.
  
    The manufacturer may choose to respect the DNS resolver recommended by the home router, in which case controls imposed by the
    resident adult may be feasible. Or the manufacturer may choose to tunnel encrypted DNS elsewhere, or hardcode IPs, in which case
    controls may be very difficult.
    
1. App-based services

    Smartphones run apps written by a software developer (OL-App). These apps may follow the traditional model of letting the
    device OS handle DNS resolution, or they may include their own DNS client implementation. The latter can involve encrypted DNS
    tunnelled to a provider chosen by the software developer. This may permit the app to work better in some way, but it comes at the cost
    of losing the OS-based intelligence implied by the previous use cases. This may impact the ability to meet those use cases.
    
### Problems to be solved

1. The SSID of a WiFi network is interpreted to communicate who is administratively responsible for the network and its DNS resolver,
   but this is not always a direct match. A reconfigured router can claim to be organization A but in fact be controlled by person B.
   This breaks the trust model of the first use case.
   
1. There needs to be a mechanism for a user to discover the set of available DNS resolvers.

1. There needs to be a mechanism for a user to discover the entity that operates each available resolver,
   the properties that they claim to offer, and the legal regime under which that entity operates.

1. The user desires a means by which their preferences for selection of the optimum resolver can be communicated to the device, remembered,
   and automatically implemented every time there is a network change.

1. In cases where the selected resolver is not the recommended one for the local network, the device OS needs a means by which it can
   retain access to locally-scoped resources. This may require a mechanism to discover the set of DNS names that are only available
   from the local resolver.
   
1. Devices with a configured VPN client may need to refrain from use of the local network for privacy-sensitive activities until the
   VPN is up.
   
1. A parent operating a home WiFi network (IL-Parent-Byod) requires a means to impose controls on the internet destinations that can
   be reached by at least some of the WiFi clients.
   
1. A resident adult requires a means to impose controls on the internet destinations, and volumes of flows, that can be reached by
   individual smart home devices.
   
1. A visiting adult requires a means to discover the set of smart devices in the home that legally need their consent to operate, and
   a means to grant or deny that consent.
   
1. A device OS needs a way of ensuring that apps comply with its own, the user's and the network's policies regarding DNS.

