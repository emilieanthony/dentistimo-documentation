## Team-5 
Alexandre Rancati-Palmer, Ann-Sofie Eriksson, Ina Johnson, Astrid Berntsson, Olga Ratushniak, Emilie Anthony, Christopher Axt

## Task description

# Links
 - [Project Trello board](https://trello.com/invite/b/jtnMl95E/05f9da2a77845b0d3ce68a2759902cff/dit355-team-5)

 # Components

 - [Clinic handler](https://git.chalmers.se/courses/dit355/test-teams-formation/team-5/team-5-clinics-service)
 - [Booking handler](https://git.chalmers.se/courses/dit355/test-teams-formation/team-5/booking-handler)
 - [Availability checking](https://git.chalmers.se/courses/dit355/test-teams-formation/team-5/availability-checker)
  - [GUI](https://git.chalmers.se/courses/dit355/test-teams-formation/team-5/team-5-client)

# Software requirement specification (SRS)

  ## Functional requirements
   
  1. The system should have one user interface.
  2. The system should allow patients to book a dentist appointment
  3. The system should allow the patients to cancel their bookings.
  4. The system should use middleware based on MQTT.
  5. The system shall display a navigable Map view of dentists' location in Gothenburg.
  6. The system should allow patients to view available time slots.
  7. The time slots should be visualised (color, symbol etc).
  8. A time slot should be 30 min starting every half or full hour
  9. The system should allow the dentist to have a lunch break (60 min).
  10. The system should allow the dentist to have a fika break (30 min).
  11. The system should track availability of free time-slots for a number of fictitious dentists
  12. The system should specify available time slots through user interface
  13. The system should send requests in predefined format.
  14. The system should provide the patient with feedback regarding their inputs.
  15. The system should allow the user to search/sort for an appointment. 
  16. The system should send a confirmation/rejection message to the user when they make a booking. 
  17. The system should send a confirmation/rejection message to the user when they cancel a booking.
  18. The system should display information about the clinics. 

  ## Non-functional requirements

   1. The system should be easy for users to use:
   2. From the main page, patients should be able to book an appointment in less than 5 clicks 
   3. The system should be fault tolerant 
   4. Architectural styles such as Pipe-and-Filter, Publish/subscribe and Client/server are supposed to be combined
   5. The system should not crash

  ## Software architecture
We are planning to use a mix of different architectural styles. The architectural styles we will use are pub/sub, event-driven and client-server. Pub/sub will be used to enable components to publish and/or subscribe to different topics. Basically it’s the way components will communicate with eachother. Event-driven is used with the MQTT being event mediator and components being event processors. Client-server style will be used to create separation between backend and frontend. 

We are planning to base our backend on node.js and use mongoose to connect it to our mongoDB database. The frontend will be based on Vuejs

#### Version 1 
This is the architectural style used for the second sprint.
- A combination between HTTP and MQTT is used.

![Architecture_-_version_1](/uploads/ebc6464297684d7a7b91a2e58988964e/Architecture_-_version_1.png)

#### Version 2
For the third sprint, changes were made in the architecture. Some of the changes include:
- MQTT is not combined with HTTP. MQTT connection is instead added to the client, and API middleware is deleted.
- A booking validator component and a user handler are added.


![Architecture_-_version_2](/uploads/1c4744db85ef437f4eddc3bb0102bc82/Architecture_-_version_2.png)
     
    

