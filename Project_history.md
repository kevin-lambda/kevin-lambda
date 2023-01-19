# Project list and history

## 
misc dev journal 1/16/2023
- 1/3 of a project is figuring out how to connect technologies together
- 1/3 is actually planning outline and coding
- 1/3 is fixing everything


## dakine ipsum
issues getting cra spa working on github pages
- gh pages doesn't work with browserrouter -> routes -> route ==> single page application
- make sure index.html, which may be searching for files has correct file paths. any thing with link href tags. for files in /public, use %PUBLIC_URL%/file.extension. HINT if this is your error is if css is not loading opnce deployed on gh pages.
- need to add homepage definition in package json, and predeploy, deploy scripts.
- need to add a base subdomain to Router tag. basename="/subdomainName". aka https://mainDomain.com/subdomainName


- needed this: https://github.com/rafgraph/spa-github-pages to allow spa on gh pages
- my config.
- copied 404.html to public
- b/c this is a project repo, and not a user account repo. set pathSegmentsToKeep = 1
- copied the index.html script to my index.html. I put it in the head tag. I think it would work in the body too.
- added  <script src="/dakine-ipsum/build/bundle.js"></script> to the body, where dakine-ipsum is the repo name


note
-  cra builds from the build folder. upon production build, all the js is bundled, then the index.html includes a script tag to read that bundled js file


<!---
Title: xxxxxxxxx
Date: xx/xx/xxxx
Technology: xxxxxxxx
Description: xxxxxxxxxxxx
Takeaways: xxxxxxxxxxxx
Link: xxxxxxxxxxxxxxxxx
--->

