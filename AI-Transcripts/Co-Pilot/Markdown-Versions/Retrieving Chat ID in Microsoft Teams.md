# Retrieving Chat ID in Microsoft Teams  

## Me
How can I retrieve the chat id of an individual chat in teams?  

## Co-Pilot
[1]: https://www.youtube.com/watch?v=9yXTOpZOlCE ""
[2]: https://www.youtube.com/watch?v=7v8-YEqgTx8 ""
[3]: https://www.youtube.com/watch?v=KpssiOAd1Og ""
[4]: https://answers.microsoft.com/en-us/msteams/forum/all/get-chat-id-in-new-teams/dd9788d3-1f5a-4da4-9fc8-cc3f35f03dba ""
[5]: https://stackoverflow.com/questions/68350367/microsoft-teams-how-can-i-get-chat-id-of-the-direct-conversation-between-bot ""
[6]: https://answers.microsoft.com/en-us/msteams/forum/all/how-to-access-individual-chat-history-in-teams/f90f29a8-0dae-425b-8d15-bf0ad14d3489 ""
[7]: https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/deep-link-teams ""
[8]: https://learn.microsoft.com/en-us/answers/questions/1203589/how-do-i-get-the-url-for-my-own-teams-chat ""

Certainly! To retrieve the chat ID of an individual chat in Microsoft Teams, follow these steps:

1. **Simple Chat:**
   - Open Microsoft Teams and navigate to the chat you want to get the Chat ID for.
   - Click on the three dots (...) next to one of the messages.
   - Copy the link and paste it into a notepad or any text editor. The Chat ID will be included in the link.

2. **Channel Chat:**
   - For channel chats, go to Teams and right-click on the channel name.
   - Select "Copy link to channel" or "Copy link to chat." The Chat ID will be part of the link copied to your clipboard.

Remember that the format for the Chat ID is `19: xxx`, where `xxx` represents the unique identifier for the chat[^1^][4] [^2^][7]. If you need further assistance, feel free to ask! 😊

Learn more: [1. answers.microsoft.com](https://answers.microsoft.com/en-us/msteams/forum/all/get-chat-id-in-new-teams/dd9788d3-1f5a-4da4-9fc8-cc3f35f03dba) 
[2. learn.microsoft.com](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/deep-link-teams) 
[3. www.youtube.com](https://www.youtube.com/watch?v=9yXTOpZOlCE) 
[4. www.youtube.com](https://www.youtube.com/watch?v=7v8-YEqgTx8) 
[5. www.youtube.com](https://www.youtube.com/watch?v=KpssiOAd1Og) 
[6. stackoverflow.com](https://stackoverflow.com/questions/68350367/microsoft-teams-how-can-i-get-chat-id-of-the-direct-conversation-between-bot) 
[7. answers.microsoft.com](https://answers.microsoft.com/en-us/msteams/forum/all/how-to-access-individual-chat-history-in-teams/f90f29a8-0dae-425b-8d15-bf0ad14d3489) 
[8. learn.microsoft.com](https://learn.microsoft.com/en-us/answers/questions/1203589/how-do-i-get-the-url-for-my-own-teams-chat)  

## Me
Thank you! Is there a way to retrieve the chat ID programmatically?  

## Co-Pilot
Certainly! To programmatically retrieve the chat ID in Microsoft Teams, you can use the Microsoft Graph API. Here are the steps:

1. **Get the Chat ID:**
   - Make an HTTP GET request to the following endpoint:
     ```
     GET https://graph.microsoft.com/v1.0/me/chats
     ```
   - This will return a list of chats you're part of. Look for the chat you're interested in and note down its `id`.

2. **Channel Chat ID:**
   - For channel chats, you can use the channel ID instead. You can get it by making an HTTP GET request to:
     ```
     GET https://graph.microsoft.com/v1.0/me/joinedTeams
     ```
     Look for the team and channel you want, and note down the `id` of the channel.

Remember to authenticate your requests using an access token. If you need further assistance or have any other questions, feel free to ask! 😊  

## Me
I retrieved the ids via workflow but don't know what chat they belong to, how do I find out?  

## Co-Pilot
To determine which chat corresponds to the retrieved IDs, you can use the Microsoft Graph API to fetch additional details about each chat. Here's how:

1. **Get Chat Details:**
   - For individual chats, make an HTTP GET request to:
     ```
     GET https://graph.microsoft.com/v1.0/me/chats/{chatId}
     ```
     Replace `{chatId}` with the actual chat ID you retrieved.
   - This will return information about the chat, including participants, messages, and other relevant details.

2. **Channel Chats:**
   - For channel chats, you can use the channel ID directly. To get channel details, make an HTTP GET request to:
     ```
     GET https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}
     ```
     Replace `{teamId}` with the team ID and `{channelId}` with the channel ID.

Remember to include the necessary authentication headers and tokens in your requests. If you encounter any issues or need further assistance, feel free to ask! 😊  

*End of this Conversation*
