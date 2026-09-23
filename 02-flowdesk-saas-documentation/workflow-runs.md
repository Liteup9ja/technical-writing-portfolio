# Workflow Runs

A workflow run represents a single execution of a Flowdesk workflow.

Each time a workflow is triggered, Flowdesk creates a run that records the steps performed during that execution.

Workflow runs help you understand whether an automation completed successfully and identify where a failure occurred.

---

## Workflow Run Lifecycle

A typical workflow run follows this process:

```text id="2h8v5m"
Trigger received
      ↓
Workflow starts
      ↓
Conditions evaluated
      ↓
Actions executed
      ↓
Workflow completed
```

If an error occurs, the run may stop at the affected step.

```text id="0w2u8m"
Trigger received
      ↓
Workflow starts
      ↓
Action executed
      ↓
Error
      ↓
Run failed
```

---

## View Workflow Runs

To view the runs for a workflow:

1. Open your Flowdesk workspace.
2. Select **Workflows**.
3. Select the workflow you want to inspect.
4. Open **Runs**.

Flowdesk displays the workflow's recent executions.

---

## Run Statuses

A workflow run can have different statuses.

| Status     | Description                                          |
| ---------- | ---------------------------------------------------- |
| Running    | The workflow is currently executing                  |
| Successful | All configured steps completed successfully          |
| Failed     | One or more steps could not be completed             |
| Cancelled  | The workflow execution was manually stopped          |
| Waiting    | The workflow is waiting for a required step or event |

The available statuses may depend on the workflow configuration.

---

## Run Details

Open a workflow run to view information about the execution.

Run details may include:

* Run ID
* Start time
* Completion time
* Trigger information
* Executed steps
* Step results
* Error messages
* Execution status

A run might look like:

```text id="qv8p3e"
Run ID: run_12345
Status: Successful

Trigger
✓ New lead received

Action
✓ Create CRM contact

Action
✓ Send notification
```

---

## Inspect Individual Steps

Each workflow step can be inspected separately.

For example:

```text id="f5cyh6"
New lead received
      ✓
Create CRM contact
      ✓
Send notification
      ✗
```

If a step fails, open the step details to view the available error information.

---

## Failed Workflow Runs

A workflow run is marked as failed when a required step cannot be completed.

Common causes include:

* An integration is disconnected
* Authentication has expired
* Required data is missing
* A field contains an invalid value
* An external service returns an error
* A webhook endpoint is unavailable

Review the failed step first.

---

## Example Failed Run

Consider a workflow that creates a CRM contact after receiving a new lead.

```text id="w3hd5v"
New lead received
      ✓
Create CRM contact
      ✗
```

The run details might indicate:

```text
Error:
CRM authorization expired.
```

In this case, reconnect the CRM integration before running the workflow again.

---

## Retry a Failed Run

If the workflow supports retries, you can retry a failed run after correcting the underlying problem.

Before retrying:

1. Identify the failed step.
2. Read the error message.
3. Correct the configuration or integration problem.
4. Confirm that the workflow is still active.
5. Retry the run.

Do not repeatedly retry a failed workflow without addressing the underlying problem.

---

## Run History

Flowdesk stores workflow execution history so that users can review previous runs.

Use run history to:

* Investigate failures
* Confirm successful executions
* Understand workflow behavior
* Identify recurring problems
* Verify recent changes

Filter or sort runs when available to find the execution you need.

---

## Run Data

A workflow run may contain information produced by triggers and actions.

For example:

```json id="q1s7pd"
{
  "run_id": "run_12345",
  "status": "successful",
  "trigger": {
    "type": "lead.created"
  },
  "actions": [
    {
      "type": "crm.contact.create",
      "status": "successful"
    },
    {
      "type": "notification.send",
      "status": "successful"
    }
  ]
}
```

Run data can help you understand exactly what happened during an automation.

---

## Monitoring Workflow Runs

For important business workflows, regularly review execution history.

Look for:

* Repeated failures
* Increasing execution times
* Integration errors
* Unexpected data
* Workflows that stop at the same step

Recurring failures may indicate a configuration problem or an issue with an external service.

---

## Example: Troubleshooting a Failed Run

Suppose a sales notification workflow suddenly stops working.

The run history shows:

```text id="1r5k2n"
Trigger
✓ New lead received

CRM Action
✓ Contact created

Notification Action
✗ Failed
```

Open the notification step.

The error indicates:

```text
Notification integration authorization expired.
```

Reconnect the notification integration and retry the workflow.

The next run should be checked to confirm that the problem has been resolved.

---

## Best Practices

### Check the Failed Step First

When troubleshooting, start with the first failed step rather than reviewing the entire workflow.

### Read the Error Message

The error message often identifies the configuration or integration problem.

### Avoid Blind Retries

Fix the underlying problem before retrying a failed run.

### Monitor Important Workflows

Review critical workflows regularly to detect recurring problems.

### Test After Changes

After modifying a workflow or reconnecting an integration, run a test before relying on the automation again.

---

## Related Documentation

* [Workflows](workflows.md)
* [Integrations](integrations.md)
* [Troubleshooting](troubleshooting.md)
