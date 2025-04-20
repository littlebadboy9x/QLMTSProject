# StaffSync - Staff Management System

A comprehensive Spring Boot application for managing staff, departments, facilities, and specializations. This system allows organizations to track staff information, manage their specializations across different facilities, and handle data import/export operations.

## Technologies Used

- **Java 17**
- **Spring Boot 3.4.4**
- **Spring Data JPA**
- **Thymeleaf** for server-side templating
- **Bootstrap 5** for responsive UI
- **jQuery** for AJAX operations
- **Microsoft SQL Server** for database
- **Apache POI** for Excel file operations
- **Lombok** for reducing boilerplate code
- **ModelMapper** for DTO conversions

## Database Schema

The system uses the following database tables:

- **staff**: Stores staff information
- **facility**: Manages facilities
- **department**: Manages departments
- **major**: Manages specializations
- **department_facility**: Links departments with facilities
- **major_facility**: Links specializations with departments at facilities
- **staff_major_facility**: Links staff with specializations at facilities

## Key Features

### Staff Management

- Create, read, update, and delete staff records
- Track staff information including code, name, FPT email, and FE email
- Toggle staff active status

### Facility and Department Management

- Manage facilities and departments
- Link departments with facilities
- Assign department heads

### Specialization Management

- Manage specializations within departments
- Assign staff to specializations at specific facilities
- Track staff specialization history

### Data Import/Export

- Download Excel template for staff
- Import staff data from Excel files
- Export staff data to Excel format

### User Interface

- Responsive web interface using Bootstrap
- Interactive forms with client-side validation
- AJAX-based operations for smooth user experience

## Setup and Installation

### Prerequisites

- Java 17 or higher
- Microsoft SQL Server
- Maven

### Database Setup

1. Create a SQL Server database named `staffsync`
2. Run the SQL script in the `database-setup.sql` file to create tables and sample data

### Application Configuration

1. Clone the repository
2. Configure database connection in `src/main/resources/application.properties`:

```plaintext
spring.datasource.url=jdbc:sqlserver://localhost:1433;databaseName=staffsync;encrypt=true;trustServerCertificate=true
spring.datasource.username=your_username
spring.datasource.password=your_password
```

3. Build the application:

```shellscript
mvn clean package
```

4. Run the application:

```shellscript
java -jar target/StaffSync-0.0.1-SNAPSHOT.jar
```

5. Access the application at `http://localhost:8080`

## API Endpoints

### Staff API

- `GET /api/staff` - Get all staff
- `GET /api/staff/{id}` - Get staff by ID
- `GET /api/staff/code/{code}` - Get staff by code
- `POST /api/staff` - Create new staff
- `PUT /api/staff/{id}` - Update staff
- `PUT /api/staff/{id}/toggle-status` - Toggle staff status

### Specialization API

- `GET /specialized-subjects/api/facilities` - Get all facilities
- `GET /specialized-subjects/api/facilities/{facilityId}/departments` - Get departments by facility
- `GET /specialized-subjects/api/department-facilities/{departmentFacilityId}/majors` - Get majors by department facility
- `GET /specialized-subjects/staff/{staffId}` - Get staff specializations
- `POST /specialized-subjects/staff/{staffId}/major-facilities/{majorFacilityId}` - Add staff specialization
- `DELETE /specialized-subjects/staff/{staffId}/major-facilities/{majorFacilityId}` - Remove staff specialization

### Excel API

- `GET /specialized-subjects/staff/{staffId}/download-template` - Download Excel template for staff

## Project Structure

```plaintext
src/main/java/com/example/staffsync/
├── config/                  # Configuration classes
├── controller/              # REST and view controllers
├── dto/                     # Data Transfer Objects
├── exception/               # Exception handling
├── Entity/                  # Entity classes
├── repository/              # JPA repositories
├── service/                 # Business logic
└── StaffSync.java          # Main application class

src/main/resources/
├── static/                  # Static resources (CSS, JS)
├── templates/               # Thymeleaf templates
└── application.properties   # Application configuration
```

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgements

- Spring Boot and Spring Data JPA for the robust backend framework
- Bootstrap for the responsive UI components
- jQuery for simplifying client-side scripting
- Apache POI for Excel file handling

---

© 2025 Tran Viet Vuong - FPOLY. All rights reserved. 
