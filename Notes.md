#NOTES

### Forloops javascript
```javascript
(let i = 0; i < 10; i++) {
    console.log("counting", i);
}
```

### Comparison operators Java
- ==
- !=
- .>
- <
- .>=
- <=

- String vergelijken gaat met:
>Als je in Java twee variabelen van het datatype String met elkaar wilt vergelijken, doe je dat niet met de ==-operator, maar met de equals() of equalsIgnoreCase()-methode.

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

### Java
- Na elke {} een tab verspringen.
- Klassenaam Hoofdletter en overeenkomen met bestandsnaam.
- Methodenamen kleine letters.
- Variabelen kunnen 1 waarde bevatten en maar 1 datatype hebben.
- 

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
###Java Methode
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
1. Access modifier
* Public (vanuit de hele applicatie aan te roepen)
* Private (alleen vanuit de klasse aan te roepen)
* geen modifier (aan te roepen vanuit klasses in dezelfde package)
* Protected (alleen aan te roepen in dezelfde package en subklassen)

2. Static of niet
   *
3. return type (data type wat je terug wilt geven, anders void)
4. methodenaam
5. parameters

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

### Constructor

