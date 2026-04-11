![1](images/M365-banner3.png)

## Operational Relevance

This project demonstrates foundational Microsoft 365 (M365) skills modeled after an IT Support environment. Proficiency with Tier-1 and Tier-2 IT support tasks is demonstrated with screenshots (click the > dropdowns to view). Troubleshooting activities are supplemented with ITSM-style tickets which are documented in a companion repository.    

(see: [Troubleshooting Journal](https://github.com/robohlstrom24/troubleshooting-journal))

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

</details>

<details>
  <summary>Troubleshooting SharePoint File Access Denial</summary>

  **Scenario:** A file is shared via direct link, but due to misconfigured file-level permissions and broken inheritance, the user is unable to access or even see the file within the SharePoint document library.

  ![1](images/SharePoint-Denial/1-hook.png)

  ![2](images/SharePoint-Denial/2-check-permissions.png)

  ![3](images/SharePoint-Denial/3-unique-permissions.png)

  ![4](images/SharePoint-Denial/4-grant-permissions.png)

  ![5](images/SharePoint-Denial/5-file-visible.png)

  **Lessons Learned:**
- Limited Access does not grant usability, it often only allows navigation to a resource, not interaction
- Always verify inheritance vs. unique permissions, as file-level overrides can silently block access even when folder access appears correct

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
![7](images/Lab1/7-share-outside-org.png)
__________________________________________
![6](images/Lab1/6.1-accept-invite.png)
__________________________________________
![8](images/Lab1/8-share-link-validation.png)
____________________________________________
![10](images/Lab1/10-no-edit-permissions.png)

**Lessons Learned:**
- Breaking SharePoint permission inheritance allows for precise resource control
- Secure sharing depends on both identity and link configuration
- Utilizing RBAC and group-based access enables superior scaling compared to direct user permissions 

</details>
