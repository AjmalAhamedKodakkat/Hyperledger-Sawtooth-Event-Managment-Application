
                                                 VEHICLE MANAGEMENT SYSTEM


**UI  User Guide**
1. Open http://localhost:3000 in the browser.
2. Navigate to the "Event Registration" page.
3. Input the User Private key and all other details in the form.
4. Submit the form.
5. Navigate to "Latest Transaction ID" page from the Event registration page.
6. View and copy the latest transaction Id.
7. Navigate to the "Transaction Receipts" page and paste the latest transaction Id in the form.
8. Now you can view and confirm the transaction receipt and the Event registration is successful.
9. Now navigate to the "Event Details" page and input the Date of event to view the Event registration details.
10. For deleting event details, navigate to the "Delete Event Details" page from "Event Registration" page and enter the private key of user and the date of event to be deleted.

**Events in Application**

Event's - In this application, we have used 2 events, one is the sawtooth inbuild block commit event, second is custom event in the Transaction Processor.

Custom Event : In Transaction family "Event_Managment_App".
When an Event Registration is done by the user and if the location of the event is "singapore", a custom event occurs as a notification.


