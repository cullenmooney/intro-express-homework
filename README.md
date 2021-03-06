# intro-express-homework

# POKE EXPRESS

![eh](http://digitalspyuk.cdnds.net/16/08/980x490/landscape-1456483171-pokemon2.jpg)

Make a Pokemon app that displays data inside server-side rendered views.

## App

User Stories
- When a user goes to the '/pokemon' route they will see an `index` of pokemon: the names of each pokemon rendered to the page.
- When a user clicks on the name of the pokemon, they will be taken to that pokemon's `show` page, and will see the pokemon's name and image.


### Structure


**In terminal:**
- clone this repo
  - `npm init`
  - create the folder structure  



<hr>
&#x1F534; The commit message should read: <br>
"Commit 1 - All my files are created"
<hr>

### Install NPM Packages

**In terminal:**
- Make sure that you are on the same directory level as your `package.json` (why?)
- `npm install express ejs`
- check your `package.json`
- <details><summary>package.json screenshot</summary>

  ![package.json image](https://i.imgur.com/JiEa7M2.png)

</details>

<hr>
&#x1F534; The commit message should read: <br>
"Commit 2 - All my npm packages are added"
<hr>


### Set up your server

- in your server file set up your server
 - require express
 - set `express()` to a variable
 - set a variable of `port` to `3000`
 - set your app to listen to the port and include a console log, so that you can tell when your server is running
 - include a get route `/` that will `res.send('Welcome to the Pokemon App!');`
So that when you got to `localhost:3000`, you will see `Welcome to the Pokemon App!`

    -**GOTCHA!** : nodemon will only work if you run it from the same location as your `package.json`
- **In the browser**
 - got to `localhost:3000`
 - check that you have your `Welcome to the Pokemon App!` message displaying

<hr>
 &#x1F534; The commit message should read: <br>
 "Commit 3 - My server is set up and running"
<hr>



### Set up your _'database'_
- You have created a file called `pokemon.js` inside your `models` folder.
- Inside of this file, put the following array of pokemon objects. This is your 'database' for tonight's homework

```
const pokemon = [ {name: "Bulbasaur", img: "http://img.pokemondb.net/artwork/bulbasaur.jpg"},
				{name: "Ivysaur", img: "http://img.pokemondb.net/artwork/ivysaur.jpg"},
				{name: "Venusaur", img: "http://img.pokemondb.net/artwork/venusaur.jpg"},
				{name: "Charmander", img: "http://img.pokemondb.net/artwork/charmander.jpg"},
				{name: "Charizard", img: "http://img.pokemondb.net/artwork/charizard.jpg"},
				{name: "Squirtle", img: "http://img.pokemondb.net/artwork/squirtle.jpg"},
				{name: "Wartortle", img: "http://img.pokemondb.net/artwork/wartortle.jpg"}
			  ];

```
- Set up your 'database' so that it can be exported to your server file, and then is `require` in your server file.  
- set this 'database' to a variable callled `pokemon` in your `server.js` file
- create a get route `/pokemon` that will `res.send(pokemon)`, which will display your pokemon data as json in the browser

<hr>
&#x1F534; The commit message should read: <br>
"Commit 4 - Connected my database, can see json in the browser"
<hr>

### Set up your index view

- Instead of displaying json at your `/pokemon` route, you should serve the `index.ejs` file you created that will display your pokemon
- You will have to set up your ejs file
  - Start with your html boilerplate code
  - Add an `<h1>` that describes this page, i.e. 'See All The Pokemon!'
  - Add a `<style>` tag so you can write some CSS directly in your html file. [More info](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/style) - In the Hungry for More section - you can work on properly linking a CSS file. 
  - Add a background-color and text color to the body, inside your `<style>` tag to be sure it is working as expected. Example:
  
  
  
```
 
  <style type="text/css">
body {
  color: blanchedalmond;
  background-color: steelblue;
}
</style>

```

  
  
  - **Stretch step, not required** : Choose a google font and add it to your html and inside your `<style>` tag
  - Change your `/pokemon` route to `res.render` your `index.ejs` file
  - In your browser, go to `localhost:3000/pokemon` and be sure to see your `index.ejs` view with h1 tag

<hr>
  &#x1F534; The commit message should read: <br>
  "Commit 5 - index.ejs view rendered at pokemon route"
<hr>

### Set up your index view to show your pokemon data
- continue working on your `index.ejs` view so that you can see:
  - the name of each pokemon, as a list item, inside an unordered list
  - this list should be dynamically rendered by ejs based on your data from your 'database'

<hr>
    &#x1F534; The commit message should read: <br>
    "Commit 6 - I can view a list of all my pokemon in the browser "
<hr>

### Set up your show route

- Inside your `server.js`, add a new get route `/pokemon/:id`
- That will `res.send(req.params.id);`
- So, when you go to `localhost:3000/pokemon/whatever`
 - `whatever` will show up in the browser

<hr>
   &#x1F534; The commit message should read: <br>
   "Commit 7 - show view shows req.params.id "
<hr>


### Link your `index.ejs` to your `show.ejs`
 - inside your `index.ejs`,
 - for each pokemon, add an `<a>` tag that will have an `href` that goes to the route `/pokemon/x`, where x is the array position of the `pokemon` in the data array. This should be set dynamically with ejs
 - when you click the link you should go to your show route and the index number corresponding to the pokemon's array position should be displayed

<hr>
   &#x1F534; The commit message should read: <br>
   "Commit 8 - added dynamic anchor tags to index.ejs "
<hr>

### Render your individual pokemon in the show view
- copy/paste your code from your `index.ejs`  into your `show.ejs` 
- change all your html code inside your `show.ejs` file's `<body>` so that 
	- your h1 tag says "Gotta Catch 'Em All"
	- add an h2 tag that will display the name of the pokemon
	- add an image tag that will display an image of the pokemon
	- add an anchor tag with the text of `back`, that will take you back to your `index.ejs` view
- update the route in the server.js to render the show view with the pokemon data

<hr>
  &#x1F534; The commit message should read: <br>
  "Commit 9 - created show views of each pokemon "
<hr>



### Hungry for more?


1. Use EJS partials! Create a partial for the head, and include it in both your views. [Nice walkthrough can be found here (starts about 1/4 of the way down)](https://scotch.io/tutorials/use-ejs-to-template-your-node-application)


5. Learn about express static in order to learn how to link a css file to your app (we'll be covering it tomorrow) - [read those docs!](https://expressjs.com/en/starter/static-files.html) Go ahead and dive right in! 
