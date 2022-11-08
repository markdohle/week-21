# week-21
MIT xPro Introduction to Tiered Applications

In Module 21: Introduction To Tiered Applications, you’ll create a basic three-tiered application. You’ll start up an Express server, create a simple database with LowDB, and then integrate it in a front-end form. At the end of the module, you’ll learn unit testing strategies that will help you use Jest within the Create React App file structure.

1. Discuss the challenges and lessons you learned from the MDN Express Tutorial
2. Set up an Express server
3. Create a database 
4. Define a three-tiered application
5. Define a npm package
6. Identify Express routing methods
7. Create a three-tiered application
8. Manipulate database records
9. Research testing strategies
10. Interpret unit tests
11. Identify testing strategies
12. Write unit tests with Jest

## Links

[Express/Node Introduction](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Introduction)

[MDN Express Tutorials](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Tutorial_local_library_website#in_this_module)

[LowDB GitHub Repository](https://github.com/typicode/lowdb)

[lowdb](https://www.npmjs.com/package/lowdb)

[Three-Tier Architecture](https://www.ibm.com/cloud/learn/three-tier-architecture)

[Jest Documentation](https://jestjs.io/docs/getting-started)

[Jest Community](https://jestjs.io/docs/jest-community)

[Awesome Jest](https://github.com/jest-community/awesome-jest)

[Testing React Apps](https://jestjs.io/docs/tutorial-react)

[Superagent](https://www.npmjs.com/package/superagent)

[How to Test Your Express API with Supertest](https://dev.to/franciscomendes10866/testing-express-api-with-jest-and-supertest-3gf)

## Video 21.1 Getting Start With Back-End Development 

In this video, Dr. Williams will introduce you to the back-end development section of the course and some of the key technologies that you will use. He will also discuss the two projects you can develop as your capstone. You can decide to complete either the Full-Stack Banking Application and Full-Stack Restaurant Application which you will be introduced to in weeks 7, 8, and 9. 

As you learn back end, you will use many tools and packages. Software changes rapidly and you may notice that a tool looks different from what you see in the video or may see instructions to use a specific version. Advanced developers become accustomed to troubleshooting these errors. As you build this skill, you can perform a Google search, review documentation, and reach out to your learning facilitator if you need additional help.

## Video 21.2 What Is The Back End?

In this video, Dr. Sanchez explains that the back end consists of a server, data store, programming language, operating system environment, and APIs.

## Video 21.3 Introduction To The Three-Tiered Application

The three-tiered application offers you the first glance at the full spectrum of possibilities, design decisions, and architectural considerations that come into play when creating an entire application. In this lesson, practice creating the entire solution that considers all the other tiers.

## MDN Express Tutorial

Practice useing the MDN Tutorial. Follow the link provided above in the links section.

Spend 60 minutes with the tutorial.

How far did you get?
1. Create a skeleton project.
- For this project, we'll use the Pug templating engine (this is the recently-renamed Jade engine), as this is one of the most popular Express/JavaScript templating languages and is supported out of the box by the generator.
- For this project, we'll use vanilla CSS (the default)
- installed nodemon in order see changes live on the website
```nodemon ./bin/www``` to run the server at ```http://localhost:3000```


What did you find challenging? How did you overcome the challenges?

I wasn't sure what command to use for nodemon. I tried ```npm start``` and that returned ```node ./bin/www``` which is the same as the the "start" value in the scripts object in the package.json file. Seems right. I can't tell.

I tried ```npm run``` and that returned devstart ```nodemon ./bin/www``` and did not start the server. I entered  ```nodemon ./bin/www``` into the command line and it launched the server. Seems right. I can't tell.

Share one thing you learned about Express.

If you go to an undefined route(http://localhost:3000/users/), then it prompts the user with a message "respond with a resource".

## Video 21.4 Set Up An Express Server

1. Navigate to a new directory and run ```npm init``` 
```
workspace $ npm init
This utility will walk you through creating a package.json file.
It only covers the most common items, and tries to guess sensible defaults.

See `npm help init` for definitive documentation on these fields
and exactly what they do.

Use `npm install <pkg>` afterwards to install a package and
save it as a dependency in the package.json file.

Press ^C at any time to quit.
package name: (workspace) 
version: (1.0.0) 
description: 
entry point: (simple-server.js) 
test command: 
git repository: 
keywords: 
author: 
license: (ISC) 
About to write to /home/nt-user/workspace/package.json:

{
  "name": "workspace",
  "version": "1.0.0",
  "description": "",
  "main": "simple-server.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC"
}


Is this OK? (yes) 
```

Create the server ```simple-server.js```

```
const express = require('express');
const app = express();
const port = 8000; // don't edit this code

app.get('/', function (req, res) {
    res.send(`On Express server running on port ${port}...`);
});

app.get('/data', function (req, res) {
    // YOUR CODE HERE
});

app.listen(port, function () {
    console.log(`Running on port ${port}...`);
});
```

Install the dependencies for this simple server. You will need to work out what the dependencies are by looking at the ```simple-server.js``` file and reviewing the contents of the ```require('express')``` statement at the top.

You can then take that value and run the following command:

```npm install <package listed in the require section>```

Note: Don't add quotation marks to the npm install command.

2. Run the server

```node simple-server.js```

3. Add the npm start script to package.json

Adding a start-up script will help you to run this project more easily in the future. In your workspace, navigate to the ```package.json``` file. In the scripts section, add a script with the key ```"start"```start and a value of node ```simple-server.js```.

```
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node simple-server.js"
  },
```

You can use ```npm start``` to re-run your Express server after you have stopped it by hitting CTRL+C or CMD+C (depending on which OS you’re using).

4. Add /data route with specific response text

Add a response for another route in your Express server. You will add a response for the ```/data``` route when navigating to ```localhost:8000/data``` in your Web Browser tab. In the ```simple-server.js``` file you will see two code blocks that start with ```app.get```. Add your own response using ```res.send('...')``` in the block for the ```/data route```.

```
app.get('/data', function (req, res) {
    res.send('data will show here...')
});
```

After adding the code, restart your Express server and navigate to ```localhost:8000/data```.

## Video 21.5 Data Store

Create a database using the package from the npm registry called LowDB. 

This database will persist data in a JSON file. Create, Read, Update and Delete(CRUD) data.

Clone the littliers repository.

```git clone git@github.com:kogsio/littletiers.git```

1. Add a post. Refer to the lowdb link for code snipets. Paste into ```simple.js```. The code at the link is deferent than what is shown in the video. Why? Is it better? What is the difference?

```
//-----Set Defaults--------
db.defaults({posts:[]}).write();

//----------add post, push properties--------
db.get('posts')
    .push({ id: 1, title: 'lowdb is awsome', published: true})
    .write()
```
Run the code ```node simple.js```. Module not found. Why? lowdb is not installed.

Install lowdb ```npm install lowdb```

Look at what dependancies are installed. Run ```cat package.json```

Now you can see that lowdb is there. Also express is listed.
```
"dependencies": {
    "express": "^4.17.1",
    "lowdb": "^1.0.0"
  }
```

Install all dependencies with ```npm install```. Even if they are already installed, you can run this command. It is robust and can handle duplication.

Run the code again and you can see data posted to the db.json file. Everytime you run the code, the data present in simple.js is saved to db.json.

Add script to simple.js to read the data back into the terminal.
```
//-------Read data back to terminal----
console.log(db.get('posts').value());
```

## Converting JavaScript Value Types

While setting up your three-tier application to receive data from a user interface, Dr. Sanchez pointed out an error causing some of the ids in the JSON body to be strings rather than numbers. In this activity, you will learn about converting JavaScript value types, which is one of the most common ways to deal with this issue.

Converting value types is sometimes necessary when working with JavaScript. For instance, a user might select their year of birth from a drop-down list on a website. The input field will return the value as a string (“1992”), but your database is set up to save it as a number.

JavaScript offers multiple methods to convert value types. For the example above, the best approach would be to use the [parseInt()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt) method:

```
let birthYearString = '1992';                     // String ‘1992’
let birthYearNumber = parseInt(birthYearString);  // Number 1992
```

Another example is an input field asking your website’s users whether they would like to subscribe to your marketing email list. The input field will return each response as a string (“true” or “false”), but your database needs to save it as a Boolean (true or false).

While JavaScript does have a [built-in](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean) way to convert a string into a Boolean, it’s generally not used because the output might be unexpected. The best way is to check whether the input value is equal to “true” or “false” and then assign a new Boolean value. Here’s an example using a [ternary operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator):

```
let canSubscribe = 'true';                          // String ‘true’
let canSubscribeBoolean = canSubscribe === ‘true’ ? true : false; // Bool true
```

As with most things in programming, there are many ways to solve the same problem. The most important thing is to recognize what the problem is. This will enable you to search for a solution.

## Video 21.6 Server Plus Data Store

Node Platform Packages thru the NPM Registry
1. LowDB
2. Express

Functionality on the server, reading and writing from the database by accessing it through the client(browser) address bar and hitting the routs defined on the server.

1. ```http_server``` bring together the functionality of server and persistant data into the same file(which is a server) with the ability to CRUD.

- add an express server

```
const express = require('express')
const app     = express();
const low     = require('lowdb');
const fs      = require('lowdb/adapters/FileSync');
const adapter = new fs('db.json');
const db      = low(adapter);
```

- add routes with addresses that will be matched when they are typed into the browser. [Express Routing](https://expressjs.com/en/guide/routing.html)

```
//------read and list all the data stored in db.json------
app.get('/data', function(req, res){
    res.send(db.get('posts').value());
});
```
```
// ------add post through browser address------
/*
test using:
curl http://localhost:3000/posts/ping/1/false
*/

app.get('/posts/:title/:id/:published', function(req, res){

    var post = {
        'id' : req.params.id,
        'title' : req.params.title,
        'published' : req.params.published,
    }
    //add the new object, "post" to db.json
    db.get('posts').push(post).write();
    console.log(db.get('posts').value());
    res.send(db.get('posts').value());

});
```

- start the server

```
//----start express server-----
app.listen(3000, function(){
    console.log('Running on port 3000: localhost:3000')
})
```

## Video 21.7 The Three Tiers

In this lesson, you need to write a user interface by using the same functionality that you built from the back end, i.e., the node packages from npm running on the top of node, Express, and LowDB. The front end will be a HTML page that leverages two libraries: Bootstrap (the most extensive framework for web styles) and Superagent (which handles calls from a HTML page to the server). As you watch the tutorial, make sure you understand the flow of the client, server, and storage tiers.

Node Platform Packages thru the NPM Registry
1. LowDB - Server 
2. Express - Server

Functionality on the server, reading and writing from the database by accessing it through the front end user interface(UI) and hitting the routs defined on the server.

Front End UI
1. Superagent - make calls to the server from html
2. Bootstrap - styles

index.html
```
<!DOCTYPE html>
<html>
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css">
<script src="https://cdnjs.cloudflare.com/ajax/libs/superagent/3.8.3/superagent.min.js"></script>

<body>

    <main role="main" class="container" style="margin-top:20px">

        <div id="status"></div>        
        <button type="button" class="btn btn-primary" onclick="data()">Show All Data</button><br>

    </main>

</body>
<script>

function data() {
    var status  = document.getElementById('status');
    var url = '/data';

    superagent
        .get(url)
        .end(function(err, res){
            if(err){
                console.log(err);
            }
            else{
                console.log(res)
                status.innerHTML = JSON.stringify(res.body)
            }
        });
}
</script>
</html>
```

http_server.js
```app.use(express.static('public'));```

## Video 21.8 Receiving Data From the User Interface

post.html
```
<!DOCTYPE html>
<html>
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css">
<script src="https://cdnjs.cloudflare.com/ajax/libs/superagent/3.8.3/superagent.min.js"></script>

<body>

    <main role="main" class="container" style="margin-top:20px">

        <input type="number" id="id" placeholder="id">
        <input type="text" id="title" placeholder="title">
        <input type="text" id="published" placeholder="published">
        <button type="button" class="btn btn-primary" onclick="post()">Submit</button>

    </main>

</body>
<script>

function post() {
    var id          = document.getElementById('id').value;
    var title       = document.getElementById('title').value;
    var published   = document.getElementById('published').value;
    //construct a string based on user inputs
    var url = `/posts/${title}/${id}/${published}`;

    superagent
        .get(url)
        .end(function(err, res){
            if(err){
                console.log(err);
            }
            else{
                console.log(res)
            }
        });
}
</script>
</html>
```

## What is a Unit Test

What Is A Unit Test?
A unit test is an automated way to test that any function you write does what you expect it to do.

For example, suppose you have the following JavaScript function:
```
function add(a, b) {

  return a+b;
}
```
A unit test for this function would make a call to the function using two parameters; it would then expect the result of that call to be the sum of those two parameters. Here’s a pseudo-code representation of this:

```Expect add(1,2) to equal 3.```

If this test passes, it means that the function called add(1,2) does return 3. You can be certain that the “add” function is correctly implemented.

While writing unit tests, here are a few things to keep in mind:

- Your test should only test one thing. 
- Write tests for sections of your code that provide the specific outcome you’re interested in. 
- When testing function logic, account for edge cases and unexpected user behavior.

Jest

Jest is a testing framework that allows you to manage unit tests within your React application.

### Installation: 

You can install it through npm by running the command ```npm install jest```. 

### Test files:

 Jest allows you to create test files, which contain the unit tests you write for your application. 

Every test file is linked to a code file and has the extension *.test.js.For example, if you have a file called index.js in your application and you want to add unit tests for it, you need to create a new file called index.test.js in the same directory. 
Your unit tests should be separated into different files, just like your component files. This will help you to keep everything well organized and will make the testing process more manageable.
Jest will allow you to run a command that checks all the unit tests and determines whether they pass or fail.

You can learn more about [Jest](https://jestjs.io/docs/getting-started) using the official documentation.

### SupterTest

[SuperTest](https://www.npmjs.com/package/supertest) is a library that helps you test API endpoints; you can use it to determine whether an API is returning what you expect it to return.

When building applications with the MERN stack, you’ll have to test different pieces of code in all layers of the application (front end and API). Jest and SuperTest allow you to do that.

### Video 21.9 Jest Hello World Test

Practice the following steps: (1) install Jest by running npm install jest, (2) develop code through HTML and CSS, and (3) test through Jest and npm.

### Best Practices for Writing Tests

Now that you understand how to use Jest, let’s look at the best practices for writing tests. By doing so, you should be able to avoid the most common pitfalls.

### Don’t strive for 100% coverage

Testing coverage depends on many factors, such as the size, complexity, and type of application. Writing tests is a very time-consuming process, so you should aim for the amount of coverage that fits with the application you’re building. It’s important to have a balance between the speed of development and code stability.

### Don’t write unnecessary tests

In order to get as much testing coverage as possible, you will end up writing more tests than you need. This adds unnecessary complexity and introduces more code that you will need to maintain. For example, review  the code below:

```
expect(user).toBeDefined();
expect(user).toHaveAProperty('email', 'test@test.com');
```

The first "expect(user)" is unnecessary. If the user isn’t defined, then the second “expect” will fail anyway when it looks for the email property.

Writing tests is just like writing any other code. Keep it as clean and straightforward as possible.

### Use realistic input data

When bugs happen in production, they often occur as a result of surprising input data. When writing tests that involve certain types of input data (like user data, for example), make sure that the test input data is as realistic as possible. Use libraries like [Faker](https://faker.readthedocs.io/en/master/) to generate the same format and structure as the real data in production.

### Describe expectations in a declarative style

Tests should be written so simply and cleanly that anyone looking at them should be able to understand what they are testing. Additionally, tests should be written in a human-like language.

### Check your dependencies

Any JavaScript framework or library will have many package dependencies; even the most popular and widely used frameworks still have some vulnerabilities. There are some tools, such as npm audit, that will alert you to any known vulnerabilities in the packages you are using.

### Name some best practices that you’ve found

The above are only some of the best practices to follow when writing tests. Please conduct some research, find one more best practice (that’s not on this list), and post it and your reason for picking it, below.

Here are some articles that will help you in your search for additional best practices:

[19 Best Practices for Automation Testing—DZone Performance](https://dzone.com/articles/19-best-practices-for-automation-testing-with-node)

[Node.js and JavaScript Testing Best Practices](https://yonigoldberg.medium.com/yoni-goldberg-javascript-nodejs-testing-best-practices-2b98924c9347)

### Unit Testing with Jest

Writing Jest Tests

At first, testing can seem overwhelming. You can get started by identifying what you want to test and putting it into the pattern
of ```setup, expected output, assertion```, and your test will soon take shape.

In this activity, you'll write tests that examine the individual functions and attributes of a JavaScript dragon class, to see if they produce the expected results.

Let's look at an example test that checks if the ```dragon``` object has a name attribute.

Here is the code you are testing:
```
class Dragon {
    constructor(name){
        this.name = name
    }
}
 
module.exports = Dragon
```

Now let's examine a test for this functionality:

```
describe("dragon attributes", () => {
 
  test("it has a name", () => {
 
    const dragon1 = new Dragon("Smaug");
    const name = dragon1.name;
 
    expect(name).toEqual("Smaug")
  });
});
```

Notice that there are several parts to this test. Let's break them down further.

The first section is the ```describe``` block. It wraps all the other tests inside of it. In this case, you are testing the dragon's attributes, so it is named ```attributes```.

The second section is the individual test, which starts with the ```test``` block. This is the smallest piece of functionality you are testing for, in this case, the ```name``` attribute.

Set Up

To test if the dragon has a name, you need to make a dragon object to test. You create this during setup with the ```new``` keyword, as you can see below.

```const dragon1 = new Dragon("Smaug")```

Expected Output

Now, isolate your expected output and define the individual attribute in a variable. You can use dot notation to pull it out of the ```dragon1``` object you defined above.

```const name = dragon1.name```

Assertion

The third block is the ```assertion``` block. This is where you will use assertions from the official [Jest documentation](https://jestjs.io/docs/using-matchers) to check if your expected output is the actual output you receive.

In this case, you expect the dragon's name to equal "Smaug". To write this with an assertion will look like this:

```expect(name).toEqual("Smaug")```

And that's it. Run ```npm test``` from the root directory of your testing suite (in this case, tests) via the command line, and Jest will run the test suite. To get into the root of your tests file, run ```cd __tests__`` in your terminal.

Task

Your task in this assignment is to use the ```setup, expected output, assertion``` pattern to write a test for each piece of functionality.

- Navigate to the ```dragon.spec.js``` file, located in the tests folder. On line four, you will see a test called

```"test.skip("dragon should be a function")"```

- Un-skip this individual test by deleting ```.skip``` from the test name, ```test.skip```

- Write your test

- Run ```npm test dragon.spec.js``` from the tests folder in your command line to see if your test passes or fails

- Keep going until you have written passing tests for each of the functions. Note Its important to explicitly name your tests and variables so you don't get lost.

You are writing tests for the following functionality, in order:

- Does the dragon function exist?

```test("dragon should be a function")```

- Is the dragon's color red by default?

```test("it should be red by default")```

- Is the dragon's color changeable?

```test("it can change color to golden")```

- Does the wakeUp function return the expected string?

```test("it should get angry when you wake it up")```

- Does the threaten function return the expected string?

```test("it should be happy when you leave")```

.test.js script

```
var Dragon = require("../dragon");

describe("exists?", () => {
  test("dragon should be a function", () => {
    //checks that the dragon class is a function
    //setup a new dragon object
    const willow = new Dragon
    //check to see that the dragon object exists, using an assertion
    expect (willow).toBeDefined
  });
});

describe("attributes", () => {
  test("it should be red by default", () => {
    //write a test to check if the default color is red
    //set up the dragon object
    const ana = new Dragon
    //isolate the color attribute in a variable
    const color = ana.color
    /*write what you expect the name variable to be 
    in the form of an assertion*/
    expect(color).toEqual("Red")
  });

  test("it can change color to golden", () => {
    //write a test to check if you can change the dragon's color
    const camillion = new Dragon
    let color = camillion.color
    color = "Golden"

    expect(color).toEqual("Golden")
  });
});

describe("sayings", () => {
  test("it should get angry when you wake it up", () => {
    /*write a test to check the return value of this function is
  what you'd expect*/
    //set up a dragon
    const bravo = new Dragon
    /*invoke the function and check to see if the return 
    value is what you expect using assertions*/
    reaction = bravo.wakeUp()
    expect(reaction).toEqual("WHO DARES DISTURB MY SLUMBER?")
  });

  test("it should be happy when you leave", () => {
    /*similar to the above, write a test to check if the return value of this 
    function is what you expect*/
    const able  = new Dragon
    const reaction =able.threaten()
    expect(reaction).toEqual("Go now, and tell the others to leave me in peace! Else you shall regret the day you first drew breath!")
  });
});
```
