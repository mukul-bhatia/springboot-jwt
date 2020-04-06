                                          SpringBoot-JWT Generation and Authentication
Note:
This procedure assumes that you have already installed JDK1.8.

Objective: This project authenticates the "username" and "password" provided by the user with the one saved in the program. It returns a JWT token on successful authentication and denies access on unsuccessful authentication. This token is a necessity to every secured request made to server. The server expects this token in "Header" and decodes it to identify and validate the user.

Steps:

Step 1: Download the project and import it on your IDE(here IDE used is STS-4).

Step 2: In the project, the credentials used is:

{

"username":"foo",

"password":"bar"
}

To change the credentials, follow path : src -> main -> java -> MyUserDetailsService.java
Here, edit the username and password (in Line no. 16).

Step 3: Here, the configured port is 8080. To change the port number follow path : src -> main -> resources -> application.properties 
Here, edit the port number (in Line no. 1).

Step 4: Now to run the project, select the project name. Right Click on it and select Run As -> Spring Boot App. Once it starts running by showing "Completed initialization", open "Postman" to test the API's.

Step 5: This jar contains 2 API's. One is to generate the JWT token and the other is to verify secured access through token. a) To generate the token :

URL : http://localhost:8080/authenticate

Method: POST

Body -> raw -> JSON

{

"username":"foo",

"password":"bar"
}

Click Send and it returns a jwt token.

b) Copy the token and make a new request :

URL : http://localhost:8080/hello

Method: GET

Headers -> Authorization : Bearer COPIED_TOKEN

Click Send and you are able to access the "/hello" API.

c) Now in the "Headers", uncheck the "Authorization" (this means that you are trying to access the "/hello" API without the token). Click Send and you can see that you are forbidden to access the "/hello" API.

d) You can also test the "/authenticate" API by passing the incorrect credentials in the body and you wil see that the access is denied and the token is not generated.

Thats All Folks...!!!
