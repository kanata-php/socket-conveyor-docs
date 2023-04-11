
# Available Actions

This package comes with some out-of-the-box Actions, but you can (and probably will need) build your own for your own needs by extending the existent ones or creating new.

## Add Listener Action

> `Conveyor\Actions\AddListenerAction`

Action responsible for adding listeners to a connection. This way messages will be filtered.

Structure:

```json
{
    "action": "add-listener",
    "listen": "action-name"
}
```

## Associate User to Fd

> `Conveyor\Actions\AssocUserToFdAction`

Action responsible for associating users to connections.

Structure:

```json
{
    "action": "assoc-user-to-fd-action",
    "userId": 1
}
```

## Base (default)

> `Conveyor\Actions\BaseAction`

This is the base action. Works like a ping pong, returning the message to the client who sent it.

Structure:

```json
{
    "action": "base-action",
    "data": "message"
}
```

> If the message sent to the server is plain text instead of json, this actino will be the one selected by Socket Conveyor.

## Broadcast

> `Conveyor\Actions\BroadcastAction`

This is for messages to be broadcasted on the context of the connection that dispatches it.

Structure:

```json
{
    "action": "broadcast-action",
    "data": "message"
}
```

## Channel Connect

> `Conveyor\Actions\ChannelConnectAction`

Action used to connect to a channel.

Structure:

```json
{
    "action": "channel-connect",
    "channel": "channel-name"
}
```

## Channel Disconnect

> `Conveyor\Actions\ChannelDisconnectAction`

Action used to disconnect from a channel.

Structure

```json
{
    "action": "channel-disconnect"
}
```

## Fanout

> `Conveyor\Actions\FanoutAction`

Action used to broadcast without context borders (to every client in the server).

```json
{
    "action": "fanout-action",
    "data": "message"
}
```
