# 📘 Creating a Telegram Bot & Obtaining Access Token

This document explains how to create a Telegram bot, retrieve its access token, and configure it as a credential in **n8n**.

---

## 1. Create a Telegram Bot
1. Open Telegram on your phone or desktop.  
2. Search for **@BotFather** (the official Telegram bot for managing bots).  
3. Start a chat and type:
```
/start
```
4. To create a new bot, type:
```
/newbot
```
5. BotFather will ask you for:
- **Bot name** → This is the display name of your bot (e.g., `TgWaBridgeBot`).  
- **Bot username** → Must end with `bot` (e.g., `tg_wa_bridge_bot`).  

6. Once created, BotFather will send you a message containing:
- **HTTP API Token** → This is the access token you’ll use in n8n.  
- Example:
  ```
  123548967:AbcdefGhIJKlmNoPQRstuVWXyz
  ```

---

## 2. Secure the Access Token
- Treat the token like a password.  
- Do **not** commit it into GitHub or share it publicly.  
- Store it in n8n’s **Credentials Manager** instead of hardcoding it in workflows.  

---

## 3. Configure Telegram Credential in n8n
1. Open your n8n instance.  
2. Go to **Credentials → Create new credential**.  
3. Select **Telegram API**.  
4. Enter the following:
- **Access Token** → Paste the token you got from BotFather.  
- **Name** → Give it a recognizable name (e.g., `Telegram account`).  
5. Save the credential.  

---

## 4. Connect the Bot to a Channel
The Telegram Trigger node in n8n listens for messages posted in a channel.  
To enable this:
1. Go to your **Telegram Channel settings**.  
2. Add your bot as an **Admin** of the channel.  
3. Once added, the bot can detect any message posted in the channel and trigger the workflow.  

---

## 5. Test the Bot
1. Open Telegram and send a message to your bot or channel.  
2. If your workflow is active, the **Telegram Trigger** node will capture the message.  
3. The workflow will then forward it to WhatsApp via the **HTTP Request** node.  

---

## ⚡ Key Notes
- **Bot Privacy**: By default, bots cannot read group messages unless you adjust privacy settings in BotFather (`/setprivacy`).  
- **Webhook Setup**: n8n automatically handles the webhook for the Telegram Trigger node — no manual setup required.  
- **Security Reminder**: Always keep your access token private and use n8n’s credential manager.  

---

✅ With this setup, your Telegram bot is ready, and n8n can use it to capture messages and redirect them to WhatsApp.
