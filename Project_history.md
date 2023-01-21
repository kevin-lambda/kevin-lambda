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
======================================================================
## Journal 1/16/2023 
- a
--->

# Dev diary

## 📚 CONTENTS

### Projects
1. [Portfolio Version 2](#project-portfolio-v2)  
1. [Dakine Ipsum Project](#project-dakine-ipsum)  

### Misc Journal
1. [Jan 16 2023: Starting Again](#journal-16-jan-2023)
1. [placeholder](#journal-16jan2023)
1. [placeholder](#journal-16jan2023)

### Tech and skills used
- Jan 16 2023 ; Basic html, css, javascript ; [Portfolio Version 2](#project-portfolio-v2)
- Jan 20 2023 ; CFG generation, React : [Dakine Ipsum Project](#project-dakine-ipsum)  

## 📖 ENTRIES

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

## Journal 16 Jan 2023
- 1/3 of a project is figuring out how to connect technologies together. This is the least fun.
- 1/3 is actually planning outline and coding. This is fun.
- 1/3 is fixing everything. This is the most challenging, and then most rewarding.


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
 - Added deployment scripts  `"predeploy": "npm run build"` and `"deploy": "gh-pages -d build"`to `package.json`.
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
[1] If using react router or making a single page application, these steps alone will NOT work. See [Dakine Ipsum Project](#dakine-ipsum)
