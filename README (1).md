# IT Support Home Lab: Active Directory for Help Desk

A hands-on IT support project where I followed a beginner Active Directory training and built the setup myself in a virtual lab. I installed **Active Directory Domain Services** on Windows Server and practiced the daily tasks of a Help Desk / Technical Support engineer: managing users, groups, Organizational Units, shared folders and printers.

> **Author:** Vishal Bagul
> **Role targeted:** IT Support / Help Desk / Desktop Support (Fresher)
> **Completed on:** 04/08/2026
> **Tools:** VirtualBox, Windows Server (YOUR VERSION), Active Directory Domain Services

## Learning Reference

I followed this video and repeated every step in my own lab:

**[Active Directory Training for Beginners | Help Desk and Technical Support](https://youtu.be/sI9pbhasVSA)**
Channel: SkillsBuild Security

---

## 1. Project Objective

To learn and demonstrate the core Active Directory tasks used in IT support:

- Installing and configuring Active Directory Domain Services
- Creating and managing user accounts
- Creating groups and managing group membership
- Recovering a deleted user
- Organizing objects with Organizational Units (OUs)
- Sharing folders and adding printers

---

## 2. Lab Environment

| Component | Details |
|---|---|
| Hypervisor | Oracle VirtualBox |
| Server OS | Windows Server YOUR VERSION |
| Server name | YOUR SERVER NAME |
| Domain name | YOUR DOMAIN NAME |
| Client OS (if used) | YOUR CLIENT OS |

---

## 3. Steps Performed

> Each step below matches a chapter of the training video. Add your own screenshots from the `screenshots/` folder.

### Step 1: Change the system name
Renamed the server to a meaningful name and restarted it, which is the first step before installing Active Directory.

![Change system name](screenshots/01-change-system-name.png)

### Step 2: Add features and roles (install Active Directory)
Used Server Manager, then Add Roles and Features, to install **Active Directory Domain Services**, then promoted the server to a domain controller by creating a new forest.

![Add roles and features](screenshots/02-add-roles-features.png)
![Promote to domain controller](screenshots/03-promote-domain-controller.png)

### Step 3: Add users
Created user accounts in Active Directory Users and Computers with a temporary password.

![Add users](screenshots/04-add-users.png)

### Step 4: Add users to groups
Added the users to the correct groups through the user's Member Of tab.

![Add users to groups](screenshots/05-add-users-to-groups.png)

### Step 5: Create groups
Created security groups for departments or teams, to manage access by group instead of by individual user.

![Create groups](screenshots/06-create-groups.png)

### Step 6: Recover a user
Restored a deleted user account so the user could log in again.

![Recover a user](screenshots/07-recover-user.png)

### Step 7: Create an Organizational Unit (OU)
Created an OU and moved users into it to keep the directory organized.

![Create OU](screenshots/08-create-ou.png)

### Step 8: Create a shareable folder
Created a folder on the server, shared it, and set permissions so only the right users or groups can access it.

![Shared folder](screenshots/09-shared-folder.png)
![Folder permissions](screenshots/10-folder-permissions.png)

### Step 9: Add a printer
Added a printer and made it available to users.

![Add printer](screenshots/11-add-printer.png)

---

## 4. Skills Demonstrated

- Active Directory installation and domain controller setup
- User account management (create, reset, recover)
- Group and OU management
- File share and permission management
- Printer setup
- Documenting IT work with screenshots

---

## 5. Problems Faced and How I Solved Them

| Problem | Solution |
|---|---|
| YOUR PROBLEM 1 | YOUR SOLUTION |
| YOUR PROBLEM 2 | YOUR SOLUTION |

> Write real problems you faced (for example a password rejected, a restart needed, or a VM setting). Interviewers like real examples.

---

## 6. Extra Practice

- Helpdesk ticket practice: see [ticket-log.md](ticket-log.md)
- Fix guides: see [knowledge-base.md](knowledge-base.md)

---

## 7. Conclusion

This project gave me practical experience with the day-to-day tasks of a help desk engineer. Next, I plan to learn Group Policy and PowerShell to automate user management.

---

## 8. Contact

- LinkedIn: https://www.linkedin.com/in/vishal-bagul-b47701222/
- Email: vishalbagul358@gmail.com
- GitHub: https://github.com/Vishal-Bagul-dev
