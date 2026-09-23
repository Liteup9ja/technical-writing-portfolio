# Integrations

Integrations allow Flowdesk to connect with external applications and services.

You can use integrations to receive information from another application, send data to an external service, or connect multiple tools within an automation workflow.

For example:

```text id="s2f5je"
Website
   ↓
Flowdesk
   ↓
CRM
   ↓
Email platform
```

---

## Before You Connect an Integration

Before connecting an application, make sure you have:

* An active Flowdesk workspace
* Access to the application you want to connect
* Permission to authorize third-party integrations
* The required account credentials

Some applications may require administrator permissions.

---

## Open the Integrations Page

To view available integrations:

1. Open your Flowdesk workspace.
2. Select **Integrations** from the navigation menu.
3. Select **Add integration**.

Flowdesk displays the applications currently available for connection.

---

## Connect an Integration

To connect an application:

1. Open **Integrations**.
2. Select **Add integration**.
3. Find the application you want to connect.
4. Select **Connect**.
5. Follow the application's authorization process.
6. Review the requested permissions.
7. Approve the connection.

After successful authorization, the application appears in your workspace's connected integrations.

---

## Authentication

Most integrations require you to authorize Flowdesk before it can access the external service.

Depending on the application, authorization may use:

* OAuth
* API keys
* Access tokens
* Connection credentials

The authentication method depends on the external application.

### OAuth

OAuth allows Flowdesk to access an application without requiring you to give Flowdesk your application password.

A typical OAuth flow looks like:

```text id="w6pt1g"
Flowdesk
   ↓
External application
   ↓
User authorization
   ↓
Permission granted
   ↓
Flowdesk receives authorization
   ↓
Integration connected
```

---

## Example: Connecting a CRM

Suppose you want Flowdesk to create CRM contacts whenever a new lead arrives.

Start by connecting your CRM.

1. Open **Integrations**.
2. Select **Add integration**.
3. Search for your CRM.
4. Select **Connect**.
5. Complete the authorization process.
6. Select the CRM account or workspace.
7. Confirm the connection.

The CRM should now appear as a connected integration.

---

## Use an Integration in a Workflow

After connecting an application, you can use it as a workflow trigger or action.

For example:

```text id="qg55xq"
New lead received
       ↓
Flowdesk
       ↓
Create CRM contact
```

The connected CRM provides the action used by the workflow.

---

## Data Mapping

Data mapping determines how information from one step is passed to another step.

For example, a lead trigger may provide:

```json id="i2x2kk"
{
  "name": "John Doe",
  "email": "john@example.com",
  "phone": "+2348000000000"
}
```

You can map these values to corresponding CRM fields:

| Flowdesk Data | CRM Field    |
| ------------- | ------------ |
| `name`        | Contact Name |
| `email`       | Email        |
| `phone`       | Phone Number |

Correct data mapping ensures that information is sent to the expected fields.

---

## Integration Status

A connected integration may have different states.

| Status                 | Description                                        |
| ---------------------- | -------------------------------------------------- |
| Connected              | The integration is available for use               |
| Authorization Required | The connection needs to be authorized              |
| Disconnected           | The integration is no longer connected             |
| Error                  | Flowdesk encountered a problem with the connection |

If an integration displays an error, open the integration details to view additional information.

---

## Reconnect an Integration

Some integrations may require reauthorization.

For example, this can happen when:

* Access permissions change
* Credentials expire
* The external application revokes access
* An administrator removes authorization

To reconnect:

1. Open **Integrations**.
2. Select the affected integration.
3. Select **Reconnect**.
4. Complete the authorization process.
5. Confirm that the integration shows **Connected**.

---

## Disconnect an Integration

To disconnect an integration:

1. Open **Integrations**.
2. Select the application.
3. Select **Disconnect**.
4. Confirm the action.

Disconnecting an integration may affect workflows that depend on it.

Before disconnecting an integration, review the workflows using that connection.

---

## Security Recommendations

Treat integration credentials and authorization permissions as sensitive information.

### Review Permissions

Only authorize the permissions required for your intended workflow.

### Avoid Sharing Credentials

Do not share API keys, access tokens, or application passwords with other users.

### Review Connected Services

Regularly review connected applications and remove integrations that are no longer required.

### Use Appropriate Workspace Access

Limit access to integration management to trusted workspace members.

---

## Troubleshooting

### Integration will not connect

Check that:

* Your external application account is active.
* You have permission to authorize the integration.
* Required authorization steps have been completed.
* The external service is available.

### Integration shows an authorization error

Try reconnecting the integration and completing the authorization process again.

### Workflow cannot find the integration

Confirm that the integration is connected to the current Flowdesk workspace.

### Data is not being mapped correctly

Review the workflow's field mappings and confirm that the source field contains the expected data.

---

## Best Practices

When working with integrations:

1. Connect only the applications you need.
2. Review permissions before authorization.
3. Test integrations before using them in production workflows.
4. Monitor workflows that depend on external services.
5. Reconnect integrations when authorization expires.
6. Remove unused integrations.

---

## Next Steps

After connecting your applications, you can use them to build automation workflows.

Continue with:

* [Workflows](workflows.md)
* [Workflow Runs](workflow-runs.md)
* [Troubleshooting](troubleshooting.md)
