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

# Azure Active Directory Setup (Stage 2):
- They're a few tiers when creating a tenant for VIP EVENTS in Azure Active Directory.
- Free, Office 365, P1, P2
- Evaluating new on-premise building, application, users and requirements; scalability of business is crucial. Higher the tier, more expensive it is per user, per monthly
- RECOMMENDED: suggest that VIP EVENTS follows through with a P1 subscription
- P1 subscription:
  Benefits of P1:
  - We can set conditional access policies for users and which resources can be accessed
  - Self service password reset (SSPR): feature included which will minimize admin work and allow users who register for this feature to reset their own password without help of admin. This allows Admins to take care of other work that requires more attention
  - P1 includes all features which comes included in Free and Office 365 subscription tiers.
 
  Azure AD Tenant (Task 1):
  - Azure AD Tenant should be created for seamless integration with organization's structure
 
  User account configuration (Task 2):
  - List below is how each device is distributed amongst workforce at VIP EVENTS:
    - Desktop Computer: total = 7 
      - Office Workers: 3
      - Equipment Manager: 1
      - Catering Manager: 1
      - Head Chef: 1
      - CEO: 1
    - Laptop computer: total = 3
        - Chefs: 3
    - Tablet: total = 11
        - Equipment Handler: 4
        - Equipment Manager: 1
        - Catering Manager: 1
        - Head Chef: 1
        - Chefs: 3
        - CEO: 1
    - Mobile Phone: total = 32
        - Temporary/Contractor: 30
        - Catering Manager: 1
        - CEO: 1

    - NOTE: The Temporary/Contractors staff will use the guest subnet
    - All users will have accounts created based on their specific role, department and group

      - ALL USERS CREATED WILL HAVE Multi-Factor Authentication (MFA) enabled for security purposes

  Group-based access control implementation (Task 3):
  - Users will be catergorized into distinct groups based on roles
  - All groups have limited access to functionalities in VIP FOODS APP
    - Equipment Handler group:
        - Members: equip_handler_1 to 4
    - Equipment Manager group:
        - Members: equip_manager
    - Chefs group:
        - Members: chef1 to 10
    - Head Chef group:
        - Members: head_chef
    - Catering Manager group:
        - Members: catering_manager
    - Office Workers group:
        - Members: office_worker_1 to 3
    - CEO (owner) group:
        - Members: ceo_owner
    - Temporary/Contractor group:
        - Members: user1_ext to however many are contracted for work

  # Role and Access (Stage 3):
  - Here we will describe the proposed Azure role and access configuration
    VIP FOOD app integration (Task 1):
    - Need to create an application registration with Azure AD (Entra ID)
    - Name: VIP_Food_App_1
      Supports single-tenants, which are just accounts in organization
    - Will grant users access to specific functionality based on role
    - After application registration, you'll have:
      - name, client ID, tenant ID, Client Secret (name, expiration date, value, secret ID, rediret URL)

    Custome Azure Role (Task 2):
    - Custom roles are to be created to align with groups and facilitated controlled access
    - Roles:
        - Equipment Manager: Tailored for equipment manager, granting access to have an overview and handling of equipment functionalities
