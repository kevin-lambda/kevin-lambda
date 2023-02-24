<!--- 
## Project
**Date:** 0  
**Description:** P  
**Link:** []()  
**Notable Technologies:** R  
**Learning focus:** U

#### Dev learnings
- **subject 1<sub>[1]</sub>:** T 
    - **CRA:** B
    - A
    - **Troubleshooting:** H
    - Y
    
- **Sunject 2:** W
    - P

#### Flagnotes
[1] I

[⬆️ Back To Contents](#-contents)
======================================================================
## Journal 1/16/2023 
- a
--->

# 📚 CONTENTS
This is a journal of my projects, lessons learned and thoughts during my coding journey.

### Projects
1. [Portfolio Version 2](#project-portfolio-v2)  
1. [Dakine Ipsum Project](#project-dakine-ipsum)  
1. [NPS Stamps](#project-nps-stamps)  
1. [This Page Belongs To](#this-page-belongs-to)  

### Journal
1. [Jan 16 2023: Starting Again](#journal-16-jan-2023)
1. [Jan 27 2023: 2.75/3](#journal-27-jan-2023)
1. [Feb 14 2023: First Migration](#journal-14-feb-2023)
1. [Feb 15 2023: First Takehome](#journal-15-feb-2023)

### Tech and skills used
- Jan 16 2023 ; Basic html, css, javascript ; [Portfolio Version 2](#project-portfolio-v2)
- Jan 20 2023 ; CFG generation, React ; [Dakine Ipsum Project](#project-dakine-ipsum)  
- Jan 27 2023 ; api, fs, require, image quantization ; [Project Retired. Jan 27 2023: 2.75/3](#journal-27-jan-2023)
- Feb 14 2023 ; Panelbear, Cronitor RUM ; [Feb 14 2023: First Migration](#journal-14-feb-2023)
- Feb 15 2023 ; code sandbox, MUI, react-chart-js-2 ; [Feb 15 2023: First Takehome](#journal-15-feb-2023)
- Feb 25 2023 ; PERN stack, Render PaaS ; [This Page Belongs To](#this-page-belongs-to)  

# 📖 ENTRIES

## This Page Belongs To

**Date:** 02/25/2023  
**Description:** Claim a website for yourself.  
**Link:** [https://this-belongs-to.onrender.com/](https://this-belongs-to.onrender.com/)  
**Notable Technologies:** PERN stack (Postgresql, Express, React, Node), [Render](https://render.com/) platform as a Service (PaaS) cloud hosting infrastructure.  
**Learning focus:** Build and deploy a PERN (Postgresql, Express, React, Node) full-stack application.

"This Page Belongs To" allows a user to input their name as the current owner of the webpage, which is prominently displayed. Any other visitor can replace the existing owner and become the new current owner. There is a persistent list of previous owners and the length of time they were owner.

#### **!!! Upkeep:**

- !!!!!! MAY 21 2023. Render database will shut down because it only lasts for 90 days. Will need to either make a copy of the database... somehow. Then in render, make a new database instance, get it's internal connection URL, and use it as the key in the web service enviroment variables.

#### **Reviewed:**

nodejs, postgresql, sequelize, model definition, file entry points, module.exports, require, restful api, date object, ISO time format, date calculations, form labels, seed file, database instances, express, express routers, middleware, path, volleyball, cors, express.static, express.jason, express.urlencoded, db.sync, app.listen, environment variables, package.json scripts, webpack, server local host, Render deploying, postbird database tool, postman api tool, web service hosting, database hosting, static site hosting

#### **To look into:**

- controlled vs uncontrolled components
- to look into react [lifting state up](https://beta.reactjs.org/learn/sharing-state-between-components) as a middle ground between **redux single source state** and **component limited state**.

#### **Extensions:**

- [L] highest time owned
- [M] input filter api
- [H] admin page w/ auth

### Dev learnings ========================================================

#### **High level review**

~ someone review this

- **Frontend vs Backend vs Database**

  - The Frontend is code that is sent to and is run on browser. This means frontend code will be seen by any client because the code is being run on their browser.
  - The Backend (web service) is code that does functions, in a fullstack context, usually a server that listens for requests and provides responses. The backend code probably is being hosted and run somewhere, but importantly, it is not running on the client's browser/machine. The only way to normally interact with the backend is through it's API, which can be a restful type api.
  - The database holds data and manages how the data may be related to each other. The database needs to live somewhere.

- **Development Frontend**

  - The frontend can be written in javascript, the language.
  - The frontend code includes all the stuff that is attached to the index.html. Which can be javascript files, html, css, public static assets.
  - The frontend can use React, the framework/library?, which uses javascript, the language.
  - React provides certain functions that do things, such as useState, components, props.
  - Frontend files should generally be in the `src` folder

- **Development Backend**

  - The backend can be written in javascript, the language. However, javascript is originally meant to only be run in the browser.
  - Node, the runtime environment, features an environment that javascript can run in that is not in the browser. It also comes with lots of functions.
  - Thus, we can use javascript, the language, running with node, the runtime environment to write code for a backend.
  - Backend code usually is in a separate directory from the frontend code such as `server`.

- **Developement Database**

  - A database can be a postgresql type database. Which is based on SQL.
  - To make things easier, instead of using SQL commands, we can use sequelize to simplify working with the database.
  - We can define the database with our code, but the actual data in the database lives somewhere else. Not in our code.
  - Define database means tables, columns attributes, how tables are related to each other.
  - The database definition usually lives with the server code, because they are often closely linked.

- **Files entry Points**

  - Between all the require, import, export of files being moved around everywhere, they eventually lead to the entry point.
  - The entry point is the one file, that when run, will run all the files used in the application. This is the highest level file.
  - Usually this is an index.js or index.html.

- **Data sending and receiving, module.exports and require, >>NODE**

  - module.exports and require are one way of sending and receiveing data such as functions, variables, classes between files. This is typically associated with nodejs...?
  - EXPORTING:

    - Every nodejs file comes with an object, called module. the module object can be console logged.
    - That object, called module, has a key for an object called exports. We can define the values in that exports object like normal objects.

      ```javascript
      console.log(module.exports) // {}
      exports = "abc" //exports is an alias for module.exports
      module.exports = "abc"
      module.exports = functionName
      module.exports = { key1: value1, key2: value2 }
      module.exports = { key1, key2 } //equivalent to { key1:key1, key2:key2 }
      ```

  - REQUIRING:
    - To get the data that a file has exported, we use require which will take in whatever is module.exports
    - Require can point to a:
      - Path with a file that is exporting something
      - Core (default) module name, comes with the environment/etc
      - node_modules package with that name.
    - Named requires will by default grab the `index.js`
    - The require returns the module.exports object, which we should then set to a variable
      - `const express = require("express")`
      - `const otherJsFile = require(../path/otherJsFile.js)`

- **Data sending and receiving, import and export >>Javascript ES6, React**

  - import and export are one way of sending and receiveing data such as functions, variables, classes between files. This is typically associated with javascript ES6, react, frontend...?

  - EXPORTING:

    - There are a bunch of ways to export... Let's just stick with a few
    - Named export at the end of a file: `export {functionName, variable, array, class}`
    - Default export: `export default function`

  - IMPORTING:
    - Importing syntax depends on how something was exported (ugh).
    - Named `import { export1, export2 } from "module-name";`
    - Default `import defaultExport from "module-name";`

#### **Frontend**

- **Axios CRUD calls to server restful api from the front end**

  - The url working in development is domainless (does axios just not care when it is localhost and doesn't need it specified?).
    - !!! But when moving to production, axios needs the **actual domain** prepended to the api path. Maybe use an environment variable to handle the axios domains ahead of time. And make it easy to switch domains between development and production.
  - Sending data to api. Probably best to format the data in the frontend before sending to the api. For consistency.
  - Deleteing, editing, for getting single, using ID from setstate
  - Full flow: Form button onclick,onChange -> setState to target.value -> form handle submit -> prevent default, axios

- **Trigger useEffect and update a list with setstate counter**

  - I've been getting useEffect to trigger by feeding it counter state dependency. Whenever an axios action is called, I update the count state, which triggers the useEffect to re-render the list. Keeping it updated upon every action. There's probably a less hacky way to do this.

    ```javascript
    const handleSubmit = async (event) => {
      event.preventDefault()
      const payload = { name: addName }
      await axios.post(
        `https://this-page-belongs-to.onrender.com/api/owners`,
        payload
      )
      setCount(count + 1)
    }
    ```

    ```javascript
    useEffect(() => {
      getOwnerList()
    }, [count])
    ```

- **Time Calculations & postgres**

  - When a row instance is created in postgres, there is a created and update date attached by default
  - This column attribute is accessable like any other data item in a row.
  - The FORMAT of the date is ISO. This is different from the Date object in javascript.
  - In order to do calculations with the created data, we need to convert it to the js date object epoch time. (the date object format keeps track of time in milliseconds from Jan 1 1970, called the epoch, which is the same as UNIX time. anyway. It just gives all date objects the same reference point to use.)
  - The new Date object conveniently accepts ISO format and converts it. `const nowInEpochFormat = new Date(createdAtDataFromPostgres_ISO_FORMAT)`
  - Now that the time converted, we can do standard calculations, it'll auto convert to milliseconds. Will probably use the block below.

  ```javascript
  const second = 1000
  const minute = 60 * second
  const hour = 60 * minute
  const day = 24 * hour
  ```

- **Form: controlled vs uncontrolled components**

  - React has forms which can have inputs. These inputs can have a value attribute. If we set the value of the input to be a state var, it will be a controlled component. Otherwise it will be an uncontrolled component.
  - The difference is something like... the controlled form input component is controlled (or tracked?) by the react state. VS being tracked by the DOM.
  - Apparently controlled components is best practice for most cases.

  ```javascript
  const [nameInput, setNameInput] = useState("")
  <form>
    <input
    value={nameInput}
    onChange={(event) =>setNameInput(event.target.value) }
    />
  </form>
  ```

- **Form: label**

  - labels usually go inside the form tags
  - the react form `label attribute htmlfor`, ties the label to the `input attribute name`. This helps with accessability

- **I was stuck in css purgatory. no more only using vanilla css for me**

#### **Backend higher level: middleware, entry point (app.js, index.js)**

- **Backend high level overview**

  - ENTRY POINT - index.js: When this file is run (like from a web service host), the sequelize model definitions for the database are synced to the actual database. And the express application (with all the middleware, api routes, etc) is activated.
  - FULL APPLICATION - app.js: This is where all the high level functions of the app are connected. Making an express instance, various middleware, api route handling, ? send file?, error handling.
  - API ROUTES - index.js & model.js: consolidates the api routes and handles the server responses for a request type and path.
  - DATABASE INSTANCE - index.js, database.js: Consolidates the models and databases. Makes and attaches a connection to the actual hosted database (through actual hosted database URL, or localhost).
  - DATABASE MODEL DEFINITION - model.js: Defines a table model and the attributes it can have.
  - SEED FILE - seed.js: A seed data file for development, which has dummy data and forces a db.sync.

  <img src="./assets/backend_logic.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 75%;">

- **Express**

  - `var express = require('express');`
    - `express` by itself is the definition of the express function
    - `express()` runs the function and makes an active express application
    - some modules return a function, or an object. The use method is not always the same, check the return from the require to.

- **Middleware & Express Tools**

  - path: Allows joining of paths. Some functions need a full absolute path. To specify certain paths, we may need the path to be variable and change depending on the home directory. In order to combine a variable to a relative path, it needs to be a certain type. path.join allows this function.
  - volleyball: gives human readable statuses when working with a server. It would be hard to read otherwise.
  - cors: enables cors for all routes. means a domain origin that is different from the api origin can talk to it from the front end. ???
  - **_express.static_**: this allows access to static files in the root folder specified. Maybe want to put build or public folder. If this is not defined, static files such as index.html, css, static assets will not be accessable. _At All._
  - express.json, express.urlencoded: Need both of these to read incoming JSON from the req.body from the client. Without this the req.body will be "undefined"

#### **Backend lower level: api, database**

- **require**

  - Reminder, require brings the entire instance of the thing. _including_ anything that is attached to it, such as middleware, route handlers, models.
  - Thus, in index.js, when app.js is required, that is bringing in _everything_ attached to the app.

- **db sync & app listen**

  - db sync is a sequelize function that makes sure the model definition matches what is in the database.
  - app listen activates the app and tells the port to listen and be ready to process requests

- **express.json & express.urlencoded**

  - data is sent from client to server via req.body
  - both middleware processes req.body content
  - express.json detects json data in the req.body and makes it available
  - express.urlencoded detects string or array data in the req.body and makes it available

- **API route domains**

  - Apparently express doesn't care or need to know what the domain of the api path we are setting up to handle. It just cares about the path.
    - `http://www.domain.com/path1/path2`
    - protocol = http://
    - domain = www.domain.com
    - path = /path1/path2
  - Once deployed, express server should still be okay.

- **Database index.js**

  - Collects the database instance, and all the model definitions to associate as needed

- **Database database.js**

  - creates a new sequelize instance which connects to a database. Usually a URI such as `'postgres://user:pass@example.com:5432/dbname'`. which is formatted somethin like this `"postgres://YourUserName:YourPassword@YourHostname:5432/YourDatabaseName"`

- **Database model definition**

  - Onto the original db instance, we attach the model definition to it. Such as below
  - exporting the model so it can be worked on or associated later. Such as making associations with another model, or doing sequelize operations on it as an API response.

  ```javascript
  const Owner = db.define("owners", {
    name: {
      type: Sequelize.STRING,
      allowNull: false,
      validate: {
        notEmpty: true,
        len: [1, 50],
      },
    },
  })
  ```

- **Database magic methods hint**

  - To see a list of magic methods for a model, if it has been associated.
    - Get an instance of the model, then call
    - `console.log(Object.keys(Model_instance.__proto__))`

- **Database seeding**

  - require the database and models
  - create an array with dummy data
  - force a db.sync, map over the dummy data array with .create
  - run the seed function, then close the db

- **API index.js**

  - Holds all the /api routes

- **API model**

  - Have a route, and method to define the request type
  - have a response, typically doing an operation on the database somehow. Such as
    - GET all, "/": model.findAll()
    - GET single, "/:id": model.findByPk(req.params.id)
    - POST, "/": model.create(req.body)
    - PUT "/:id": model.findByPk(req.params.id) ; model.update(req.body)
    - DELETE, "/:id": model.findByPk(req.params.id) ; model.destroy()

- **Express static**
  - Static files in an express project can't be accessed normally. Need to use the middleware app.use(express.static)
  - In this case for a create react app, have a folder in public, like "assets". then access it by
  - `app.use(express.static('build'))` OR `app.use(express.static('public'))`
  - If the file is located >>> `[project root]/public/assets/picture.jpg`
    - Access it with `<img src="/assets/picture.jpg"`

#### **Build Tooling**

- **Environment Variables**

  - Enviroment variables are variables that belong to _whatever_ enviroment is running the application. This could be the local machine, a hosting web service, or another machine. Each will have _different_ enviroment variables.
  - Current machine os may be linux, a different may be windows, another macos.
    -In node, environment variables are stored in the object `process.env`
  - The env variable can be accessed with `process.env.variable1` or `process.env.variable2`
  - However, to use _local_ environment variables, we need to 1. create the environment variables, and 2. use the dotenv npm package to load those variables into process.env

    - 1. In the root directory, create the file ".env"
    - 2. In that file, write `VARIABLE_NAME=variable_data_here_1`
      - Create React App has special rules for variable naming. The variable name _must_ be prefixed with `REACT_APP`
    - 3. In another file that wants to access the env variable, add the following `const dotenv = require('dotenv')`
    - 4. For env variables that hold a secret key, make sure to add `.env` to the .gitignore file.

  - In the case that a web service is running the server, if the web service runs node, then the web service it self can have its own process.env. Therefore...
    - We can call the environment variable of the web service in the same way. With `process.env.KEY_NAME`

- **Scripts in package.json**

  - Writing scripts in package.json is an easy way to run files and do dev operations.
  - A package.json script can be executed from anywhere (within the project directory) with `npm run SCRIPT_NAME`
  - `npm run SCRIPT_NAME` will trigger as if it is from the package.json root level. This is helpful if we want to execute a file, but the file is nested in directories.
  - Whatever CLI commands we do, can be scripted.
  - To save time, we can attach multiple commands to one script, such as performing a build and then starting the server. `"serverb": "react-scripts build && nodemon server/index.js",`
  - nodemon is actually useful. especially for servers, use it.

- **Webpack and create react app**

  - Webpack is a process of bundling many js files into one js file, and then injecting that js file as a script into the index.html.
    - Reminder that the way js files run in a html file is by enclosing the js file in a script tag in html.
    - Without webpack, we would have to manually get our js app entry point and put it in the html.
    - Webpack does this by creating a "build" folder, where the production ready app (with injected bundled js file) lives.
    - The build process usually takes some time.
  - Create react app, includes this webpack process. **However**, by default, the configuration file is hidden from view and not accessable. This means we can't change or specify certain things webpack is doing without significant modification to create react app.

- **_!!!!!!!!!!!!! Development local host, server and static site_**

  - When developing a full stack application, it will probably have a static site (front end react stuff), and a backend (server api to handle requests). Each of these needs a host to run on.
    - The front end needs a host to read the html,css,js and render it
    - The back end needs a host to read the backend node and listen for requests
  - This means in development (and deployment), we need **TWO** separate hosts.
  - FRONTEND: Typically for create react app, `npm run start` will trigger the front end to start, and will be hosted on localhost:3000
  - BACKEND: For express, we will have specified a port, usually 5000. Then when we execute the server entry point file, `node ./server/index.js` or `nodemon ./server/index.js`. This will run the server, hosted on localhost:5000.

  - At this point,

    - localhost:3000 is hosting the front end
    - localhost:5000 is hosting the backend

  - Typically our front end will make calls to the backend, to CRUD data. This means we want to have our front end call to **where** the backend is hosted. This means `axios.get(http://localhost:5000/api/owners)`. We need the `http://` protocol in front.
  - When we deploy, we will need to change these axios calls to the deployed web service url.

#### **Deploying on Render**

**DATABASE: connecting to postgres**

- A database needs to live somewhere.
- Render (the platform as a service) website features a hosted postgres database. After creating a postgres database on Render, it will be accessable by a URL. This URL is a secret.

  - In the same way we had the localhost as the connection URL for sequelize i our backend to connect to `postgres://localhost:5432/${DATABASE_NAME}`
  - Render provides a connection URL for the database.

- However, if we are also using Render to host (we are) our backend (as a web service), we should use Render's web service environment variables. So, don't do anything with the secret database url key yet.

**DATABASE: checking connection**

- We may want to check that the Render postgres database is able to be connected to and is working. And may want to use something like postbird to check that.
  - However, in the case of postbird, it won't accept the render url by itself. It wants ssl security. To do that just append `ssl=true` to the end of the database url
  - `postgres://user:pass@host:port/database?ssl=true`

**BACKEND: Hosting the server aka web service**

- The server (api) that handles and listens for requests needs to live and be on somewhere. It is also called a web service.
- On Render, it asks for two things a build command and start command. Render acts like how we were running commands before our localhost was able run the server. It needs libraries, the entry point for the app. It works the same way, so we need to let it know what commands to run.
  - Build command, typically `npm install`
  - Start command, whatever the server entry point is `node server/index.js`

**BACKEND: Deployed enviroment variables**

- Just like how the local machine has environment variables, the hosting platform can hold environment variables for the hosted server application to access.
- This is where we grab the database connection secret url and input it into Render's platform.
- Just like local .env, we make a variable key and enter the secret url.
- Then, when the deployed application runs, it searches the environment of the hosting platform, in this case, Render. And will be able to access the environment variable we input. Using the same syntax `process.env.VARIABLE_NAME`

**Deploy Cache**

- Sometimes, we need to deploy with the option that says to delete the build cache to see updates on the live site. Not sure if this is 100% true.

**FRONTEND**

- Similarly to the web service, Render will ask for two things. Build command, and publish directory.
  - Build Command, just like regular `npm run build`
  - Publish Directory, we know our production build is in the build folder. `./build`

[⬆️ Back To Contents](#-contents)


## Journal 15 Feb 2023
Takehome assessment - P

- Code sandbox
  
  First experience with code sandbox. It's a good streamlined tool for development. Default settings are comfortable. Installing dependencies is really easy to do.

- MUI
  
  First time using MUI. A highly opinionated component library. Unless using the totally stock stylings, its tricky to work with MUI before even know what the default styling will look like. Then customizing it is a challenging as the docs are mysteriously scant on the details given how big material UI is in the current design paradigm.

  - Popover
    
    I learned there are lots of different types of pop, not just popup. For the task of having a card appear upon table row click, I chose popover as the method. That ended up being challenging to work with positioning later. I didn't know any better at the time. Popover is designed for tooltips.
  - Typeography, Chip, Rating, Table
    Working with these components were more straightforward. Pretty much plug and play. Very useful.

- react-chart-js-2, bar charts
  
  First time using react-chart-js-2. This chart library is helpful but also more challenging to work with. The rev history on major version change on this library moves fast, and thus a lot of old breaking syntax is still floating around. That made charts hard to work with, as the docs are also very scant on detailed examples. Why do they do this? Make a whole library and provide just one simple example.

- json data parsing, for UI
  
  Data parsing is kinda fun. I think the best part, seeing what data is available, and thinking about how to present it. Then think about how to manipulate that data to get it in a format that will feed into the presentation. +1

- UI styling
  
  UI styling isn't second nature to me yet, so it was difficult to come up with a design on the spot. I don't have institutional knowledge of design practices to just make it up as I go along. I'll have to dedicate time to learning the basic implemented design patterns for a heuristic check.

![Card 1](./assets/15Feb2023_p_takehome1.png)
![Card 2](./assets/15Feb2023_p_takehome2.png)

[⬆️ Back To Contents](#-contents)



## Journal 14 Feb 2023
Service migration

Made my first service migration from Panelbear to Cronitor. Panelbear was aquired by Cronitor and is suspending it's service, to be replaced by Cronitor. 


In this case, migration was a simple 2 liner change. I'd guess things like this are where developer knowledge and experience with a codebase is key. It would have been a non-trivial task to migrate a service, without originally having done it myself.

[⬆️ Back To Contents](#-contents)

## Project NPS stamps

**Date:** 02/02/2023  
**Description:** Finds national park service passport stamps.   
**Link:** [https://kevin-lambda.github.io/nat-park-stamps/](https://kevin-lambda.github.io/nat-park-stamps/)    
**Notable Technologies:** [NPS API](https://www.nps.gov/subjects/developer/api-documentation.htm), [pico](https://picocss.com/) minimalist css framework.  
**Learning focus:** Using an api on the front end and implementing a css framework.

Finds national park passport stamps for you based on your state. Due to the implementation of the API, returned data for a state includes parks, trails, places that can span across the entire US. Thus data filtering was required to show the most relevant information. The API is also not the most accurate source of data for the stamp locations. That can be found [here](https://americasnationalparks.org/passport-to-your-national-parks/passport-cancellation-locations/)

#### Dev learnings
**Reviewed:** api data handling, import, useEffect dependencies, react forms, fetch.then.catch, JSON data parsing, api url syntax, html tables

**To look into:** async promises interaction with state and non state variables, how to make multiple calls to api within the same render cycle for fetched data

**API access:** 

- Getting a CORS allowed API, since this is a front end, client side application (aka did not set up a backend server with routes and databases to store data), will need a CORS allowed API for easiest integration.
- Getting an API key, just signed up, gave a purpose of use and got an api key immediately
- Testing calls to api: It was useful to use the api key and make queries to the api to check json data format and the syntax of how to access the api
- Before making any commits with the API key, stored it as an environment variable file, using this [method](https://dev.to/anuradhasivasubramanian/5-things-to-remember-when-using-an-env-file-to-store-you-api-key-in-a-react-app-4f2o). 
    - Note. This method is not super secure, the key can still be found. For better security, the api key should be in a backend.


**API code integration:** 

- To call the API, I used async await try catch axios. There are other methods such as fetch .then .catch. async await try catch axios seems to be a good modern approach.
- Implementation
    - `npm i axios`
    - `import axios from “axios”`
    - Create an async function. 
    ```
    const getData = async () => {
    }
    ```
    - Create a try catch block
    ```
    const getData = async () => {
        try {
        } catch (error) {
            console.log("error in axios get nps: ", error)
        }
    }
    ```
    - Call the api url in an await axios.get(URL)
    ```
    const getData = async () => {
        try {
            const fetchedData = await axios.get(`${API_NPS_URL}`)
        } catch (error) {
            console.log("error in axios get nps: ", error)
        }
     }
    ```
    - Still within the try block Parse the return data as needed, and set it to a state variable. It seems to be not ideal to set promise type returns to a normal non state variable if it needs to be parsed or processed. It’s hard to get that variable out the of async function without promise sync clashes.
    ```
    const getData = async () => {
        try {
            const fetchedData = await axios.get(`${API_NPS_URL}`)
            parseStampData(fetchedData)
        } catch (error) {
            console.log("error in axios get nps: ", error)
        }
    }
    ```
    - Call that async function in a useEffect
        - To call api only on first render leave the dependency array empty.
        - To call api based on change, put a STATE type variable in the array.
    ```
    useEffect(() => {
        getData()
    }, [])
    ```
    ```
    useEffect(() => {
        getData()
    }, [userState, checkBoxFlag])
    ```

**API code integration:** Aside from integrating the api call, parsing the return data was the most work. I ended up creating a bunch of new state data to manage it all. Messy. Could be written better.

**Pico css:** Pico css is a minimalist, highly opinionated css framework. It comes with predefined css styles that apply to html tags automatically. Default styles can be customized or overwritten.
- To implement: `npm i @picocss/pico` then `import "@picocss/pico"` at the APP level of the application. Where the routes are, before attaching to the html root element.
- How to use: Once integrated, just write html like normal and css styles will work.
- To customize: You can customize the themes that pico comes with. I don't know how to do this. Alternatively, you can overwrite or add on to styles by writing css like normal.
    - Have a style.css in the public folder
    - link that css file in the html header like normal `<link rel="stylesheet" href="%PUBLIC_URL%/style.css" />`
    - Give your target html classes, ids, etc. Then write css in your css file. Styles in your css will overwrite/add to the existing css from pico.

**Github pages deploy notes, once more:**
- `npm i gh-pages`
- In package.json, have `"homepage": "https://GITHUB_USER_NAME.github.io/REPO_NAME",` and the scripts `"predeploy": "npm run build",    "deploy": "gh-pages -d build",`
- Make sure the repo on github is not private
- `npm run deploy`


**ISSUE - Multiple Calls to API within the same render cycle:** 
- An extension I tried was to call the api again to get additional data on the items from the first call. This became an issue when trying to run it all in one render cycle. 
- Also, running an api call on each item from the first api call sounds like O(n<sup>2</sup>). - Implications include calling api magnitude 10 times per page load. Probably not good.

[⬆️ Back To Contents](#-contents)

## Journal 27 Jan 2023
2.75/3 of a project is figuring out how to connect technologies together. This is the least fun.

- First project put on indefinite hiatus. Was trying to use an api to grab an image and then create a color palette from that image using another api.
- Ran into MANY roadblocks
    - Trying to connect to an api from the frontend can cause CORS erros. Which apparently react components constitutes the front end.
        - CORS errors is a browser based technology and is when one domain is trying to access resources from another domain. Domains trying to access data is a front end thing. 
        - There are a ton of suggestions to solve this. I've found that are mainly two that seem "reasonable". 1. Use a proxy service, which routes your domain asking for data to something else that pretends to be a server. api and cors are apparently fine with server to server interactions. However, this is not a robust solution, but it __can be__ a quick temporary solution. You just put another domain in front of the URL you are trying to connect to. 2. Create a backend server to connect to the api to use it there. This sounds like a lot of work just to grab a random image of coffee.
    - Trying to use fs in the frontend. It seems like it was not meant to be used there. Work arounds seem janky. It looks like it is best to use it in the backend.
    - Trying to use fs in the backend and then trying to run a build. An error something about polyfill... didn't look into that. Related to webpack most likely

Was able to run image quantization, connect to image api, connect to palette api. But couldn't link everything together.

[⬆️ Back To Contents](#-contents)

## Project Dakine Ipsum

**Date:** 01/19/2023  
**Description:** Ipsum Lorem generator using context free grammar with Hawaii Creole English (Hawaiian pidgin)  
**Link:** [https://kevin-lambda.github.io/dakine-ipsum/](https://kevin-lambda.github.io/dakine-ipsum/)  
**Notable Technologies:** [Tracery](https://github.com/galaxykate/tracery) CFG generator, [spa-github-pages](https://github.com/rafgraph/spa-github-pages) script method, [Tracery to nodejs](https://github.com/v21/tracery) port  
**Learning focus:** Using a cfg library implemented with react features.

#### Dev learnings
**Reviewed:** useState, map, passing props, form, input, sumbit, handle event, ternary operator  

**To look into:** spread operator, named/default import/export and require

**CRA single page app with react router on github pages:** Single page apps, or a react app using react router will not work with github pages by default. Something about server vs client side path/file/rendering.

Github pages will have trouble finding the correct paths for files to run. You'll need to do a hacky workaround using the 404.html reroute method as explained in 
[spa-github-pages](https://github.com/rafgraph/spa-github-pages). To get my build to work, my steps were
 - Copy the 404.html from [spa-github-pages](https://github.com/rafgraph/spa-github-pages) and put into the public folder, where index.html also lives.
   - If the repo is using github pages domain, such as  `https://<github-username-here>.github.io/dakine-ipsum/`, then you need to change pathSegmentsToKeep to 1 ` var pathSegmentsToKeep = 1`.
 - If using BrowserRouter, you need to add the basename property with your project repo like so `<BrowserRouter basename="/project-repo-name" />`. This should tell your app what the base domain is. So in your js, all your routes that are `"/"` & `"/some-path"` will become in production `"/project-repo-name/"` & `"/project-repo-name/some-path"`, which is what github pages will expect and look for.
 - Copy the [redirect](https://github.com/rafgraph/spa-github-pages/blob/gh-pages/index.html#L21-L42) script from [spa-github-pages](https://github.com/rafgraph/spa-github-pages) and put into index.html. I put mines in the head tag and it seems to work there.
 - I also added a script tag to the body of my index.html `<script src="/<your-repo-name>/build/bundle.js"></script>`

- Troubleshooting: You might find your styles are not loading. make sure you have in your index.html paths with %PUBLIC_URL% to your public files. `<link rel="icon" href="%PUBLIC_URL%/favicon.ico" />`

**CFG generation:** Following the Tracery library documentation and examples were logical to creating a CFG. These were the main takeaways
- Gathering all the word and parsing the data took the most work
- I organized the grammar rules into three categories. 1. Single words or phrases. 2. Grammar structure phrases. 3. Origin phrases.

```
// Single
  In: ["wit", "on", "fo", "wen", "down", "off"], //preposition
  Ar: ["da", "wan", "da kine"], // article
  Ph: ["can handle?", "howzit?", "k den", "like beef?", "moke action"], //phrase
  
// Structure phrases
  // non terminal
  NP: ["#Ar# #Nn#", "#Ar# #Aj# #Nn#", "#Nn#"],
  VP: ["#V# #NP#", "#V# #PP#"],
  PP: ["#In# #NP#"],
  SP: ["#Ph#.", "#Ex#"],
  
// origin
  S: [
    "#NP# #VP#.",
    "#NP# #VP#.",
    "#NP# #VP#.",
    "#NP# #VP#.",
    "#NP# #VP#.",
    "#SP#",
  ],
```

**Named import/export, default import/export and require:** Still looking into how _exactly_ these all work.

[⬆️ Back To Contents](#-contents)

## Journal 16 Jan 2023
- 1/3 of a project is figuring out how to connect technologies together. This is the least fun.
- 1/3 is actually planning outline and coding. This is fun.
- 1/3 is fixing everything. This is the most challenging, and then most rewarding.

[⬆️ Back To Contents](#-contents)

## Project Portfolio v2
**Date:** 01/19/2023  
**Description:** Portfolio version two, software engineering focused.  
**Link:** [https://kevin-lambda.github.io/](https://kevin-lambda.github.io/)  
**Notable Technologies:** React via npx create-react-app, gh-pages  
**Learning focus:** Using the bare minimum to refresh knowledge on the foundational basics of javascript, html, css.


#### Dev learnings
**Reviewed:** All the basics of javascript, html, css  

**Create React App and Github Pages <sub>[1]</sub>:** To host a react app via create react app (CRA) on github pages, one easy way is to use npm gh-pages. This is needed because github pages is searching for the index.html to load at the root level. CRA structure does not work that way. 
- **CRA:** By default the index.html is in the public folder, which should **contain all** files that index.html uses. such as favicon.ico and style.css.
    ```
    <link rel="icon" href="/favicon.ico" />
    <link rel="stylesheet" href="/style.css" />
    ```
 - All the other files, components etc should be in the `src` folder
 - To deploy an app you need to `npm run build`. When CRA `builds` for production, it takes all needed files and puts it into a `build` folder. This is the folder that is read, executed, run in production.
 - During the build process, CRA takes all the src js files and "bundles" it into one js file. It takes that bundle file and inserts a `<script>` tag into the index.html. That is how all the bundled js is run.
 - Now we have a build version of the app, and want to deploy it on github pages. However, as mentioned above, github pages is looking for the index.html in the root directory.  But our production index.html is in the build folder.
- **Github pages:** Following the [gh-pages github](https://github.com/gitname/react-gh-pages) repo instructions, these were the steps I took to use gh-pages. Which enables CRA to deploy on github pages. 
 - Added `"homepage": "https://<github-username-here>.github.io"` to the top level `package.json` object. This seems to tell the app that any paths defined as `/` will use the `homepage` value as it's base.
     - The above works for non regular repo projects. If it is a regular repo, instead add ` "homepage": "https://GITHUB_USERNAME_HERE.github.io/REPO_NAME_HERE",`
 - Added deployment scripts  `"predeploy": "npm run build", "deploy": "gh-pages -d build"`to `package.json`.
 - Deploy site to github pages & push a gh-pages build version to a gh-pages branch with `npm run deploy`. This command does two things. 
 - One, pushes a special configured version of the CRA build folder to a gh-pages branch (it creates the branch if it does not already exist). This special branch puts, from the CRA production build, the index.html (and other public files) into the root directory. This allows github pages to correctly find and read the files to deploy.
 - Two, it reads the special gh-pages branch, and deploys the site to github pages. This can take a few minutes and you will see a ✔️ next to the commit log once the deploy is successful.

**Troubleshooting:** Here were some fixes to errors
- You see html and content but no styling. Check the css file path in your index.html
- You updated your site and don't see changes after deploy. Try deleting your browser cache.
    
**Asset organization:** When there are a lot of assets, such as images, it can quickly get unorganized. Here is an organization method using an index and an IMAGES object.
- Put all assets into a folder. Make an index.js. Do all the seprate imports in this index.js, such as `import logo from "./logo.jpg"`
- Create an object `const IMAGES = {}`
- Put all the imports into the object `const IMAGES = {logo, profile_pic, code, lightbulb, linkedin, github}`
- Export that object as default `export default IMAGES`
- To use those assets in a different file, `import IMAGES from "<filepath>/assets/index.js"`
- Then get an asset by calling the object key `IMAGES.logo`


#### Flagnotes
[1] If using react router or making a single page application, these steps alone will NOT work. See [Dakine Ipsum Project](#project-dakine-ipsum)  

[⬆️ Back To Contents](#-contents)
