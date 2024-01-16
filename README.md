# Todo list

run `npm init` in your project directory to generate a package.json file.

run `npm install webpack webpack-cli --save-dev` to install webpack to the node_modules directory of your project.

`npm install --save-dev html-webpack-plugin`

```js
//webpack.config.js
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist'),
  },
  plugins: [
    new HtmlWebpackPlugin({
      title: 'Todo App',
    })
  ],
};
```

`npm install --save-dev webpack-dev-server`

```json
{
  "name": "todo-list-oden-project",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "build": "webpack --mode production",
    "start": "webpack serve --mode development --open",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "html-webpack-plugin": "^5.6.0",
    "webpack": "^5.89.0",
    "webpack-cli": "^5.1.4",
    "webpack-dev-server": "^4.15.1"
  }
}
```

Create `src/index.js`

```js
console.log('hello');
```

The npm build and npm start commands are used to run predefined scripts specified in your package.json file under the scripts section. These scripts are not built into npm but are defined by the project based on its requirements.

`npm run build` wil create dist folder and contents with HTML plugin

This command typically runs a script that compiles and builds the project for production deployment.
In the context of a project using Webpack, the build script often runs Webpack in production mode, which includes optimizations like minification, tree shaking, and more efficient bundling to make the output as efficient as possible for production.
The actual command might look like "build": "webpack --mode production" in your package.json.

`npm start`

This command is usually used to start your application in a development environment.
In a Webpack-based project, the start script commonly starts a development server (like webpack-dev-server) which provides features like hot module replacement (HMR), live reloading, and more. This allows developers to see changes in real time as they develop the application.

After `npm start` view the message in the console.

Your ‘todos’ are going to be objects that you’ll want to dynamically create, which means either using factories or constructors/classes to generate them. They should have properties like a title, description, dueDate and priority, completed, in progress, notes, checklist. Your todo list should have projects or separate lists of todos. When a user first opens the app, there should be some sort of ‘default’ project to which all of their todos are put. Users should be able to create new projects and choose which project their todos go into.

Separate your application logic (i.e. creating new todos, setting todos as complete, changing todo priority etc.) from the DOM-related stuff, so keep all of those things in separate modules.

The User Interface does the following:
view all projects
view all todos in each project (probably just the title and due date)
expand a single todo to see/edit its details
delete a todo

For inspiration, check out the following great todo apps
Todoist
Things
any.do

Use webpack. Add external libraries from npm like date-fns gives you a bunch of handy functions for formatting and manipulating dates and times.

We haven’t learned any techniques for actually storing our data anywhere. You should add some persistence to this todo app using the Web Storage API. localStorage allows you to save data on the user’s computer. Set up a function that saves the projects (and todos) to localStorage every time a new project (or todo) is created, and another function that looks for that data in localStorage when your app is first loaded.

Additionally, here are a couple of quick tips to help you not get tripped up:
Make sure your app doesn’t crash if the data you may want to retrieve from localStorage isn’t there!
You can inspect data you saved in localStorage using DevTools! To do this, open the Application tab in DevTools and click on the Local Storage tab under Storage. Every time you add, update and delete data from localStorage in your app, those changes will be reflected in DevTools.
localStorage uses JSON to send and store data, and when you retrieve the data, it will also be in JSON format. You cannot store functions in JSON, so you’ll have to figure out how to add methods back to your object properties once you fetch them.

Use SOLID design principles