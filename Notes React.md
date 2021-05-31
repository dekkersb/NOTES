# Notes React

Als je een project van een ander opent moet je eerst alle node modules ophalen.
Dit gaat met npm install.

Daarna openen met npm start.

1. .idea folder toevoegen aan git-ignore.
2. (readme aanpassen als je deze op Git zet).
3. index.html: title aanpassen naar je applicatienaam.
4. reportwebvitals en setupTests niet verwijderen!
5. index.css leeg maken.
6. tekst binnen app functie leeg maken.
7. logo verwijderen.
8. app.test.js verwijderen.
9. app.css leegmaken.

Functies met react componenten altijd met Hoofdletter.

Om te stylen van je react gebruik je className ipv class om styling toe te voegen.

Bestanden met een React component ook met hoofdletter.

Gebruik je String doe dan ""

Gebruik je variabele doe dan {}

Fragments:
Fragments zijn tags die geen functie hebben. Het wrappen van andere elementen.
Zodat je 1 return value kan meegeven. Dit kan op 2 manieren:
```React
import React, { Fragment } from 'react';

function App() {
  return (
    <Fragment>
      <div>Eerste element</div>
	  <div>Tweede element</div>
    </Fragment>
  );
}
```

of

```React
function App() {
  return (
    <>
       <div>Eerste element</div>
       <div>Tweede element</div>
    </>
  );
}
```
---
## React use state

Wanneer je wilt dat je React iets interactiefs doet heb je state nodig.
om deze uit te lezen gebruik je useState hooks.

const [color, setcolor] = React.useState ('');

[start variabele, state setterfunctie]

De functie moet altijd 1 van deze namen ontvangen:
- set <naam van object>
- toggle <naam van object>

Vervolgens kun je hem altijd aanspreken onder de naam van de key.

altijd buiten de return functie!

vergelijking:
```javascript
{score === 10 && <p> Jij bent de winnaar </p>}
```

&&

als links van de && waar is, voer dan rechts uit.


of

```javascript
{score === 10 ? <p> Jij bent de winnaar </p> : <p> jij moet beter je best doen! </p>}
```
als score = 10, voer dan de functie links van : uit, anders voer de andere functie uit.

---
## React hook form.

Form builder op react-hook-form.com/form-builder

```terminal
npm install react-hook-form --save
```

```javascript
import { useForm } from 'react-hook-form';

function App() {
  //.. formulier
}
```

maak een const aan:
```javascript
const { handleSubmit } = useForm();
```

geef je eigen onFormSubmit mee als parameter:
```javascript
function onFormSubmit(e) {
   e.preventDefault();
   console.log('Submitted!');
 }
 
 return (
   <form onSubmit={handleSubmit(onFormSubmit)}>
```

Het event object hoeft nu niet meer opgevangen te worden en kan je dus aanpassen naar een prop:
```javascript
function onFormSubmit(data) {
  console.log(data);
}
```

Deze zal echter undefined geven en wordt pas een waarde toegegeven als deze wordt geregristreerd.
Nu moet je dus de input-velden registreren, dit gaat met de register functie.

```javascript
function App() {
    const { handleSubmit, register } = useForm();
//register toevoegen in de useForm functie.
    
    function onFormSubmit(data) {
        console.log(data);
    }

    return (
        <form onSubmit={handleSubmit(onFormSubmit)}>
            <fieldset>
                <legend>Gegevens</legend>

                <label htmlFor="details-name">
                    Naam:
                    <input
                        type="text"
                        id="details-name"
                        {...register("name")}
                        //spread operator en register toevoegen met het type wat opgeslagen wordt.
                    />
                </label>
            </fieldset>
        </form>
);
}
```

### Validatie

* Verplicht veld (required)
* Minimale lengte (minLength)
* Maximale lengte (maxLength)
* Minimaal getal (min)
* Maximaal getal (max)
* Een specifiek patroon, zoals het wel of niet bevatten van speciale tekens (pattern)
* Een zelfgemaakte validatie die je meegeeft als callback functie (validate)

Required toevoegen aan de register functie:
```javascript
<label htmlFor="details-name">
  Naam:
  <input
    type="text"
    id="details-name"
    {...register("name", { required: true })}
  />
</label>
```

Custom toevoegen, of de data geen @ bevat:
```javascript
<label htmlFor="details-name">
  Naam:
  <input
    type="text"
    id="details-name"
    {...register("name", { 
      required: true, 
      validate: (value) => value.includes('@'),
    })}
  />
</label>
```

of aan een maximaal lengte moet voldoen:
```javascript
<label htmlFor="recipe-comments">
  Opmerkingen:
  <textarea
    id="recipe-comments"
    rows="4"
    cols="40"
    placeholder="Wat vond je van het recept?"
    {...register("comments", {
      required: true,
      maxLength: 50,
    })}
  >
  </textarea>
</label>
```

Je moet de gebruiker er natuurlijk wel op wijzen waaraan het moet voldoen, dit kan in hetzelfde stuk:
```javascript
<label htmlFor="recipe-comments">
  Opmerkingen:
  <textarea
    id="recipe-comments"
    rows="4"
    cols="40"
    placeholder="Wat vond je van het recept?"
    {...register("comments", {
      required: {
        value: true,
        message: 'Dit veld mag niet leeg zijn',
      },
      maxLength: {
        value: 50,
        message: 'Er mogen maximaal 50 karakters gebruikt worden',
      },
    })}
  >
  </textarea>
</label>
```

Om de error's weer te kunnen geven moeten we ze uit de formState halen.
```javascript
const { handleSubmit, formState: { errors }, register } = useForm();

//en voeg de paragraaf op de plek toe waar ze moeten worden getoond.
{errors.comments && <p>{errors.comments.message}</p>}
```

Wil je een specifiek inputveld tonen (bijv als de gebruiker ander kiest) dan heb je de watch functie nodig.
1. Voeg de watch functie toe aan je useForm();
2. Maak een variabele om de data op te slaan en mee te geven.
3. Refereer naar je variabele onder de select optie.
4. Maak een nieuw input veld onder je variabele
5. Verwijs naar de naam en register deze.

```javascript
function App() {
    // 1.
  const { handleSubmit, formState: { errors }, register, watch } = useForm();
  // 2.
  const selectedReferrer = watch('found-through');
}

<label htmlFor="referrer">
    Hoe heb je dit recept gevonden?
    <select
        id="referrer"
        {...register("found-through")}
    >
        <option value="google">Google</option>
        <option value="vriend">Vriend</option>
        <option value="advertentie">Advertentie</option>
        <option value="anders">Anders</option>
    </select>
</label>
// 3.
{selectedReferrer === 'anders' && (
    // 4.
    <input
        type="text"
        // 5.
        {...register("found-through-anders", { required: true })}
    />
)}
```

### Formulier opties

* onSubmit: pas valideren wanneer er op de submit-knop geklikt wordt (standaard)
* onBlur: valideren zodra een gebruiker een veld weer heeft 'verlaten'
* onChange: valideren terwijl de gebruiker aan het typen is, dus op ieder onChange-event. Let op: het formulier zal bij elke toetsaanslag opnieuw valideren, dus dit heeft impact op de perfomance van jouw formulier. Bij een klein formulier (zoals alleen gebruikersnaam en wachtwoord) is dit geen probleem, maar bij een groter formulier wordt dit niet aangeraden.
* onTouched: valideren zodra een gebruiker een veld voor de eerste keer heeft 'verlaten', en daarna op ieder onChange-event.

Als je dit wilt wijzigen kun je de mode instelling van het formulier overschrijven:
```javascript
function App() {
  const { handleSubmit, formState: { errors }, register, watch } = 
      useForm({ mode: 'onBlur' });
}
// en eventueel default waardes meegeven:
function App() {
    const { handleSubmit, errors, register, watch } = useForm({
        mode: 'onBlur',
        defaultValues: {
            'found-through': 'advertentie',
            age: 12,
        },
    });
}
```
Let er wel op dat de keys moeten overeenkomen met de name attributen. (Eerste argument dat we aan de register functie meegeven)

## React routing

Omdat react een single page applicatie is willen de gebruikers wel dat de Url klopt en dat ze volgende en vorige kunnen doen.

Install react router dom.
```terminal
npm install react-router-dom --save
```

```React
import { 
    BrowserRouter as Router,
    Switch,
    Route,
} from "react-router-dom";
```

Als je hebt geimporteerd, vervang dan het huidige <> voor <Router>. (Dit moet om alle componoenten heen)

Nu moet je het <Switch> component plaatsen om alle pagina's waartussen je wilt switchen op basis van de url.

Nu gaan we bedenken welke pagina we bij welke URL we willen zien, wikkel je pagina in een route component en voeg path toe.
```react
<Route path="/"> //Met de / in je path bedoel je dit dus als basis-url.
 <HomePage />
</Route>
```

Zorg dat je URL's duidelijk beschreven staan en nooit hoofdletter of spaties bevat.

Voeg bij je homepage altijd exact toe aan je path.

Je kan nu niet meer naar "inwendige" sites linken met < a > dit zal nu met <Link> moeten.
Om sites te linken moet je { Link } importeren. "import { Link } from 'react-router-dom';"
en om naar andere sites te verwijzen gebruik je: 
```react
<p>Leer <Link to="/tanden-bleken">hier</Link> meer over het bleken van tanden</p>
```
#### Navigatie links
Om de navigatiebar bruikbaar te maken.
Een NavLink is bijna hetzelfde als een Link maar je kan ook een activeClassName toevoegen waardoor je met CSS styling kan toepassen als de link actief is.
Bijv. dat de tekst van de knop wordt onderstreept als deze werkzaam is.

```react
import {NavLink} from "react-router-dom";

<NavLink to = "/" exact activeClassName = "active-link">
          <li>
            Home
          </li>
          </NavLink>
          
          //CSS 
       .active-link {
  border-bottom: 2px solid white;
}   
```

#### Use history
Om de gebruiksgeschiedenis kort op te slaan, zodat de gebruiker op vorige en volgende kan klikken.

```react
import { Link, useHistory } from 'react-router-dom';

function HomePage() {
  const history = useHistory();
}

// Voeg een knop toe en link deze verder.

function HomePage() {
 const history = useHistory();

 function handleClick() {
   history.push(‘/afspraak-maken’);
 }

return (
  <button type="button" onClick={handleClick}>
   Maak gelijk een afspraak!
  </button>
  );
}

```

Er zijn nog meer handige hooks zoals:
* useLocation - om de huidige URL op te halen.
* useParams - om de waarde uit een dynamische url op te halen.
* useRouteMatch - wanneer je gebruik wil maken van deep linking.

