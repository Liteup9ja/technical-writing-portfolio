# Troubleshooting

This guide helps you diagnose common problems when using Flowdesk.

If an issue cannot be resolved using the steps below, collect the relevant error information before contacting support or investigating the issue further.

---

## Troubleshooting Checklist

Before investigating a problem, check:

* Your account is active.
* You are working in the correct workspace.
* Required integrations are connected.
* Authentication has not expired.
* The workflow is active.
* Required fields contain valid data.
* The latest workflow run contains no unexpected errors.

---

## Account and Login Issues

### Unable to Sign In

If you cannot sign in:

1. Confirm that you are using the correct email address.
2. Check that your password is correct.
3. Reset your password if necessary.
4. Confirm that your account has not been disabled.
5. Try signing in again.

If password reset emails do not arrive, check your spam or junk folder.

---

## Workspace Issues

If you cannot access a workspace:

1. Confirm that you are signed in to the correct account.
2. Check whether you have been invited to the workspace.
3. Confirm that the invitation was accepted.
4. Ask a workspace administrator to verify your membership and role.

Your available actions may depend on your workspace role.

---

## Integration Connection Issues

An integration may fail to connect because of:

* Invalid credentials
* Expired authorization
* Incorrect configuration
* Unsupported permissions
* Temporary service problems

To troubleshoot:

1. Open **Integrations**.
2. Select the affected integration.
3. Review its connection status.
4. Reconnect the integration if authorization has expired.
5. Test the integration again.

---

## Authorization Errors

Authorization problems usually occur when Flowdesk can no longer access an external service.

Common causes include:

* An expired OAuth authorization
* Revoked permissions
* Changed account credentials
* Removed application access

### Fix

Reconnect the affected integration and grant the required permissions.

After reconnecting, test the workflow that uses the integration.

---

## Workflow Is Not Triggering

If a workflow does not start:

1. Open the workflow.
2. Confirm that the workflow is **Active**.
3. Review the configured trigger.
4. Confirm that the trigger event actually occurred.
5. Check the workflow's run history.
6. Review any available error messages.

For example, if a workflow triggers when a new lead is created, confirm that the lead was actually created after the workflow was activated.

---

## Workflow Action Failed

If a workflow starts but an action fails:

1. Open the workflow.
2. Open **Runs**.
3. Select the failed run.
4. Identify the first failed step.
5. Read the error message.
6. Check the configuration for that action.
7. Verify the related integration.
8. Correct the problem.
9. Retry the run if supported.

Start with the first failed step because later steps may fail as a result of the original error.

---

## Data Mapping Problems

Incorrect data mapping can cause actions to fail or produce unexpected results.

For example, an action may require:

```text
customer_email
```

but the previous step provides:

```text
email_address
```

Check that:

* Required fields are mapped.
* Field names are correct.
* Data types match the destination field.
* Empty values are handled correctly.
* Trigger data contains the expected information.

Test the workflow after correcting the mapping.

---

## Workflow Run Problems

Use the workflow run history to investigate execution problems.

Open:

**Workflows → Select workflow → Runs**

Review:

* Run status
* Trigger information
* Executed steps
* Failed steps
* Error messages
* Execution times

For more information, see the [Workflow Runs](workflow-runs.md) guide.

---

## Delayed Workflow Execution

A workflow may not execute immediately in some situations.

Possible causes include:

* Temporary service delays
* External integration delays
* Large amounts of queued work
* Delayed webhook events

Check the workflow run history before making configuration changes.

If the trigger eventually appears in the run history, the workflow may have been delayed rather than completely failed.

---

## Integration Data Delays

External services may take time to send or process information.

If expected data is missing:

1. Confirm that the external event occurred.
2. Check the integration connection.
3. Review the workflow trigger.
4. Check recent workflow runs.
5. Verify that the expected fields were included.

Avoid repeatedly triggering the same event until you understand whether the original event is still being processed.

---

## Webhook Problems

If a webhook-based workflow is not receiving events:

Check:

* Webhook URL
* Integration status
* Authentication
* Event configuration
* Recent workflow runs
* External service configuration

If the external service provides webhook delivery logs, check whether the event was successfully delivered.

---

## Workflow Was Working Before

If a previously working workflow suddenly fails, check for recent changes.

Review:

* Integration authorization
* Workflow configuration
* Field mappings
* Trigger settings
* External service changes
* Workspace permissions

A previously successful workflow can fail when an external integration changes its authentication or data structure.

---

## Collecting Troubleshooting Information

When reporting a technical problem, collect as much useful information as possible.

Include:

* Workspace name
* Workflow name
* Workflow run ID
* Approximate time of the failure
* Integration involved
* Error message
* Steps that were executed
* Recent configuration changes

Avoid sharing passwords, API keys, access tokens, or other sensitive credentials.

---

## Troubleshooting Example

Suppose a customer onboarding workflow stops after creating a CRM contact.

The workflow run shows:

```text
Trigger
✓ Customer created

CRM Action
✓ Contact created

Email Action
✗ Failed
```

Open the failed email step.

If the error indicates that the email integration authorization has expired:

1. Open **Integrations**.
2. Select the email integration.
3. Reconnect the integration.
4. Return to the workflow.
5. Run a test.
6. Review the new workflow run.

If the test succeeds, monitor the next real execution.

---

## When to Escalate

Escalate an issue when:

* The error continues after configuration has been verified.
* An integration cannot be reconnected.
* Multiple workflows are affected.
* Workflow runs fail without a clear error.
* An external service appears unavailable.
* The problem cannot be reproduced or explained.

Provide the troubleshooting information collected above when escalating the issue.

---

## Final Troubleshooting Checklist

Before escalating an issue, confirm:

* [ ] I am using the correct workspace.
* [ ] My account has the required permissions.
* [ ] The integration is connected.
* [ ] Authentication is valid.
* [ ] The workflow is active.
* [ ] Required fields are mapped correctly.
* [ ] I checked the workflow run history.
* [ ] I identified the first failed step.
* [ ] I reviewed the error message.
* [ ] I tested the workflow after making changes.
* [ ] I recorded the workflow run ID and relevant details.

---

## Related Documentation

* [Getting Started](getting-started.md)
* [Account Setup](account-setup.md)
* [Integrations](integrations.md)
* [Workflows](workflows.md)
* [Workflow Runs](workflow-runs.md)
