# Cyber Security Proposal Project
This is a repo to showcase a CyberSecurity Proposal Project transforming business requirements into a Proposal.

#5 stages of Project
1. Company Requirements (gather requirements)
2. Azure AD Setup (Specify Azure AD tenant structure)
3. Role and Access (Define granular access permissions)
4. Azure AD Connections (Integrate Azure AD with apps and services)
5. Policy Implementation (Detail Security Policies)

# Company Requirements (Stage 1)
This section will have details in regards to the scope of project, network design along with required tasks to implement identified network architecture.

- VIP EVENTS' cybersecurity requirements (Task 1)
  VIP Events company is relocating to a brand new 3-story building to upscale business operations.
  - Ground floor: Loading dock/storage space for machinery
  - First floor: Food prepartion, Kitchen and storage
  - Second floor: Office space and conference rooms

- Info:
- VIP Events is expanding its' workforce to 21 employees, bringing along 46 mobile devices and 7 fixed devices that will be required to have security access to the new network
- Each floor will have it's devices segmentated within network for security purposes.
- 32 mobile phones, 11 tablets, 3 laptops, 7 desktop computers
- WorkStaff (total of 21):
- CEO, Head Chef, Equipment Manager, 3 office workers, 10 head chefs, 4 equipment handlers. *Temporary employees*
- ROLES:
- Equip Handler, Equip Manager, Chef, Head Chef, Catering Manager, Office/Admin, CEO, Temporary

VIP FOOD APP: functionalities 
- Equipment management
- Kitchen Management
- Event Management
- Administration


BUILDING STRUCTURE AND NETWORK DESIGN (Task 2 & 3):
- We will have network segmentation within the network. Guided by a defense in depth priniciple, this will protect the network from any unauthorized access to information or data. By preventing unilateral movement and safeguarding assets, this will reduce the risk of potential threats.
- Network architecture suggested below will have subnets for both wired/wireless devices on-premise
- Each subnet has role-based restrictions for those with specific roles within the floor they're working on.

Ground floor subnets:
- Equipment handlers:
  Wired: 10.0.1.0/26
  Wireless: 10.0.1.128/26
- Equipment Manager:
  Wired: 10.0.1.68/26
  Wireless: 10.0.1.192/26

   First floor subnets:
  - Chefs:
    Wired: 10.0.2.0/26
    Wireless: 10.0.2.128/26
  - Head Chef:
    Wired:10.0.2.68/26
    Wireless: 10.0.2.192/26
  - Catering Manager:
    Wired: 10.0.2.128/26
    Wireless: 10.0.2.0/26

    Second Floor subnets:
    - Office Workers:
      Wired: 10.0.3.0/26
      Wireless: 10.0.3.128/26
    - CEO:
      Wired: 10.0.3.64/26
      Wireless: 10.0.3.128/26

    Production subnets (servers, printers, systems):
      Wired: 10.1.0.0/24
      Wireless: 10.1.0.128/25

    Management subnets (routers, switches, firewalls):
      Wired: 10.1.1.0/24
      Wireless: 10.1.1.128/25

    Guest/Temporary subnets (laptops, tablets, smartpohones):
      Wired: 10.1.2.0/24
      Wireless: 10.1.2.128/25

  Access control and Security policies (Task 4):
  - Advisable to implement access controls for every subnet to guarantee a secure and well-structured network environment
  - Policies within on-premise Firewall should oversee user access to the subnets
  - Azure Policies will be implemented later in security section
  - Highly recommended to install firewalls at the network perimeter to effectively filter inbound/outbound traffic
  - Intrusion Detection and Prevention System implementation:
    Also highly recommended to implement at the network perimeter. Doing this will assist in continously monitoring network activities, ensuring
    swift responses to any suspicious activity or possible intrusion threats

  User roles and Access requirements (Task 5):
  - Azure AD Tenant should be configured along with user accounts being created which includes their specific roles within company.
  - Assigning roles directly within the group, for seamless approach to resource management
  - Integrate tenant with VIP FOOD APP to streamline user authentication and authorization
  - Specific roles will have specific features within APP based on their role within company
 
  Physical Security (Task 6):
  - Robust ID-based access control system should be required to effectively regulate entry and exit points within physical premises
  - By doing this, authorized employees have access to the designated areas to which they're authorized to be in, within the building.
  - Integration of ID-based access control system with Azure Active Directory is highly recommended to have a centralized point of authentication, enabling Azure AD's robust features for advanced identity management and access policies

    Door and Main entrance integration:
    - VIP Events should also extend these security measures for the main entrance and doors in building
    - Extra layer of security always contributes to safety and exclusivity of on-premise location, protecting against unauthorized access

    CCTV integration:
    - Cameras should be strategically placed to provide comprehensive surveillance footage
    - CCTV system can also be integrated with the exisiting access-control system

    Real-time monitoring:
    - Utilizing real-time monitoring can complement physical security features
    - Security Personnel to aide with observing access logs, handling alerts from unauthorized access or anomalies
   
    Visitor authentication:
    - To ensure heightened security, recommended for VIP EVENTS to streamline authentication process for guests
    - Implement a secure registration for individuals who aren't directly associated with VIP EVENTS
