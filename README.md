# Backend Chat

[![Hexlet Ltd. logo](https://raw.githubusercontent.com/Hexlet/assets/master/images/hexlet_logo128.png)](https://ru.hexlet.io/pages/about?utm_source=github&utm_medium=link&utm_campaign=exercises-javascript)

This repository is created and maintained by the team and the community of Hexlet, an educational project. [Read more about Hexlet (in Russian)](https://ru.hexlet.io/pages/about?utm_source=github&utm_medium=link&utm_campaign=js-fastify-blog).

## Install

```bash
make install
```

## Run

```sh
$ make start
# curl http://localhost:5000/api/v1/data
```

## Install npm-package

```bash
npm i @hexlet/chat-server
```

## Run npm-package

```bash
npx start-server
```

## Usage

```
Usage: start-server [OPTIONS]

Options:
  -v, --version  output the version number
  -a, --address  address to listen on (default 0.0.0.0)
  -p, --port     port to listen on (default 5001)
  -h, --help     display help for command
```

## REST API

### Login

`/api/v1/login`

```javascript
axios.post('/api/v1/login', { username: 'admin', password: 'admin' }).then((response) => {
  console.log(response.data); // => { token: ..., username: 'admin' }
});
```

### Get data

`/api/v1/data`

```javascript
axios.get('/api/v1/data').then((response) => {
  console.log(response.data); // => { channels: [...], currentChannelId: 1, messages: [] }
});
```

### Create new user

`/api/v1/signup`

```javascript
axios.post('/api/v1/login', { username: 'newuser', password: '123456' }).then((response) => {
  console.log(response.data); // => { token: ..., username: 'newuser' }
});
```

## Chat API

`Socket`

```javascript
// subscribe new messages
socket.on('newMessage', (payload) => {
  console.log(payload); // => { body: "new message", channelId: 7, id: 8, username: "admin" }
});
```

```javascript
// emit new message
socket.emit('newMessage', { body: "message text", channelId: 1, username: 'admin' });
```

```javascript
// subscribe new channel
socket.on('newChannel', (payload) => {
  console.log(payload) // { id: 6, name: "new channel", removable: true }
});
```

```javascript
// emit new channel
socket.emit('newChannel', { name: "new channel" });
```

```javascript
// subscribe remove channel
socket.on('removeChannel', (payload) => {
  console.log(payload); // { id: 6 };
});
```

```javascript
// emit remove channel
socket.emit('removeChannel', { id: 6 });
```

```javascript
// subscribe rename channel
socket.on('renameChannel', (payload) => {
  console.log(payload); // { id: 7, name: "new name channel", removable: true }
});
```

```javascript
// emit rename channel
socket.emit('removeChannel', { id: 7, name: "new name channel" });
```
