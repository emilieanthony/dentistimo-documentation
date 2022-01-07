# Team-5 Dentistimo Documentation

## What is Dentistimo?

Dentistimo is a web application that offers a geolocalisation based dental care booking system. To book an appointment users can choose a dentist from the map, choose a time and fill in their details. 

## Task description

 # Components

 - [Clinic handler](https://git.chalmers.se/courses/dit355/test-teams-formation/team-5/team-5-clinics-service)
 - [Time slot generator](https://git.chalmers.se/courses/dit355/test-teams-formation/team-5/team5-time_slot_generator)
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

  ## Software Architecture Diagrams
We use a mix of different architectural styles. The architectural styles we use are pub/sub, event-driven and client-server. Pub/sub will is used to enable components to publish and/or subscribe to different topics. Basically it’s the way components will communicate with each other. Event-driven is used with the MQTT being event mediator and components being event processors. Client-server style will be used to create separation between backend and frontend. 

We base our backend on node.js and use mongoose to connect it to our mongoDB database. The frontend will be based on Vue.js 


![_Current_state__System_Component_Diagram-7_jan.drawio](/uploads/1b6e1034386a6dfe53115cd98fffcf56/_Current_state__System_Component_Diagram-7_jan.drawio.png)

## Technical specification

 ### Fault tolerance
  Taking into consideration that some sort of fault tolerance should be implemented into the system, the team selected Time-slot-generator as the   component and implement fault tolerance in form of a circuit breaker. The circuit breaker will aid the time-slot-generator in..

 ### Quality of service

 ## Technologies

 ### Software
  
 - [ NPM ](https://drive.google.com/drive/folders/1GLthbAZoj0aKaIgKPQe57GbSQ-Mt9-9g?usp=sharing) 
 - [ Vue.js ](https://drive.google.com/drive/folders/1GLthbAZoj0aKaIgKPQe57GbSQ-Mt9-9g?usp=sharing)
 - [ Opossum ](https://drive.google.com/drive/folders/1GLthbAZoj0aKaIgKPQe57GbSQ-Mt9-9g?usp=sharing)
 - [ Bootstrap Vue ](https://drive.google.com/drive/folders/1GLthbAZoj0aKaIgKPQe57GbSQ-Mt9-9g?usp=sharing) 
 - [ Mapbox ](https://drive.google.com/drive/folders/1GLthbAZoj0aKaIgKPQe57GbSQ-Mt9-9g?usp=sharing)
 - [ Vuex ](https://drive.google.com/drive/folders/1GLthbAZoj0aKaIgKPQe57GbSQ-Mt9-9g?usp=sharing)
 - [ MQTT](https://drive.google.com/drive/folders/1GLthbAZoj0aKaIgKPQe57GbSQ-Mt9-9g?usp=sharing)

 ### Project Management
 
 - [ Google Drive ](https://drive.google.com/drive/folders/1GLthbAZoj0aKaIgKPQe57GbSQ-Mt9-9g?usp=sharing)
 - [ Trello board ](https://trello.com/invite/b/jtnMl95E/05f9da2a77845b0d3ce68a2759902cff/dit355-team-5)
 - [ Diagrams.net ](https://app.diagrams.net/?src=about)
 - [ Gitlab Team-5 ](https://git.chalmers.se/courses/dit355/test-teams-formation/team-5)
           
  Commits in our repositories can be traced to tasks on trello board
  


## Team members
 - Alexandre Rancati-Palmer
 - Ann-Sofie Eriksson
 - Ina Johnson
 - Astrid Berntsson
 - Olga Ratushniak
 - Emilie Anthony
 - Christopher Axt

  ### Roles
   Roles for each sprint ( See [Trello] (https://trello.com/b/jtnMl95E/dit355-team-5) `roles` column)

    

