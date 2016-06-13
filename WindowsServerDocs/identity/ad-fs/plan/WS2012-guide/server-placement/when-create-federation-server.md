---
title: When to Create a Federation Server
ms.custom: 
  - AD
ms.prod: windows-server-2012
ms.reviewer: na
ms.suite: na
ms.technology: 
  - techgroup-identity
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c5eb15d0-976d-48db-8854-2e9e61521340
author: billmath
---
# When to Create a Federation Server
When you create a federation serverin Active Directory Federation Services \(AD FS\), you provide a means by which your organization can:  
  
-   Engage in Web single\-sign\-on \(SSO\)–based communication with another organization \(that also has at least one federation server\) and, when necessary, with the employees in your own organization \(who need access over the Internet\).  
  
-   Enable front end services to impersonate users to infrastructure services using identity delegation. For more information, see [When to Use Identity Delegation](../../../../ad-fs/plan/WS2012-guide/deployment/when-use-identity-delegation.md).  
  
The following sections describe some of the key decisions for determining when and where to create one or more federation servers.  
  
## Determine the organizational role for the federation server  
To make an informed decision regarding when to create a new federation server, you must first determine in which organization the server will reside. The role that a federation server plays in an organization depends on whether you place the federation server in the account partner organization or in the resource partner organization.  
  
When a federation server is placed in the corporate network of the account partner, its role is to authenticate the user credentials of browser, Web service, or identity selector clients and send security tokens to the clients. For more information, see [Review the Role of the Federation Server in the Account Partner](Review-the-Role-of-the-Federation-Server-in-the-Account-Partner.md).  
  
When a federation server is placed in the corporate network of the resource partner, its role is to authenticate users, based on a security token that is issued by a federation server in the resource partner organization, or its role is to redirect token requests from configured Web applications or Web services to the account partner organization that the client belongs to. For more information, see [Review the Role of the Federation Server in the Resource Partner](Review-the-Role-of-the-Federation-Server-in-the-Resource-Partner.md).  
  
## Determine which AD FS design to deploy  
You create federation servers in your organization whenever you want to deploy any of the following AD FS designs:  
  
-   [Web SSO Design](../../../../ad-fs/plan/WS2012-guide/map-goals-to-plan/web-sso-design.md)  
  
-   [Federated Web SSO Design](Federated-../../../../ad-fs/plan/WS2012-guide/map-goals-to-plan/web-sso-design.md)  
  
If necessary, an organization that deploys a Federated Web SSO design can configure a single federation server so that it acts in both the account partner role and in the resource partner role. In this case, the federation server may produce Security Assertion Markup Language \(SAML\) tokens, based on user accounts in its own organization, or reroute token requests to the organization, based on where the users' accounts reside.  
  
> [!NOTE]  
> For the Federated Web SSO design, there must be at least one federation server in the account partner and at least one federation server in the resource partner.  
  
## Differences between a federation server and a federation server proxy  
A federation server can serve out Web pages for sign\-in, policy, authentication, and discovery in the same way that a federation server proxy does. The primary differences between a federation server and a federation server proxy have to do with what operations a federation server can perform that a federation server proxy cannot perform.  
  
The following are the operations that only a federation server can perform:  
  
-   The federation server performs the cryptographic operations that produce the token. Although federation server proxies cannot produce tokens, they can be used to route or redirect the tokens to clients and, when necessary, back to the federation server. For more information about using federation servers, see [When to Create a Federation Server Proxy](../../../../ad-fs/plan/WS2012-guide/proxy-placement/when-create-federation-server-proxy.md).  
  
-   Federation servers support the use of Windows Integrated Authentication for clients on the corporate network; federation server proxies do not. For more information about using Windows Integrated Authentication with federation server, see [When to Create a Federation Server Farm](../../../../ad-fs/plan/WS2012-guide/server-placement/when-create-federation-server-farm.md).  
  
> [!CAUTION]  
> Communication between federation servers and SQL Server configuration databases, SQL Server attribute stores, domain controllers, and AD LDS instances is not integrity or confidentiality protected by default. To mitigate this, consider protecting the communication channel between these servers using IPSEC or using a physically secure connection between all of these servers. For communication between federation servers and SQL servers, consider using SSL protection in the connection string. For connections between federation servers and domain controllers, consider turning on Kerberos signing and encryption. For LDAP, LDAP\/S is not supported for AD LDS\/AD DS.  
  
## How to create a federation server  
You can create a federation server using the AD FS Federation Server Configuration Wizard or the Fsconfig.exe command\-line tool. When you use either of these tools, you can select any of the following options to create a federation server.  
  
-   Create a stand\-alone federation server  
  
    For more information about how to set up a stand\-alone federation server, see [Create a Stand-Alone Federation Server](Create-a-Stand-Alone-Federation-Server.md).  
  
-   Create the first federation server in a federation server farm  
  
    For more information about how to set up the first federation server or add a federation server to a farm, see [Create the First Federation Server in a Federation Server Farm](Create-the-First-Federation-Server-in-a-Federation-Server-Farm.md).  
  
-   Add a federation server to a federation server farm  
  
    For more information about how to add a federation server to a farm, see [Add a Federation Server to a Federation Server Farm](Add-a-Federation-Server-to-a-Federation-Server-Farm.md).  
  
For more detailed information about how each of these options work, see [The Role of the AD FS Configuration Database](../../../../ad-fs/plan/tech-ref/key-concepts/the-role-ad-fs-configuration-database.md).  
  
For more information about how to set up all the prerequisites necessary to deploy a federation server, see [Checklist: Setting Up a Federation Server](Checklist--Setting-Up-a-Federation-Server.md).  
  
