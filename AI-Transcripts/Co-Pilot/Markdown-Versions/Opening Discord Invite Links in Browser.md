# Opening Discord Invite Links in Browser  

## Me
When I try to open a discord invite link in my browser, I get the following message (see attached image), however I don't want to go to teh app, I want to open the link in my browser and acceptr teh invite with the account signed in my brpwser, how can I change my settings to achieve this? [Uploaded Image Expired]  

## Co-Pilot
It sounds like Discord is automatically redirecting you to the app when you click on an invite link. To change this behavior and open the invite link in your browser instead, you can try the following steps:

1. **Open the Invite Link in Incognito Mode**: Sometimes, opening the invite link in an incognito or private browsing window can bypass the prompt to open the app.
2. **Clear Browser Cache and Cookies**: Clearing your browser’s cache and cookies can sometimes reset the settings and allow you to open the link in the browser.
3. **Disable the Discord App Protocol**: You can disable the protocol that automatically opens the Discord app. This can be done by:
   - In Chrome: Go to `chrome://settings/handlers` and remove Discord as a handler.
   - In Firefox: Go to `about:preferences#general`, scroll down to “Applications,” and change the action for `discord` to “Always ask.”
4. **Use a Different Browser**: Sometimes, using a different browser that does not have the Discord app protocol set up can help.
5. **Manually Copy the Invite Link**: Copy the invite link and paste it directly into the browser’s address bar.

By following these steps, you should be able to open the invite link in your browser and accept the invite with the account signed in your browser.

Does this help resolve your issue?  

## Me
I can't find the protocol in firefox settings  

## Co-Pilot
No worries, let's try another approach. You can disable the Discord protocol handler directly in your operating system settings. Here’s how you can do it on Windows:

1. **Open Default Programs**: Go to `Control Panel` > `Default Programs`.
2. **Associate a File Type or Protocol with a Program**: Click on `Associate a file type or protocol with a program`.
3. **Find Discord**: Look for `discord` in the list and select it.
4. **Change the Action**: Change the action to `Always ask` or `Open with` and choose your browser.

This should prevent Firefox from automatically redirecting Discord links to the app and allow you to open them in your browser instead.

Does this help?  

(1) [support.discord.com](https://support.discord.com/hc/en-us/community/posts/360048222492-Disable-Discord-Web-App-support-for-Firefox-on-Windows-7-8-8-1-10-and-Chrome-on-Windows-XP-Vista)  

*End of this Conversation*
