# Sending MeshMS messages via the command line
The following steps outline how to send [MeshMS](http://developer.servalproject.org/dokuwiki/doku.php?id=content:tech:meshms) messages manually via the command line.

All of the commands below assume you have authority to call ServalD commands (i.e. `sudo`)

First we'll need to set up a keyring and we'll assign a [DID](https://github.com/servalproject/serval-dna/blob/development/doc/REST-API-Keyring.md#did) to make it easier to find in the Serval Chat app. This only needs to be done once per device.

1. `servald keyring create`  
   A new keyring has been initialised, but there aren't any keys in it yet.
2. `servald keyring add`  
   This will generate a new identity and store it in the keyring. You'll need this later.
3. `servald keyring set did <sid> <phone> <name>`  
   Now you've attributed a phone number and name to your identity (DID). You are now easier to identify and the [Serval Chat app](http://developer.servalproject.org/dokuwiki/doku.php?id=content%3Aservalchat%3Amain_page) will be able to see and respond to your messages.

The keyring and identity have been set up, so now you can send and receive messages within the Serval Mesh network.

4. `servald meshms send message <sid> <recip_sid> <message>`  
   The message is lodged in the [Rhizome](http://developer.servalproject.org/dokuwiki/doku.php?id=content:tech:rhizome) database and will be propagated throughout the network.
5. `servald meshms list conversations <sid>`  
   You should see the recipient's SID and some details about the conversation.
6. `servald meshms list messages <sid> <recip_sid>`  
   Now you can read the message history.
7. `servald meshms read messages <sid> <recip_sid>`  
   This should mark the last received message as read.
