# Notes Javascript
- node (bestandsnaam).js
- nodemon (bestandsnaam).js (werkt automatisch bij als je saved)
- const variabel (1x toewijzen)
- let variabel  (meerdere keren toewijzen)
- uitkomst loggen -> console.log()
- undefined = per ongeluk niks
- null = expres niks

### If-else statements
```javascript
const grade = 8.7;

if (grade < 5.5) {
   console.log('Onvoldoende');
} else if ((grade >= 5.5 && grade < 8)) {
   console.log('Voldoende');
} else {
  console.log('Goed'); 
}
```
> je kan ook alleen " if " gebruiken.

Heb je meer dan 3/4 if's gebruik dan een switch met cases.

```javascript
const fruit = "Appels";

switch (fruit) {
  case 'Bananen':
    console.log('Het zijn bananen!');
    break;
  case 'Appels':
    console.log('Het zijn appels!');
    break;
  case 'Citroenen':
    console.log('Het zijn citroenen!');
    break;
  default:
    console.log('Er is geen vrucht gekozen');
}
```

### Array's
Array is een lijst waarin waardes zijn opgeslagen.

```javascript
let lasagneIngredients = [“Geraspte kaas”, “Spinazie”, “Knoflook”, “Olijfolie”, “Lasagne bladen”, “Ui”];
```

##### Lengte
```javascript
lasagneIngredients.length;
``` 

##### Overschrijven
```javascript
lasagneIngredients[3] = "Kokosolie";
```
### Objects
Een object groepeert variabelen bij elkaar die iets met elkaar gemeen hebben.

```javascript
const recipe = {
     name: 'Spinazie lasagne',
     cookingTime: 45,
     isGlutenFree: false,
     ingredients: ['Lasagne bladen', 'Spinazie', 'Kaas'],
     printInfo: () => {
         console.log('Dit recept is niet glutenvrij.');
     }
};
```

Toegang krijgen van de data in een object kan met:
```javascript
const lasagneInfo = recipe.printInfo();
```
Waardes aanpassen in een object:
```javascript
recipe.cookingTime = 55;
```

### Forloops javascript
Een loop wordt gebruikt om herhaaldelijk dezelfde code uit te voeren.
```javascript
for (let i = 0; i < 10; i++) {
    console.log("counting", i);
}
```

### Functies
Een functie is een groepje statements en expressies die samen een specifieke taak uitvoeren.

De waarde die je bij een functie meegeeft noem je parameters.

Als je verwacht dat de functie ook een waarde teruggeeft noem je die **return value**.

Lege functie:
```javascript
function functieNaam(parameters, parameters) {
    // code blok, wat moet er uitgevoerd worden?
}
//eventueel return met: return parameters;
//functieaanroepen: functieNaam()
```

Functie voorbeeld met return:
```javascript
function bereidGroente(groente) {
    // 1. Was groente
    // 2. Laat groente uitlekken
    // 3. Snij groente
    
    return groente;
}
bereidGroente(tomaten);
bereidGroente(sperziebonen);
```

Functie voorbeeld met parameters.
```javascript
function getArea(width, length) {
    return width * length;
}
```
Dit roep je dan op met:
```javascript
const livingroom = getArea (4, 6);
const kitchen = getArea (10, 4);
```

Wil je meerdere waardes terug geven return dan met een array.
```javascript
function getAreaSizes(width, length, depth) {
   const area = width * length;
   const volume = width * length * depth;
   return [area, volume];
}

const kitchenSizes = getAreaSizes(4, 4, 2.5);
console.log(kitchenSizes); // geeft [16, 40]
```



