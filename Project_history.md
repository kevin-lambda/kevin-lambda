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

### Misc Journal
1. [Jan 16 2023: Starting Again](#journal-16-jan-2023)
1. [Jan 27 2023: 2.75/3](#journal-27-jan-2023)
1. [Feb 14 2023: First Migration](#journal-14-feb-2023)

### Tech and skills used
- Jan 16 2023 ; Basic html, css, javascript ; [Portfolio Version 2](#project-portfolio-v2)
- Jan 20 2023 ; CFG generation, React ; [Dakine Ipsum Project](#project-dakine-ipsum)  
- Jan 27 2023 ; api, fs, require, image quantization ; [Project Retired. Jan 27 2023: 2.75/3](#journal-27-jan-2023)

# 📖 ENTRIES

## Journal 14 Feb 2023
Service migration

Made my first service migration from Panelbear to Cronitor. Panelbear was aquired by Cronitor and is suspending it's service, to be replaced by Cronitor. 


In this case, migration was a simple 2 liner change. I'd guess things like this are where developer knowledge and experience with a codebase is key. It would have been a non-trivial task to migrate a service, without having done it myself.

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
