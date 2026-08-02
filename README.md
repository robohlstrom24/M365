![1](images/M365-banner3.png)

## Operational Relevance

This project showcases foundational Microsoft 365 (M365) skills modeled after an IT Support environment. Proficiency with Tier-1 and Tier-2 IT support tasks is demonstrated with screenshots (click the > dropdowns to view). Troubleshooting activities are supplemented with ITSM-style tickets which are documented in a companion repository.    

(see: [Troubleshooting Journal](https://github.com/robohlstrom24/troubleshooting-journal))

## Job Skills Demonstrated:

- Hybrid identity lifecycle management 
- Conditional Access policy configuration and MFA enforcement
- SharePoint permissions management 
- Entra B2B external identity and secure contractor access provisioning
- M365 license troubleshooting via group-based license inheritance
- Troubleshooting email delivery failure with message trace
- Entra ID SSO Troubleshooting 
  
## Tier-2 Job Duties

<details>
  <summary>Hybrid Identity Lifecycle (AD + M365 + Entra + Intune) - Joiner | Mover | Leaver</summary>

**Project summary: Employee Steve Smith is hired as an IT Support Specialist, promoted to a Systems Administrator, placed on medical leave, brought back from leave, and then terminated. Identity and access management principles are applied to each change across on-premises and cloud platforms (least privilege, RBAC, MFA authentication controls, data protection for BYOD).**

  <details>
    <summary>Phase 1: Employee onboarding</summary>

  ![1](images/capstone1/01_AD-User-Created.png)
  ________________________________________________
  ![2](images/capstone1/02_MFA-enabled.png)
  ______________________________________________
  ![3](images/capstone1/03_outlook-login.png)
  
  </details>

  <details>
    <summary>Phase 2: Security Controls</summary>

 ![4](images/capstone1/04_create-conditional-access.png)
 _______________________________________________________
 ![5](images/capstone1/05_conditional-access-applied.png)
 ________________________________________________________
 ![6](images/capstone1/06_Intune-policy-config.png)
 _______________________________________________________
 ![7](images/capstone1/07_Intune-applied-Outlook.png)
 _______________________________________________________
 ![9](images/capstone1/09_copy-paste-blocked.png)
    
  </details>
  
<details>
  <summary>Phase 3: Employee promotion</summary>

![10](images/capstone1/10_add-admin-role.png)
________________________________________________
![11](images/capstone1/11_move-to-sysadmin.png)
__________________________________________________
![12](images/capstone1/12_RDP-access-control.png)
____________________________________________________
![13](images/capstone1/13_GPO-verified.png)
________________________________________________
![14](images/capstone1/14_RDP-deny-confirm.png)
______________________________________________
![15](images/capstone1/15_RDP-success.png)

</details>

<details>
  <summary>Phase 4: Medical leave</summary>

![16](images/capstone1/16_leave-Entra-disabled.png)
___________________________________________________
![17](images/capstone1/17_leave-AD-disabled.png)
_____________________________________________________
![18](images/capstone1/18_M365-lock-confirmed.png)
______________________________________________________
![19](images/capstone1/19_AD-lock-confirmed.png)
____________________________________________________
![20](images/capstone1/20_return-M365-unlocked.png)
_______________________________________________________
![21](images/capstone1/21_return-AD-unlocked.png)

</details>

<details>
  <summary>Phase 5: Termination (offboarding)</summary>

![22](images/capstone1/22_AD-group-removal.png)
_______________________________________________
![23](images/capstone1/23_AD-disable-user.png)
________________________________________________
![24](images/capstone1/24_Entra-revoke-sessions.png)

</details>

**Troubleshooting Activities:**

Steve could not initially access the server remotely after promotion despite GPO application granting access. Root cause: IT-SysAdmins AD group was not added to the server’s local Remote Desktop Users group, preventing RDP access despite the correct domain permissions. 
(see ITSM-style trouhleshooting ticket: [Troubleshooting Journal T-0015](https://github.com/robohlstrom24/troubleshooting-journal) ) 

**Lessons Learned:**

-Identity changes span multiple layers (AD groups, local server permissions, cloud RBAC)

-Lifecycle management is a security control, ensuring access is granted, modified, and revoked appropriately as employee roles change

-Hybrid environments require coordination between on-prem identity systems and cloud identity platforms 

</details>


<details>
  
  <summary>Troubleshooting Email Malfunction After Inadvertant Licensing Group Removal</summary>

**Scenario:** 
A user's licensing group is inadvertantly removed during department/role change, offboarding/reboarding error, or automation error with a bulk group cleanup script

![1](images/email.licences/error.full.png)

__________________________________________

**User not assigned any licenses**

![2](images/email.licences/no.license.assigned.png)

_________________________________________________

**User not a member of security group**

![3](images/email.licences/no.group.membership.png)

___________________________________________________

**User added back to security group**

![4](images/email.licences/user.added.back.png)

_________________________________________________

**User inherits license from security group**

![5](images/email.licences/license.inherited.png)

__________________________________________________

**Email functionality restored**

![6](images/email.licences/email.works.png)

**Lessons Learned:**

-M365 group membership acts as the source of truth for service provisioning

-Always investigate the assignment source (group vs. direct) before making changes

-Assigning licenses via group membership instead of directly helps to avoid inconsistent access, orphaned licenses, and unnecessary licensing costs

</details>

<details>
  <summary>SharePoint Controlled Link Distribution to Non-Tenant User</summary>

  **Scenario: A company hires an external contractor to collaborate on an internal project. The contractor requires edit access to a specific SharePoint file, while access to all other internal resources must remain restricted.**

![2](images/Lab1/2-groups-created.png)
__________________________________________
![1](images/Lab1/1-invite-external-user.png)
___________________________________________
![5](images/Lab1/2.1.1-add-group.png)
_____________________________________________
![4](images/Lab1/3.1-break-inheritance.png)
______________________________________________
![5](images/Lab1/5.1-reconfigure-permissions.png)
________________________________________________
![7](images/Lab1/7-share-outside-org.png)
__________________________________________
![6](images/Lab1/7.2-consent.png)
__________________________________________
![8](images/Lab1/8-share-link-validation.png)
____________________________________________
![10](images/Lab1/10-no-edit-permissions.png)

**Lab Troubleshooting:**

Permissions inadvertantly assigned at the library-level instead of file-level, resulting in overly-broad access.

  See: [Troubleshooting Journal T-0018](https://github.com/robohlstrom24/troubleshooting-journal) for ITSM-style troubleshooting ticket
  
**Lessons Learned:**
- Breaking SharePoint permission inheritance allows for precise resource control
- Secure sharing depends on both identity and link configuration
- Utilizing RBAC and group-based access enables superior scaling compared to direct user permissions 

</details>

<details>
  <summary>Entra ID SSO (SAML/OIDC/Troubleshooting)</summary>

____________________________________________
**This lab provided hands-on experience with CompTIA Security+ concepts, demonstrating how SSO is applied in real-world scenarios.** 

**Tools Utilized:**

-Microsoft Entra ID (M365 Business Premium License) - IdP 

-IAM Showcase (sptest.iamshowcase.com) - SAML 2.0 test SP that displays assertion contents after successful federation

-OpenID Connect Debugger (oidcdebugger.com) - test tool for OIDC flows which captures the authorization code and token response

**Lab Build:**

**SAML Demonstration:**

![1](images/SSO/1-SSO.png)
_____________________________
![2](images/SSO/2-SSO.png)
___________________________
![3](images/SSO/3-SSO.png)
___________________________

**OIDC/OAuth Demonstration:**

![4](images/SSO/4.1-SSO.png)
___________________________
![5](images/SSO/5-SSO.png)
______________________________
![6](images/SSO/6-SSO.png)
_______________________________
![7](images/SSO/7-SSO.png)
______________________________

**Troubleshooting scenario:**
User John Doe unable to access application via SSO due to removal from app assignment in Entra ID.

**Potential root causes:** human error during admin cleanup, offboarding process gone wrong, group-based assignment changes.
![8](images/SSO/8-SSO.png)

See: [Troubleshooting Journal T-0019](https://github.com/robohlstrom24/troubleshooting-journal) for ITSM-style troubleshooting ticket

**Lessons Learned:**

-SAML and OIDC enable SSO through different mechanisms: SAML uses XML assertions for legacy enterprise apps, whereas OIDC uses JSON-based ID tokens for modern web and mobile apps

-Authentication and authorization are distinct layers: valid credentials don’t guarantee app access if something is blocking the user downstream

-Entra ID sign-in logs are the first tool to utilize when investigating SSO failures

-An effective SSO diagnostic framework isolates the problem to the IdP side (account not assigned to the app, MFA failure, CA block) or the SP side (misconfigured Entity ID, ACS URL mismatch)

 
</details>

<details>
  
  <summary> Diagnosing Email Delivery Failure (Message Trace) </summary>

  **Lab Build: Distribution List creation and transport rule enforcement**

  ![1](images/DL/1-MT.png)
  _____________________________
  ![2](images/DL/2-MT.png)
  _____________________________

  **Troubleshooting scenario: an employee sends an email to company-all distribution list. Recipients report they never received it — and the sender never saw a bounce-back**

  ![3](images/DL/3-MT.png)
  __________________________
  ![4](images/DL/4-MT.png)

  **Note: Microsoft's auto-generated "How to fix it" guidance for the error was written for sender-side troubleshooting, not mentioning that resolution required moderator action. Following it as written could send an admin down the wrong path entirely. The event detail text, not the suggested fix, is what pointed to the real root cause.**
  
  _________________________
  ![5](images/DL/5-MT.png)
  __________________________
  
  **Not shown: moderator approves email for distribution**

  ![6](images/DL/6-MT.png)
  ______________________________

  **Lessons learned:**

Distribution lists with many recipients are a high blast-radius target. Because SMTP relay is a store-and-forward mechanism rather than instantaneous delivery, Exchange Online can intercept a message mid-transit via transport rules

-Status labels in Exchange message trace can look identical for very different root causes — a genuine bounce and a policy hold both surface as "Failed." Always read the event detail before concluding root cause; don't diagnose off the headline status

-Built-in "fix it" guidance is written for the most common case, not necessarily aligned with the true root cause. Treat it as a starting hypothesis to verify, not a script to follow

</details>

<details>
  <summary>Exploring Email Authentication (SPF/DKIM/DMARC) and Troubleshooting Common Issues</summary>
__________________________________________________________________
  
**This lab involved building and validating a custom domain, then exploring email authentication troubleshooting scenarios.** 

**Lab Build:**

(screenshots not shown)
-Custom domain acquired (Namecheap)
-Domain name added in M365 admin center
-Domain ownership verified: M365-generated TXT record added to domain registrar → successfully propagated and resolved  
-M365 service records added to domain registrar to activate mail flow (MX for routing, CNAME for Autodiscover, SPF TXT) → successfully propagated and resolved

![1](images/email-auth/email-auth-1.png)
______________________________________
![2](images/email-auth/email-auth-2.png)
______________________________________
![3](images/email-auth/email-auth-3.png)
_____________________________________
Screenshots not shown:
-DMARC policy authored manually (v=DMARC1; p=none; rua=mailto:mjones@rob-domain-homelab.it.com
-TXT record published directly as _dmarc at the domain registrar → propagated and resolved
_________________________________________________
![4](images/email-auth/email-auth-4.png)
______________________________________
![5](images/email-auth/email-auth-5.png)
_____________________________________
-Subsequent screenshots represent diagnostic entry points that an IT Support tech would check for email authentication troubleshooting 
-Each screenshot maps to a distinct symptom, not a fixed step-by-step sequence
____________________________________________
![6](images/email-auth/email-auth-6.png)
______________________________________
![7](images/email-auth/email-auth-7.png)
______________________________________
![8](images/email-auth/email-auth-8.png)
_____________________________________
![9](images/email-auth/email-auth-9.png)
_____________________________________

**Lessons Learned:**

-DNS serves as the foundation for email authentication through TXT/CNAME records that carry authorization lists (SPF), cryptographic public keys (DKIM), and enforcement policy (DMARC)

-Troubleshooting email authentication isn't a single checklist: different symptoms lead to different approaches (third-party DNS lookups, Defender Portal, email message headers)

-Delivery and authentication are separate concerns. Exchange Message Trace confirms a message was processed and handed off to the recipient's server, not that it passed SPF/DKIM/DMARC

</details>
___________________________________________________

## Tier-1 Job Duties

<details>
  <summary> Employee Onboarding ( Create User, Assign License, Validate Mailbox ) </summary>

  ![1](images/create.user.png)
  ____________________________

  ![2](images/assign.license.png)
  _______________________________

  ![3](images/user.active.png)
  ________________________________

  ![4](images/mailbox.verification.png)
  
</details>

<details>
  <summary> Password Reset & Sign-in Block </summary>

  ![1](images/password.reset.png)
  _________________________________

  ![2](images/block.sign.in.png)
  _________________________________

  ![block](images/block.sign.in2.png)
  
</details>

<details> 
  <summary>Access Provisioning Through Groups (RBAC) </summary>

  ![1](images/create.security.group.png)
  _________________________________________

  ![2](images/add.user.to.group.png)
  
</details>

<details>
  <summary>Create Shared Mailbox and Assign Access </summary>

  ![1](images/create.shared.mailbox.png)
  ________________________________________

  ![2](images/assign.user.access.png)
</details>

