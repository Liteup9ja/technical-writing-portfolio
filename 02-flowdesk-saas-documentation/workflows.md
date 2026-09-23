# Workflows

Workflows allow you to automate tasks by connecting a trigger to one or more actions.

A workflow defines:

* What event starts the automation
* What conditions should be checked
* What actions should be performed
* What data should be passed between steps

A basic workflow looks like:

```text
Trigger
   ↓
Condition
   ↓
Action
   ↓
Result
```

---

## Before You Create a Workflow

Make sure you have:

* A configured Flowdesk workspace
* At least one connected integration
* Permission to create workflows
* A clear automation goal

For example:

> When a new lead is received, create a CRM contact and notify the sales team.

---

## Create a Workflow

To create a workflow:

1. Open your Flowdesk workspace.
2. Select **Workflows**.
3. Select **Create workflow**.
4. Enter a workflow name.
5. Configure the trigger.
6. Add any required conditions.
7. Add one or more actions.
8. Test the workflow.
9. Activate the workflow.

---

## Name Your Workflow

Choose a name that clearly describes what the workflow does.

For example:

```text
New Lead → CRM Contact → Sales Notification
```

Avoid vague names such as:

```text
Workflow 1
Test
Automation
```

A descriptive name makes it easier for team members to understand the purpose of a workflow.

---

## Triggers

A trigger defines the event that starts a workflow.

Examples include:

* New form submission
* New customer created
* New CRM record
* Incoming webhook
* Scheduled event

For example:

```text
New lead received
       ↓
Workflow starts
```

### Configure a Trigger

To configure a trigger:

1. Select **Add trigger**.
2. Choose an event.
3. Select the connected integration if required.
4. Configure the event settings.
5. Save the trigger.

---

## Conditions

Conditions allow a workflow to check information before performing an action.

For example, you may only want to process leads from a specific country.

```text
New lead
   ↓
Is country = Nigeria?
   ↓
Yes → Continue
No  → Stop
```

Conditions can help prevent unwanted actions and make workflows more precise.

---

## Add an Action

An action defines what Flowdesk should do after the trigger and conditions have been processed.

Examples include:

* Create a CRM contact
* Send an email
* Send a notification
* Add a spreadsheet row
* Send a webhook
* Update a record

To add an action:

1. Select **Add action**.
2. Choose an integration.
3. Select the action.
4. Configure the required fields.
5. Save the action.

---

## Data Mapping

Actions often require information from the trigger.

For example, a lead trigger might provide:

```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "phone": "+2348000000000"
}
```

You can map these values to an action:

| Trigger Value | Action Field  |
| ------------- | ------------- |
| `name`        | Contact Name  |
| `email`       | Email Address |
| `phone`       | Phone Number  |

This allows information collected by the trigger to be used by later workflow steps.

---

## Multiple Actions

A workflow can contain multiple actions.

For example:

```text
New lead
   ↓
Create CRM contact
   ↓
Send Slack notification
   ↓
Send welcome email
```

Actions are executed according to the workflow configuration.

---

## Example: Lead Management Workflow

A sales team could create the following workflow:

```text
New website lead
        ↓
Check lead information
        ↓
Create CRM contact
        ↓
Notify sales team
        ↓
Send acknowledgement email
```

This eliminates several manual steps from the lead-management process.

---

## Example: Customer Onboarding

Flowdesk can also automate customer onboarding.

```text
New customer
     ↓
Create customer record
     ↓
Send welcome email
     ↓
Create onboarding task
     ↓
Notify account manager
```

Each action uses information from the previous workflow steps.

---

## Test a Workflow

Always test a workflow before activating it.

To test a workflow:

1. Open the workflow.
2. Select **Test**.
3. Provide test data if required.
4. Run the workflow.
5. Review the result.

For example:

```json
{
  "name": "Test Customer",
  "email": "test@example.com"
}
```

Review each step to confirm that the expected data was received and the configured actions were executed.

---

## Workflow Runs

Every workflow execution creates a workflow run.

A workflow run records information about the execution, such as:

* Start time
* End time
* Trigger
* Executed actions
* Status
* Errors

For more information, see [Workflow Runs](workflow-runs.md).

---

## Activate a Workflow

After testing successfully:

1. Open the workflow.
2. Review the configuration.
3. Select **Activate**.
4. Confirm the activation.

An active workflow listens for its configured trigger and executes automatically.

---

## Pause a Workflow

You may need to temporarily stop a workflow without deleting it.

Open the workflow and select **Pause**.

Paused workflows remain saved but do not process new trigger events until they are activated again.

---

## Edit a Workflow

To modify a workflow:

1. Open **Workflows**.
2. Select the workflow.
3. Select **Edit**.
4. Modify the required trigger, condition, or action.
5. Save your changes.
6. Test the workflow again.

Test modified workflows before returning them to production use.

---

## Delete a Workflow

To permanently remove a workflow:

1. Open the workflow.
2. Open the workflow options.
3. Select **Delete**.
4. Confirm the deletion.

Deleting a workflow may remove its configuration and prevent future executions.

If you may need the workflow later, consider pausing it instead.

---

## Workflow Best Practices

### Use Descriptive Names

Make the workflow purpose obvious from its name.

### Keep Workflows Focused

A workflow should have a clear purpose.

Instead of creating one very large workflow, consider splitting complex processes into smaller workflows when appropriate.

### Test Before Activation

Always test new and modified workflows.

### Monitor Workflow Runs

Regularly review workflow executions to identify failures or unexpected behavior.

### Review Connected Integrations

Make sure the integrations used by your workflows remain authorized and available.

---

## Troubleshooting

If a workflow does not execute:

1. Confirm that the workflow is active.
2. Check that the trigger event occurred.
3. Verify that the required integration is connected.
4. Review conditions.
5. Check field mappings.
6. Review the workflow run history.
7. Check for integration errors.

For more troubleshooting guidance, see [Troubleshooting](troubleshooting.md).

---

## Next Steps

After creating a workflow, learn how to monitor its executions:

→ [Workflow Runs](workflow-runs.md)

You can also review:

* [Integrations](integrations.md)
* [Troubleshooting](troubleshooting.md)
