# The Realtime Chat App
To develop a real chat application, we have to put in place a real-time system of sending/receiving data. It will be possible to do it with WebSocket and the library Socket.io.

## Technical stack
Here is the technical stack that I used to make this app.
### WebSockets and socket.io
WebSockets is a protocol that allows a bilateral synchronous exchange between a client and a server.
Socket.io is a library based on this protocol to make the use of WebSockets easier.
### Javascript
Node.js comes with its own package manager: npm. It becomes easy to install, update, delete packages.
In this app, I used express.js. It’s a micro web framework based on node.js.
### Set up of the development environnement
First of all, we need to configure our development environment.
The first thing to do is to start npm, our packages manager. To do so, open a new terminal, create a new repository which will contain our project, go in it and initialize npm:
```
$ mkdir chatroom
$ cd chatroom
$ npm init -y
```
Now there is a new file called package.json in our file directory. This file is listing all the dependencies.
So now we should install the all packages neede to develop our chat app.
express: the micro web application framework for node.js
socket.io: the famous package than manage WebSockets
To install them on our environment:
```
$ npm install express socket.io --save
```
Our environment is set up, we are ready to develop our application.

## The Chat App
### Architecture of the app

First of all, we have to separate to part in the development of an application: the client part and the server part. We will have to develop the two parts to make our application up and running.

![Screenshot 2024-06-07 102645](https://github.com/Rashmi-Wijenayaka/Realtime-Chat-App/assets/130863723/2921760b-0991-4525-9ec6-e2fb496dadb5)

The server will be handled by node.js to launch the packages and the website. This code will not be seen by the client.
The client part will be loaded on the computer of the client. The client will have direct access to the files (html/css and js).

## Server side:
We have to create the file server.js that will launch our server and all the packages.

![image](https://github.com/Rashmi-Wijenayaka/Realtime-Chat-App/assets/130863723/25edb425-5a1a-4507-acc9-eebc7cc03a72)

This bunch of code is actually initializing our express app.

![image](https://github.com/Rashmi-Wijenayaka/Realtime-Chat-App/assets/130863723/b63ad5dd-bf2d-4949-9554-106a6c8b12be)

Here, the io object will give us access to the socket.io library.

![image](https://github.com/Rashmi-Wijenayaka/Realtime-Chat-App/assets/130863723/654e3784-7dc2-4ef7-b7bf-88713f8fcacb)

io object is now listening to each connection to our app. 
Upon connection, users can emit events like newuser, exituser, and chat, which trigger corresponding actions on the server. 
These actions include broadcasting messages to all other connected users, notifying them of new participants joining or existing users leaving the conversation, and disseminating chat messages across the board.

![image](https://github.com/Rashmi-Wijenayaka/Realtime-Chat-App/assets/130863723/40b3a177-b3f9-4189-8bde-3e6933defa52)

The server listens on port 5000.
Using this line, we can launch our chat app.
```
$ node server.js
```
For the moment socket.io is only installed on the server part. Next, we will do the same work on the client side.

![image](https://github.com/Rashmi-Wijenayaka/Realtime-Chat-App/assets/130863723/390bf0eb-e04e-4179-8667-13d009d70c39)

## Client side:
Custom JavaScript logic is contained in code.js, which likely handles user interactions, message sending/receiving, and UI updates based on the state of the chatroom. And create a code.js file in the public folder. The HTML and CSS files are also in the public folder.

![image](https://github.com/Rashmi-Wijenayaka/Realtime-Chat-App/assets/130863723/2cbe1cc6-6ace-4571-8234-a8d7e2395b9d)

Users can join a chat session by entering a unique username, after which they are presented with a chat interface where they can send messages to other participants in real time. 
The application also handles user interactions such as sending messages and exiting the chat, ensuring a smooth and responsive user experience. 
Additionally, it dynamically updates the chat display with messages received from the server, including those from other users and system notifications about users joining or leaving the chat.

### Joining a chat room

![image](https://github.com/Rashmi-Wijenayaka/Realtime-Chat-App/assets/130863723/338671e8-be7b-4969-9567-ddaa2e55ff33)

This handles the process of a user joining a chat room by validating their input, communicating their presence to the server, storing their username, and updating the UI to reflect their transition into the chat environment.

### Sending messages

![image](https://github.com/Rashmi-Wijenayaka/Realtime-Chat-App/assets/130863723/74458c99-8427-4833-9243-4990d3a600b5)

It validates the message, renders it locally to confirm the user's action, sends the message to the server for broadcasting, and finally clears the input field for the next message.

### Exit from the chatroom and handling realtime updates

![image](https://github.com/Rashmi-Wijenayaka/Realtime-Chat-App/assets/130863723/8843d680-17af-4355-bebe-650d00f856ab)

This manages user-initiated exits from the chatroom by notifying the server and potentially refreshing the application's state. 
Additionally, it handles real-time updates from the server, including system messages and chat messages from other users, by rendering them appropriately within the chat interface.

And also, the renderMessage function is responsible for rendering different types of messages in a chat interface, including handling user-generated messages, messages received from others, and system or update messages. It dynamically creates these messages, styles them according to their type, appends them to the chat container, and ensures the chat window is scrolled to the latest message.

![image](https://github.com/Rashmi-Wijenayaka/Realtime-Chat-App/assets/130863723/7a3efbe4-aa8f-436f-a612-4d8d7c0c2bcd)




Here is the final result of chatapp:
![image](https://github.com/Rashmi-Wijenayaka/Realtime-Chat-App/assets/130863723/ca69f103-fa23-4e5c-89a0-5abb686eabcd)






