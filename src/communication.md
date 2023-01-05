# Communication

All communication is on top of TCP. The next layer above TCP is the message protocol - a way of separating the data stream into individual messages between client and server. There are multiple ways this can be done. The following protocols will be supported.

Websockets: these are commonly used, there is plenty of documentation on the internet. To initiate a websocket connection, send the websocket handshake.

Message-length: First the message length is sent, then the message. Several bytes are sent, representing the message length l in base 255. Then '\xff', the 255 byte, is sent, representing the end of the message length and the start of the message. Then l bytes of the message are sent. To initiale a message-length connection, send the single byte 'l'.

## Serialization

While the user is not playing a game, they send messages to the server - to view which games are available, join a game, configure their account, etc. The type of message being sent is indicated by the first byte. When a user joins a game, all their messages are processed directly by the game itself, unless the user decides to leave. This is also specified by the first byte.

Below are the types of messages.

## Message schema

Messages passed from the client to the server in the lobby take one of these forms:

- Greet (this is always the first message sent to the server by an incoming connection. It thus has no code.)
    - username: String
- New game (g)
    - gamemode (specified by UUID)
    - newline
    - parameters: structure determined by game type
- Games (g) (request list of games active on the server)
- GameTypes (t) (request types of games available on the server)
- GameInfo (i) (get information about a game)
    - game ID (or name?)
- Join (j)
    - game: Game ID (number)
Once the user joins a game, the following messages are available:
- Ingame ('\x01')
    - data buffer
    - Any starting byte other than 0 or 1 results in an ingame message. For example, 'abc' and '\x01abc' both result in the bytes 'abc' being transmitted to the game. The sole way to communicate a null byte as data to the game is the message '\x01\x00'.
- ForceLeave ('\x00', null byte)
    - The player is returned to the lobby

Messages passed from the server to the client takes one of these forms while the user is in the lobby:

- ActiveGames (responds to client sending Games)
    - buffer of form:
        - UUID
        - Game ID
        - buffer of player names
- AvailableGames (responds to client sending GameTypes)
    - buffer of UUIDs
- Malformed (to signify bad or out of context client message)

While in a game, the user receives data from that game. The format of that data is determined by the game type.

## Join process
The server listens for connections, which are placed in a pool of waiting connections.
The server waits for data from connections, which must specify their message protocol (for example, send the websocket handshake). The server uses this information to create players with these connections, which are added ot the pool of waiting players.

The server waits for greet messages from these players. If a proper greet message is received, the player gains an identity, and is moved to the waiting room. Players in the waiting room can send create, join, games, and gameTypes messages. A join message moves a player to a game.

While in a game, players can send Ingame or ForceLeave messages. ForceLeave messages return players to the waiting room.

We might want to add an option for users to reconnect after losing connection.


Typical join process:
Client connects to the server, sends the websocket handshake, and receives a reply. The client sends the player name to log in - for example, "Caleb". The client sends the one-byte message "g", and the server replies with a list of games as newline-separated strings - for example, "Test 1\nMinesweep 5\nNumber Guess". The client sends a join message , consisting of the single byte 'j' followed by the game name - for example, "jMinesweep 5". The client is now connected to the game.  Messages will be sent between the game and client - see communication in (./area_attack.md).  When the player is ready to leave the game, it sends the single-byte message '\x00'. The player will be removed from the game and the join process may be repeated.
