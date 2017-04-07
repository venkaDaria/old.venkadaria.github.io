---
layout: post
title: NodeJS
tags: history javascript nodejs
---
## Кто?
[Node.js Developers](https://github.com/nodejs/node-v0.x-archive/blob/master/AUTHORS)

## Что?
[NodeJS](https://nodejs.org/uk/) - Javascript для back-end. 

Написана на Javascript, C++ и C.

Последняя версия: 7.5.0.

## Когда?
2009г.

## Server

```javascript
var http = require('http');
var server = http.createServer(function (req, res) {
    console.log('Начало обработки запроса');
    res.writeHead(200, {
        'Content-Type': 'text/plain; charset=UTF-8'
    });
    res.end('Hello world!');
});

server.listen(2002, "127.0.0.1", function () {
    console.log('Сервер запущен http://127.0.0.1:2002/');
});
```

## RESTful API using Express

```javascript
var express = require('express');        
var app = express();
var bodyParser = require('body-parser');

app.use(bodyParser.urlencoded({ extended: true }));
app.use(bodyParser.json());
var port = 8080; 
var router = express.Router();

router.get('/', function(req, res) {
    res.json({ message: 'Hello, world!' });   
});
app.use('/api', router);
app.listen(port);
console.log('Server listen a port ' + port);
```

## Server and client using sockets

```javascript
var io = require('socket.io');
var http = require('http');

var app = http .createServer();
var io = io.listen(app);
app.listen(8080);

io.sockets.on('connection', function (socket) {
	socket.on('eventServer', function (data) {
		console.log(data);
		socket.emit('eventClient', { data: 'Hello Client' });
	});
	socket.on('disconnect', function () {
		console.log('user disconnected');
	});
});
```
```html
<html>
<head>
	<title>Test socket.io</title>
	<script src="https://cdn.socket.io/socket.io-1.2.1.js"></script>
	<script>	
	var socket = io.connect('http://localhost:8080');
	socket.on('eventClient', function (data) {
		console.log(data);	
		document.write(data["data"] + "<br><br>");		
	});
	</script>
</head>
<body>
	<script>
	socket.emit('eventServer', { data: 'Hello Server' });
	socket.emit('eventServer', { data: 'Hello Server' });
	</script>
</body>
</html>
```