# 📚 CONTENTS

This is a journal of my projects, lessons learned and thoughts during my coding journey.

### Projects

1. [Portfolio Version 2](#project-portfolio-v2)
1. [Dakine Ipsum Project](#project-dakine-ipsum)
1. [NPS Stamps](#project-nps-stamps)
1. [This Page Belongs To](#this-page-belongs-to)
1. [npm @kevin-lambda/kindly](#npm-kindly)
1. [next CRUD](#next-crud)
1. [Bowlerator](#bowlerator)
1. [How old am I](#how-old-am-i)
1. [Solari](#solari)
1. [Bit bot](#bit-bot)
1. [Cash Stack](#cash-stack)

### Tech and skills used

Jan 16 2023 ; Basic html, css, javascript ; [Portfolio Version 2](#project-portfolio-v2)  
Jan 20 2023 ; CFG generation, React ; [Dakine Ipsum Project](#project-dakine-ipsum)  
Jan 27 2023 ; api, fs, require, image quantization ; [Project Retired. Jan 27 2023: 2.75/3](#journal-27-jan-2023)  
Feb 02 2023 ; api CORS, pico css ; [NPS Stamps](#project-nps-stamps)  
Feb 14 2023 ; Panelbear, Cronitor RUM ; [Feb 14 2023: First Migration](#journal-14-feb-2023)  
Feb 15 2023 ; code sandbox, MUI, react-chart-js-2 ; [Feb 15 2023: First Takehome](#journal-15-feb-2023)  
Feb 25 2023 ; PERN (postgresql, express, react, nodejs) stack, Render PaaS ; [This Page Belongs To](#this-page-belongs-to)  
Mar 08 2023 ; npm package publishing ; [npm @kevin-lambda/kindly](#npm-kindly)  
Apr 12 2023 ; Nextjs, Prisma ORM, Bulma css, Typescript, Vercel ; [next CRUD](#next-crud)  
Apr 14 2023 ; Layout design, Nextjs ; [Bowlerator](#bowlerator)  
Apr 20 2023 ; Routine website build and deployment, sass ; [How old am I](#how-old-am-i)  
May 01 2023 ; Java, intelliJ IDEA ; [May 01 2023: Mocha JAVA latte](#journal-01-may-2023)  
May 17 2023 ; recharts, Bulk data analysis ; [Solari](#solari)  
Jun 19 2023 ; Open AI chatgpt-3.5-turbo, NextJS, Bulma ; [Bit Bot](#bit-bot)  
Jun 29 2023 ; cheerio, jQuery, NextJS, Bulma, recharts; [Cash Stack](#cash-stack)

### Articles Published

Mar 13 2023 - [Medium: Jr dev asks — Why would I want to publish a personal npm package](https://kevin-lambda.medium.com/jr-dev-asks-why-would-i-want-to-publish-a-personal-npm-package-8d27afd42ca5)  
Mar 23 2023 - [Medium: Jr Dev asks — What’s a basic layout design to use for a business website?](https://kevin-lambda.medium.com/jr-dev-asks-whats-a-basic-website-layout-to-use-for-a-business-35ff4a7ef700)  
Mar 23 2023 - [Medium: Jr Dev asks — What do you put on websites? The who, what and why framework.](https://kevin-lambda.medium.com/jr-dev-asks-what-do-you-put-on-websites-the-who-what-and-why-framework-c045fb1e31b2)  
Apr 22 2023 - [Medium: Jr Dev asks — How to use custom Bulma variables with sass in Next.js 13.](https://kevin-lambda.medium.com/jr-dev-asks-how-to-use-custom-bulma-variables-with-sass-in-next-js-13-830604c717d5)

### Journal

[Jan 16 2023: Starting Again](#journal-16-jan-2023)  
[Jan 27 2023: 2.75/3](#journal-27-jan-2023)  
[Feb 14 2023: First Migration](#journal-14-feb-2023)  
[Feb 15 2023: First Takehome](#journal-15-feb-2023)  
[Feb 26 2023: A search history](#journal-26-feb-2023)  
[Mar 13 2023: Does it scale?](#journal-13-mar-2023)  
[Mar 21 2023: UX/UI Don't make me think! A basic business page](#journal-21-mar-2023)  
[Mar 31 2023: Two things at once, three times as slow](#journal-31-mar-2023)  
[Apr 07 2023: Don't use it like that!](#journal-07-apr-2023)  
[May 01 2023: Mocha JAVA latte](#journal-01-may-2023)  
[May 06 2023: CRUD Linked Lists](#journal-06-may-2023)  
[May 11 2023: psql reminder](#journal-11-may-2023)  
[Jun 04 2023: React basics](#journal-04-jun-2023)  
[Jun 12 2023: Rusty](#journal-12-jun-2023)  
[Jul 06 2023: Crud repeat](#journal-06-jul-2023)

# 📖 ENTRIES

## Journal 06 Jul 2023

### Crud repeat

I'm doing a fullstack CRUD app over and over until I build muscle memory.
Built with

- Database: Postgres
- ORM: Prisma
- Framework: Nextjs (React, Typescript)
- CSS: Tailwind

#### Medium level checklist

0.0 INSTALL AND SETUP
[] Start project: npx create-next-app@latest
[] Install Dependencies: prisma, @prisma/client, ts-node
[] Generate prisma files: npx prisma init

0.1 CONFIGURATION POSTGRES DATABASE
[] Create Database Method 1: In terminal, `createdb -h localhost -U postgres -W <database name>`, then enter password. (self note its `postgres`)
[] Create Database Method 2: Login to psql with `psql -h localhost -U postgres -W`, then enter password `postgres`. Then create db with `CREATE DATABASE <database name>`
[] Check database is created in postbird/databse navigator

0.2 CONFIGURATION .env DATABASE URL
[] Include .env in gitignore
[] In the .env, set the Database URL: `DATABASE_URL="postgresql://postgres:postgres@localhost:5432/<database_name>"` . Database url is in the form `postgresql://USER:PASSWORD@HOST:PORT/DATABASE`

0.3 CONFIGURATION PRISMA ORM - SCHEMA
[] Check prisma schema generator client: should be `provider = "prisma-client-js"`
[] Check prisma schema datasource db: should be `provider = "postgresql"` and `url = env("DATABASE_URL")`
[] Define prisma schema models: fieldname - type - attributes. each model should have some primary key (id).

0.4 CONFIGURATION PRISMA ORM - SYNC SCHEMA & GENERATE CLIENT
[] Sync defined schema to database: `npx prisma db push` OR `npx prisma migrate dev --name <message_name_init>`
[] Generate prisma client (load config into prisma, still need to create and import it): `npx prisma generate`
[] Add client generation to package json build script (so it keeps updated on build): `"build": "prisma generate && next build"`

0.5 SEED DATA
[] Make seed file: at `/prisma/seed.ts`
[] Containing: PrismaClient import, new PrismaClient() instance, main function with prisma seed operations, main function call, then disconnect methods. See detailed code.
[] Add seed script to package.json (from docs): as `"prisma": {"seed": "ts-node --compiler-options {\"module\":\"CommonJS\"} prisma/seed.ts"}`
[] Seed script for non-nextjs: `"prisma": {"seed": "ts-node prisma/seed.ts"}`
[] Run seed command: `npx prisma db seed` , check seeded data

0.6 CREATE PRISMA CLIENT INSTANCE
[] Make a folder and prisma file: `/lib/prisma.ts`
[] Containing: PrismaClient import, global aliases, export prisma new PrismaClient, with if condition. See detailed code.

1 BACKEND API WITH PRISMA QUERIES
[] Set up nextjs app directory style api route handler files: `/app/api/<table_name>/route.ts` and probably dynamic route `/app/api/<table_name>/[id]/route.ts`
[] Files include imports: `{prisma} from '@/lib/prisma.ts'` and `{NextResponse} from 'next/server'`
[] Make nextjs style RESTful prisma query route handlers containing: `export async function METHOD(){}` , `await` parse http request (as needed), `await` prisma query, `return NextResponse.json(<RETURN_HERE>)`, within a try catch.

2 FRONTEND EVENT TRIGGERS AND FETCHES
[] Make an async getAll function: await fetch, await parse json, setState
[] Make a useEffect for getAll
[] Make UI forms with `input text onChange setState`, and `button onSubmit handlers`
[] Create UI event handlers with: preventDefault(), await fetch WITH url plus config containing **_method_** and **_JSON.stringify()_** body, probably call getall at the end. All in a try catch.

**PRISMA - SCHEMA MODEL**

- Models are/should be? named with uppercase. `model User{}`
- When referred to from prisma instance, it is in lower case... `prisma.user.create()`
- Each model should have a primary key, usually an id. This is specified by the attribute `@id`. Like this ` id Int @id @default(autoincrement())`

- Name fields: are camelcase, nothing much to note
- Type: Straightforward, though the docs are messy
- Attributes/Functions: Common ones are, `@id` makes this the primary key?, `@default(<value>)` makes this the specified value the default value, `autoincrement()` automatically increments for each row - usually use with @id and @default(), `@unique` checks that each created row will have a unique data, `@relation()` creates model relations see next point

- Relations: for an example Task model with User owners, `owner User @relation(fields:[ownerId], references:[id])`

  - !! the form is: `relation_name Captialized_Model_Name_To_Relate @relation(fields:[currentModelKeyToUse], references:[otherModelKeyToMatchTo])`
  - !! on the other model, there MUST be a matching relation in the form: `relation_name MatchingModel[]`

  - fields: the key to read on the **_CURRENT_** model
  - references: the key to find and match on the **_OTHER_** model

```prisma
model User {
  id Int @id @default(autoincrement())
  email String @unique
  task Task[]
}

model Task{
  id Int @id @default(autoincrement())
  taskText String
  owner User @relation(fields:[ownerId], references:[id])
  ownerId Int
}
```

**PRISMA - SCHEMA SYNCING AND GENERATING CLIENT**

- In syncing schema,
  - `push` is a quick way to sync the database with the schema. It doesn't have a lot of control, like making sure no data is lost, or renaming columns, track changes.
  - `migrate` syncs the database WITH ability to fine tune the syncing AND creates a migration file. Which... tracks or configs things?
- In generating client, must be done anytime there is a change to schema. Prisma doesn't automatically "intake" the schema definition on save. Client must be generated to absorb the changes.

**PRISMA - SEED DATA FILE**

```ts
import { PrismaClient } from "@prisma/client"

const prisma = new PrismaClient()

// prisma data create here
const userSeed = [
  { email: "apple@a.com" },
  { email: "banana@a.com" },
  { email: "carrot@a.com" },
]

const seedData = { userSeed }

async function seedDb(seedData) {
  const users = await prisma.user.createMany({
    data: seedData.userSeed,
  })
  console.log({ users })
}

seedDb(seedData)
  .then(() => prisma.$disconnect())
  .catch(async (e) => {
    console.error(e)
    await prisma.$disconnect()
    process.exit()
  })
```

**PRISMA - CLIENT INSTANCE FILE**

- Need to do this extra global stuff to work with nextjs properly. To only open up one instance.

```ts
import { PrismaClient } from "@prisma/client"
const globalForPrisma = globalThis as unknown as {
  prisma: PrismaClient | undefined
}
export const prisma = globalForPrisma.prisma ?? new PrismaClient()
if (process.env.NODE_ENV !== "production") {
  globalForPrisma.prisma = prisma
}
```

**BACKEND - API PRISMA ROUTES**

- DO NOT USE THE REQUEST ARG IN DELETE METHOD. current nextjs issue
- DO NOT USE THE REQUEST ARG IN DELETE METHOD. current nextjs issue
- DO NOT USE THE REQUEST ARG IN DELETE METHOD. current nextjs issue
- Remember
  - `async function METHOD(request, {params})`
  - `await request.json()`
  - `await prisma.model.query()`
  - `NextResponse.json()`
  - `parseInt(params.id)`
- typical prisma queries
  - get one: `findUnique({where:{id:<value>},include:{}})`
    - where matches to, include brings in relation data
  - get all: `findMany()`
  - create: `create({data: <value> })`
  - delete: `delete({where:{id:<value>}})`
  - update: `update({where:{id:<value>}, data:<value>})`

**FRONTEND - UI EVENTS AND HANDLERS**

- Remember

  - event triggers onSubmit, onChange: never set an invoked function. Only function definitions.

    - ✔️ `onSubmit={handleSubmit}`
    - ✔️ `onSubmit={(event)=>{return handleSubmit(event,id)}}`
    - ✔️ `onChange={(event) => setUpdateInput(event.target.value)}`

    - ❌ `onSubmit={handleSubmit(event,id)}`

  - handlers
    - fetch body MUST BE `JSON.stringify(<data>)`

**MISC**

- Just leave the frontend api fetches in the same location as the data consuming component. Tried to modularize them, but separating the fetches from the data caused hydration issues. KISS.

[⬆️ Back To Contents](#-contents)

<br><br>

## Cash Stack

**Date:** 06/29/2023  
**Description:** This project compares what thing is taller; the height of a thing or the cost of it stacked as $1 bills.  
**Link:** n/a  
**Notable Technologies:** cheerio, jQuery, NextJS, Bulma, recharts  
**Learning focus:** Learn how to use jQuery to query HTML DOM for data

I heard about querying websites for data in a programmatic way, and wanted to try it out. That lead me to jQuery and cheerio. I combined this with an old idea I had for comparing the physical height of a thing to its price stacked as $1 bills.

#### **Reviewed:**

recharts, jQuery, cheerio, api endpoints, data parsing, bulma, awesome font

#### **To look into:**

Headless browser like Puppeteer

<img src="./assets/29jun2023cover.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 50%;">

### Dev learnings ========================================================

#### **jQuery**

- jQuery is a way to select elements from a HTML DOM. It pretty much uses css selectors to choose things.

- first the data from a website needs to get fetched, then the data loaded as a jQuery type object(?)

```js
const { data } = await axios.get(inputUrl)
const $ = cheerio.load(data)
```

- There are nuances to how to query. Kinda like an art. Sometimes an element is specific enough that we can just query it directly. Sometimes we need to chain a bunch of descendants or children elements.
  - Othertimes, we can go into the element's data after a query to further select things.
- the return from jQuery is a special array or object type.
  - the array will return all the matches from the query
  - the object has a lot of things, including parent, child, sibling elements. also any kind of data that element might have.
- usually, we want the text from an element.
- here are some examples of queries

```js
const price1 = $("div.statsValue > span").text()
const price2raw = $("div.statsValue")
const price2 = price2raw[0].children[0].data
const address = $("div.street-address").text()
const state = $("div.dp-subtext.bp-cityStateZip").text()
const lotSizeRaw = $("div.table-row > span.table-label:contains(Lot Size)")
const lotSize = lotSizeRaw[0].next.children[0].data
```

Overall, it can be a way to fetch data from a website.

#### **Nextjs env variables**

- There are TWO kinds of env variables in nextjs.
  - The BACKEND server, route handlers
  - The browser FRONTEND client side
- In `.env.local` file in the root directory
  - backend env variables: `XYZ_ANYTHING=justPutTheCharactersNoQuotes`
  - for browser frontend side: `NEXT_PUBLIC_XYZ_ANYTHING=abcdefg`

#### **querying data as local vs deployed**

- warning. if you try to query websites that you do not own, this may be against the terms of service for those websites.
  - It's possible for the website to detect querying in this way and deny the data fetch.
- This can happen first at the local dev level or at the deployed level. The closer you get to a deployed function, the more likely you will be denied.

[⬆️ Back To Contents](#-contents)

<br><br>

## Bit bot

**Date:** 06/19/2023  
**Description:** This project is a proof of concept exploring a user interaction based context AI chatbot.  
**Link:** n/a  
**Notable Technologies:** Open AI chatgpt-3.5-turbo, NextJS, Bulma  
**Learning focus:** Use an ai chat bot in a novel way.

The goal was to use an ai chatbot in a new method. As some of the options, this project showcases ui elements including button click, hover, menu change. The ai will respond to each action and the context of the action. This type of ai chatbot application could be described as an interaction context sensitive ai chatbot. This opens a new aspect of user experience as the user interacts with the ui. Receiving feedback during the ui interactions. Instead of interaction strictly through text chat input.

This web app will be disabled by default and in a debug mode. Demo available by request.

#### **Reviewed:**

Open AI api - chatgpt-3.5-turbo, Prompt Engineering, Nextjs 13, Bulma css, api route handling, interaction handlers, deploying env variables

#### **To look into:**

Response text streaming, further model fine tuning, input chat option

<img src="./assets/20jun2023p2.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 50%;">
<img src="./assets/20jun2023p3.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 50%;">

### Dev learnings ========================================================

#### **Prompt engineering**

Several prompt iterations were tested. One notable finding was strongly delineated prompt parameters (via colon per parameter) caused the responses to mirror that and also become delinated. Which broke the natural language effect of the responses. There was more successing in using natural language in the prompt to get a return of natural language.

- prompt_char1 was very robotic and kept prefacing its answers with user: does action. bot: responds. It also kept playing out the entire scenario with multiple back and forths.
- prompt_char2 is much more conversational. Not as conversational as chatgpt as time of writing, but much closer. It seems chatgpt-3.5-turbo tries to mimic that initial prompt.

- Takeaway, prompt as how we want the model to respond.

```js
const prompt_char1 = `Consider the entire scenario. Then respond to the action, remarking as the count increases.

  You are a friendly creature hungry for data. The user interacts with the website ui to feed you. 
  For each interaction, your response will consider the counter, action type and effect.

    counter: ${count}, counter is the number of times a user repeats action type. 
    user action:  ${action}, user action is the interaction type
    action property: ${effect}, action property is the effect of the action`
```

```js
const prompt_char2 = `
  Assume the role of a website named bit bot that is hungry to be fed data by the user.

  This is the ui that the user can interact with. Button click to feed you, drop down menu to choose data feed type (bit, nibble, or btye), and image hovers of feed type.

  React to the following action: User used ${action} ${count} time and ${effect} 
  `
```

#### **NextJS api route handling**

NextJS has a route handling feature which abstracts parts of the backend api endpoint making process. There are some differences or things to be mindful of as making these.

x.BACKEND

1.  via the **app** directory, any file named `route` will be marked as a route handler file. Whatever folder it is in will behave as the path for the route handler. Probably just make these in `app/api/xyz/route.js`
2.  These route files have **pre-defined patterns**. We make functions to export with names of REST verbs. The functions must(?) be named these REST verbs. Then the predefined functions will come with certain arguments, such as **POST** coming with **request**.

    ```js
    export async function GET() {}
    export async function POST(request) {}
    ```

3.  gotcha 1. for an incoming POST request (which we would expect to be sent as a body), we need to process the request via json, which is an **async** method. This is because requests (I think) come in two parts, the head, then the body. Its not just regular json! The body could be a large file, so the head comes through first. So, we must process the request, and it must be awaited. `const parseRequest = await request.json()`
4.  At this point, `parseRequest` will contain just the "body". We can extract data as needed.
5.  optional. If we want to access an external api, we can do so with `fetch`. Since fetch is async(it could take a long time), we have to `await` it.
6.  optional. To use the fetched data, same thing. We have to process it. Do so with the same `await fetchedData.json()`
7.  To finish the api endpoint, we can have a returning response. In NextJS route handler, the best practice function is called `NextResponse` this is from `import {NextResponse} from 'next/server'`
8.  `NextResponse` can be thought of as a **general response holder**. If we want to respond with json, we have to define it as such. We usually want json response. Note that we don't need to await .json here. That's because this .json is part of NextResponse and isn't(?) processing anything. We're just saying, respond, and it will be json.

        ```js
        return NextResponse.json({ returningText: "returning text stuff" })
        ```

    x. FRONTEND
    To hit the api endpoint from the frontend

9.  Use `fetch` in an async function, with a **METHOD** and **BODY**

    ```js
    const fetchedData = await fetch("http://placeholder.com/api", {
      method: "POST",
      body: JSON.stringify(userContext),
    })
    return fetchedData.json()
    ```

10. We have to `await` the fetch (remember fetch can take a while so it is async). Remember to process the fetch data (remember fetch data needs to be processed, it comes in different parts) not sure why .json() here doesn't need to be awaited....
11. REMEMBER that body NEEDS TO BE **_JSON.stringify()_**.
12. REMEMBER that body NEEDS TO BE **_JSON.stringify()_**.
13. REMEMBER that body NEEDS TO BE **_JSON.stringify()_**.
14. if this fetch is in a helper async function, the helper async function will also need to be awaited.

#### **Open AI api setup**

The basic setup to access the Open ai api has 4 steps.

1. configure "openai" with an api key, have an api key in env variables

   ```js
   const { Configuration, OpenAIApi } = require("openai")

   const configuration = new Configuration({
     apiKey: process.env.OPENAI_API_KEY,
   })
   const openai = new OpenAIApi(configuration)

   export default openai
   ```

2. access openai and initiate a method, such as createChatCompletion
3. configure the completion with at least model and messages, which will return the completion
   ```js
   const completion = await openai.createChatCompletion({
     model: "gpt-3.5-turbo",
     messages: [
       {
         role: "user",
         content: prompt_char2,
       },
     ],
   })
   ```
4. access the completion, likely with `completion.data.choices[0].message.content`

[⬆️ Back To Contents](#-contents)

<br><br>

## Journal 12 Jun 2023

Rusty

Explored Rust recently, and learned about two new concepts that seem applicable to many programming languages.

**memory management**
In javascript, we pretty much didn't worry or think about memory management at all. zero. But in Rust, and I imagine other languages, where and when values are being stored, recalled in memory matters.

Going through Rust made me think about when a value is initialized, and how long its lifetime is valid. When it will go out of scope. What is allowed to access it. Which leads to the next topic of read write (mutability) access.

**mutability**
In Rust, trying to use a variable needs to be intentional. How are we allowed to use this variable? Can we change it? are we the owner of it?
Can we temporarily _borrow_ this variable value without owning it?

I did a brief dive into these topics, and being exposed to these concepts now make me aware of this way of thinking.

[⬆️ Back To Contents](#-contents)

<br><br>

## Journal 04 Jun 2023

### React basics in depth: onClick, useState, onChange

**onClick**

- In react jsx, onClick can be a property on _any_ element. Not just `<button>`.

  ```
  <button onClick={()=>setCount(1)}> reset </button>

  <div    onClick={()=>setCount(1)}> reset </div>

  <p      onClick={()=>setCount(1)}> reset </p>

  ```

- ✔️ **onClick action:** The recommended pattern to define onClick, is to use an inline arrow function, that **RETURNS** a function.  
  The **RETURN** of the onClick defined function will activate on a click. Doing other stuff may cause unexpected behavior, such as triggering on every page render.

  ```
  // probably use these the most
  <div onClick={handleClick}> calls function on click, and that func has access to event (event is automatically passed to the onClick function) </div>
  <div onClick={(arg) => handleClick(arg)}> calls function on click, if we want to send a specific argument, and that func has access to event </div>
  <div onClick={() => setCount((count) => count + 1)}> increment state </div>

  // alternatives
  <div onClick={(event) => handleClick(event)}> sends event to function </div>
  <div onClick={() => setCount(1)}> reset to 1 </div>
  <div onClick={() => {return handleClick(arg)}}> sends arg to function </div>
  <div onClick={() => setCount((count) => {return count + 1})}> increment </div>
  <div onClick={testFunction}> called a function reference, won't run on every render. testFunction has access to event. even though we don't directly pass it.</div>
  ```

- ❌ **onClick action:** Below are ways that can work to define the onClick action, but are not recommended. These may have unintended behavior. Most of these are not returning a function. Which is why they will run on each render.

  ```
  <div onClick={console.log("direct")}> direct statement will run on every render </div>
  <div onClick={function testFunction(event) {console.log("test text"), event}}> won't run on every render, but not a good pattern </div>
  <div onClick={testFunction(arg)}> DANGER. will run on every render, b/c we are now invoking it </div>
  ```

- **onClick event:** the function defining an onClick will get access to `event` object as an argument. This event refers to the element that was clicked.

  - Two useful properties of the event object are event.preventDefault() and event.target

  ```
  <div onClick={(event) => handleClick(event)}> sends event to function </div>

  ////

  function handleClick(event) {
    console.log(event)
  }

  ```

**useState: explicit vs function**
There are two methods to do the setState of useState

1. Setting state to an explicit value (not basing/updating from state).
   ```
   setCount(42)
   ```
2. Setting state that is based from state. When working with state, we should use a function to ensure expected behavior.
   ```
   setCount((count) => {count + 1}) // ✔️ use this
   setCount(count++)                // ❌ not as reliable
   ```

**onChange**
onChange is probably used with just `<input>`. It sometimes goes directly in the input tag type, sometimes it is in a parent tag.

```
// text input
<input type="text" onChange={(event) => setInputText(event.target.value)}></input>
<input type="text" onChange={handleInputChange}></input>

// radio input no form
<div onChange={handleRadioChange}>
  <input type="radio" name="options" value={"option 1"}></input> one
  <input type="radio" name="options" value={"option 2"}></input> two
  <input type="radio" name="options" value={"option 3"}></input> three
</div>

...
function handleRadioChange(event) {
  setRadio(event.target.value)
}

// radio input with form
<form onSubmit={formSubmit}>
  <label>
    <input
      type="radio"
      value={"Blue"}
      checked={radio2 === "Blue"}
      onChange={handleRadioChange2}
    ></input>{" "}
    Blue
  </label>
  <label>
    <input
      type="radio"
      value={"Green"}
      checked={radio2 === "Green"}
      onChange={handleRadioChange2}
    ></input>{" "}
    Green
  </label>
  <label>
    <input
      type="radio"
      value={"Red"}
      checked={radio2 === "Red"}
      onChange={handleRadioChange2}
    ></input>{" "}
    Red
  </label>
</form>

// input select
<div>
  <select value={select} onChange={handleSelect}>
    <option value={"option 1"}>Option 1</option>
    <option value={"option 2"}>Option 2</option>
    <option value={"option 3"}>Option 3</option>
  </select>
</div>
```

**onBlur**
Blur means when the active element is no longer focused on. aka when we click off on if, if it was an input.
When we click off of this input, onBlur is triggered

```
<input
  type="text"
  value={testBlur}
  onChange={(event) => {
    setTestBlur(event.target.value)
  }}
  onBlur={handleBlur}
/>
```

[⬆️ Back To Contents](#-contents)

<br><br>

## Solari

**Date:** 05/17/2023  
**Description:** A solar energy analysis tool modeled with three years of data  
**Link:** [https://solari-kl.vercel.app/](https://solari-kl.vercel.app/)  
**Notable Technologies:** recharts, next.js, bulma css, vercel  
**Learning focus:** Make a tool modeled on actual data presented scientifically

This is a planning tool that simulates energy output of a solar energy project using historical data for 2020 to 2023 based in Inner Sunset neighborhood of San Francisco.

#### **Reviewed:**

Bulk data analysis, nextjs 13, bulma css, recharts, bulk props passing

#### **To look into:**

Ways to organize prop passing, details of setting state between components, understanding more about solar data

#### **Extensions:**

[M] incorporate cost effects of missed energy demand days  
[H] add more detailed variable controls  
[H] find a less specific question to answer

<img src="./assets/17may2023main.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 50%;">
<img src="./assets/19may2023changes.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 50%;">

### Dev learnings ========================================================

#### **Passing state as props**

how to handle changing state from another component using inputs form

For this project I intentionally wanted to work with modular code and passing props. In this case I needed a child input form component to set the state of a parent component.

I did this by sending the setState as a prop to the child component. This works, but I started to need to send a lot of setStates and its on the edge of the point of not scaling well.

<img src="./assets/18may2023props.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 50%;">

Another challenge was that I needed the default values of the inputs to match the parent component state. That means I just ended up passing both the state and setstate for many variables to the child component via props. Then a third complication was I needed a another group of states for the inputs.

This has lead to some unexpected behavior when using the input controls. After this experience, I understand why we would want a better way to do this.

#### **Hardcoding bulk raw data**

The raw data has about 1200 lines of values in an excel file. I did initial parsing into JSON format in excel. I briefly looked for a tool to do this, but it seemed faster just to do it myself.

After parsing in excel, I copied all 1200 lines then tried to paste it into a vscode file. Apparently, there is a character limit for pasting. When pasting, the data just stopped 2/3s of the way. I manually copied the second half the data and pasted again.

I think there must be another way to paste hardcoded bulk data into vscode.

<img src="./assets/18may2023state.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 50%;">

#### **Type errors in data calculations**

This is the first project where I started to run into type errors and javascript "silently failing". Because I was doing a lot of calculations and working with floats and rounding and summing, I started to get mysterious calculation errors.

Math that I know works, was suddenly not working.

Then I saw that methods I was using returned strings instead of numbers. Such as `toFixed()` Even though the console log looked like numbers, it was a string.

I can see why for data calculation intensive projects, a strongly typed language can be useful.

#### **recharts**

recharts is the most intuitive chart library I've used so far.

<img src="./assets/18may2023rechart.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 50%;">

The mental model I understand it with is

- have a data set `array of objects`
- choose a chart type and link it with the data `<BarChart />`
- use child components of that chart to customize the chart `<XAxis/> <Tooltip/>`

The documentation is generally very helpful and clear. I'll probably be using this again.

#### **Solar data**

Before I could present and calculate any solar data, I needed to understand it better.

- Global Horizontal Irradiance (GHI) was one of the fields for the raw data. But there was also Dirent Normal Irradiance (DNI) and Diffuse Horizontal Irradiance (DHI). I learned that DNI and DHI are components of GHI. Therefore to get the total irradiance, the project needed to use GHI.
- Power and Energy are different. Understanding this at a fundamental level was important in doing the correct calculations. Power is at an instant in time. Energy is that power over a period of time.
- The main calculation in the project is solving for energy per day of a solar installation. I used the solar irradiance, applied it to the solar installation area and panel effciency over an estimated 5 hour baseline, then compared that energy to the measured energy data.

[⬆️ Back To Contents](#-contents)

<br><br>

## Journal 11 May 2023

Reminder to get into psql

`psql -h localhost -U postgres -W`  
`postgres`

[⬆️ Back To Contents](#-contents)

<br><br>

## Journal 06 May 2023

CRUD Linked Lists

I built a singlely linked list from scratch with CRUD. It was the most effective way for me to actually get a feel for how linked lists work. Probably this is the same for most data structures. Just build it to understand it the best.

[The spaghetti code for linked list crud](https://github.com/kevin-lambda/crack-code-int/blob/main/linked_lists/create-linked-list.js)

[⬆️ Back To Contents](#-contents)

<br><br>

## Journal 01 May 2023

Mocha JAVA latte

Today I tried a mock work experience program with java. It was from this site [the forage](https://www.theforage.com/). It was a fun experience.

### Thoughts:

#### General

- It was somewhat refreshing to enter a completely new dev environment, where I didn't know how anything worked.
- I got to just poke around, guess and check. See what things did what. It was a fun exploration.
- public static void. whats up with all this boilerplate?

#### Java

- the intelliJ IDEA (IDE) was pretty cool. One big thing I noticed about java or at least the editor. The variables we declare are STRONGLY linked to each other. And you'll know it when at development time. Such as a class method with a double parameter better only be invoked with a double argument. Even in different files. It will know and yell at you.
- Its cool how java specifically defines public vs private. I eventually figured this out. But it's cool the control we can have over what variables are shared and how in front of our face it is. Since we always (?) have to declare public or private
- I haven't worked with classes since ever. It's not too bad. But it does feel like... programming programming. Whereas javascript feels loose and flexible. I can see why big enterprises might want something like java. Bigger product needs more built in checks.

#### theforage

- the program I did was just two tasks, create a class and some tests. It was a good intro to java, but not really helpful in gaining real world experience. I highly doubt that any real ticket is something soooo small. But maybe.
- Felt more like a tutorial assignment than a work experience simulation.
- I expect the longer programs to have more challenging content. Not that this wasn't challenging for me; I'd never used java before.

Overall, I enjoyed it. I'll be back to try the tougher programs.

<img src="./assets/1may2023program.jpg" alt="age"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 30%;">

<img src="./assets/1may2023tests.jpg" alt="age"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 30%;">

[⬆️ Back To Contents](#-contents)

<br><br>

## How old am I

**Date:** 04/20/2023  
**Description:** A novelty website displaying my current age  
**Link:** [https://how-old-is-kql.vercel.app/](https://how-old-is-kql.vercel.app/)  
**Notable Technologies:** next.js, bulma css, vercel  
**Learning focus:** Static website end to end delivery practice

This is a novelty website displaying my age because I always forget my age.

#### **Reviewed:**

Basic website build and deployment process

<img src="./assets/20apr2023.jpg" alt="age"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 50%;">

### Dev learnings ========================================================

#### **How fast could I deliver a simple website **

It took 1 hour, from npx to deploy. It was good practice to get the skill of deploying a simple static page to feel like a routine task.

[⬆️ Back To Contents](#-contents)

<br><br>

## Bowlerator

**Date:** 04/14/2023  
**Description:** A basic small business site with a bowl meal idea generator  
**Link:** [https://bowlerator.vercel.app/](https://bowlerator.vercel.app/)  
**Notable Technologies:** next.js, bulma css, pico css, vercel  
**Learning focus:** Practice basic webpage layout design and copy

This is a mock up exercise for a small business with an app that generates meal bowl ideas.

#### **Reviewed:**

Nextjs routing, next/link, next/image, file organization, globals css with bulma/pico css library interaction, website layout design, copy, hero responsive banner image sizing css, fontawesome

#### **To look into:**

scss, typography, color theory, copy, mobile layout design

#### **Extensions:**

[H+] Logic for good ingredient pairings  
[M] Bowl ingredient amounts  
[M] Bowl cuisine selector  
[L] More ingredients with cuisine labels

<img src="./assets/14mapr2023_coverPage.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 50%;">

### Dev learnings ========================================================

#### **Basic Website Layout Design**

I followed my own advice as I wrote in _[Medium: Jr Dev asks — What’s a basic layout design to use for a business website?](https://kevin-lambda.medium.com/jr-dev-asks-whats-a-basic-website-layout-to-use-for-a-business-35ff4a7ef700)_. The guide I wrote was actually helpful in designing the layout. When designing, I noticed there were three main gaps in the design relating to typography,color theory, and copy. More on the design later. First, here were the implementation challenges for the layout design.

**Hero background banner**
Here is the css to do a hero background banner. Note that this method ties the image to the css. There's probably a better way, but this is one way.

```
.hero {
  background-color: #b9a477; /* Used if the image is unavailable */
  background-image: url("../assets/hero.jpg");
  background-size: cover; /* Resize the background image to cover the entire container */
  background-position: center; /* Center the image */
  height: 65vh;
}
```

**Fully responsive design**
The design is mildly responsive. But it is far from a polished user experience. Techniques I recall that I would like to implement in the next round are

- Changing images based on viewport
- Mobile layout design fundamentals, currently building for desktop first
- Navbar hamburger collapse
- Column responsive spacing management

#### **Further design studies**

Here's a list of study topics for design based on issues I came across when building.

**Typeface choice**

- What general characteristics of typefaces go well with certain designs. Fundamentals
- Typeface pairings
- Alignment

**Color theory**

- What basic colors pair well together
- How to theme a website color wise, how many, when and where to use colors
- Image and text pairing, what makes certain colors readable over images

#### **CSS library preferences**

I prefer bulma css, it isn't as heavy as tailwind, but not so minimal as pico css. I ran into issues trying to do more complex things with pico css. Before refactoring to bulma.

I'll use pico css if its a non design focused app. Otherwise I'll use bulma css for my default choice.

[⬆️ Back To Contents](#-contents)

<br><br>

## Next CRUD

**Date:** 04/12/2023  
**Description:** CRUD application showcasing Next.js React framework and Prisma ORM  
**Link:** n/a  
**Notable Technologies:** Next.js, Prisma, Vercel, Typescript  
**Learning focus:** Build CRUD functionality with Next.js and Prisma ORM

This is a basic Create Read Update Delete functionality demonstration.

#### **Reviewed:**

Next.js, use client, next useRouter, next link, router.refresh, Prisma, Prisma findMany, Create, findUnique ,update ,delete, Typescript, fetch, fetch method, fetch body, JSON.stringify(body) npx, schema, db sync, db migration, app directory routing, params routing

#### **Extensions:**

- Deploy the site. Try after app directory routing and fetch are stable.

<img src="./assets/12apr23_home.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 50%;">

<img src="./assets/12apr23_single.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 50%;">

### Dev learnings ========================================================

#### **Next.js**

- **Routing**

  - Next.js 13.2 uses a directory based routing with a directory called app
    - Pages are routed by creating a page file in directories
    - URL '/' = `/app/page.tsx`
    - URL '/users' = `/app/users/page`
    - URL '/users/:id' = `/app/users/[id]/page`
  - This applies to api routes as well

- **Where to put other files**

  - Other files like components can be in other directories in the root folder. They can be accessed like normal

- **Server vs client components and rendering**

  - Mainly for performance reasons, Next.js has a special way of rendering files based on if it is a server or client component.
  - Server components are limited to **NON-INTERACTIVE ELEMENTS**.
  - Client components can contain interactive elements such as buttons, forms

  - Next.js treats components as **SERVER** components by **DEFAULT**
  - When making interactive elements, we need to use `"use-client"` to mark the file as a client component

  - In summary, you need to consider if a component is interactive or not, and define it as such.

  <img src="./assets/12apr23_components.jpg" alt="Backend logic"  style="display: block;  margin-left: auto;  margin-right: auto;  margin-top: 1rem;  margin-bottom: 1rem;  width: 50%;">

- **Rendering techniques**

  - Server components stay entirely on the server, are prerendered, cached (saved), and send a "finished" file to the browser. So the browser doesn't need to think to render a server component.
  - Client components kind of can prerender half of itself on the server (HTML skeleton), is sent to the client, then the client finishes rendering the rest of the interactive elements (hydration).
  - Both server and client components can be rendered in any of the below ways, with some difference in method. But similar in rendering strategy.

  - All of the below basically says _when_ to do a full fresh render (which gets fresh data). Never, sometimes, or always.
  - **STATIC RENDERING** For both SERVER and CLIENT components. After the first render which caches the finished result, by default any future requests are served the cached version, so it saves work by not having to rerender. Use this if data is not changing.
  - **REVALIDATION** For certain functions like fetch, there is an option to define how often the cache will refresh. "no-cache" means, do not save a render and always freshly render something aka dynamic rendering. "60" can mean every 60 seconds do a fresh render and refresh the data at that interval.
  - **DYNAMIC RENDERING** If using a function or fetch that is dynamic, such as useSearchParams() or fetch cache: 'no-store', the component (client or server) will become dynamically rendered. This means the component will be rendered freshly, and won't send a saved (cached) version. Basically, it is **IMPORTANT** to use this for data that is frequently changing.

  - In summary, next.js requires you to think about how frequently data may be changing and define it.

- **File types**

  - Next.js file routing via app directory has certain file names reserved that do things, including:
  - page makes a page
  - layout makes a layout that the page lives in
  - error will send that error page upon an error
  - route, this is usually for api endpoint routes

- **SUMMARY**
  - use directories as the page routing system
  - consider if a component has interactive elements or not, then designate it as client if needed
  - consider how often data might change, then designate it as fully dynamic or set a revalidation interval

#### **Prisma**

- Prisma is a ORM similar to sequelize. It is **NOT** a database type. It _handles_ the talking to the database. Postgresql is a database type.

- **Configuration**

  - Similar to sequelize (prisma is way easier a word to type), you need to set up certain things.
  - Database url (how to connect to the database), schema (tables), syncing method (send the instructions we wrote in prisma to the actual database to set up the schema)
  - seeding is optional but usually done
  - Data syncing is called _migration_
  - Before a build (for production deployment), database needs to be synced. This is important.

- **Seeding**

  - Currently, seeding needs to be done/adjusted with a special script. Dunno what this is about.
  - Otherwise, after script adjustment seed with `npx prisma db seed`

- **Migration**

  - With initial migration (sync written prisma commands to sync db with schema), we can use `npx prisma migrate dev --name init`
  - For deployment, this works... `prisma db push` or maybe `prisma migrate deploy`

- **Instances**
  - Like sequelize, we only want one connection instance to the database from our app at a time. Once we get a prisma instance, we then export and do all of our operations (api crud) on it.

#### **CRUD nextjs prisma checklist**

For this project, I focused on making a checklist of major tasks to build a CRUD app.

**SETUP**  
[] create project npx  
[] create psql database for project. createdb  
[] install dependencies. prisma, @prisma/client, ts-node

**DB CONFIGURE CONNECTION**  
[] configure prisma ORM, to connect to the database URL, via .env if needed  
[] make schemas  
[] sync prisma schema to postgres via `npx prisma migrate dev --name init` command  
[] adjust script to ensure schemas are sync in deploy build `"build": prisma generate && next build`

**DB SEED**  
[] adjust package to make a prisma seed command ` "prisma": { "seed": "ts-node --compiler-options {\"module\":\"CommonJS\"} prisma/seed.ts" },`  
[] make a seed file in /prisma  
[] run the seed command with `npx prisma db seed`

**DB INSTANCE**  
[] make the single prisma instance in a file in /lib

**API ROUTE HANDLING**  
[] create folder structure in /app. /api /schema and /[id]. create route.ts for each folder  
[] get ready to make GET, POST in /api/schema. GET single, PUT, DELETE in /api/schema/[id]

**API ROUTES**  
[] import prisma and NextResponse as needed  
[] GET all (request){}. prisma.schema.findMany()  
[] POST(request){}. prisma.schema.create({data:{ ..... }}), body = await request.json()  
[] GET single (request, {params}){}. prisma.schema.findUnique({where:{.... }}), params 2nd from GET  
[] PUT (request,{params}){}. prisma.schema.update({where:{ ... }},data:{ ... }), params from PUT , body from request  
[] DELETE (request,{params}){}. prisma.user.delete({where:{ ... }}), params from PUT

**API FETCH FUNCTION CALLS**
[] get all - fetch(url,{method:"GET", cache:"no-store"})  
[] get one - fetch(url/${id},{method:"GET", cache:"no-store"})  
[] post    - fetch(url,{method:"POST", body:JSON.stringify(body)})  
[] put     - fetch(url/${id},{method:"PUT", body:JSON.stringify(body)})  
[] delete - fetch(url/${id},{method:"DELETE"})

**FRONTEND ROUTING**  
[] home page, with all users, edit, delete, add `/app/page.tsx`  
[] single user page `/app/users/[id]/page.tsx`

**FRONTEND USING FETCH FUNCTIONS**  
[] get all - const users = await getAllUsers()  
[] get one - const fetchedData = await getOneUser(params.id)  
[] post - await postUser(body)  
[] put - putUser(editBody, user.id)  
[] delete - deleteUser(user.id)

**DEPLOYING: DATABASE**  
[] make new cloud db instance and get connection url  
[] sync local prisma config to cloud db by running `prisma db push` ? or maybe `prisma migrate deploy`

**DEPLOYING: WEBSITE**  
[] deployed on vercel with environment variables to Database and base domain url

X - Full deployment didn't work. Retiring at this point. Goal to make a CRUD app with nextjs was acheived.

#### **Detailed steps and gotchas**

- **psql**

  - I messed up psql because prisma required a password to access postgres. now psql has a password for default user postgres. It's confusing.
  - Anyway, to access psql do this:
  - -h for hostname
  - -U for user
  - -W for password prompt
    1. `psql -h localhost -U postgres -W`
    1. `postgres`
  - postbird wants a password too
  - maybe check out this link to fix issue later. https://dba.stackexchange.com/questions/83164/postgresql-remove-password-requirement-for-user-postgres

  To create a database in postgres

  - in the regular terminal create the database with the command `createdb <name of db>`. Make sure postbird or db tool is closed....
  - OR in regular terminal `createdb -h localhost -U postgres -W <database name>`. then enter password `postgres`
  - OR if that doesn't work... in psql; `CREATE DATABASE <database name>;`

- **Prisma set up**

  - `npm i prisma --save-dev`
  - `npm i @prisma/client`
  - `npx prisma init`
  - check schema.prisma .env file, input database url
  - to sync to db `npx prisma migrate dev --name init`
  - adjust json.package with `"build": prisma generate && next build`
  - and config seeding in json.package with
    ```
      "prisma": {
        "seed": "ts-node --compiler-options {\"module\":\"CommonJS\"} prisma/seed.ts"
      },
    ```
  - make a seed file `seed.ts`
  - finally run `npx prisma db seed`

- **Backend API**

  - Import prisma
  - In Next.js functions named after RESTful (GET, PUT, POST, DELETE) come with certain things like request for the body, or params. I don't know if this is limited to the api directory or route file.

    - `export async function GET(request){}`
    - `export async function POST(request){}`
    - `export async function GET(request,{params}){}`
    - `export async function PUT(request,{params}){}`
    - `export async function DELETE(request,{params}){}`

  - For GET request, also need a current workaround thing called NextResponse in order to return json data nicely. import `{NextResponse} from 'next/server'`
  - GET `const users = await prisma.user.findMany()` prisma gets the db connection instance, user is the schema/table, findMany(), finds all
    - ` return NextResponse.json({ users })` NextResponse is nextjs's way of sending a response. we need to put .json to return a json object. then we send whatever object in the return
  - POST ` const makeUser = await prisma.user.create({DATA_OBJ_HERE})`, create expects an object
  - GET single `const getInt = +params.id` `prisma.user.findUnique({where:{id: ___ }})`
    - `params.id` turns a string into a number. findUnique,where,id expects a number
  - PUT `prisma.user.update({where:{},data:{}})`
    - update,where expects a number id
    - update, data expects a data object matching the schema
  - DELETE `prisma.user.delete({where:{}})`

    - delete,where expects a number id

  - **Fetching Function**

    - get all. fetch(url,{method:"GET", cache:"no-store"}) // DYNAMIC RENDERING
    - get one. fetch(url/${id},{method:"GET", cache:"no-store"}) // DYNAMIC RENDERING
    - post . fetch(url,{method:"POST", body:JSON.stringify(body)}) //STATIC
    - put . fetch(url/${id},{method:"PUT", body:JSON.stringify(body)}) //STATIC
    - delete . fetch(url/${id},{method:"DELETE"}) //STATIC

  - **Frontend caling fetch function**

    - GET

      - get all - const users = await getAllUsers()
      - get one - const fetchedData = await getOneUser(params.id)

    - POST, PUT

      - UI is form, label, input, onChange, value pattern
      - onChanges are setting states
      - onChange handlers include preventDefault, body with state object, fetch function, setState clearing, router.refresh from next/navigation
      - router.refresh updates the fetches, kinda like useEffect

      - post - await postUser(body)
      - put - putUser(editBody, user.id)

    - DELETE
      - delete - deleteUser(user.id)

[⬆️ Back To Contents](#-contents)

<br><br>

## Journal 07 Apr 2023

Don't use it like that!

I interacted with the [This Page Belongs To](#this-page-belongs-to) project in a way I hadn't before. And it broke it.

I accessed the live hosted database via postbird to modify some data. I hadn't done this before since deploying the site. This caused new POSTs to the database to order themseves in a weird way. This broke my functionality of showing the current owner.

I had to refresh my knowledge of the dev environment to work on this project. Luckily (or rather making my own luck), I left myself clear steps of how to do just that. I got back in the dev environment and a little bit of bug fixing later it works!

The hints I leave for future self are paying off!

[⬆️ Back To Contents](#-contents)

<br><br>

## Journal 31 Mar 2023

Two things at once, three times as slow

I'm currently learning nextjs 13, which recently released it's 13.2 version. When I ran `npx create-next-app@latest --experimental-app` I decided to also turn on typescript.

I have no experience with typescript.

So now, I'm learning two new things at once. It feels three times as slow.

If it can be helped, maybe just learn one new thing at a time.

[⬆️ Back To Contents](#-contents)

<br><br>

## Journal 21 Mar 2023

UX/UI Don't make me think! A basic business page

**Articles**  
[Medium: Jr Dev asks — What’s a basic layout design to use for a business website?](https://kevin-lambda.medium.com/jr-dev-asks-whats-a-basic-website-layout-to-use-for-a-business-35ff4a7ef700)  
[Medium: Jr Dev asks — What do you put on websites? The who, what and why framework.](https://kevin-lambda.medium.com/jr-dev-asks-what-do-you-put-on-websites-the-who-what-and-why-framework-c045fb1e31b2)

On a project building a small business webpage for H, I delved heavily into ui and design.

For my approach, Steve Krug's essential web usability book says it all in the title, _Don't Make Me think_.

From that design philosophy, I decided to use the most basic, consistent, uniform, expected, comfortable webpage design. Here's the drawn up low fidelity wireframes in whole, and in detail.

<img src="./assets/21mar2023_uxui_basicBusiness.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 100%;">
<img src="./assets/21mar2023_uxui_basicBusiness_home.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 100%;">
<img src="./assets/21mar2023_uxui_basicBusiness_about.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 100%;">
<img src="./assets/21mar2023_uxui_basicBusiness_services.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 100%;">
<img src="./assets/21mar2023_uxui_basicBusiness_contact.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 100%;">

**Whosa what now? the story / user journey:**
For the user journey, the approach is to focus on showing the user the story of WHO, WHAT and WHY to drive conversions. The home page tells the story twice. Once condensed in the hero section, and then again as it follows condensed versions of the who we are, what we do, and why choose us. Finally, a call to action is at the end of the journey.

The website as a whole also tells the story, About tells the who, services, tells the what, contact tells a brief why followed by a call to action.

Shown below, we can see the story of WHO,WHAT,WHY,Call to action three times.

- website wide level
- hero section level
- homepage level

Repeat and layer the stories.

<img src="./assets/21mar2023_hero_site.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 100%;">
<img src="./assets/21mar2023_hero.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 100%;">
<img src="./assets/21mar2023_hero_home.jpg" alt="Backend logic"
  style="display: block;
  margin-left: auto;
  margin-right: auto;
  margin-top: 1rem;
  margin-bottom: 1rem;
  width: 100%;">

[⬆️ Back To Contents](#-contents)

<br><br>

## Journal 13 Mar 2023

Does it scale?

I'm aware that this dev log format is not going to scale well.

Until now, I've never had to experience a tech architecture not scaling well on a personal project. But I intentionally wanted to experience a project not scaling well in a low stakes way.

This is just a giant markdown file, as low stakes and simple as it can get. After 2.5 months it is 800 lines and starting to be unwieldy. I want to experience working on something that is using a non optimal tech and dealing with the issues. I imagine many real world companies are working like this. We'll see how long it lasts.

From this experience, I forsee myself learning how to better think about correctly sized capabilities in the future.

[⬆️ Back To Contents](#-contents)

<br><br>

## npm kindly

**Date:** 03/08/2023  
**Description:** A continuously updated personal npm utility package  
**Link:** [https://www.npmjs.com/package/@kevin-lambda/kindly](https://www.npmjs.com/package/@kevin-lambda/kindly)  
**Notable Technologies:** npm package publishing  
**Learning focus:** Publish a npm package for personal use  
**Published Article:** [jr dev asks why would I want to publish a personal npm package](https://kevin-lambda.medium.com/jr-dev-asks-why-would-i-want-to-publish-a-personal-npm-package-8d27afd42ca5)

This is a library of personal helper functions.

#### **Reviewed:**

npm publishing

#### **Extensions:**

[~] Continue to add helper functions

### Dev learnings ========================================================

#### **Process**

The process to publish a npm package is very simple, similar to making a github repo. The challenge I believe is in how to align its use with best coding practices.

#### **Balance**

As with everything, I believe there is a good balance to strike in good code. Brevity vs Verbosity. On the verbose extreme, code could be verbose and explain every single step and acheive maximum tracable checkable detail. On the brevity extreme, an entire 1 TB program could be a single function call.

_Anyway_, abstracting functions out to a npm package takes a step towards brevity (abstraction), and we should be mindful of the ripple effects that can arise from it.

[⬆️ Back To Contents](#-contents)

<br><br>

## Journal 26 Feb 2023

A search history

- what react framework to try
- what is next.js
- what is server vs client side rendering
- what is client side vs server side
- what is a script

[⬆️ Back To Contents](#-contents)

<br><br>

## This Page Belongs To

**Date:** 02/25/2023  
**Description:** Claim a website for yourself.  
**Link:** [https://this-belongs-to.onrender.com/](https://this-belongs-to.onrender.com/)  
**Notable Technologies:** PERN stack (Postgresql, Express, React, Node), [Render](https://render.com/) platform as a Service (PaaS) cloud hosting infrastructure.  
**Learning focus:** Build and deploy a PERN (Postgresql, Express, React, Node) full-stack application.

"This Page Belongs To" allows a user to input their name as the current owner of the webpage, which is prominently displayed. Any other visitor can replace the existing owner and become the new current owner. There is a persistent list of previous owners and the length of time they were owner.

#### **!!! Upkeep:**

- !!!!!! August 09 2023. Render database will shut down because it only lasts for 90 days. Will need to either make a copy of the database... somehow. Then in render, make a new database instance, get it's internal connection URL, and use it as the key in the web service enviroment variables.

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
  width: 50%;">

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
    - domain = `www.domain.com`
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

- **User Input Filter API**
  - Used Pugomalum API to filter user input. Very easy RESTful method.

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

- **DATABASE: connecting to postgres**

  - A database needs to live somewhere.
  - Render (the platform as a service) website features a hosted postgres database. After creating a postgres database on Render, it will be accessable by a URL. This URL is a secret.

    - In the same way we had the localhost as the connection URL for sequelize i our backend to connect to `postgres://localhost:5432/${DATABASE_NAME}`
    - Render provides a connection URL for the database.

  - However, if we are also using Render to host (we are) our backend (as a web service), we should use Render's web service environment variables. So, don't do anything with the secret database url key yet.

- **DATABASE: checking connection**

  - We may want to check that the Render postgres database is able to be connected to and is working. And may want to use something like postbird to check that.
    - However, in the case of postbird, it won't accept the render url by itself. It wants ssl security. To do that just append `ssl=true` to the end of the database url
    - `postgres://user:pass@host:port/database?ssl=true`

- **BACKEND (web service): Hosting the server aka web service**

  - The server (api) that handles and listens for requests needs to live and be on somewhere. It is also called a web service.
  - On Render, it asks for two things a build command and start command. Render acts like how we were running commands before our localhost was able run the server. It needs libraries, the entry point for the app. It works the same way, so we need to let it know what commands to run.
    - Build command, typically `npm install`
    - Start command, whatever the server entry point is `node server/index.js`

- **BACKEND (web service): Deployed enviroment variables**

  - Just like how the local machine has environment variables, the hosting platform can hold environment variables for the hosted server application to access.
  - This is where we grab the database connection secret url and input it into Render's platform.
  - Just like local .env, we make a variable key and enter the secret url.
  - Then, when the deployed application runs, it searches the environment of the hosting platform, in this case, Render. And will be able to access the environment variable we input. Using the same syntax `process.env.VARIABLE_NAME`

- **Deploy Cache**

  - Sometimes, we need to deploy with the option that says to delete the build cache to see updates on the live site. Not sure if this is 100% true.

- **Dependency Error**

  - For a deploy, the hosting site needs to run build or installation. This can cause errors in some cases.
  - For this case, `fsevents` was causing an installation error, even though the local host run worked.
  - To solve this, add the optional dependencies to `package.json`

  ```javascript
   "optionalDependencies": {
      "fsevents": "2.1.2"
    },
  ```

- **FRONTEND (static site)**

- render calls the front end a static site
- Similarly to the web service, Render will ask for two things. Build command, and publish directory.
  - Build Command, just like regular `npm run build`
  - Publish Directory, we know our production build is in the build folder. `./build`

[⬆️ Back To Contents](#-contents)

<br><br>

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

<br><br>

## Journal 14 Feb 2023

Service migration

Made my first service migration from Panelbear to Cronitor. Panelbear was aquired by Cronitor and is suspending it's service, to be replaced by Cronitor.

In this case, migration was a simple 2 liner change. I'd guess things like this are where developer knowledge and experience with a codebase is key. It would have been a non-trivial task to migrate a service, without originally having done it myself.

[⬆️ Back To Contents](#-contents)

<br><br>

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
- In package.json, have `"homepage": "https://GITHUB_USER_NAME.github.io/REPO_NAME",` and the scripts `"predeploy": "npm run build", "deploy": "gh-pages -d build",`
- Make sure the repo on github is not private
- `npm run deploy`

**ISSUE - Multiple Calls to API within the same render cycle:**

- An extension I tried was to call the api again to get additional data on the items from the first call. This became an issue when trying to run it all in one render cycle.
- Also, running an api call on each item from the first api call sounds like O(n<sup>2</sup>). - Implications include calling api magnitude 10 times per page load. Probably not good.

[⬆️ Back To Contents](#-contents)

<br><br>

## Journal 27 Jan 2023

2.75/3 of a project is figuring out how to connect technologies together. This is the least fun.

- First project put on indefinite hiatus. Was trying to use an api to grab an image and then create a color palette from that image using another api.
- Ran into MANY roadblocks
  - Trying to connect to an api from the frontend can cause CORS erros. Which apparently react components constitutes the front end.
    - CORS errors is a browser based technology and is when one domain is trying to access resources from another domain. Domains trying to access data is a front end thing.
    - There are a ton of suggestions to solve this. I've found that are mainly two that seem "reasonable". 1. Use a proxy service, which routes your domain asking for data to something else that pretends to be a server. api and cors are apparently fine with server to server interactions. However, this is not a robust solution, but it **can be** a quick temporary solution. You just put another domain in front of the URL you are trying to connect to. 2. Create a backend server to connect to the api to use it there. This sounds like a lot of work just to grab a random image of coffee.
  - Trying to use fs in the frontend. It seems like it was not meant to be used there. Work arounds seem janky. It looks like it is best to use it in the backend.
  - Trying to use fs in the backend and then trying to run a build. An error something about polyfill... didn't look into that. Related to webpack most likely

Was able to run image quantization, connect to image api, connect to palette api. But couldn't link everything together.

[⬆️ Back To Contents](#-contents)

<br><br>

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
  - If the repo is using github pages domain, such as `https://<github-username-here>.github.io/dakine-ipsum/`, then you need to change pathSegmentsToKeep to 1 ` var pathSegmentsToKeep = 1`.
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

<br><br>

## Journal 16 Jan 2023

- 1/3 of a project is figuring out how to connect technologies together. This is the least fun.
- 1/3 is actually planning outline and coding. This is fun.
- 1/3 is fixing everything. This is the most challenging, and then most rewarding.

[⬆️ Back To Contents](#-contents)

<br><br>

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
- Now we have a build version of the app, and want to deploy it on github pages. However, as mentioned above, github pages is looking for the index.html in the root directory. But our production index.html is in the build folder.
- **Github pages:** Following the [gh-pages github](https://github.com/gitname/react-gh-pages) repo instructions, these were the steps I took to use gh-pages. Which enables CRA to deploy on github pages.
- Added `"homepage": "https://<github-username-here>.github.io"` to the top level `package.json` object. This seems to tell the app that any paths defined as `/` will use the `homepage` value as it's base.
  - The above works for non regular repo projects. If it is a regular repo, instead add ` "homepage": "https://GITHUB_USERNAME_HERE.github.io/REPO_NAME_HERE",`
- Added deployment scripts `"predeploy": "npm run build", "deploy": "gh-pages -d build"`to `package.json`.
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
