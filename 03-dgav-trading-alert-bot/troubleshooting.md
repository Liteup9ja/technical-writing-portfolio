# Troubleshooting

This guide provides solutions for common issues users may encounter when interacting with Dangeaky Alert Vitals (DGAV) through Telegram.

---

## Bot Does Not Respond

If the DGAV bot does not respond after you send a command:

1. Confirm that you are messaging the correct DGAV bot.
2. Check that your Telegram connection is working.
3. Send `/start` to restart the interaction.
4. Wait briefly for the bot to respond.
5. Try the command again.

If the issue continues, check whether other Telegram messages are being delivered normally.

---

## I Am Not Receiving Alerts

If you expect to receive a DGAV alert but nothing arrives, check the following:

1. Confirm that you have started the DGAV bot.
2. Confirm that you are using the correct Telegram account.
3. Check your subscription status if alerts require an active subscription.
4. Confirm that the relevant alert conditions have been triggered.
5. Check that Telegram notifications are enabled.
6. Make sure Telegram can receive messages from the DGAV bot.

If the issue continues, review the other troubleshooting sections below.

---

## Telegram Notifications Are Disabled

Telegram may receive a message without displaying an immediate notification if notifications are disabled.

Check your Telegram notification settings and make sure notifications are enabled for the DGAV conversation.

---

## A Command Does Not Work

If a DGAV command does not work:

1. Confirm that the command is spelled correctly.
2. Make sure the command starts with `/`.
3. Try sending `/start` first.
4. Check whether the command is available to your account.
5. Try the command again after restarting the bot interaction.

Available commands include:

```text id="x8p5k1"
/start
/feature
/alert
/subscription
/plans
```

---

## Subscription or Plan Information Is Missing

If subscription or plan information is not displayed as expected:

1. Send `/subscription`.
2. Send `/plans`.
3. Follow any instructions returned by the bot.
4. Confirm that you are using the correct Telegram account.

If the problem continues, the issue may require assistance from the DGAV administrator.

---

## Alerts Are Delayed

If an alert appears later than expected, first confirm that:

* The alert conditions were actually triggered.
* Your Telegram connection is working.
* Telegram notifications are enabled.
* Your DGAV access is active if subscription access is required.

The timing of an alert may depend on when the configured conditions are detected and when the message is delivered through Telegram.

---

## Alert Information Looks Different

DGAV alerts may contain different information depending on the alert.

An alert can include:

* Price
* Alert trigger
* Conditions that were met
* Additional details

If an alert looks different from an example in this documentation, review the actual information provided in the message.

---

## Quick Troubleshooting Checklist

Before requesting assistance, confirm:

* [ ] You are using the correct Telegram account.
* [ ] You have started the DGAV bot.
* [ ] Telegram is connected to the internet.
* [ ] Telegram notifications are enabled.
* [ ] Your subscription status has been checked if applicable.
* [ ] The relevant alert conditions have been triggered.
* [ ] You are using a valid DGAV command.

---

## When to Request Help

If you have completed the troubleshooting steps and the issue continues, provide the DGAV administrator with useful information about the problem.

Where appropriate, include:

* The command you used.
* What you expected to happen.
* What actually happened.
* The approximate time the issue occurred.
* Any error message returned by the bot.

Avoid sharing sensitive account information in public messages.

---

## Related Documentation

* [Getting Started](getting-started.md)
* [Bot Setup](bot-setup.md)
* [Alerts](alerts.md)
* [Commands](commands.md)
* [Alert Format](alert-format.md)
* [FAQ](faq.md)
