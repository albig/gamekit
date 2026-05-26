# Iss die Pizza!

### @explicitHints true

## Einführung @showdialog

![Spielanimation](/static/tutorials/chase-the-pizza/chasing.gif)

Erstelle ein Spiel, bei dem du so viel Pizza wie möglich essen musst, bevor die Zeit abläuft.


## {Schritt 2}

**Hintergrundfarbe festlegen**

---

- :tree: Öffne das <br/>
``||scene:Szene||``<br/>
Werkzeug und ziehe <br/>
``||scene:setze Hintergrundfarbe auf [ ]||`` <br/>
in den **leere** ``||loops(noclick):beim Start||``-Block, der sich bereits auf deinem Arbeitsbereich befindet.

~hint Was bedeutet das? 🤷🏽

---

Wenn wir Anweisungen geben, markieren wir manchmal bestimmte Texte, damit du leichter findest, wonach du suchst.

Wenn wir zum Beispiel den <br/>
``||scene:setze Hintergrundfarbe auf [ ]||``<br/>
Block erwähnen, meinen wir damit <br/>

```block
scene.setBackgroundColor(13)
```

hint~

💡 _Du kannst natürlich auch eine andere Farbe wählen, wenn dir die vorgeschlagene nicht gefällt._


---

- :mouse pointer: Klicke auf den Button **Weiter**, um zum nächsten Schritt des Tutorials zu gelangen.


#### ~ tutorialhint
```blocks
// @highlight
scene.setBackgroundColor(13)
```


## {Schritt 3}

Füge einen Spieler-**Sprite** hinzu.

---

- :paper plane: Öffne die Kategorie ``||sprites:Sprites||`` und ziehe <br/>
``||variables(sprites):setze [mySprite] auf Sprite [ ] vom Typ [Player]||`` <br/>
an **das Ende** des bereits vorhandenen ``||loops(noclick):beim Start||``-Blocks auf deinem Arbeitsbereich.

---


~hint Was ist ein Sprite? 💡

---

In Arcade nennt man jede Figur oder jedes Bild, das etwas tut, einen **SPRITE**.

Sprites besitzen Eigenschaften, die du verändern kannst —
zum Beispiel Größe, Position oder Lebensdauer.

Auch unser Spieler wird ein Sprite sein.

hint~


~hint Zeig es mir 🔍

![Sprite-Block hinzufügen](/static/tutorials/chase-the-pizza/mySprite.gif)

hint~


#### ~ tutorialhint
```blocks
let mySprite: Sprite = null
scene.setBackgroundColor(13)
// @highlight
mySprite = sprites.create(img`.`, SpriteKind.Player)
```

## {Schritt 4}

- :mouse pointer: Zeichne deinen Sprite, indem du auf das leere graue Quadrat im <br/>
``||variables(sprites):setze [mySprite] auf Sprite [ ] vom Typ [Player]||`` <br/>
Block klickst, um den **Sprite-Editor** zu öffnen.

💡 _Klick auch auf **Galerie**. Hier sind fertige Sprites zur Auswahl. Wähle ein Bild mit 16x16 Pixel._


- :mouse pointer: Klicke auf **Fertig**, wenn du mit dem Zeichnen fertig bist.

~hint Zeig es mir 🔍

![Bildeditor](/static/tutorials/chase-the-pizza/draw.gif)

hint~



## {Schritt 5}

**Den Sprite bewegen**

---

- :game: Öffne ``||controller:Controller||`` und ziehe<br/>
``||controller:bewege [mySprite] mit Knöpfen||``<br/>
an **das Ende** des bereits vorhandenen<br/>
``||loops(noclick):beim Start||``-Blocks.

Jetzt kannst du deinen Sprite mit den Pfeiltasten oder dem Steuerkreuz bewegen.


~hint Zeig es mir 🔍

![Bewegungsblock hinzufügen](/static/tutorials/chase-the-pizza/move.gif)

hint~


#### ~ tutorialhint
```blocks
controller.moveSprite(mySprite)
```


## {Schritt 6}

- :binoculars: Teste dein Projekt im Spielfenster!

Du solltest deinen Sprite jetzt mit den Pfeiltasten oder dem Steuerkreuz bewegen können.


![Das Spielfenster befindet sich unten rechts](/static/tutorials/chase-the-pizza/game.png)



## {Schritt 7}

**Füge etwas Pizza hinzu**

---

- :paper plane: Öffne ``||sprites:Sprites||`` und ziehe<br/>
``||variables(sprites):setze [pizza] auf Sprite [ ] vom Typ [Player]||``<br/>
an **das Ende** des bereits vorhandenen <br/>
``||loops(noclick):beim Start||``-Blocks.


- :mouse pointer: Klicke auf **Player** im<br/>
``||variables(noclick):setze [pizza] auf Sprite [ ] vom Typ [Player]||``<br/>
Block und wähle stattdessen **Food** aus.

---

~hint Zeig es mir 🔍

![Pizza auf Food ändern](/static/tutorials/chase-the-pizza/food.gif)

hint~


## {Schritt 8}

- :mouse pointer: Wähle deine Pizza aus, indem du auf das leere graue Quadrat im <br/>
``||variables(noclick):setze [pizza] auf Sprite [ ] vom Typ [Food]||`` <br/>
Block klickst, um den **Sprite-Editor** zu öffnen.

- :mouse pointer: Wechsle oben zum Reiter **Galerie**.
![Galerie auswählen](/static/skillmap/assets/gallery.png)


- :mouse pointer: Suche dir eine Pizza aus und klicke anschließend auf **Fertig**.

~hint Zeig es mir 🔍

![Bildergalerie](/static/tutorials/chase-the-pizza/gallery.gif)

hint~

💡 _Du kannst natürlich auch deine eigene Pizza zeichnen!_


## {Schritt 9}

**Lass etwas passieren, wenn sich die Sprites berühren!**

---

- :paper plane: Öffne ``||sprites:Sprites||`` und ziehe den<br/>
``||sprites:wenn [sprite] der Art [Player] überlappt [otherSprite] der Art [Food] berührt||``<br/>
Container in einen **leeren Bereich** des Arbeitsbereichs.


🤷🏽‍♀️ _Brauchst du Hilfe? Klicke auf die Glühbirne unten, um zu sehen, welche Blöcke du brauchst._


#### ~ tutorialhint
```blocks
// @highlight
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {

})
```


## {Schritt 10}

**Füge einen Punkt hinzu, wenn sich die Sprites berühren**

---

- :id card: Öffne ``||info:Info||`` und ziehe<br/>
``||info:ändere Punktzahl um [1]||``<br/>
in den leeren<br/>
``||sprites(noclick):wenn [sprite] ... überlappt [otherSprite] ||``<br/>
Container auf deinem Arbeitsbereich.


#### ~ tutorialhint
```blocks
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
    // @highlight
	info.changeScoreBy(1)
})
```


## {Schritt 11}

- :binoculars: Teste dein Spiel!

Du wirst merken, dass du VIEEEEL zu viele Punkte bekommst,
wenn dein Spieler-Sprite die Pizza berührt.

Das beheben wir im nächsten Schritt.


## {Schritt 12}

**Teleportiere die Pizza bei jeder Berührung an eine zufällige Position.**

~hint Was bedeutet zufällig? 🤷🏽‍♀️

---

Eine „zufällige“ Zahl ist ein Wert, den man vorher nicht vorhersagen kann.

In Arcade verwenden wir diesen Block:

```block
randint(0, scene.screenWidth())
```

um eine Zufallszahl zwischen **0** und der **Breite des Bildschirms** zu erzeugen.

hint~

---

- :paper plane: Öffne ``||sprites:Sprites||`` und ziehe <br/>
``||sprites:setze Position von [pizza] auf...||``<br/>
an das Ende des<br/>
``||sprites(noclick):wenn [sprite] ... überlappt [otherSprite] ||``<br/>
Containers.


#### ~ tutorialhint
```blocks
let pizza: Sprite = null
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
	info.changeScoreBy(1)
    // @highlight
    pizza.setPosition(randint(0, scene.screenWidth()), randint(0, scene.screenHeight()))
})
```


## {Schritt 13}

**Starte einen Countdown, wenn sich die Sprites berühren.**

---

- :id card: Ziehe aus ``||info:Info||`` den Block<br/>
``||info:starte Countdown [3] (s)||`` <br/>
an das Ende des<br/>
``||sprites(noclick):wenn [sprite] ... [otherSprite] berührt||``<br/>
Containers.


#### ~ tutorialhint
```blocks
let pizza: Sprite = null
sprites.onOverlap(SpriteKind.Player, SpriteKind.Food, function (sprite, otherSprite) {
	info.changeScoreBy(1)
    pizza.setPosition(randint(0, scene.screenWidth()), randint(0, scene.screenHeight()))
    // @highlight
    info.startCountdown(3)
})
```


## {Finale}

**🎉 Super gemacht! 🎉**

Du hast ein **„Iss die Pizza“**-Spiel erstellt.

Teste dein Spiel:
Wie viele Punkte kannst du sammeln, bevor die Zeit abläuft?

Wenn du fertig bist, klicke auf **Fertig**, um dein Spiel mit Familie und Freunden zu teilen!