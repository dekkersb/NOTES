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

1. Access modifier
* Public
* Private
* Protected

2. Static of niet
   *
3. return type
4. methodenaam
5. parameters
