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
---
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
---
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
---
### Forloops javascript
Een loop wordt gebruikt om herhaaldelijk dezelfde code uit te voeren.
```javascript
for (let i = 0; i < 10; i++) {
    console.log("counting", i);
}
```
---
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
---
#### Arrow Functions

De nieuwe 'verkorte' manier om functies te gebruiken.
```javascript
const getArea = (width, length) => {
   return width * length;
}

// wanneer je alleen een return-statement in de functie hebt staan mag je het zelfs verkorten tot:
const getArea = (width, length) => width * length;

getArea(3, 4);
```
---
### Scope

Scope geeft aan in hoever variabelen toegankelijk zijn.
Dit kan je goed zien door middel van de { } waartussen de variabelen staan.

De lokale scope kan wel naar buiten kijken, maar je kan niet van buiten de scope naar binnen kijken.
Bij functies geldt hetzelfde principe.
---

### Methodes

Een methode is een functie als property in een object.

```javascript
// 1. FUNCTIE
function congratulate() {
  console.log("Gefeliciteerd!");
}

// 2. METHODE, want hij is een property op het birthday object
const birthday = {
  congratulate: function () {
      console.log("Gefeliciteerd!");
  },
};
```

In JavaScript zitten heel veel ingebouwde functies met methodes die gegroepeerd zijn in een aantal ingebouwde JavaScript objecten:

#### String object (strings bewerken)
> Als je met een string object gaat werken krijgt iedere karakter een indexnummer (begint bij 0)
> * toUppercase() (alle letters naar hoofdletters)
> * toLowercase() (alles naar kleine letters)
> * charAt() (returned het karakter dat op het gevraagde indexnummer staat)
> * indexOf() (returned het indexnummer van de plek waarop het opgevraagde karakter het eerst voorkomt)
> * lastIndexOf()  (returned het indexnummer van de plek waarop het opgevraagde karakter het laatst voorkomt)
> * substring()  (returned alle karakters tussen de meegegeven indexnummers)
> * split() (hakt de string in stukjes op basis van een conditie en returned de stukjes in een array)
> * trim() (verwijdert spaties aan het begin en einde van een string)\
> * replace() (vervangt alle instanties van de gespecificeerde karakters met iets anders)
> * includes() (checkt of de string een specifiek karakter(s) bevat)

#### Math object (rekenkundige operaties uitvoeren)
> Bij math objecten moet je altijd de naam van het globale Math object benoemen!
> * Math.PI is een property (dus gebruik je niet de ronde haken!) en bevat het wiskundige getal pi
> * Math.round() rondt een getal af naar het dichtstbijzijnde hele getal
> * Math.sqrt() geeft de wortel van een getal terug
> * Math.ceil() rondt een getal naar boven af
> * Math.floor() rondt een getal naar beneden af
> * Math.random() genereert een random getal tussen 0 en 1 - en is dus bij iedere aanroep anders!

#### Date object (datums maken en formatteren)
> Om met datums te werken gebruik je Date object, zo een object representeert 1 specifiek moment in de tijd.
> Wanneer je een nieuwe date instantie maakt zonder specificaties zal deze automatisch "nu" worden.
```javascript
const dateOfBirth = new Date('Dec 26, 1992 15:45:55');
const dateOfBirth = new Date(1992, 11, 26, 15, 45, 55);
const dateOfBirth = new Date(1992, 11, 26);
```
> * getTime() - geeft het aantal milliseconden dat zijn verstreken sinds de epoch
> * getDay() - geeft de dag van de week (0 - 6)
> * getHours() - geeft het uur (0 - 23)
> * getMinutes() - geeft de minuten (0 - 59)
> * getMonth() - geeft de maand (0 - 11)
> * getSeconds() - geeft het aantal seconden (0 - 59)
```javascript
const dateOfBirth = new Date(1992, 11, 26);

// Hier hebben we niet zoveel aan:
const englishDate = dateOfBirth.toDateString(); // geeft Sat Dec 26 1992

// Nederlandse versie voluit
const longOptions = { 
  weekday: 'long',
  year: 'numeric',
  month: 'long',
  day: 'numeric', 
};

const dutchDate = dateOfBirth.toLocaleDateString('nl-NL', longOptions); // geeft zaterdag 26 december 1992
        
// Nederlandse versie kort
const shortOptions = {
  weekday: 'short', 
  month: 'long',
  day: 'numeric',
};

const dutchShortDate = dateOfBirth.toLocaleDateString('nl-NL', shortOptions); // geeft za 26 december
```

#### Array object (om arrays te bewerken)
> Werk je met het type array dan heb je array methodes nodig:
> * concat() - voegt twee arrays samen 
> * includes() - checkt of één van de items in de array een bepaalde waarde bevat, zoals “Lasagne bladen” of het getal 45. 
> * indexOf() - checkt het indexnummer van het item in de array met een bepaalde waarde, zoals “Lasagne bladen” 
> * join() - maakt een string van alle items in de array door ze achter elkaar te plakken. Wanneer je een argument meegeeft, zoals bijvoorbeeld een spatie, wordt deze tussen de items geplaatst.
> * push() - “pusht” een nieuw item, ofwel: voegt een item toe aan het einde van de array 
> * reverse() - draait de volgorde van de array om 
> * pop() - verwijdert het laatste item in de array en returned deze waarde 
> * shift() - verwijdert het eerste item in de array en returned deze waarde 
> * slice() - maakt een referentieloze kopie van een deel van de array. Dit betekent dat de originele array niet wordt aangepast. Dit kan handig zijn omdat je soms niet de originele array wil aanpassen, wat alle bovenstaande methodes wel doen.
> * splice() - voegt een item toe, vervangt of verwijderd een item op basis van indexnummer in de array. Het is dus een hele diverse methode die op verschillende manieren gebruikt kan worden! Deze methode verwacht drie parameters:

>  1. Het indexnummer (dus de positie) waar de operatie moet plaatsvinden
>  2. Hoeveel items er verwijderd moeten worden (wil je niets weghalen? Dan vul je 0 in)
>  3. Wat er toegevoegd moet worden (wil je niets toevoegen? Dan vul je 0 in)

### Array methodes
Je moet bij array methodes altijd een callback functie meegeven. Een callback is een functie die wordt aangeroepen door een andere functie, waarbij deze als parameter meegegeven wordt.
De orginele array's blijven intact.
```javascript
const students = ['Henk Jansen', 'Piet Pieters', 'Marieke Smit'];

students.map(() => {
   console.log('Student!');
});
```
#### map()
> Geeft een nieuwe array terug, waarin de waardes van de oude array en de gemaakte aanvullingen staan. De orginele array wordt niet aangepast.

>Een soort for loop type, als je returned in een variabele wordt het altijd een array!
> De parameter die je de callback meegeeft (altijd enkelvoud van de naam van de array zelf) bevat altijd de volledige entry van de loop
> Maak een variabele aan om de return type op te slaan.
```javascript
const outcome = students.map((student:string) => {
    console.log(student);
});
```

#### filter() (alle resultaten die voldoen terug)
> Geeft een nieuwe array terug met alle waardes die voldoen aan de gestelde conditie, orginele array wordt niet aangepast.

```javascript
const students = [
   {
       name: 'Henk Jansen',
       course: 'FSD Bootcamp',
       averageGrade: 7,
   },
   {
       name: 'Piet Pieters',
       course: 'HBO Software development',
       averageGrade: 6,
   },
   {
       name: 'Marieke Smit',
       course: 'FSD Bootcamp',
       averageGrade: 7.5,
   },
];

const bootcampStudents = students.filter((student) => {
    return student.course === 'FSD Bootcamp';
    // je kunt dit ook uitschrijven als:
    // if (student.course === 'FSD Bootcamp') {
    //    return true
    // }
})
```
#### find() (altijd maar 1 resulaat terug(de eerste die die vindt))
> Geeft een enkele waarde terug, het eerste element dat voldoet aan de gestelde conditie.
> De find methode is hetzelfde als hierboven alleen stopt deze als hij de eerste waarde vind.
#### sort()
> Geeft niets terug maar sorteert de bestaande array op basis van de gestelde conditie.
Sorteren gebeurt door het herhaaldelijk vergelijken van twee waardes: de huidige (a) met de vorige (b)
> *  Een negatief getal (dan moet a vóór b komen te staan)
> * Een positief getal (dan wordt b vóór a komen te staan)
> * Het cijfer 0 (dan zijn beide waardes gelijk)
```javascript
const numbers = [3, 1, 5, 4, 2];

numbers.sort((a, b) => {
   // als a groter is dan b, geef een positief getal terug
   if (a > b) {
       return 1;
   }
   // als a kleiner is dan b, geef een negatief getal terug
   if (a <  b) {
       return -1;
   }

   // als bovenstaande condities allebei niet waar zijn,
   // zijn de waardes even groot
   return 0;
})

console.log(numbers); // geeft [ 1, 2, 3, 4, 5 ]

// laag naar hoog:
numbers.sort((a, b) => {
    return a - b;
})

// of zelfs nog korter, omdat we slechts één regel in onze functie hebben staan:
numbers.sort((a, b) => a - b);

//hoog naar laag:
numbers.sort((a, b) => b - a);
```

### Destructuring

Het beknopter opschrijven van variabelen die vaker terug komen.
Het is belangrijk dat je de keys van het object exact overneemt anders krijg je undefined.

```javascript
const person = {
  firstname: 'Henk',
  lastname: 'Pieters',
  city: 'Amsterdam',
};

const first = person.firstname;
const last = person.lastname;

//word:

const { firstname, lastname } = person;
```
Het aanpassen van de data binnen destructuring kan ook dmv : daarmee overschrijf je de oorsponkelijke key.

```javascript
const studentInfo = {
    first: 'Henk',
    last: 'Pieters',
    contact: {
        email: {
          home: 'henkpieters@gmail.com',
          education: 'h.pieters@novi-education.nl',
        },
    }
};

const education = "Hogeschool Novi";

const { home, education: universityEmail } = studentInfo.contact.email;

console.log(education); // geeft "Hogeschool Novi"
console.log(universityEmail) // geeft "h.pieters@novi-education.nl"
```

Het hernoemen van verschillende variabelen gaat dus vrij makkelijk met destructureren:
```javascript
const dog = { name: "Pluisje", color: "black" };
const cat = { name: "Minoes", color: "red" };

const { name: dogName } = dog;
const { name: catName } = cat;

console.log(dogName) // geeft "Pluisje"
console.log(catName) // geeft "Minoes"
```

Je kan ook Array's desctructuren. Ipv de {} gebruik je nu de [] haken.
Alleen bij Array's kan je ze niet hernoemen. Dit is allemaal afhankelijk van de volgorde van de array.

```javascript
const someArray = ['one', 'two', 'three'];

const [third, second, first] = someArray;

console.log(first); // geeft "three"
console.log(second); // geeft "two"
console.log(third); // geeft "one"
```
Wil je bij een array bepaalde variabelen of object aanspreken gaat dit met een extra komma.
```javascript
function getNames() {
  return ['Henk', 'Piet', 'Jan'];
}

const [nameOne, nameTwo, nameThree] = getNames();
console.log(nameOne); // geeft "Henk"
console.log(nameTwo); // geeft "Piet"
console.log(nameThree); // geeft "Jan"
//----------------------------------
const [first,, second] = getNames();

console.log(first); // geeft "Henk"
console.log(second); // geeft "Jan"
//----------------------------------
function getNames() {
    return ['Henk', 'Piet', 'Jan', 'Klaas'];
}

const [first, ...rest] = getNames();

console.log(first); // geeft "Henk"
console.log(rest); // geeft ['Piet', 'Jan', 'Klaas']
```

### Truthy en falsy
Soort van war en soort van niet waar.

## TESTEN!
Testen is superbelangrijk! Je zelf continu tussendoor testen zorgt dat je op tijd bij fouten bent.
CHECK YO SELF BEFORE YOU WRECK YO SELF!

Dit kan natuurlijk automatisch, maar dit kost werk om op te zetten. Zie het als een investering.

Een veelgebruikte testing library voor Javascript is Jest.

Als je denkt dit moet makkelijker kunnen is er vast al een andere developer die dit heeft gemaakt en openbaar aanbied.
Dit soort dingen staan op NPM (NODE PACKAGE MANAGER) als je iets download dan download je een package.
Als je deze integreert in je code heet dit een dependency.

Dependencies zijn nodig om de applicatie te draaien.

Development dependencies zijn nodig tijdens het ontwikkelen. (zoals Jest)

Alle dependencies die we in een project installeren komen in de map node-modules terecht.
DEZE MAP NOOIT VERSTUREN NAAR GITHUB. altijd node_modules toevoegen aan git ignore bestand.

NPM vertrouwt op package.json hierin staat een lijst die alle packages van het project bijhouden.

package.json aanmaken:
```
npm init
//stappen doorlopen en daarna zal er ongeveer zo uit zien:
{
    "name": "De-naam-van-jouw-project-map",
    "version": "1.0.0",
    "description": "Dit project is een demo voor het gebruik van packages!",
    "main": "index.js",
    "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
},
    "keywords": ["demo", "project", "novi", "hogeschool"],
    "author": "Piet pieters",
    "license": "ISC",
    "dependencies": {
}
}
//Bij installeren van een dependencie altijd aangeven om welk type het gaat:
// gewone dependency
npm install NAAM-VAN-DE-PACKAGE --save

// development dependency
npm install NAAM-VAN-DE-PACKAGE --save-dev
```

Jest:
-Arrange (klaarzetten).
-Act (handelen).
-Assert (beweren).

Jest expect functie.

Code loskoppelen van de tests.

1. Maak een package.json aan door npm te initialiseren "**npm init**".
2. Installeer jest met het commando "**npm install jest --save-dev**"
3. Voeg de node_modules toe aan de .gitignore file.
4. Voeg "**npx jest**" toe aan de **test key** in de package.json en "n**px jest --watch**" (of --watchAll als je zonder git bezig bent) aan de **test:watch key**.
5. Maak een map genaamd "**__tests__**" en stop daar jouw testbestand in "index.test.js".
6. Roep daarin de "test functie" aan en geef deze een beschrijving en anonieme functie mee
```javascript
test("Controleer of de test wel werkt", ()=>{
    console.log("Ik wordt uitgevoerd!");
})
```
7. Test altijd eerst even of dit werkt met een "console.log" en voer het test commando uit: "npm run test"
8. ARRANGE: zet de waardes klaar waar je mee gaat testen
9. ACT: voer de functie uit en geef de gecontroleerde waardes daaraan mee.
10. ASSERT: maak een bewering over de verwachte uitkomst en vergelijk dit met de daadwerkelijke uitkomst door middel van de "**expect**" functie, met daaraan een beweringsfunctie gekoppeld zoals "**.toEqual**".

Loskoppelen van de code.
11. Maak een apart bestand met een gewone ".js" extensie (zoals index.js) 
12. Plak de functies daar in en haal ze weg uit het test-bestand.
13. Exporteer de functies met "module.exports = {naam: functieNaam }"
14. Importeer de functies in het testbestand met de "require" functie die wijst naar het pad waar de functies in staan (const add= require("../index.js).add)
15. Bonus: schrijf het netter op door destructuring te gebruiken.
```javascript
function add(num1, num2) {
    return num1 + num2;
}

function findByName (names, user){
    for (let i = 0; i < names.length; i++) {
        const currentUser = names[i];
        if (currentUser.name === user){
            return currentUser;
        }
    }
    return null;
}

module.exports = {
    add: add,
    findByName: findByName,
}
```
```javascript
const add = require("../index").add;
const findByName = require("../index").findByName;

const { add, findByName } = require("../index");
```

## Koppelen aan je webpagina

Je koppelt je javascript pagina net als je CSS bestand in je Html pagina met de script tag.

```html
<script src="main.js"></script>
```

Het interacteren met HTML gaat niet zomaar, hier heb je DOM voor nodig (Document Object Model)

Dit is een losstaande set regels.

* Een model van een HTML pagina maken
* Javascript toegang geven tot onderdelen op de pagina om ze aan te kunnen passen.

In DOM praat je niet over HTML elementen maar over NODES.
Alle nodes samen is de document node. Je begint altijd bij de document node.

Wanneer je iets aan wilt passen in de DOM tree moet je de volgende stappen nemen:
1. Lokaliseer de plek van het het element waar je mee wil werken en sla deze referentie op.
    * Een enkel element: wellicht willen we een element toevoegen aan de <div> node. Om dit element te lokaliseren gebruiken we zijn unieke id attribuut:
```html
const container = document.getElementById("page");
```
 * Meerdere elementen tegelijkertijd: wellicht willen we alle <li< nodes selecteren om een aanpassing te maken. Dit kan op basis van hun class-attribuut (die is immers hetzelfde) en geeft een array met nodes terug.
```html
const listItems = document.getElementsByClassName("ingrediënt");
```

2. Aanpassingen 
   maken
Wanneer je het element hebt gevonden kun je aanpassingen maken.
   * Een nieuwe node maken
    
```html
const warningMessage = document.createElement(‘p’);. 
```
* Een attribuut toevoegen.
```html
warningMessage.setAttribute(‘class’, ‘warning’);
```
* Een attribuut verwijderen.
    
```html
warningMessage.removeAttribute(‘class’);
```
* Tekst toevoegen
```html
warningMessage.textContent = “Hier wordt je dik van”;
```

* Een element toevoegen aan de DOM tree
```html
container.appendChild(warningMessage);
```    

## Event Listeners

We willen ook kunnen reageren op acties van de gebruikers. Dit gaat op de volgende manier:

1. Interactie triggert een event (zoals een muisklik of het invoeren van tekst)
2. Dit event triggert code (zoals een specifieke functie)
3. De code reageert op de gebruiker (door bijvoorbeeld een aanpassing te maken in de DOM)

Om een event te kunnen triggeren heb je een event listener nodig.
Die zet je op een specifiek element die wacht tot er iets gebeurt. En wanneer dit gebeurt zal de event listener uitvoeren.

Verschillende soorten events:

* Keyboard events - heeft een gebruiker een toets ingedrukt of losgelaten?
* Mouse events - heeft de gebruiker iets met de muis gedaan?
* Focus events - wordt een invoerveld gebruikt?
* Clipboard events - is er iets gekopieerd, geplakt of geknipt?
* Form events - is het formulier verstuurd of gereset?
* View events - is er iets met de weergave gebeurd?

Iedere keer als er een event wordt getriggered zal de event listener een event object aanmaken.
Daarin staat alle informatie wat zojuist gebeurd is. 
Welke toets bij een keyboard event, welk element etc.

Wil je dit event object gebruiken dan moet je event als parameter verwachten. Dit geef je aan met (e).

Verschillende dingen die je kan vinden:
* keycode - welke knop heeft de gebruiker ingedrukt.
* timestamp - welk moment werd dit event getriggered.
* target value - de waarde van het input veld toen het event werd getriggered.

Wanneer je een functie wilt aanroepen op basis van een event gebruik je:
```html
button.addEventListener('click', () => {
 calculateSum(2,4);
});
```