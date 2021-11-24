# microcontroller@Interview Task 2

A simple stateless microservice in Nodejs, with two major functionalities -  Authentication JSON patching And a dashboard to display the process and data. 

# Public end points

arbitrary username/password pair Treat it as a mock authentication service and accept any username/password. Return a signed Json Web Token(JWT, https://jwt.io/) which can be used to validate future requests.

# private end points

The JWT obtained in the “Login” endpoint is attached to each request header. If the JWT is missing or invalid, these endpoints should reject the request with the appropriate message to the user.

 Json Patch Request body contains a JSON object and a JSON patch object (http://jsonpatch.com/). Apply the json patch to the json object, and return the resulting json object.



## Setup

The API requires [Node.js](https://nodejs.org/en/download/)

To get up and running: 

**1.** Clone the repo.
```
git clone https://github.com/pedropinchez/microcontroller.git
```

**2.**  ```cd``` into repo. Use the same directory name(below) if you do not change it.
```
cd yourprojectfolder
```

**3.**  Setup the application by installing its dependencies with
```
npm install
```

**4.**  The app gets up and running on port 3000 with ```npm start```.

**5.**  **Important** Create a ```.env``` file and set ```jwtSecret``` to any secret phrase you want.
 
 
 ## Testing the API routes.

Since this is mostly an API with post and patch requests, testing will be done with [Postman](https://www.getpostman.com/)

### Authentication
This is a mock authentication so you can pass in any username or password to login.
 1. Set the request to **POST** and the url to _/api/users/login_. 
 2. In the **Body** for the Postman request, select **x-www-form-urlencoded**.
 3. You will be setting 2 keys (for username and password). Set the ```username``` key to any name. Set ```password``` to any password (minimum of 6 characters).
 4. Hit ```Send```. You will get a result in this format:
 ```
 {
    "user": "moi",
    "authorized": true,
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im1vaSIsImlhdCI6MTUzMjAwNDkwMSwiZXhwIjoxNTMyMDI2NTAxfQ.sonItbpZ_yKsRLDXNfDqwN6yN5VbdMVDhgKAMxDmPFY"
}
 ```


 ### JSON patching
Apply json patch to a json object, and return the resulting json object.
 1. Set the request to **PATCH** and the url to _/api/patch-object_.
 2. Set the key ```jsonObject``` to an object you would like to patch. Set the key ```jsonPatchObject``` to the object you want to use to patch the ```jsonObject```.
 ```
 Examples:
 jsonObject
 { "user": { "firstName": "Albert", "lastName": "Einstein" } }

 jsonPatchObject
 [{"op": "replace", "path": "/user/firstName", "value": "Leonardo"}, {"op": "replace", "path": "/user/lastName", "value": "da Vinci"}]
 ```
 3. Since this is a secure route, for testing, you will have to set the token in the ```Header```. Set key as ```token``` and value as token you received from **Authentication**.
 4. Expected result should be:
 ```
 { "user": { "firstName": "Leonardo", "lastName": "da Vinci" } }
 ```

