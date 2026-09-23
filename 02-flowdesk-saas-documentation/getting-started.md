# Getting Started

This guide explains how to create a Flowdesk account, configure your workspace, connect an integration, and create your first automation workflow.

By the end of this guide, you will have a working workflow that can receive an event and perform an automated action.

---

## Before You Begin

Before setting up Flowdesk, make sure you have:

* A valid email address
* Access to the application you want to connect
* Permission to configure that application's integration
* A clear idea of the task you want to automate

For your first workflow, choose a simple repetitive task.

For example:

> When a new lead is received, create a contact in your CRM.

---

## Step 1: Create Your Account

Open the Flowdesk application and select **Create account**.

Enter:

* Your name
* Email address
* Password

Then select **Create account**.

Flowdesk will create your user account and take you to the workspace setup screen.

---

## Step 2: Create a Workspace

A workspace is the environment where your team manages integrations and workflows.

Enter a workspace name.

For example:

```text
Acme Sales
```

Select your preferred configuration options and click **Create workspace**.

Your new workspace becomes the central location for your Flowdesk automation projects.

---

## Step 3: Open the Integrations Page

From the workspace dashboard:

1. Open the navigation menu.
2. Select **Integrations**.
3. Select **Add integration**.

Flowdesk displays the applications that can be connected to your workspace.

Choose the application you want to use.

---

## Step 4: Connect an Integration

Select an application from the integrations list.

Follow the authentication instructions provided by the application.

Depending on the integration, you may need to:

* Sign in to your account
* Authorize Flowdesk
* Select an account or workspace
* Grant required permissions

After authorization is complete, Flowdesk displays the integration as connected.

### Security Note

Only grant the permissions required for the workflow you intend to create.

Review the permissions requested by an integration before authorizing it.

---

## Step 5: Create Your First Workflow

Open **Workflows** from the workspace navigation.

Select **Create workflow**.

Give the workflow a descriptive name.

For example:

```text
New Lead → CRM Contact
```

A workflow consists of a trigger and one or more actions.

```text
Trigger
   ↓
Action
```

---

## Step 6: Configure the Trigger

The trigger defines the event that starts the workflow.

Select **Add trigger**.

Choose the event that should start the workflow.

For example:

```text
New lead received
```

Configure the required trigger settings and save the trigger.

Your workflow should now look like:

```text
New lead received
       ↓
     Action
```

---

## Step 7: Add an Action

Select **Add action**.

Choose the application and action you want Flowdesk to perform.

For example:

```text
Create CRM contact
```

Configure the required fields.

You may need to map information from the trigger to the action.

Example:

| Trigger Data | CRM Field    |
| ------------ | ------------ |
| Lead name    | Contact name |
| Lead email   | Email        |
| Lead phone   | Phone        |

After configuring the action, save the workflow.

---

## Step 8: Review the Workflow

Before activating the workflow, review the configuration.

Confirm that:

* The correct trigger is selected.
* The correct integration is connected.
* Required fields are configured.
* Data mappings are correct.
* The action performs the intended operation.

A completed workflow might look like:

```text
New lead received
        ↓
Check lead information
        ↓
Create CRM contact
        ↓
Send notification
```

---

## Step 9: Test the Workflow

Use the workflow's test option to verify that the configuration works as expected.

Trigger a test event.

For example:

```text
Test lead
test@example.com
```

Flowdesk should process the event and execute the configured action.

Check the workflow run details to confirm whether the action succeeded.

---

## Step 10: Activate the Workflow

After a successful test, select **Activate workflow**.

The workflow will now monitor for the configured trigger and execute automatically when the event occurs.

Your automation is now active.

---

## Example Use Case

Imagine a business receives leads through a website.

Without automation:

```text
Website
   ↓
Lead arrives
   ↓
Employee checks email
   ↓
Employee opens CRM
   ↓
Employee creates contact
   ↓
Employee notifies sales team
```

With Flowdesk:

```text
Website
   ↓
Lead arrives
   ↓
Flowdesk
   ↓
CRM contact created
   ↓
Sales notification sent
```

This reduces repetitive manual work and creates a more consistent process.

---

## Troubleshooting

If your workflow does not run as expected:

### Check the integration

Make sure the required application is still connected.

### Check the trigger

Confirm that the event you are testing matches the configured trigger.

### Check required fields

Make sure all required fields and data mappings are configured.

### Check workflow status

Confirm that the workflow is activated.

### Check workflow runs

Open the workflow run history to see whether Flowdesk received the event and where the workflow stopped.

For more troubleshooting guidance, see the [Troubleshooting](troubleshooting.md) guide.

---

## Next Steps

After completing your first workflow, you can explore:

* [Account Setup](account-setup.md)
* [Integrations](integrations.md)
* [Workflows](workflows.md)
* [Workflow Runs](workflow-runs.md)
* [Troubleshooting](troubleshooting.md)
