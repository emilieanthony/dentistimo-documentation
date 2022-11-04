# Team-5 Dentistimo Documentation

## What is Dentistimo?

Dentistimo is a web application that offers a geolocalisation based dental care booking system. To book an appointment users can choose a dentist from the map, choose a time and fill in their details. 

The purpose of Dentistimo is to provide an interface which users can use to book dentist appointments in Gothenburg. The interface will guide the user through the whole process and enable them to complete their booking from their own device.

Dentistimo is developed in an effort to try an ease the pressure on the already fully booked dentist clinics. Instead of having to search through multiple, complicated booking systems, Dentistimo makes it easy for the user by gathering all clinics in Gothenburg on a map so the user can see which clinic is closest to them. Then the user can navigate to the specific booking page and recieve a booking confirmation.

The system is built around a map API which helps displays all clinics in Gothenburg. 

 # Components

  A link is provided to the repositories of the components are provided. In each repository, a detailed description of each components responsibilities are also provided

 - [**Clinic handler**](https://github.com/emilieanthony/clinic-handler)

 The Clinic handler fetches dentist data, stores it in the database and publishes dentist data to the frontend.

 - [**Time slot generator**](https://git.chalmers.se/courses/dit355/test-teams-formation/team-5/team5-time_slot_generator)

 The Time slot generator generates time slots when a user choses a date in the GUI. 

 - [**Booking handler**](https://git.chalmers.se/courses/dit355/test-teams-formation/team-5/booking-handler)

 The Booking handler creates new bookings and stores them in the database.

 - [**Availability checker**](https://github.com/emilieanthony/availability-checker)

 The Availability checker filters generated time slots so that the user is only shown available time slots. The component also validates booking request and forwards validated requests to the booking handler.

- [**GUI**](https://git.chalmers.se/courses/dit355/test-teams-formation/team-5/team-5-client)

The GUI displays an interactive map allowing users to navigate to dentist practices
and allows users to book an appointment at a chosen clinic.



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
    - Cancelled due to low priority from start and time constraints
  17. The system should send a confirmation/rejection message to the user when they cancel a booking <br>
    - Cancelled due to choice of not allowing users to cancel their bookings
  7. The time slots should be visualised (color, symbol etc). <br>
    - Solved by only displaying available time slots to the user and the team therefore decided that colour visualisation was redundant. 
  15. The system should allow the user to search/sort for an appointment. <br>
    - We decided not to implement a specific search function as we thought finding a clinic on the map and choosing a date was sufficient and would satisfy the needs of the user in terms of achieving their goal of booking an appointment.


 # Software Architecture 

## Architectural drivers
  - **Availability**

In order for a user to book an appointment at any time, the system must be running and available most of the time. Otherwise, it is inconvenient for potential patients and there is a risk that the clinics lose business opportunities.

  - **Usability**

Usability is an important architectural driver as a prominent part of the system is the graphical user interface. As we cannot assume that the target user is familiar with the user interface previously, the system should allow the user to achieve their goal, i.e. book an appointment, in an effective, efficient and satisfactory way. 

  - **Scalability & Modifiability**

The Dentisimo service is right now available to residents in Gothenburg. However, the system might expand in the future and therefore it is important that the system can scale in a time efficient and cost effective way. This also includes changing already existing resources and functionality. 

  - **Maintainability**

Maintainability is also an architectural driver as it impacts the level of ease in which the system can be maintained in to e.g. maximise the system’s useful life, meet new requirements and cope with a changing environment.


 ## Architecture component diagram
![_Current_state__System_Component_Diagram-7_jan.drawio__1_](/uploads/8b98944c9d2e435fa724c4472ca4e884/_Current_state__System_Component_Diagram-7_jan.drawio__1_.png)

**Timeslot generator**
 - Triggered when a user picks a date on the booking page in the GUI
 - Responsible for generating time slots based on dentist information
 - Responsible for sending the unfilterd time slots to the Availability checker

 **Clinic handler**
 - Triggered by the frontend requesting dentist data
  - Responsible for fetching dentist data from dentistry DB
  - Store dentist data in our database
  - Publish dentist data to frontend for the map view

  **Booking handler**
  - Triggered by the Availability checker when there is a valid booking request forwarded
  - Responsible for creating new bookings
  - Responsible for storing new bookings
  - Responsible for publishing bookings

  **Availability checker**
  - Triggered by timeslots being forwarded by the Time slot generator.
  - Responsible for forwarding filtered time slots to the frontend
  - Responsible for checking if a chosen time slot has available appointments
  - Responsible for validating booking requests and forward validated booking requests to the Booking handler

  **Request generator**
  - This component is responsible for creating requests for test purposes

 ## Architectural styles
We use a mix of different architectural styles. The architectural styles we use are:
- **Publish/subscribe**

Publish/subscribe is used  as a way for the components to communicate with each other publishing and/or subscribe to different topics. Subscribers in our system will receive all messages published to the topics to which they subscribe. The publisher is responsible for defining the topics to which subscribers can subscribe. The massaging between component goes through a broker, in our case MQTT.

- **Event-driven**

We use an event-driven architecture that uses events to trigger and communicate between the decoupled components which can asynchronously publish and subscribe to events via an event broker, in our case MQTT. An event is a change in state, or an update. An example where we use this is when a user pick a date and triggers the time slot generator to generates time slots. 

- **Client-server**

Client-server style will be used to create separation between backend and frontend. 

- **Pipe-filter**

We use pipe filter architecture where the MQTT broker is the pipe and the components are the filters. For example the availabilty checker transforms the data before forwarding it to the broker.

## Technical specification

 ### Fault tolerance
Taking into consideration that some sort of fault tolerance should be implemented into the system, the team selected Time-slot-generator as the component and implement fault tolerance in form of a circuit breaker. The circuit breaker protects the component from being spammed while already being partly unavailable due to high load. We have also implemented a request generator to test the system's ability to handle high load. 



 ### Quality of service

The components in the backend of this system use a QOS level 1 since we want to guarantee that the message is delivered at least once.

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
     
  Commits in our repositories can be traced to tasks on Trello board
  
## Project management

### Project methodology

- We used Scrum, an agile development methodology based on an iterative and incremental process.
- We worked as a self-organising cross-functional development team with assigned roles such as Product Owner and Scrum Master.
- By having bi-weekly sprint planning meetings, sprint reviews and sprint retrospectives, we could be flexible to change.
- In order to keep track of the teams progress, we exercised daily stand-ups in written format. 
- We also used Trello to manage our product backlog, sprint backlog and keep track of our progress.
- In the later parts of the project, we estimated user stories and tasks using a minimalistic form of Planning Poker and added the story point to relevant cards on Trello.
- The first sprint was dedicated to creating artefacts to help the project move forward, decide on architecture and set up repository structure. 

 ### Project management tools used
 
 - [ Google Drive ](https://drive.google.com/drive/folders/1GLthbAZoj0aKaIgKPQe57GbSQ-Mt9-9g?usp=sharing)
 - [ Trello board ](https://trello.com/invite/b/jtnMl95E/05f9da2a77845b0d3ce68a2759902cff/dit355-team-5)
 - [ Diagrams.net ](https://app.diagrams.net/?src=about)
 - [ Gitlab Team-5 ](https://git.chalmers.se/courses/dit355/test-teams-formation/team-5)
 - [ Google calendar ](https://calendar.google.com/calendar/u/1?cid=Y19tbjZvbmNmaXA2OXBuanNibnFydXN1Z2RiOEBncm91cC5jYWxlbmRhci5nb29nbGUuY29t)

## Team members
 - Alexandre Rancati-Palmer
 - Ann-Sofie Eriksson
 - Ina Johnson
 - Astrid Berntsson
 - Olga Ratushniak
 - Emilie Anthony
 - Christopher Axt

  ### Roles
   Roles for each sprint, see [Trello](https://trello.com/b/jtnMl95E/dit355-team-5) `roles` column

    

