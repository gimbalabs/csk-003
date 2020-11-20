# Part 4: Building an Interactive App with React, Bootstrap, and Axios

## Create React App
1. In Visual Studio Code, Open a new folder
2. Now that you have Node and npm installed, Create React App is a convenient way to start a new app.

- https://reactjs.org/docs/create-a-new-react-app.html
- https://create-react-app.dev/

We can create a new React App called "quote-app" with the following:

```
$ npx create-react-app quote-app
```

3. Take a look at the folders and files in your React App.
4. On the command line, change the directory to ```quote-app``` and start the app with:

```
$ cd quote-app
$ npm start
```
This launches your app in your "local" development environment, and you'll be able to see the app in your browser at [http://localhost:3000](http://localhost:3000).

5. We'll make changes to the file ```App.js```. Change the text inside of the ```<p></p>``` tags, save the file, and note the changes in your browser.

## Adding Bootstrap and Creating a Card

1. Why I love [npm](https://www.npmjs.com/)
2. [Bootstrap](https://getbootstrap.com/) is a "front-end open source toolkit". Today we'll use just a little bit of the CSS that comes with Bootstrap. It also includes JavaScript plugins.

```
$ npm install bootstrap
```

3. Note the new "dependency" in ```package.json```
4. Add this import to the ```index.js``` file:

```
import 'bootstrap/dist/css/bootstrap.css';
```
5. Bootstrap provides all sorts of styling options, built on CSS. Use ```class``` to target specific elements.
6. Now that we have added Bootstrap to our project, we can create a [Card container](https://getbootstrap.com/docs/4.0/components/card/). Try replacing everything inside of the ```<header></header>``` tags with this:

```
<div class="card" style={{width: '25rem'}}>
  <div class="card-header">
    Cardano Starter Kit #003
  </div>
  <div class="card-body">
    This is a card!
  </div>
</div>
```
7. What happens if we remove the Bootstrap import from ```index.js```?

## The Magic of React: Separate, Re-usable Components

1. In the ```/src``` directory, create a new file called ```Quote.js```
2. Create a new function called Quote - you can copy and paste the following:

```
import React from 'react';

function Quote() {
    return (
        
    )
}

export default Quote;
```
3. Cut and paste our "card" markup inside the parentheses for ```return```, so it looks like this:

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

4. Make sure that you've removed the "card" markup from ```App.js```, and replace it with ```<Quote />```

5. At the top of the ```App.js``` file, add an ```import``` statement for your new ```Quote``` component:

```
import Quote from './Quote';
```

## Creating a Simple Form to take User Input
Next we'll add a form inside of ```Quote.js```

1. Replace ```This is a card!``` with the following:

```
<form onSubmit={handleSubmit}>
    <div className="form-group">
        <label>Enter a symbol:</label>
        <input
        type="text"
        class="form-control mb-2"
        value={symbol}
        onChange={e => setSymbol(e.target.value)}
        />
    </div>

<input type="submit" value="Submit" />
</form>
```

2. Form elements like ```input``` and ```submit``` are built into HTML
3. We added Bootstrap to our project, so the ```input``` field and the ```submit``` button are styled with Bootstrap's built-in CSS
4. We will write some JavaScript to handle user interaction with the form.

## React Hooks
To make a long story short, React Hooks provide an easier way for developers to create responsive, interactive apps.
1. Import ```useState``` and ```useEffect```
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
3. Now our app should work. Let's take a look at the difference between ```symbol``` and ```lookup```.

## Calling the Messari API to Get Data
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
Note the difference between the "initial states" of ```name``` and ```price```.

4. Below the ```handleSubmit()``` function and above the ```return()```, add the following:
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

## Making it user friendly: what should we display before the user looks up a symbol?
With the following function, we can change the behavior of our card, before and after user input. We need to ```import``` Fragment in order for this code to work.

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

Once we've created this ```coinInfo()``` function, we can call it inside the ```return()``` to render the appropriate ```<Fragment>``` on our card. 

### At this point, you should have a working app - congratulations!

## Extensions:
- Style your app to make it look better (read the [Bootstrap docs](https://getbootstrap.com/docs/4.0/getting-started/introduction/) to see what you can do)
- Add a different font from [Google Fonts](https://fonts.google.com/)
- Call additional data from the [Messari.io API](https://messari.io/api) and add it to the app
- Curious using some of Bootstrap's JavaScript plugins? [Take a look here](https://getbootstrap.com/docs/4.5/getting-started/javascript/), and be sure to follow up with any questions you have.

## Challenges:
- Access your GitHub account from the command line and deploy your App to GitHub Pages. Here's an example. If enough people try this, I'll make a video about it.
- Add some logic to ```Quote.js``` so that if a user inputs symbol that does not exist, your app returns some sort of error message.
