# Cardano Starter Kit #003

You should use this Cardano Starter Kit if
- You're brand new to web development and need a place to start
- You have ideas for businesses and Dapps to be built on Cardano, and you're trying to get an idea of what that might entail

## Learning Targets
- I understand the role of a blockchain in a development stack.
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
3. When you're ready, copy the template repository [CSK #003a](https://github.com/GimbaLabs/csk003a) to your GitHub account
 
---

## Part 3: Now We're Cooking
When you're getting started, you might find that preparing to make software is harder than writing the code itself. Let's take a whirlwind tour of how to get ready to build something.

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

## Part 4: Let's Build an App!

### Create React App
1. Open Visual Studio Code and Open a new folder
2. Create React App

```
$ npx create-react-app
```

3. Take a look at the folders and files in your React App.
4. Start the app

```
$ npm start
```

5. We'll make changes to the file App.js. Change the title of the page and save the file.

### Adding Bootstrap and Creating a Card

1. Why I love [npm](https://www.npmjs.com/)
2. Bootstrap

```
$ npm install bootstrap
```

3. Note the new "dependency" in package.json
4. Add this import to the index.js file:

```
import 'bootstrap/dist/css/bootstrap.css';
```
5. Bootstrap provides all sorts of styling options, built on CSS. We use "class" to target specific elements.
6. Now that we have added Bootstrap to our project, we can create a Card container. Try adding this:

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

### Creating a Simple Form to take User Input

1. Hooks - abstractions
2. Form fields -> HTML
3. Form handling -> JavaScript

### Calling the Messari API to Get Data

4. Axios
5. What we're doing

Note the role of npm, want to go down that rabbit hole?
Note that "hooks" are new, and were actually hard to learn, because devs had to unlearn certain things. You could say you're at an advantage if you're new here.

### References:
- https://reactjs.org/docs/create-a-new-react-app.html
- https://create-react-app.dev/
- https://getbootstrap.com/docs/4.0/components/card/



### Extensions:
- Style your app to make it look better
- Add a different font
- Call additional data from Messari.io and add it to the app

### Challenge:
- Access your GitHub account from the command line and deploy your App to GitHub Pages. Here's an example. If enough people try this, I'll make a video about it.

