# Cardano Starter Kit #003
## Where Does Blockchain Fit in the Development Stack?

This CSK is an experiment in mobilizing people to get started on building web apps. If successful, this starter kit will help to demystify app development a bit, and give you context for what "front end" web development means.

## Intended Audience
You should use this Cardano Starter Kit if
- You're brand new to web development and need a place to start
- You have ideas for businesses and Dapps to be built on Cardano, and you're trying to get an idea of what that might entail

## Learning Targets
- I understand the role of a blockchain protocol in a development stack.
- I can describe the role of HTML, CSS, and JavaScript in web development.
- I can use GitHub Pages to publish a basic web page.
- I can set up a development environment on my computer.
- I can create a web app that calls on and displays external data based on user input.

## Outcomes
At the end of this Cardano Starter Kit, you will
- Know enough about development to understand what you need when you have an idea that you want to build.
- Be on your journey toward learning more about building web apps.

---

## Part 1: Introduction
- CSK videos are currently hosted on [YouTube](http://youtube.com)
- Deck: pdf and Markdown files are here
- Solutions are provided, but of course it's better not to look

---

## Part 2: Party Like It's 1999
To prepare to build a modern app, let's go back in time to build a basic web page using HTML, CSS and JavaScript.
1. If you're brand new to GitHub, take a look at [CSK #001](https://workshopmaybe.com/learn/cardano-starter-kits/starter-kit-001/starter-kit-001a/)
2. Follow along with [this video]()
3. As shown in the video, you'll copy the template repository [CSK #003a](https://github.com/GimbaLabs/csk003a) to your GitHub account
 
---

## Part 3: Now We're Cooking
When you're getting started, you might find that preparing to make software is harder than writing the code itself. Let's take a whirlwind tour of how to set up an environment where we can build something.

The tools we'll use are choices, and we could choose others ([except perhaps for Node.js](https://medium.com/techinpieces/a-world-without-node-js-12fec4b18733)). In Parts 3 and 4 of this CSK, I'm choosing tools that are popular and accessible. If you're wondering what else is out there, follow that curiosity! Soon, you'll be replacing your Netflix diet with reading documentation and watching tutorial videos on all the different options.

1. Learn by doing: today we will use the command line
2. Real developer skills: searching, copying + pasting, and [asking the right questions](https://stackoverflow.com/).
3. Install [Visual Studio Code](https://code.visualstudio.com/)
4. In Visual Studio Code, clone the CSK #003a repo from GitHub and view the HTML files
5. On the command line, check versions of Node, npm and git
6. [Install Node](https://nodejs.org/en/), or read the [Visual Studio Code tutorial on Node](https://code.visualstudio.com/docs/nodejs/nodejs-tutorial)
7. Running JavaScript files using Node

### Extensions:
- Take a look at the [Visual Studio Code documentation](https://code.visualstudio.com/docs)
- Learn more about [Node at The Odin Project](https://www.theodinproject.com/courses/nodejs)
- Learn more about the [Command Line at codecademy](https://www.codecademy.com/learn/learn-the-command-line) or at [Learn Enough Command Line to Be Dangerous](https://www.learnenough.com/command-line-tutorial/basics)
- Read about [installing the Cardano node from source](https://docs.cardano.org/projects/cardano-node/en/latest/getting-started/install.html).

### How you can help:
- [Join us on Discord to ask questions and give feedback](https://discord.gg/dErH6vS). What sorts of documentation would you like to see here?
- Create a video about how to set up Visual Studio Code and Node on Windows

---

## Part 4: Building a Crypto Quote App

### Create React App
1. Open Visual Studio Code and Open a new folder
2. Now that you have Node and npm installed, Create React App is a convenient way to start a new app.

- https://reactjs.org/docs/create-a-new-react-app.html
- https://create-react-app.dev/

We can create a new React App called "quote-app" with the following:

```
$ npx create-react-app quote-app
```

3. Take a look at the folders and files in your React App.
4. On the command line, change the directory to "quote-app" and start the app with:

```
$ cd quote-app
$ npm start
```

5. We'll make changes to the file App.js. Change the title of the page and save the file.

### Adding Bootstrap and Creating a Card

1. Why I love [npm](https://www.npmjs.com/)
2. [Bootstrap](https://getbootstrap.com/) is a "front-end open source toolkit". Today we'll use just a little bit of the CSS that comes with Bootstrap. It also includes JavaScript plugins.

```
$ npm install bootstrap
```

3. Note the new "dependency" in package.json
4. Add this import to the index.js file:

```
import 'bootstrap/dist/css/bootstrap.css';
```
5. Bootstrap provides all sorts of styling options, built on CSS. Use "class" to target specific elements.
6. Now that we have added Bootstrap to our project, we can create a [Card container](https://getbootstrap.com/docs/4.0/components/card/). Try adding this:

```
<div class="card">
  <div class="card-header">
    Cardano Starter Kit #003
  </div>
  <div class="card-body">
    This is a card!
  </div>
</div>
```
### The Magic of React: Separate, Re-usable Components

1. In the /src directory, create a new file called Quote.js
2. Create a new function called Quote - you can copy and paste the following:

```
import React from 'react';

function Quote() {
    return (
        
    )
}

export default Quote;
```
3. Cut and paste our "card" markup inside the parentheses for return, so it looks like this:

```
import React from 'react';

function Quote() {
    return (
        <div class="card">
         <div class="card-header">
           Cardano Starter Kit #003
         </div>
         <div class="card-body">
           This is a card!
         </div>
       </div>
    )
}

export default Quote;
```

4. Make sure that you've removed the "card" markup from App.js, and replace it with <Quote />

5. At the top of the App.js file, add an import statement for your new Quote component:

```
import Quote from './Quote';
```

### Creating a Simple Form to take User Input
Next we'll add a form inside of Quote.js

1. Replace "This is a card!" with the following:

```
<form onSubmit={handleSubmit}>
    <input
      type="text"
      value={symbol}
      onChange={e => setSymbol(e.target.value)}
    />
  <br />
  <br />
  <input type="submit" value="Submit" />
</form>
```

2. Form elements like "input" and "submit" are built into HTML
3. We added Bootstrap to our project, so the input field and the submit button are styled with Bootstrap's built in CSS
4. We will write some JavaScript to handle user interaction with the form.

### React Hooks
To make a long story short, React Hooks provide an easier way for developers to create responsive, interactive apps.
1. Import useState and useEffect
```
import React, { useState, useEffect } from 'react';
```
2. At the top of the Quote() function, add the following:
```
  const [symbol, setSymbol] = useState("");
  const [lookup, setLookup] = useState("");
  
  const handleSubmit = (e) => {
    e.preventDefault();
    setLookup(symbol);
  }
  
```
3. Now our app should work. Let's take a look at the difference between symbol and lookup.

### Calling the Messari API to Get Data
Application Programming Iterfaces, or APIs, allow us to send and receive data betweeen different apps. Some APIs are open and free, others restricted. Some, like Cardano, take a bit more setting up - so we'll get to that in a future CSK!

Today we'll use [Messari's free API](https://messari.io/api/) to get data about the current price of different cryptocurrencies into our app. We will also use a package called Axios to simplify our API calls a bit.

1. Back on the command line, add [Axios](https://www.npmjs.com/package/axios) to your app:
```
npm install axios
```
2. In Quote.js, import Axios
```
import Axios from 'axios';
```
3. We'll need more useState() hooks to hold the data returned by an API. For example, let's add
```
  const [name, setName] = useState ("");
  const [price, setPrice] = useState(0);
```
Note the difference between the "initial states" of name and price.

4. Below the handleSubmit() function and above the return(), add the following:
```
useEffect(() => {
  async function fetchData() {
      const request = await Axios.get('https://data.messari.io/api/v1/assets/' + lookup + '/metrics/market-data');
      setName(request.data.data.name);
      setPrice(request.data.data.market_data.price_usd);
      return request;
  }

  fetchData();
}, [lookup]);
```

5. Now, just like we display the values of ```symbol``` and ```lookup```, we can do the same with ```name``` and ```price```

### Making it user friendly: what should we display before the user looks up a symbol?
With the following function, we can change the behavior of our card, before and after user input.

```
function coinInfo() {
  if(lookup !== ""){
    return(
      <Fragment>
        <p>Name: {name}</p>
        <p>Price: {price}</p>  
      </Fragment>
    );
  }
  else{
    return(
      <Fragment>
        <p>Name: Look up a coin</p>
        <p>Price: Awaiting your input</p>
      </Fragment>
    );
  }
}
```


### References:





### Extensions:
- Style your app to make it look better
- Add a different font from Google Fonts
- Call additional data from Messari.io and add it to the app
- Curious using some of Bootstrap's JavaScript plugins? [Take a look here](https://getbootstrap.com/docs/4.5/getting-started/javascript/), and be sure to follow up with any questions you have.

### Challenge:
- Access your GitHub account from the command line and deploy your App to GitHub Pages. Here's an example. If enough people try this, I'll make a video about it.

