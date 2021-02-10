# CSS to the Rescue @cmda-minor-web 2020 - 2021

## Keuze voor de opdracht
Ik kies voor de opdracht van **het restaurant menu**, omdat ik tijdens de introductie van Vasilis zag wat voor interessante dingen je hiervoor zou kunnen doen.

### Contexten
* Prefers-color-scheme

### Restricties
* Responsive zonder mediaqueries
* Twee kleuren

## CSS technieken die ik het eerste ga gebruiken/zoeken
* Ik wil iets met een parallax effect maken voor diepte
* Ik ga waarschijnlijk shapes snel nodig hebben

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