### To deploy application:

- Import as maven project
- Run BookingRestServiceApplication.java

### Application uses:

- Spring-MVC and Spring-Security
- HSQLDB
- Hibernate and Hibernate Validator

- For authentication I have used HTTP basic authentication, role-based.

- Users in the system

  |  Login   |   Password   |      Role     |
  |  ------- |  ---------   | ------------- |
  |  jsmith	 |	  qwerty    | ROLE_EMPLOYEE |
  |  jdoe		 |	 mySecret   | ROLE_EMPLOYEE |
  |  admin	 |	 q1w2e3r4   | ROLE_ADMIN    |



- Custom constraint @ConsistentDates - used to check if dateTo is not before dateFrom.

### REST API:

- **Managing users**:
	- http://localhost:8080/api/users
	    - **HTTP method**: GET
      - **requires**: HTTP Basic Authentication (Allowed for ADMIN_ROLE and EMPLOYEE_ROLE)
      - **input**: no
      - **output**: list of all users, HttpStatus.OK
      
  - http://localhost:8080/api/users
      - **HTTP method**: POST
      - **requires**: HTTP Basic Authentication (Allowed only for ADMIN_ROLE)
      - **input**: properties of user
      - **output**: properties of user that inserted in db, HttpStatus.OK
      
  - http://localhost:8080/api/users
      - **HTTP method**: PUT
      - **requires**: HTTP Basic Authentication (Allowed only for ADMIN_ROLE)
      - **input**: properties of user
      - **output**: properties of user that updated in db, HttpStatus.OK
      
  - http://localhost:8080/api/users
      - **HTTP method**: DELETE
      - **requires**: HTTP Basic Authentication (Allowed only for ADMIN_ROLE)
      - **input**: login of user
      - **output**: message about success, HttpStatus.OK
------------------------------------------
- **Managing rooms**:
	- http://localhost:8080/api/rooms
	    - **HTTP method**: GET
      - **requires**: HTTP Basic Authentication (Allowed for ADMIN_ROLE and EMPLOYEE_ROLE)
      - **input**: no
      - **output**: list of all rooms, HttpStatus.OK
      
  - http://localhost:8080/api/rooms
      - **HTTP method**: POST
      - **requires**: HTTP Basic Authentication (Allowed only for ADMIN_ROLE)
      - **input**: properties of room
      - **output**: properties of room that inserted in db, HttpStatus.OK
      
  - http://localhost:8080/api/rooms
      - **HTTP method**: PUT
      - **requires**: HTTP Basic Authentication (Allowed only for ADMIN_ROLE)
      - **input**: properties of room
      - **output**: properties of room that updated in db, HttpStatus.OK
      
  - http://localhost:8080/api/rooms
      - **HTTP method**: DELETE
      - **requires**: HTTP Basic Authentication (Allowed only for ADMIN_ROLE)
      - **input**: name of room
      - **output**: message about success, HttpStatus.OK
  ------------------------------------------
- **Managing bookings**:
	- http://localhost:8080/api/bookings
	    - **HTTP method**: POST
      - **requires**: HTTP Basic Authentication (Allowed for ADMIN_ROLE and EMPLOYEE_ROLE)
      - **input**:
          - dateFrom in format - YYYY-MM-DD hh:mm:ss
          - dateTo in format - YYYY-MM-DD hh:mm:ss
          - login of user
          - name of room
      - **output**: booking insered in db, HttpStatus.OK
      
  - http://localhost:8080/api/bookings
      - **HTTP method**: GET
      - **requires**: HTTP Basic Authentication (Allowed for ADMIN_ROLE and EMPLOYEE_ROLE)
      - **input**: 
          - dateFrom in format - YYYY-MM-DD hh:mm:ss
          - dateTo in format - YYYY-MM-DD hh:mm:ss
      - **output**: list of bookings, HttpStatus.OK
      
  - http://localhost:8080/api/bookings/room
      - **HTTP method**: GET
      - **requires**: HTTP Basic Authentication (Allowed for ADMIN_ROLE and EMPLOYEE_ROLE)
      - **input**: 
          - dateFrom in format - YYYY-MM-DD hh:mm:ss
          - dateTo in format - YYYY-MM-DD hh:mm:ss
          - name of room
      - **output**: list of bookings, HttpStatus.OK
      
  - http://localhost:8080/api/bookings/user
      - **HTTP method**: GET
      - **requires**: HTTP Basic Authentication (Allowed for ADMIN_ROLE and EMPLOYEE_ROLE)
      - **input**: 
          - dateFrom in format - YYYY-MM-DD hh:mm:ss
          - dateTo in format - YYYY-MM-DD hh:mm:ss
          - login of user
      - **output**: list of bookings, HttpStatus.OK
