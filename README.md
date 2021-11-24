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
 
