NYCDA Backend Exam - Part 2

Given that we have a "customer" resource/model in our web server,

1 - How would you design the routes of your server based on REST convention? List them with VERB and /route
const express = require('express'),
      morgan = require('morgan'),
      bodyParser = require('body-parser'),
      methodOverride = require('method-override'),
      pug = require('pug');

var db = require('./models');

var app = express();

var namemapRouter = require('./routes/namemap');

app.set('view engine', 'pug');

app.use(express.static('public'));

app.use(morgan('dev'));

app.use(bodyParser.urlencoded({ extended: false }));

app.use(methodOverride((req, res) => {
  if (req.body && typeof req.body === 'object' && '_method' in req.body) {
    var method = req.body._method;
    delete req.body._method;
    return method;
  }})
);

app.get('/', (request, response) => {
  response.redirect('/namemap');
});

app.use('/namemap', namemapRouter);


db.sequelize.sync().then(() => {
  app.listen(3000, () => {
    console.log('Web Server is running on port 3000');
  });
});

2 - Which pages would require templates, and how would you name them? List them with /route and template-name.extension
hier you use the view engine like pug for example. index.pug, edit.pug etc...
requie like this:
var nameRouter = require('./routes/name');
app.set('view engine', 'pug');

app.get('/', (request, response) => {
  response.redirect('/name');
});  

3 - What is a database constraint? Name the 3 types of database constraints you have learned.
constraints are used to specify rules for the data in a table.
1. primary 2.foreign 3. unique

4 - What is a foreign key? Given that you have a Factory that has many cars and car that belongs to a factory, What would be your foreign key column?
-Ensure the referential integrity of the data in one table to match values in another table
car-id = foreign

5 - List all the model lifecycle hooks you have learned from sequelize and explain them briefly if necessary.

1.This adds a default hook to all models, which is run if the model does not define its own  beforeCreate hook:
 var User = sequelize.define('user');
var Project = sequelize.define('project', {}, {
    hooks: {
        beforeCreate: function () {
            // Do other stuff
        }
    }
});

User.create() // Runs the global hook
Project.create() // Runs its own hook (because the global hook is overwritten)


2.This code will run beforeDestroy/afterDestroy on the Tasks table
var Projects = sequelize.define('projects', {
  title: DataTypes.STRING
})

var Tasks = sequelize.define('tasks', {
  title: DataTypes.STRING
})

Projects.hasMany(Tasks, { onDelete: 'cascade', hooks: true })
Tasks.belongsTo(Projects)

6 - What is the difference between database-level validations and application-level validations?
database level: Validations are used to ensure that only valid data is saved into your database
-application-level:
application level validates befor db validation

7 - Why do we use bcrypt. Write down 3 reasons why we use it if you can.
1.safe way to store user passwords in your Node.js application
2.It allows you to hash and encrypt sensitive data like user passwords before storing them in your database.
3. turn a plain text password into an encrypted hash.



8 - What is a flash message?
The flash is typically used in combination with redirects, ensuring that the message is available to the next page that is to be rendered.
It's a type of user data that you show once and then destroy. Usually a top alert like "Your action has been successful" or similar.
Flash messages are stored in the session. First, setup sessions as usual by enabling cookieParser and session middleware. Then, use flash middleware provided by connect-flash.

9 - What is the difference between minifying and obfuscating JavaScript?
-The goal of minification is to improve performance
-The goal of obfuscation is to try to hide your original source code from other people

10 - What are the 3 reasons that makes Gulp a good choice as an asset build library?
1. allows you to take repetitive tasks and automate them
2.its compressed format so that the file is as small as possible.
3.Gulp solves the problem of repetition. Quickly running unit tests.
