# Architecture Summary
This Spring Boot application uses both MVC and REST controllers.
Thymeleaf templates are used for the Admin and Doctor dashboards, while REST APIs serve all other modules.
The application interacts with two databases—MySQL (for patient, doctor, appointment, and admin data) and MongoDB (for prescriptions).
All controllers route requests through a common service layer, which in turn delegates to the appropriate repositories.
MySQL uses JPA entities while MongoDB uses document models.

# Flow of data and control
1. User accesses AdminDashboard or Appointment pages.
2. The action is routed to the appropriate Thymeleaf or REST controller.
3. The controller calls the respective service layers for modules that uses structured data with MySQL repository or document-based data with MongoDB repository.
4. Repository layer accesses the repsective databases.
5. Database accesss for data storage and retrieval.
6. Model binding of data: JPA Entities (MySQL) and Document objects (MongoDB)
7. Usage of modeled data: MVC flows - passed from controller to Thymeleaf templates, REST flows - models serialized into JSON and sent back to client as HTTP response.
