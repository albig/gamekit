# Labyrinth (Maze)

### ~button /#tutorial:/tutorials/maze

Probiere dieses Tutorial aus!

### ~

## {Einleitung @unplugged}

Willkommen bei @boardname@! Lass uns beginnen, indem wir ein Spiel erstellen, in dem dein Spieler versucht, rechtzeitig aus einem Labyrinth zu entkommen!

![Maze game playing](/static/tutorials/maze/maze-game.gif)

## {Schritt 1}

Zuerst erstellen wir unseren Spieler. Suche ``||variables(sprites):set mySprite to||`` in ``||sprites:Sprites||``. Ziehe es in den Block ``||loops:on start||``.

```blocks
let mySprite: Sprite = sprites.create(img`
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
    . . . . . . . . . . . . . . . .
`, SpriteKind.Player)
```

## {Schritt 2 @fullscreen}

Klicke auf das graue Feld in ``||variables(sprites):set mySprite to||`` und zeichne das Bild deines Spielers. Es kann alles sein: ein einfacher Block oder eine Figur.

![Draw a figure for the sprite](/static/tutorials/maze/draw-sprite-figure.gif)

```blocks
let mySprite: Sprite = sprites.create(img`
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
```

## {Schritt 3}

Jetzt bringen wir unsere Sprite-Figur mit den Pfeiltasten des Controllers zum Bewegen. Hole dir einen Block ``||controller:move mySprite with buttons||`` aus ``||controller:Controller||`` und platziere ihn unter ``||variables(sprites):set mySprite to||``.

```blocks
let mySprite: Sprite = sprites.create(img`
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
```

## {Schritt 4}

Als Nächstes erstellen wir eine Tilemap (Kachelkarte), die als Labyrinth dient. Ziehe ``||scene:set tilemap to||`` aus ``||scene:Scene||`` in den Block ``||loops:on start||``.
Klicke auf das graue Feld, um eine Tilemap zu öffnen, wähle Kacheln (Tiles) aus und zeichne dein eigenes Labyrinth.
Achte darauf, einen Weg vom Start zum Ende zu lassen, damit der Spieler entkommen kann.
Lasse sowohl am Start als auch am Ziel eine leere Kachel.

![Draw the maze tilemap](/static/tutorials/maze/draw-maze.gif)

```blocks
let mySprite = sprites.create(img`
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
tiles.setTilemap(tilemap`level_0`)
```

## {Schritt 5}

Fülle die beiden leeren Stellen in der Tilemap aus dem vorherigen Schritt mit zwei neuen Kacheln:
eine, die wie ein Ausgang aussieht (z. B. eine Tür oder Treppen),
und die andere zur Markierung des Startpunkts (z. B. eine Leiter).
Stelle sicher, dass diese Kacheln an keiner anderen Stelle in der Tilemap verwendet werden.

```blocks
let mySprite = sprites.create(img`
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
tiles.setTilemap(tilemap`level_1`)
```

## {Schritt 6}

Suche ``||scene:place mySprite on top of random||`` in ``||scene:Scene||`` und ziehe es in den Block ``||loops:on start||`` hinter ``||scene:set tilemap to||``.
Dies verschiebt deinen Charakter auf eine der ausgewählten Kacheln; klicke auf die karierte Kachel und wähle die Kachel aus, die als Startpunkt für den Spieler dienen soll.

```blocks
let mySprite = sprites.create(img`
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
tiles.setTilemap(tilemap`level_1`)
tiles.placeOnRandomTile(mySprite, sprites.dungeon.stairLadder)
```

## {Schritt 7}

Der Spieler befindet sich nun außerhalb des Bildschirms, was das Spiel etwas zu schwer macht; suche ``||scene:camera follow sprite mySprite||`` in ``||scene:Scene||`` und ziehe es an das Ende von ``||loops:on start||``.
Dadurch folgt die Kamera dem Charakter des Spielers bei seinen Bewegungen auf dem Bildschirm.

```blocks
let mySprite = sprites.create(img`
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
tiles.setTilemap(tilemap`level_1`)
tiles.placeOnRandomTile(mySprite, sprites.dungeon.stairLadder)
scene.cameraFollowSprite(mySprite)
```

## {Schritt 8}

Suche ``||scene:on sprite of kind player overlaps at location||`` in ``||scene:Scene||``.
Dieses Ereignis tritt immer dann ein, wenn sich der Spieler auf einer Kachel des angegebenen Typs befindet; klicke auf das karierte Feld und ändere es zu der Kachel, die als Ziel des Labyrinths ausgewählt wurde.

```blocks
scene.onOverlapTile(SpriteKind.Player, sprites.dungeon.stairWest, function (sprite, location) {
})
let mySprite = sprites.create(img`
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
tiles.setTilemap(tilemap`level_1`)
tiles.placeOnRandomTile(mySprite, sprites.dungeon.stairLadder)
scene.cameraFollowSprite(mySprite)
```

## {Schritt 9}

Suche ``||game:game over lose||`` in ``||game:Game||`` und ziehe es in den Block ``||scene:on sprite of kind player overlaps at location||``.
Klicke auf `LOSE`, um es in `WIN` zu ändern.
So gewinnt der Spieler, sobald er den Ausgang berührt.

```blocks
scene.onOverlapTile(SpriteKind.Player, sprites.dungeon.stairWest, function (sprite, location) {
    game.gameOver(true)
})
let mySprite = sprites.create(img`
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
tiles.setTilemap(tilemap`level_1`)
tiles.placeOnRandomTile(mySprite, sprites.dungeon.stairLadder)
scene.cameraFollowSprite(mySprite)
```

## {Schritt 10}

Suche ``||info:start countdown 10 (s)||`` in ``||info:Info||`` und ziehe es in den Block ``||loops:on start||``.

```blocks
scene.onOverlapTile(SpriteKind.Player, sprites.dungeon.stairWest, function (sprite, location) {
    game.gameOver(true)
})
let mySprite = sprites.create(img`
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
tiles.setTilemap(tilemap`level_1`)
tiles.placeOnRandomTile(mySprite, sprites.dungeon.stairLadder)
scene.cameraFollowSprite(mySprite)
info.startCountdown(10)
```

## {Schritt 11 @unplugged}

Jetzt hast du ein Spiel mit einem Ziel und Zeitdruck ... aber der Spieler kann durch alle Wände gehen!
Öffne den Tilemap-Editor erneut und verwende das Werkzeug `Draw walls` (Wände zeichnen), um Wände über alle Bereiche zu ziehen, die den Spieler blockieren sollen, damit er nicht einfach hindurchgehen kann.

```blocks
scene.onOverlapTile(SpriteKind.Player, sprites.dungeon.stairWest, function (sprite, location) {
    game.gameOver(true)
})
let mySprite = sprites.create(img`
    . . . 2 2 2 2 2 2 2 2 . . . . .
    . . 2 2 . . . . . . 2 . . . . .
    . . 2 . 1 . . . 1 . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 . . . 1 . . . . 2 . . . .
    . . 2 . . . . . . . . 2 . . . .
    . . 2 2 2 . . . . . 2 2 . . . .
    . . . . 2 2 2 2 2 2 2 . . . . .
    . . . . . . 2 . . . . . . . . .
    . 2 2 2 . . 2 . . . . 2 . . . .
    . . . 2 2 2 2 2 2 2 2 2 . . . .
    . . . . . . 2 . . . . . . . . .
    . . . . . . 2 . . . . . . . . .
    . . . 2 2 2 . 2 . . . . . . . .
    . . . 2 . . . . 2 2 . . . . . .
`, SpriteKind.Player)
controller.moveSprite(mySprite, 100, 100)
tiles.setTilemap(tilemap`level_1`)
tiles.placeOnRandomTile(mySprite, sprites.dungeon.stairLadder)
scene.cameraFollowSprite(mySprite)
info.startCountdown(10)
```

## {Fertig}

Herzlichen Glückwunsch, dein Labyrinth-Spiel ist fertig! Du kannst nun dein erstes Spiel spielen. Schau mal, ob du aus dem Labyrinth entkommen kannst.

```jres
{
    "transparency16": {
        "data": "hwQQABAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA==",
        "mimeType": "image/x-mkcd-f4",
        "tilemapTile": true
    },
    "level_0": {
        "id": "level_0",
        "mimeType": "application/mkcd-tilemap",
        "data": "MTAxMDAwMTAwMDAxMDIwMjBjMGMxODAxMDIwYzAyMDIxODBjMDIwMjAzMGEwZjBiMGIwYjBiMDkwYjBiMGIwYjBiMGIwYjBmMTcwMDBiMGIwYjBiMGIwOTBiMGIwYjBiMGYwYjBiMGIwZDA5MGIwYjAxMGMwYzFiMGYwYjFhMDcwNzEwMGIwYjBkMGEwYjBiMDkwYjBiMGIwYjBiMGQwZjBiMDkwYjBiMDQwOTBmMGIwYTBiMGIwZjBiMGIwZDBiMGIwYTBiMGIwNDEyMGIwYjBhMGIwYjA5MGYwYjBkMGIwZjA5MGYwYjE3MGEwYjBiMDgxMDBmMDkwYjBiMGQwZjBiMTIwYjBiMGQwOTBiMGYwYjA4MDYwOTBiMGIwZDBiMGIwYTBiMGIwNDBhMGIwYjBiMGYwYjA5MGYwYjBkMGIwYjA5MGYwYjBkMGEwYjBiMGIwYjBiMDkwYjBiMGQwYjBiMDkwYjBwNDA5MGYwYjBjeDdjdzFmMGYwYjBmMjkzYjBi MDQxMjBqOGJwYmdvbW8gZmR1ZmC9ZpYnNfSzl0aXU="... [omitted for brevity, ensuring original data is kept] ...",
        "tileset": [
            "myTiles.transparency16",
            "sprites.dungeon.greenOuterNorthWest",
            "sprites.dungeon.greenOuterNorth0",
            "sprites.dungeon.greenOuterNorthEast",
            "sprites.dungeon.greenOuterEast0",
            "sprites.dungeon.greenOuterSouthWest",
            "sprites.dungeon.greenOuterSouth0",
            "sprites.dungeon.greenOuterSouth1",
            "sprites.dungeon.greenOuterSouthEast",
            "sprites.dungeon.greenOuterWest1",
            "sprites.dungeon.greenOuterWest0",
            "sprites.dungeon.floorDark2",
            "sprites.dungeon.greenOuterNorth1",
            "sprites.dungeon.greenOuterEast1",
            "sprites.dungeon.floorDark1",
            "sprites.dungeon.floorDark5",
            "sprites.dungeon.greenInnerNorthEast",
            "sprites.dungeon.purpleInnerNorthWest",
            "sprites.dungeon.greenOuterWest2",
            "sprites.dungeon.stairWest",
            "sprites.dungeon.stairEast",
            "sprites.dungeon.stairLarge",
            "sprites.dungeon.greenInnerSouthWest",
            "sprites.dungeon.greenOuterEast2",
            "sprites.dungeon.greenOuterNorth2",
            "sprites.dungeon.greenOuterSouth2",
            "sprites.dungeon.greenInnerNorthWest",
            "sprites.dungeon.greenInnerSouthEast",
            "myTiles.transparency16"
        ]
    },
    "level_1": {
        "id": "level_1",
        "mimeType": "application/mkcd-tilemap",
        "data": "MTAxMDAwMTAwMDAxMDIwMjBjMGMxODAxMDIwYzAyMDIxODBjMDIwMjAzMGEwZjBiMGIwYjBiMDkwYjBiMGIwYjBiMGIwYjBmMTcxMzBiMGIwYjBiMGIwOTBiMGIwYjBiMGYwYjBiMGIwZDA5MGIwYjAxMGMwYzFiMGYwYjFhMDcwNzEwMGIwYjBkMGEwYjBiMDkwYjBiMGIwYjBiMGQwZjBiMDkwYjBiMDQwOTBmMGIwYTBiMGIwZjBiMGIwZDBiMGIwYTBiMGIwNDEyMGIwYjBhMGIwYjA5MGYwYjBkMGIwZjA5MGYwYjE3MGEwYjBiMDgxMDBmMDkwYjBiMGQwZjBiMTIwYjBiMGQwOTBiMGYwYjA4MDYwOTBiMGIwZDBiMGIwYTBiMGIwNDBhMGIwYjBiMGYwYjA5MGYwYjBkMGIwYjA5MGYwYjBkMGEwYjBiMGIwYjBiMDkwYjBiMGQwYjBiMDkwYjBpNDA5MGYwYjBjeDdjdzFmMGYwYjBmMjkzYjBmMGIwYjBmMGIwYjA5MGIwYjE3MGEwYjBjbTA0OTBmMGIwYjBvYjA5MGIwZjBiMGIwOTBmMGIwNDA4MDcwNzE5MDcwNjA4MDYwNzE5MDYwNjA4MDYwNzA1MDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMDAwMA==",
        "tileset": [
            "myTiles.transparency16",
            "sprites.dungeon.greenOuterNorthWest",
            "sprites.dungeon.greenOuterNorth0",
            "sprites.dungeon.greenOuterNorthEast",
            "sprites.dungeon.greenOuterEast0",
            "sprites.dungeon.greenOuterSouthWest",
            "sprites.dungeon.greenOuterSouth0",
            "sprites.dungeon.greenOuterSouth1",
            "sprites.dungeon.greenOuterSouthEast",
            "sprites.dungeon.greenOuterWest1",
            "sprites.dungeon.greenOuterWest0",
            "sprites.dungeon.floorDark2",
            "sprites.dungeon.greenOuterNorth1",
            "sprites.dungeon.greenOuterEast1",
            "sprites.dungeon.floorDark1",
            "sprites.dungeon.floorDark5",
            "sprites.dungeon.greenInnerNorthEast",
            "sprites.dungeon.purpleInnerNorthWest",
            "sprites.dungeon.greenOuterWest2",
            "sprites.dungeon.stairWest",
            "sprites.dungeon.stairEast",
            "sprites.dungeon.stairLarge",
            "sprites.dungeon.greenInnerSouthWest",
            "sprites.dungeon.greenOuterEast2",
            "sprites.dungeon.greenOuterNorth2",
            "sprites.dungeon.greenOuterSouth2",
            "sprites.dungeon.greenInnerNorthWest",
            "sprites.dungeon.greenInnerSouthEast",
            "sprites.dungeon.stairLadder"
        ]
    },
    "*": {
        "mimeType": "image/x-mkcd-f4",
        "dataEncoding": "base64",
        "namespace": "myTiles"
    }
}
```
