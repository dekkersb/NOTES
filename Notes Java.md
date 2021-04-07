# NOTES Java

- Na elke {} een tab verspringen.
- Klassenaam Hoofdletter en overeenkomen met bestandsnaam.
- Methodenamen kleine letters.
- Variabelen kunnen 1 waarde bevatten en maar 1 datatype hebben.
-
---
### Comparison operators Java
- ==
- !=
- .>
- <
- .>=
- <=

- String vergelijken gaat met:
> Als je in Java twee variabelen van het datatype String met elkaar wilt vergelijken, doe je dat niet met de ==-operator, maar met de equals() of equalsIgnoreCase()-methode.
---
### Java Primitieve datatypes
- Integer (Getal)
- Boolean (True / False)
- Char (1 letter)
- Double (Getal met cijfers achter de komma)

### Java niet primitieve datatypes
- String (tekst)
- Array (Lijst - verzameling)
- Class (Klasse)
- Interface (...?)
---
### Java If-Else
https://www.youtube.com/watch?v=yvWnj_HfG6s
- Als de conditie waar is, voer dan de code tussen de accolades uit.
```java
public class VoorbeeldIfElse {
    public static void main(String[] args) {
        int cijfer = 6;
        if(cijfer >= 6) {
            System.out.println("Jij hebt een voldoende. Goed gedaan!");
        } else {
            System.out.println("Je hebt helaas een onvoldoende. Ik geloof dat je het kunt. Succes bij het hertentamen.");
        }
    }
}
```
- Je kan hier nog meerdere "else if" aan toevoegen. Worden dit er echter teveel gebruik dan switch/case.
  Om de code te stoppen als een waarde wordt gevonden gebruik je break; wordt er geen waarde gevonden gebruik dan default. (dan wordt er een standaard bericht geplaatst)
  https://www.youtube.com/watch?v=O4KGYGQvHmw&
```java
public class WeekdagenSwitch {
    public static void main(String[] args) {
        int weekdag = 0; // verander deze waarde
        String dag;
        switch(weekdag) {
            case 0:
                dag = "zondag";
                break;
            case 1:
                dag = "maandag";
                break;
            case 2:
                dag = "dinsdag";
                break;
            case 3:
                dag = "woensdag";
                break;
            case 4:
                dag = "donderdag";
                break;
            case 5:
                dag = "vrijdag";
                break;
            case 6:
                dag = "zaterdag";
                break;
            default:
                dag = "onbekend";
        }
        System.out.println("Het is: " + dag);
    }
}
```
---
### Java Methode
https://www.youtube.com/watch?v=cCgOESMQe44

Onderdeel van een object of klasse.

```java
public class VoorbeeldMetReturn {
    public static void main(String[] args) {
        String name = lastWinner();
        System.out.println("The last winner is: " + name);

    }
    public static String lastWinner() {
        List<String> winners = new ArrayList();
        winners.add("Nico Rosberg");
        winners.add("Lewis Hamilton");
        winners.add("Lewis Hamilton");
        winners.add("Lewis Hamilton");
        
        // Save last winner to temporary variable:
        String lastWinnerName = winners.get(winners.size() - 1);
        return lastWinnerName; // return key word is needed to return.
    }   
}
```
1. Access modifier. https://www.youtube.com/watch?v=H0OetoieSDQ
* Public (vanuit de hele applicatie aan te roepen)
* Private (alleen vanuit de klasse aan te roepen)
* geen modifier (aan te roepen vanuit klasses in dezelfde package)
* Protected (alleen aan te roepen in dezelfde package en subklassen)

2. Static of niet. https://www.youtube.com/watch?v=yn9cDLVr_wk
   
3. return type (data type wat je terug wilt geven, anders void)
4. methodenaam
5. parameters
---
### Klassen en objecten
https://www.youtube.com/watch?v=Mm06BuD3PlY

Klasse is een blauwdruk voor een object, een klasse beschrijft wat een object weet en doet.

```java
public class Ingredient {
    public String name;
    public String colour;
}
public class Voetbalclub {
    public String naam;
    public String afkorting;
    public int oprichtingsjaar;
} 
```
Je maakt van een klasse een object met keyword **"new"**.

```java
public class VoorbeeldInitialisatie { 
    public static void main(String[] args) { 
        Ingredient vanille = new Ingredient();
        vanille.name = "Vanille";
        vanille.colour = "Yellow";
        System.out.println("Kleur van het object Vanille: " + vanille.colour);
        
        Voetbalclub ajax = new Voetbalclub();
        ajax.naam = "Ajax Amsterdam";
        ajax.afkorting = "AFCA";
        ajax.oprichtingsjaar = 1902;
        System.out.println(ajax.naam + " is opgericht in: " + ajax.oprichtingsjaar);

    }
}
```
---
### Getters & Setters
https://www.youtube.com/watch?v=6wVmqY-CrGM

In java gebruik je voor variabelen normaal een private access modifier. Om dan de gegevens toch aan te passen gebruik je public getters & setters.
Deze kan je simpel toevoegen door een shortcut van intelliJ: **rechterklik / generate / getters en setters.**
```java
public class Voetbalclub {
    private String naam;
    private String afkorting;
    private int oprichtingsjaar;
    
    // Getters
    public String getNaam() {
        return naam;
    }
    
    public String getAfkorting() {
        return afkorting;
    }
    
    public int getOprichtingsjaar() {
        return oprichtingsjaar;
    }

    // Setters
    public void setNaam(String naam) {
        this.naam = naam;
    }
    
    public void setAfkorting(String afkorting) {
        this.afkorting = afkorting;
    }   
    public void setOprichtingsjaar(int oprichtingsjaar) {
        this.oprichtingsjaar = oprichtingsjaar;
    }
}


//Ziet er zo uit in de main:

public class VoorbeeldGetterSetter { 
    public static void main(String[] args) {   
        Voetbalclub ajax = new Voetbalclub();
        ajax.setNaam("Ajax Amsterdam");
        ajax.setAfkorting("AFCA");
        ajax.setOprichtingsjaar(1902);
        System.out.println(ajax.getNaam() + " is opgericht in: " + ajax.getOprichtingsjaar());

    }
}
```
---
### Constructor
https://www.youtube.com/watch?v=G1Iln3PSrUg

Constructor lijkt op een methode maar is het niet. Heeft geen return type, geen void en kan alleen opgeroepen worden met "new".

Constructor heeft dezelfde naam als de klassenaam.
Je kan met een constructor gebruik maken van parameters, zodat je minder code hoeft te schrijven om variabelen aan te roepen.
```java
public Voetbalclub(String naam, String afkorting) {
    System.out.println("Deze code wordt gedraaid bij het instantieren van het object!");        
    System.out.println("De parameter naam heeft als waarde: " + naam);        
    System.out.println("De parameter afkorting heeft als waarde: " + afkorting);        
}
```
---
### Array's
https://www.youtube.com/watch?v=pTAda7qU4LY

Array geruik je als je het vast aantal weet.

- Array maken: **String[] firstnames;**
- Array's beginnen te tellen bij **[0]**
- Array inhoud aanpassen met "=" teken: **firstnames[1] = "Jan";**
- Array lengte: **firstnames.length**
- Array aanpassen met lengte (hier word de eerste positie aangepast omdat je bij 0 begint te tellen): **firstnames[firstnamesLength-1] = "Laatste naam";**

Arraylist gebruik je als je hem wilt kunnen uitbreiden.

Je moet hem wel eerst even toevoegen:
> import java.util.List; & import java.util.ArrayList;

Arraylist aanmaken:
> List<String> firstnames = new ArrayList<>();

- List inhoud ophalen met: **.get()**
- List lengte ophalen met: **.size()**
- List inhoud toevoegen met: **.add()**
- List inhoud aanpassen met: **.set()**
- List inhoud verwijderen met: **.remove()**
- List helemaal legen met: **.clear()**

Arraylist begint ook te tellen bij [0]

---
### Loops
#### For loop 
https://www.youtube.com/watch?v=3jMaKlNBjug

Word gebruikt om een exact aantal te herhalen.
```java
public class VoorbeeldForLussen {
    public static void main(String[] args) {
        String[] cities = {"Zeist", "Burg-Haamstede", "Den Dolder", "Soest"};
        
        // For-lus zonder index
        for(String city : cities) {
            System.out.println(city);     
        }
        
        // For-lus met index
        for(int i = 0; i < cities.length; i++) {
          System.out.println(cities[i] + "staat op positie: " + i);
        }
    }    
}
```
#### While loop 
https://www.youtube.com/watch?v=SGJ9DpxGCkY&

Word gebruikt op basis van een bewering, voor elke herhaling wordt gekeken of deze waar of onwaar is.
Blijft zich herhalen zolang deze waar is.

Bij een do-while lus wordt de code altijd minimaal 1x uitgevoerd ongeacht of de conditie waar of onwaar is.

```java
public class VoorbeeldWhileLussen {
    public static void main(String[] args) {
        int amountOfVisitors = 0;
        while (amountOfVisitors <= 10) {
            System.out.println("Amount of people inside: " + amountOfVisitors);
            amountOfVisitors++;
        }
        System.out.println("No more people allowed inside.");
    }
}
```
---
### Relaties
(Has-a)

Er zijn 2 types relaties: Aggregratie en Compositie

>Aggregratie
> 
> Een aggregatie is een relatie waarin geen eigenaarschap zit vastgelegd. Het ene object kan dus leven zonder het andere object.
> 
> * Gaat maar 1 kant op.
> * Een 0 tot meer relatie (een object kan 0 tot meerdere andere objecten bevatten)


> Compositie
> 
> Een compositie-relatie heeft dat wel. Als je een Car-object hebt met verschillende Part-objecten, waar de Car de eigenaar is, dan blijven de Part objecten alleen bestaan zolang het Car-object blijft bestaan. Verwijder je het Car-object dan worden ook alle Part-objecten verwijderd.

> Kardinaliteiten
>
> Het aantal relaties die objecten met elkaar hebben.
> - 0 tot 1 relatie: Een persoon heeft 0 of 1 rijbewijzen.
> - 1 tot 1 relatie: Een kind heeft altijd 1 biologische vader.
> - 0 tot N (of meer) relatie. Een persoon bezit 0 tot meerdere auto's
> - 1 tot N relatie. Een bon bevat 1 tot meer bestelregels.
> - Een N tot N relatie. Meerdere personen zijn eigenaar van een bedrijf en een bedrijf heeft meerdere eigenaren.
---

### Super- en subklassen
https://www.youtube.com/watch?v=iV-rrFETXjY

Als je veel dezelfde variabelen gebruikt wil je deze zoveel mogelijk opnieuw gebruiken.
Dit kan het beste met een super klasse, waar je de variabelen in zet.
Je kan dan met een subklasse diezelfde variabelen aanspreken en gebruiken.

> "The subclass extends the superclass"
> 
> (een klasse extends niet als je geen is-a kan doen.)
>
> Je kan maar 1 klasse extenden.

Je neemt niet alleen de variabelen over maar ook de methodes.

Maak alleen een subklasse als je de klasse meer specifiek moet maken.

In de subclass kan je ook nog eigen variabelen toevoegen en zelfs methodes overschrijven (@override https://www.youtube.com/watch?v=2b7B1n84dY4)

Om een subklasse te maken gebruik je extends in je klasse en verwijs je naar de superklasse.
>public class FamilyDoctor **extends** Person {

Je kan ook de methode van de superklasse uitbreiden. In de subklasse voeg je **super()** toe. (https://www.youtube.com/watch?v=hLYOpvoM4vk&)

#### Wanneer gebruik je override en wanneer gebruik je super?
> "Wil ik alle functionaliteit van de methode uit de superklasse en daarna nog iets extra's toevoegen?". Dan gebruik je super(). 
> 
> "Wil ik een gedeelte van de functionaliteit of wil ik de functionaliteit van de methode aanpassen?" Dan gebruik je @Override.
---
### Polymorphism
https://www.youtube.com/watch?v=Ft88V_rDO4I

> "Wanneer je een superklasse definieert, kan elke subklasse vervangen worden door zijn supertype."
 
> Overerving garandeert dat alle klassen gegroepeerd onder een superklasse dezelfde methodes hebben als de superklasse.
---
### Abstract

https://www.youtube.com/watch?v=52frlN8webg

Om een klasse abstract te maken moet je tussen public en class het woord **"abstract"** plaatsen.
> public abstract class Person

Als je een abstracte methode toevoegt aan een klasse moet de klasse ook abstract zijn.

Je gebruikt een abstracte klasse alleen om extend te worden. (soort template van een klasse)

---
