## Google Sheets Structure

The project uses the following sheets:

### `telegram_leads`

Stores accepted leads.

| Column            | Description                         |
| ----------------- | ----------------------------------- |
| `created_at`      | Lead creation timestamp             |
| `chat_id`         | Telegram chat ID                    |
| `username`        | Telegram username                   |
| `first_name`      | Telegram first name                 |
| `text`            | Original message text               |
| `normalized_text` | Lowercase normalized message        |
| `dedupe_key`      | Unique key for duplicate protection |
| `lead_type`       | Classified lead type                |
| `status`          | Lead status                         |

### `telegram_events`

Stores workflow events.

| Column       | Description        |
| ------------ | ------------------ |
| `created_at` | Event timestamp    |
| `chat_id`    | Telegram chat ID   |
| `username`   | Telegram username  |
| `text`       | Original lead text |
| `dedupe_key` | Related dedupe key |
| `lead_type`  | Lead type          |
| `event_type` | Event type         |
| `note`       | Event note         |

Example event types:

```text
reply_sent
follow_up_sent
follow_up_skipped
duplicate
```

### `telegram_user_state`

Stores the latest user state used to decide whether a follow-up should be sent.

| Column            | Description             |
| ----------------- | ----------------------- |
| `chat_id`         | Telegram chat ID        |
| `username`        | Telegram username       |
| `last_message_at` | Last message timestamp  |
| `last_text`       | Last user message       |
| `last_dedupe_key` | Last message dedupe key |

### `workflow_errors`

Stores failed workflow executions.

| Column               | Description                   |
| -------------------- | ----------------------------- |
| `created_at`         | Error timestamp               |
| `workflow_name`      | Failed workflow name          |
| `workflow_id`        | Failed workflow ID            |
| `execution_id`       | Failed execution ID           |
| `error_node`         | Node where the error happened |
| `error_message`      | Error message                 |
| `error_stack`        | Error stack trace             |
| `last_node_executed` | Last executed node            |
| `mode`               | Execution mode                |

---
