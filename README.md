# PRG08 Week2 oefening1

## OPDRACHT

- Maak de [Bomb Clicker opdracht van week 1 af](https://github.com/HR-CMGT/PRG08-Week1-oefening1)
- Maak de Game class een singleton.
- Maak een Util class met een static method `checkCollision`. 
- Maak een DomObject class met inheritance, voor de Car en Bomb. In het DomObject wordt de "div" gemaakt en aan de "foreground" toegevoegd met AppendChild.
- Bestuur de auto met de cursortoetsen. 
- Verwijder de click handler van de bombs.
- De bombs moeten nu verwijderd worden door er met de auto onder te gaan staan. 
- Als een bomb de auto raakt krijg je een punt en gaat de bomb weg.
- Als er vier bommen doorgekomen zijn is het game over.
- Laat een upgrade vallen net zoals de bombs. Als je die pakt, dan zijn alle gebouwen weer gefixed.

## BONUS OPDRACHT

- Maak de besturing geschikt voor mobiel: door op het scherm te drukken rijdt de auto die richting op.

## Voorbeeldcode

### Singleton

```
class SingletonExample {
    private static instance: SingletonExample;

    private constructor() { }

    public static getInstance() {
        if (! SingletonExample.instance) {
            SingletonExample.instance = new SingletonExample();
        }
        return SingletonExample.instance;
    }
}
```

### Collision 

Gebruik de DOM rectangle om de positie en afmeting van een element te achterhalen:

```
let element : HTMLElement = document.createElement("div")
let rectangle : ClientRect = element.getBoundingClientRect()

function checkCollision(a: ClientRect, b: ClientRect) {
    return (a.left <= b.right &&
          b.left <= a.right &&
          a.top <= b.bottom &&
          b.top <= a.bottom)
}
```

### Movement controls

```
class Fish {
    leftSpeed : number = 0
    rightSpeed : number = 0

    constructor(){
        window.addEventListener("keydown", (e:KeyboardEvent) => this.onKeyDown(e))
        window.addEventListener("keyup", (e:KeyboardEvent) => this.onKeyUp(e))
    }
    onKeyDown(event:KeyboardEvent):void {
        switch(event.keyCode){
        case 87:
            this.leftSpeed = 5
            break
        case 83:
            this.rightSpeed = 5
            break
        }
    }
    
    onKeyUp(event:KeyboardEvent):void {
        switch(event.keyCode){
        case 87:
            this.leftSpeed = 0
            break
        case 83:
            this.rightSpeed = 0
            break
        }
    }
}
```


