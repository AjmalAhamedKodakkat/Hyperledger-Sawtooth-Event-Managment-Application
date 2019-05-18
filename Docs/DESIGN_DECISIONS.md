



**Note** - The application is designed for demonstrating Hyperledger sawtooth consisting of a single transaction family 

1. Event addressing Scheme --- Event addressing scheme is the first 6 hex character is the hash of FamilyName,then the next 64 hex character is hash of the Date of Event
Of course, there are several other possibilities but we have considered the above.

Address = hash(FamilyName).slice(0,6)+hash(date).slice(0,64)

Hashing is done using SHA512.

2. About Transaction Family's --- We have a single Transaction Family "Event_Managment_App"

3. Node's of the network - Only a single node is considered for demonstration purpose

4. Event's - In this application, we have used 2 events. First, sawtooth inbuild block commit event, second is the custom event in the Transaction Processor.


7. Permissioning: Note that, in this application, we have designed in such a way that when the network turns up, a set of public and private key are produced for a participant or a user who does the transaction and it can be used for setting permissions

Note: Application can also be used without setting permissions. In that case we can use any private key 



