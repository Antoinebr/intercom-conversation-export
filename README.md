# intercom-exporter-node
This is a fork from intercom-exporter-node by kevin Goedecke


# Exporting Conversations from Intercom

To export all conversations from Intercom, follow these steps:

## 1. Retrieve Conversation URLs in Batches

Get all the conversations' URLs in batches of 20. The URLs will look like this:

```markdown
https://api.intercom.io/conversations?starting_after=WzE3MDYwODc0MDgwMDAsOTc1NDcxMTM5NTQ3ODAsMl0=
```

Store these URLs, taking into consideration the rate limit managed by the script. Retrieving each URL may take up to 4 seconds.

## 2. Query and Save Conversation Data

Once you have all the URLs, query each URL individually and save the result. Use the following code snippet:

```javascript
const data = await getNextPages(conversationURL);

console.log(`On ${conversationURL}, there's ${data.data.conversations.length} conversation / ids`);

console.log(JSON.stringify(data.data.conversations[0], null, 2));
```

In this code, the first conversation of a given page is retrieved. Add a loop to save the conversation data somewhere. Consider using a NO SQL database to store the data, making it easier to export and clean later on.



