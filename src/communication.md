# Communication

## Message schema

Messages passed from the client to the server takes one of these forms:

- Greet
    - username: String
- Create
    - gamemode (specified by UUID)
    - parameters: data buffer
- Join
    - game: Game ID (number)
- Ingame
    - data buffer
- ForceLeave
- Games (request list of games active on the server)
- GameTypes (request types of games available on the server)

Messages passed from the server to the client takes one of these forms:

- ActiveGames (responds to client sending Games)
    - buffer of form:
        - UUID
        - Game ID
        - buffer of player names
- AvailableGames (responds to client sening GameTypes)
    - buffer of UUIDs
- Malformed (to signify bad or out of context client message)

## Serialization
