# Team-5 Dentistimo Documentation

## What is Dentistimo?

Dentistimo is a web application that offers a geolocalisation based dental care booking system. To book an appointment users can choose a dentist from the map, choose a time and fill in their details. 

The purpose of Dentistimo is to provide an interface which users can use to book dentist appointments in Gothenburg. The interface will guide the user through the whole process and enable them to complete their booking from their own device.

Dentistimo is developed in an effort to try an ease the pressure on the already fully booked dentist clinics. Instead of having to search through multiple, complicated booking systems, Dentistimo makes it easy for the user by gathering all clinics in Gothenburg on a map so the user can see which clinic is closest to them. Then the user can navigate to the specific booking page and recieve a booking confirmation.

The system is built around a map API which helps displays all clinics in Gothenburg. 

 # Components

  A link is provided to the repositories of the components are provided. In each repository, a detailed description of each components responsibilities are also provided

 - [Clinic handler](https://git.chalmers.se/courses/dit355/test-teams-formation/team-5/team-5-clinics-service)

 The Clinic handler fetches dentist data, stores it in the database and publishes dentist data to the frontend.

 - [Time slot generator](https://git.chalmers.se/courses/dit355/test-teams-formation/team-5/team5-time_slot_generator)

 The Time slot generator generates time slots when a user choses a date in the GUI. 

 - [Booking handler](https://git.chalmers.se/courses/dit355/test-teams-formation/team-5/booking-handler)

 - [Availability checking](https://git.chalmers.se/courses/dit355/test-teams-formation/team-5/availability-checker)

 The availability checker filters generated time slots to the user is only shown available time slots. The component also validates booking request and forward validated requests to the booking handler.

- [GUI](https://git.chalmers.se/courses/dit355/test-teams-formation/team-5/team-5-client)


# Software requirement specification (SRS)

  ## Functional requirements
   
  1. The system should have one user interface.
  2. The system should allow patients to book a dentist appointment
  4. The system should use middleware based on MQTT.
  5. The system shall display a navigable Map view of dentists' location in Gothenburg.
  6. The system should allow patients to view available time slots.
  8. A time slot should be 30 min starting every half or full hour
  9. The system should allow the dentist to have a lunch break (60 min).
  10. The system should allow the dentist to have a fika break (30 min).
  11. The system should track availability of free time-slots for a number of fictitious dentists
  12. The system should specify available time slots through user interface
  13. The system should send requests in predefined format.
  14. The system should provide the patient with feedback regarding their inputs.
  15. The system should allow the user to search/sort for an appointment. 
  16. The system should send a confirmation/rejection message to the user when they make a booking. 
  18. The system should display information about the clinics. 

  ## Non-functional requirements

   1. The system should be easy for users to use:
   2. From the main page, patients should be able to book an appointment in less than 5 clicks 
   3. The system should be fault tolerant 
   4. Architectural styles such as Pipe-and-Filter, Publish/subscribe and Client/server are supposed to be combined
   5. The system should not crash

## Cancelled (Choose not to implement)

  3. The system should allow the patients to cancel their bookings. <br>
    - Cancelled due to time constraints
  17. The system should send a confirmation/rejection message to the user when they cancel a booking <br>
    - Cancelled due to time constraints.
  7. The time slots should be visualised (color, symbol etc). <br>
    - Cancelled due to time constraints. 


 # Software Architecture 

## Architectural drivers
  - Availability

     In order for a user to book an appointment at any time, the system must be running and available most of the time. Otherwise, it is          inconvenient for potential patients and there is a risk that the clinics lose business opportunities.

  - Usability

     usability is an important architectural driver as a prominent part of the system is the graphical user interface. As we cannot assume that the target user is familiar with the user interface previously, the system should allow the user to achieve their goal, i.e. book an appointment, in an effective, efficient and satisfactory way. 

  - Scalability & Modifiability

  The Dentisimo service is right now available to residents in Gothenburg. However, the system might expand in the future and therefore it is important that the system can scale in a time efficient and cost effective way. This also includes changing already existing resources and functionality. 

  - Maintainability

Maintainability is also an architectural driver as it impacts the level of ease in which the system can be maintained in to e.g. maximise the system’s useful life, meet new requirements and cope with a changing environment.


 ## Architecture component diagram
![_Current_state__System_Component_Diagram-7_jan.drawio](/uploads/1b6e1034386a6dfe53115cd98fffcf56/_Current_state__System_Component_Diagram-7_jan.drawio.png)

 ## Architectural styles
We use a mix of different architectural styles. The architectural styles we use are:
- Publish/subscribe

Pub/sub will is used to enable components to publish and/or subscribe to different topics. Basically it’s the way components  will communicate with each other.

- Event-driven

Event-driven is used with the MQTT being event mediator and components being event processors.

- Client-server

Client-server style will be used to create separation between backend and frontend. 

## Technical specification

 ### Fault tolerance
  Taking into consideration that some sort of fault tolerance should be implemented into the system, the team selected Time-slot-generator as the   component and implement fault tolerance in form of a circuit breaker. The circuit breaker will aid the time-slot-generator in..

 ### Quality of service

 ## Technologies

 ### Software

 We base our backend on node.js and use mongoose to connect it to our mongoDB database. The frontend is based on Vue.js
  
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

    

