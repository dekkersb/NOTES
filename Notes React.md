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

---
## React hook form.

```javascript
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