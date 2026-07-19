## Test Scenarios

### 1. Website lead

Input:

```text
I need a website for a coffee shop
```

Expected result:

```text
lead_type = website
event_type = reply_sent
```

### 2. Bot lead

Input:

```text
I need a Telegram bot for client bookings
```

Expected result:

```text
lead_type = bot
event_type = reply_sent
```

### 3. Automation lead

Input:

```text
I need automation for leads in Google Sheets and CRM
```

Expected result:

```text
lead_type = automation
event_type = reply_sent
```

### 4. Other lead

Input:

```text
Hello, I want to discuss a project
```

Expected result:

```text
lead_type = other
event_type = reply_sent
```

### 5. Duplicate lead

Input:

```text
I need a website for a coffee shop
```

Send the same message again.

Expected result:

```text
No new lead row is created
event_type = duplicate
Duplicate reply is sent
```

### 6. Follow-up skip

Input:

```text
I need a bot for a school
```

Then send another message before the follow-up delay ends:

```text
It should save requests to Google Sheets
```

Expected result:

```text
The original follow-up is skipped
event_type = follow_up_skipped
```

### 7. Follow-up sent

Send a supported text message and do not send another message during the configured delay.

Expected result:

```text
Follow-up message is sent
event_type = follow_up_sent
```

### 8. Start command

Input:

```text
/start
```

Expected result:

```text
Welcome message is sent
No lead row is created
```

### 9. Unsupported message

Send a photo, voice message, file, or sticker without supported text.

Expected result:

```text
User is asked to send text
No lead row is created
Workflow completes successfully
```

### 10. Error workflow

Trigger a controlled error using `Stop and Error`.

Expected result:

```text
Error is logged in workflow_errors
Admin alert is sent to Telegram
```

---
