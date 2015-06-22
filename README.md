# Ganomede Friends

This module allows to manage an users' list of friend. This list isn't linked to a specific game.

Relations
---------

 * "AuthDB" (Redis) -> to check authentication status of user making requests
   * see https://github.com/j3k0/node-authdb
 * "FriendsDB"
   * store "username" -> Array of friends

Configuration
-------------

Variables available for service configuration (see [config.js](/config.js)):

 * `PORT`
 * `ROUTE_PREFIX`
 * `REDIS_AUTH_PORT_6379_TCP_ADDR` — IP of the AuthDB redis
 * `REDIS_AUTH_PORT_6379_TCP_PORT` — Port of the AuthDB redis
 * `COUCH_FRIENDS_PORT_5984_TCP_ADDR` — Couch friends host
 * `COUCH_FRIENDS_PORT_5984_TCP_PORT` — Couch friends port

# Friends [/friends/v1/:authToken]

## Get the list [GET]

### Arguments

    offset (int) ... offset to the first returned element
    limit (int)  ... number of elements to return

### 200 (OK)

    [
        {
            "username": "rober123",
            "fullname": "Roberto Marciello"
        },
        {
            "username": "jenny961",
            "fullname": "Jennifer Aligato"
        }
    ]

## Add to the list [PUT]

Add some players to your list of friends (DO NOT replace the list).

### Body (application/json)

    [{
        "username": "jenny961",
        "fullname": "Jennifer Aligato"
    }]

### 200 (OK)

# Single Friend [/friends/v1/:authToken/username]

## Retrieve [GET]

### 200 (OK)

    {
        "username": "jenny961",
        "fullname": "Jennifer Aligato"
    }

## Add to the list [POST]

### Body (application/json)

    {
        "username": "jenny961",
        "fullname": "Jennifer Aligato"
    }

### 200 (OK)

## Remove from friends [DELETE]

### 200 (OK)
