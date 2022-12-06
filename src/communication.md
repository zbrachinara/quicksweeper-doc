# Communication

## Message schema

Messages passed from the client to the server takes one of these forms:

- Greet
    - username: String
- Create (c)
    - gamemode (specified by UUID)
    - parameters: data buffer
- Join (j)
    - game: Game ID (number)
- Ingame (n)
    - data buffer
- ForceLeave (l)
- Games (g) (request list of games active on the server)
- GameTypes (t) (request types of games available on the server)
- GameInfo (i) (get information about a game)
    - game ID (or name?)
Messages passed from the server to the client takes one of these forms:

- ActiveGames (responds to client sending Games)
    - buffer of form:
        - UUID
        - Game ID
        - buffer of player names
- AvailableGames (responds to client sending GameTypes)
    - buffer of UUIDs
- Malformed (to signify bad or out of context client message)
Also data directly from the game? (should be most messages)
## Join process
The server listens for connections, which are placed in a pool of waiting connections.
The server waits for data from connections, which must specify their message protocol (for example, send the websocket handshake). The server uses this information to create players with these connections, which are added ot the pool of waiting players.

The server waits for greet messages from these players. If a proper greet message is received, the player gains an identity, and is moved to the waiting room. Players in the waiting room can send create, join, games, and gameTypes messages. A join message moves a player to a game.

While in a game, players can send Ingame or ForceLeave messages. ForceLeave messages return players to the waiting room.

We might want to add an option for users to reconnect after losing connection.
## Serialization
All communication is on top of TCP. The next layer above TCP is the message protocol - a way of separating the data stream into individual messages between client and server. There are multiple ways this can be done. I think we should implement the first two.

Websockets: We will probably have to implement these, since they are the only option for in-browser clients and hosting on replit. The downsides are that there are many unnecessary features of the protocol that complicate implementation, and that extremely long messages have to be send in multiple frames (although this is more of a theoretical issue).

Message-length: First the message length is sent, then the message. Since the message length can itself be considered a message, another protocal is needed to send the message length. The easiest is to use an end character. The websocket protocol is a more complicated version of this protocol. The advantages to the message-length protocol are that it is simple to implement, correct, and efficient. The disadvantages are that it will only be available for desktop clients and will have to be coded in scratch, as it is not already in a library.

End character: One character is designated as the end character, signalling the end of the message. This characetr cannot be included in the message itself, so instead of sending base 256 data, this protocol will result in base 255 data. This is probably bad, so to fix it an escape character is needed. The escape character can escape itself or the end character.

## Serialization (for real)
Messages from the client to the server indicate the message type with the first byte. The remaining bytes in the message are the data. Each game will have its own format for the data, so all that needs to be specified is the messages that are intercepted by the server. In general, clients will be sending (and receiving) ints and strings, which can be separated by an agreed-upon character (possibly null or newline).
Below is the format of the data that comes after the first character:
Greet: username
Create: gamemode (uuid), then newline, then parameters (the gamemode determines the structure for these)
Join: game ID
Ingame: bytes to send to the game, format determined by the gamemode
ForceLeave: none
Games: none
GameTypes: none
