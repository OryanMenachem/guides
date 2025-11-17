# Express.js Cheat Sheet

## Create App
```js
import express from 'express';
const app = express(); // create an Express app
```

## Router
```js
const router = express.Router();
router.get('/users', (req, res) => res.send('Users list'));
app.use('/api', router);
```
- Helps organize routes in modules

## Routes by Method
```js
app.get('/', handler);
app.post('/submit', handler);
app.put('/update', handler);
app.delete('/remove', handler);
```
- Connect functions to handle HTTP requests by type

## Middleware
```js
app.use((req, res, next) => { console.log(req.url); next(); });
```
- Functions run before/after routes
- Used for logging, authentication, parsing, etc.

### Built-in Middlewares
```js
app.use(express.json()); // parse JSON body
app.use(express.urlencoded({ extended: true })); // parse form data
app.use(express.static('public')); // serve static files
```

## app.all
```js
app.all('/secret', handler);
```
- Handles all request types for a path

## app.route
```js
app.route('/user')
   .get(handler)
   .post(handler)
```
- Define multiple handlers for the same path by method

## req – Request object
- `req.params` – URL params (`/user/:id`)
- `req.query` – Query string params (`?name=abc`)
- `req.body` – Request body
- `req.headers` – HTTP headers
- `req.method` – Request type
- `req.url` – Request URL

## res – Response object
- `res.send()` – Send text or HTML
- `res.json()` – Send JSON
- `res.status(code)` – Set status code
- `res.redirect(url)` – Redirect
- `res.render(template, data)` – Render template

## Error-handling Middleware
```js
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```
- Special middleware for errors

## app.listen
```js
app.listen(3000, () => console.log('Server running on 3000'));
```
- Start the server and listen on a port
