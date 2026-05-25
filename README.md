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

Füge den Block `move sprite with buttons` hinzu.

```blocks
controller.moveSprite(spieler, 100, 100)
```

---

## Schritt 3: Hintergrund festlegen

Setze eine Hintergrundfarbe.

```blocks
scene.setBackgroundColor(9)
```

---

## Schritt 4: Münze erstellen

Jetzt erstellen wir eine Münze.

```blocks
let muenze = sprites.create(img`
    . . 2 2 2 . .
    . 2 2 2 2 2 .
    2 2 2 2 2 2 2
    2 2 2 2 2 2 2
    2 2 2 2 2 2 2
    . 2 2 2 2 2 .
    . . 2 2 2 . .
`, SpriteKind.Food)

muenze.setPosition(80, 60)
```

---

## Schritt 5: Punkte sammeln

Wenn der Spieler die Münze berührt,
gibt es einen Punkt.

```blocks
info.setScore(0)

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