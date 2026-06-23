# Fang die Münzen!

## Schritt 1: Spieler erstellen

Erstelle zuerst deinen Spieler.

Ziehe einen `set mySprite to sprite` Block in `on start`.

Wähle ein Bild für deine Figur aus.

```blocks
let spieler = sprites.create(img`
    . . 5 5 5 . .
    . 5 5 5 5 5 .
    5 5 5 5 5 5 5
    5 5 f 5 f 5 5
    5 5 5 5 5 5 5
    . 5 5 5 5 5 .
    . . 5 5 5 . .
`, SpriteKind.Player)
```

---

## Schritt 2: Bewegung hinzufügen

Jetzt soll sich die Figur bewegen können.

- :game: Öffne ``||controller:Controller||`` und ziehe<br/>
``||controller:bewege [mySprite] mit Knöpfen||``<br/>
an **das Ende** des bereits vorhandenen<br/>
``||loops(noclick):beim Start||``-Blocks.


```blocks
controller.moveSprite(spieler, 100, 100)
```

---

## Schritt 3: Hintergrund festlegen

- :tree: Öffne das <br/>
``||scene:Szene||``<br/>
Werkzeug und ziehe <br/>
``||scene:setze Hintergrundfarbe auf [ ]||`` <br/>
in den ``||loops(noclick):beim Start||``-Block.

```blocks
scene.setBackgroundColor(9)
```

---

## Schritt 4: Münze erstellen

Jetzt erstellen wir eine Münze.

- :paper plane: Öffne ``||sprites:Sprites||`` und ziehe<br/>
``||variables(sprites):setze [muenze] auf Sprite [ ] vom Typ [Player]||``<br/>
an das Ende des ``||loops(noclick):beim Start||``-Blocks.

- :mouse pointer: Ändere den Typ von ``Player`` zu ``Food``.

- :mouse pointer: Klicke auf das graue Quadrat und zeichne eine Münze.

#### ~ tutorialhint
```blocks
let muenze = sprites.create(img`
    . . 2 2 2 . .
    . 2 2 2 2 2 .
    2 2 2 2 2 2 2
`, SpriteKind.Food)

muenze.setPosition(80, 60)
```

---

## Schritt 5: Punkte sammeln

Wenn der Spieler die Münze berührt,
soll es einen Punkt geben.

- :paper plane: Öffne ``||sprites:Sprites||`` und ziehe<br/>
``||sprites:wenn [sprite] vom Typ [Player] [otherSprite] vom Typ [Food] berührt||``<br/>
in einen freien Bereich.

- :id card: Öffne ``||info:Info||`` und füge<br/>
``||info:ändere Punktestand um [1]||``<br/>
in den neuen Block ein.

#### ~ tutorialhint
```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (spieler, muenze) {
    info.changeScoreBy(1)

    muenze.setPosition(
        randint(10, 150),
        randint(10, 110)
    )
})
```

---

## Schritt 6: Spiel starten

Teste jetzt dein Spiel!

Bewege deine Figur und sammle Punkte.

# Fertig!

Du hast dein erstes Arcade-Spiel gebaut 🎉