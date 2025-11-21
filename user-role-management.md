---
copyright:
  years: 2025
lastupdated: "2025-11-21"

subcollection: dr-automation-powervs

keywords: user, MFA, multi autentication user, new user, permissions, user role management 
---

# User role management
{: #user-ro-mang}

{{site.data.keyword.DR_full}} introduces role-based access control (RBAC) to strengthen security and streamline user management. This feature allows administrators to define roles with specific permissions, ensuring that only authorized users can perform actions such as managing, discovering, or recovering virtual machines.

> **Note**:

## Working in the user role management screen
{: #work-user-ro-mang}

Use the following procedures to access and manage user roles in the User Role Management section of the DR automation GUI.

### Procedure to create a new user
{: #urm-procedure}

1. Click **root** in the user menu at the top-right of the screen. Select User Role Management from the menu displayed. The web-browser displays the User Role Management screen.
2. Select **Users** and it displays username, role name, and permission granted to a user in the list displayed, MFA Status, Actions and add a new user.
3. Click **Add New User**and provide the username, email address, and phone number, and optionally enable MFA for the user.
4. Under **Assign Role & Permissions**, select the role you want to assign from the list or click Add New Role to create a custom role and assign permissions to the role.
4. Click **Create New User**.

The new user is created and added to the user list with the assigned role and permissions.

### Procedure to Add new Role
{: #urm-procedure-role}

1. Click **root** in the user menu at the top-right of the screen. Select User Role Management from the menu displayed. The web-browser displays the User Role Management screen.
2. Select **Roles** and it displays the list of predefined roles that are root, admin, and monitor, along with the permissions assigned to each role. You can view existing roles or create a new role.
3. Click **Add New Role** and provide the role name and select the permissions you want to assign to this role.
4. Click **Create New Role**.

The new role is created and added to the list of available roles with the selected permissions.
