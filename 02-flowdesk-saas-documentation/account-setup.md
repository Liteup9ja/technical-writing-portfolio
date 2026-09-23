# Account Setup

This guide explains how to configure your Flowdesk account and workspace after creating your account.

A properly configured workspace provides the foundation for managing integrations, workflows, and team members.

---

## Account Overview

Your Flowdesk account contains your personal profile and access to one or more workspaces.

A typical setup looks like:

```text
Flowdesk Account
      ↓
Workspace
      ↓
Integrations
      ↓
Workflows
```

Your personal account controls your access, while the workspace contains the business automation configuration.

---

## Update Your Profile

After creating your account, open your profile settings.

You can configure information such as:

* Full name
* Profile photo
* Email address
* Password
* Notification preferences

Select **Save changes** after updating your information.

---

## Create a Workspace

A workspace is the main environment where automation projects are managed.

To create a workspace:

1. Open the workspace selector.
2. Select **Create workspace**.
3. Enter a workspace name.
4. Select **Create**.

Example:

```text
Workspace name:
Acme Operations
```

Choose a name that clearly identifies the team, company, or project using the workspace.

---

## Workspace Settings

Open **Workspace Settings** to configure your workspace.

Depending on your account configuration, you may find settings for:

* Workspace name
* Workspace description
* Default timezone
* Notification preferences
* Team access
* Connected integrations

### Timezone

Set the workspace timezone to match the primary location of your team.

The timezone can affect how scheduled automation tasks are interpreted.

For example:

```text
Timezone:
Africa/Lagos
```

---

## Invite Team Members

Workspace administrators can invite other users.

To invite a team member:

1. Open **Workspace Settings**.
2. Select **Members**.
3. Select **Invite member**.
4. Enter the person's email address.
5. Select a role.
6. Send the invitation.

The invited user receives an email containing instructions for joining the workspace.

---

## Workspace Roles

Flowdesk can use role-based access to control what members can do.

Example roles include:

| Role   | Description                           |
| ------ | ------------------------------------- |
| Owner  | Full control of the workspace         |
| Admin  | Manage workspace settings and members |
| Editor | Create and modify workflows           |
| Viewer | View workflows and workflow activity  |

Assign the least amount of access required for each team member's responsibilities.

---

## Manage Notifications

Flowdesk can notify users about important workspace activity.

Notification preferences may include:

* Workflow failures
* Integration errors
* Workflow completion
* Team invitations
* Account activity

Configure notification preferences from your account or workspace settings.

---

## Configure Your First Integration

After setting up your workspace, connect the applications you want Flowdesk to work with.

Open:

**Integrations → Add integration**

Select an application and follow its authorization process.

For detailed integration guidance, see [Integrations](integrations.md).

---

## Recommended Setup

For a new business workspace, the following order is recommended:

```text
Create Account
     ↓
Create Workspace
     ↓
Set Timezone
     ↓
Invite Team Members
     ↓
Connect Integrations
     ↓
Create Workflow
     ↓
Test Workflow
     ↓
Activate Workflow
```

Completing these steps before creating production workflows helps reduce configuration problems later.

---

## Security Recommendations

Protect your Flowdesk account by following basic security practices.

### Use a Strong Password

Use a unique password that is not reused across other services.

### Protect Account Access

Do not share your account credentials with other team members.

Instead, invite team members to the workspace and assign appropriate roles.

### Review Permissions

Regularly review workspace members and remove access that is no longer required.

### Review Integrations

Check connected integrations periodically and disconnect services that are no longer needed.

---

## Troubleshooting Account Setup

### I cannot create a workspace

Check that your account has permission to create workspaces and that all required fields have been completed.

### A team member did not receive an invitation

Ask the team member to check their spam or junk folder.

Verify that the invitation was sent to the correct email address.

### I cannot access workspace settings

Your role may not have permission to manage workspace settings.

Contact a workspace owner or administrator.

### My timezone is incorrect

Open Workspace Settings and update the workspace timezone.

---

## Next Steps

After configuring your account, continue with:

* [Integrations](integrations.md)
* [Workflows](workflows.md)
* [Workflow Runs](workflow-runs.md)
* [Troubleshooting](troubleshooting.md)
