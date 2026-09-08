# Work Type Guardrails for Jira

Work Type Guardrails lets a project admin block specific work item type changes in a Jira project. You choose which type changes are not allowed, and Jira prevents them.

Rules apply to all four ways a work item's type can change. That covers inline edit on the issue, Move Issue, Bulk Move, and subtask conversion. Some of these changes never go through a workflow transition, so workflow validators do not run on them and other apps cannot block them. Work Type Guardrails does.

The app is free. There are no paid tiers. It runs on Atlassian and makes no external network calls. See the [privacy policy](privacy.md) for details on what it stores.

## Opening the settings page

1. Open your project.
2. Go to **Project settings**.
3. Select **Apps**.
4. Select **Work Type Guardrails**.

You need project admin permission to open this page and manage rules.

## Adding a rule

A rule names one work type change to block. It has a **From** type and a **To** type.

1. On the settings page, find the **Add a rule** section.
2. Choose the **From type**. This is the type the work item currently has.
3. Choose the **To type**. This is the type the change would set.
4. Select **Add rule**.

The type pickers list the work types in your project. Subtask types are marked so you can tell them apart.

Rules are directional. A rule that blocks Task to Story does not block Story to Task. Add a second rule if you want to block the other direction.

## Removing a rule

1. Find the rule in the **Blocked changes** table.
2. Select **Remove** on that row.
3. Confirm in the dialog.

## Changes take effect immediately

There is no separate save step. A rule starts blocking as soon as you add it. It stops blocking as soon as you remove it. The table always shows the rules that are currently in force.

## What a blocked user sees

When a rule blocks a change, Jira shows the user this exact message.

> Work Type Guardrails: this work type change is blocked by a rule set for this project. If it should be allowed, ask a project admin to review the rules in Project settings -> Apps -> Work Type Guardrails.

The message is the same for every rule. It cannot name the specific rule or the work types involved. This is a limit of the Jira validation feature the app uses. If a user asks why a change was blocked, check the rules on the settings page for the project.

## When a work type is deleted

If you delete a work type that a rule refers to, the rule still refers to an ID that no longer exists. The app does not break. Type changes keep working, and the rule simply never matches anything.

The settings page flags these rules so you can find them. The affected side shows as a deleted work type, and the row is marked as stale. The app never removes a rule on its own. Delete the stale rule yourself if the work type was removed on purpose. Keep it if the type is being recreated as part of a reorganisation, and it will work again once the type returns.

## What it does not cover

These are stated plainly so you know the limits before you rely on the app.

- **Deleting a work type and migrating its items.** When you delete a work type, Jira offers to move existing items to another type. That migration does not go through the validator, so a rule cannot block it. This is intended. It means a rule can never lock you out of deleting a work type.
- **Migrate as a separate flow.** Bulk Move is covered and verified. If your Jira exposes a distinct "Migrate" flow separate from Bulk Move, it has not been tested, and its behaviour is not known.

## Support

Work Type Guardrails is published by Aqib Ilyas.

For questions, issues, or feedback, email [worktypeguardrails@gmail.com](mailto:worktypeguardrails@gmail.com).
