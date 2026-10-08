# Salesforce Outbound Email via Apex

This repository contains a simple, lightweight Apex script to send a single outbound email from Salesforce using the `Messaging.SingleEmailMessage` class. It is ideal for testing email deliverability and learning Apex scripting through the Salesforce Developer Console.

## 💻 Apex Source Code

Copy and paste the following Apex code directly into the **Execute Anonymous Window**:

```apex
// 1. Initialize the email object
Messaging.SingleEmailMessage email = new Messaging.SingleEmailMessage();

// 2. Set the target recipient email address
String[] toAddresses = new String[] {'dhanyath91@gmail.com'};
email.setToAddresses(toAddresses);

// 3. Set the subject and body of the email
email.setSubject('Hello from Salesforce Developer Console!');
email.setPlainTextBody(
    'Success! This email was sent using Apex code in the Developer Console.'
);

// 4. Send the email
Messaging.sendEmail(
    new Messaging.SingleEmailMessage[] { email }
);

// 5. Print a confirmation message to the logs
System.debug('🚀 Email command sent to Salesforce servers!');
```
<p align="center">
  <img src="Screenshot 2026-08-11 214927.png" alt="Salesforce Email Screenshot" width="800">
</p>
## 🚀 Step-by-Step Execution Guide

### Step 1: Open the Developer Console

1. Log in to your **Salesforce** account.
2. Click the **Gear Icon (⚙️)** in the top-right corner of your Salesforce Lightning homepage.
3. Select **Developer Console**.

### Step 2: Open the Execute Anonymous Window

In the Developer Console:

1. Click **Debug** from the menu bar.
2. Select **Open Execute Anonymous Window**.
3. Alternatively, use:

   * **Windows:** `Ctrl + E`
   * **Mac:** `Cmd + E`

### Step 3: Paste and Modify the Code

1. Clear any existing code from the window.
2. Paste the Apex code provided above.
3. Update the recipient email address if required:

```apex
String[] toAddresses = new String[] {'your-email@example.com'};
```

### Step 4: Execute the Script

1. Check **Open Log** at the bottom-right of the execution window.
2. Click **Execute**.

### Step 5: Verify the Logs

Once the execution log opens:

1. Select the **Debug Only** checkbox at the bottom of the log viewer.
2. Look for the following debug message:

```text
USER_DEBUG|[18]|DEBUG|🚀 Email command sent to Salesforce servers!
```
<p align="center">
  <img src="Screenshot 2026-08-11 214904.png" alt="Salesforce Email Screenshot" width="800">
</p>

This confirms that the Apex script successfully submitted the email request to Salesforce.

### Step 6: Check Your Inbox

Open the recipient's email inbox and look for the message.

If the email does not appear in the primary inbox within a few minutes, check the **Spam/Junk** folder.

> **Note:** Successful execution of `Messaging.sendEmail()` means Salesforce accepted the email request. Actual delivery can still depend on Salesforce email settings, organization limits, recipient mail-server policies, and spam filtering.
<p align="center">
  <img src="Screenshot 2026-08-11 214848.png" alt="Salesforce Email Screenshot" width="800">
</p>

## 🛠️ Technologies Used

* **Salesforce**
* **Apex**
* `Messaging.SingleEmailMessage`
* **Salesforce Developer Console**


