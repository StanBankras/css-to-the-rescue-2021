# CSS to the Rescue @cmda-minor-web 2020 - 2021

## Keuze voor de opdracht
Ik kies voor de opdracht van **het restaurant menu**, omdat ik tijdens de introductie van Vasilis zag wat voor interessante dingen je hiervoor zou kunnen doen.

### Contexten
* Prefers-color-scheme

### Restricties
* Responsive zonder mediaqueries
* Twee kleuren

**Update 10-2-2021**
* Ik zie af van de 'responsive zonder mediaqueries' eis, en stap over op sterke accessibility

## CSS technieken die ik het eerste ga gebruiken/zoeken
* Ik wil iets met een parallax effect maken voor diepte
* Ik ga waarschijnlijk shapes snel nodig hebben

**Update 10-2-2021:**
* Ik ga verder werken met (3D) transforms en positioning
* Ik wil nog steeds iets met shapes doen om gerechten unieke te vormgeven

## Grootste uitdagingen
* Altijd in het achterhoofd de responsiveness zonder mediaqueries
* Interactie toevoegen zonder Javascript

## Mislukte experimenten
* Header goed centreren

![Header centreren](https://github.com/StanBankras/css-to-the-rescue-2021/blob/master/images/header-center.png?raw=true)
```css
body > header {
  display: flex;
  flex-direction: column;
  align-items: center;
}

body > header h1 {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 300px;
}

body > header h1:before {
  content: "";
  position: absolute;
  left: 50%;
  bottom: 0;
  background-color: red;
  height: 0.5em;
  width: 140%;
  z-index: -1;
  transform: translateX(-50%);
}

body > header h1 span {
  display: block;
  width: 50%;
}

body > header h1 span:nth-child(2) {
  font-size: 2em;
  position: absolute;
  width: unset;
  left: 40%;
  top: 50%;
  transform: translate(-50%, -50%);
}

body > header h1 span:last-child {
  text-align: right;
}
```

Ik wil graag de tekst 'appetizing since 1924' gecentreerd hebben met het & teken, maar dit lukt me nog niet.

## Accessibility sessie
* Contrast is belangrijk (hoog contrast) ([contrast checker](https://contrast-ratio.com/))
* Focus states op elementen zijn belangrijk
* Semantische HTML
* Reduced motion (voor animaties) - prefers-reduced-motion
* Screenreader: Header elementen, links, 
  * Display none niet leesbaar
  * Skip to content om de nav te omzijlen
  * Area attributen worden voorgelezen

## Week 1
* Keuze over de eisen gemaakt
* Keuze voor restaurant menu kaart gemaakt
* Eerste idee bedacht aan de hand van de presentatie (poster met parallax effect)

![Week1 concept](https://github.com/StanBankras/css-to-the-rescue-2021/blob/master/images/schets.jpg?raw=true)

## Week 2
* (3D) transforms sessie gevolgd, aan de hand hiervan een idee gekregen voor een concept.
Begin van dit concept is hieronder te zien. Het idee is om per categorie op het menu een uitvouwbare kaart te maken:
![Week2 concept](https://github.com/StanBankras/css-to-the-rescue-2021/blob/master/images/concept-week-1.gif?raw=true)
* De volgende dag had ik de accessibility sessie van Vasilis. Hierbij zag ik dat het met een simpele hover niet goed zou gaan voor screenreaders. Hier heb ik echt veel geleerd over CSS selectoren als '+' en '~' omdat ik met inputs ben gaan werken.

Hierdoor zijn de categorieën nu klikbaar geworden met alleen CSS en HTML, iets wat ik nooit voor mogelijk had gehouden:

![Week2 concept](https://github.com/StanBankras/css-to-the-rescue-2021/blob/master/images/concept-week-2.gif?raw=true)

Dit heb ik werkend gemaakt door gebruik te maken van labels en inputs, de samen één **name** attribuut delen:
```html
<input type="radio" name="category" id="noshes">
  <section>
    <label for="noshes">
      <header>
        <h2>Noshes</h2>
        <p>small dishes</p>
      </header>
    </label>
    ...
```

Wanneer je op dit label klikt, wordt de radio button selected, waardoor deze CSS andere articles (items op de menukaart) zichtbaar maakt:

```css
main > input:checked + section label ~ article {
  opacity: 1;
  background-color: rgb(228, 251, 255);
  backface-visibility: hidden;
  transform: rotateY(0);
  transition-delay: calc((var(--nth-child)) * .1s);
}
```

De '+' en '~' selector had ik hiervoor nog nooit gebruikt, dus ik vond het wel fascinerend om te zien wat voor mogelijkheden dit opent.

**Plannen voor volgende week**
* Ik wil graag de kleuren aanpassen zodat ik aan de 'twee kleuren' eis voldoe
* Ik wil het menu responsive gaan maken
* Ik wil met overige tijd vormpjes / animaties maken per menu om het op te vrolijken