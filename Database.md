# Databases


Data toevoegen aan je database

Database woorden in HOOFDLETTERS, namen van tabellen en kolommen in kleine letters.

jpa of hibernate zijn ORM's

Iets toevoegen aan een tabel:
1. INSERT INTO
```
INSERT INTO table [ ( column [, ...] ) ]
    { DEFAULT VALUES | VALUES ( { expression | DEFAULT } [, ...] ) [, ...] | query }
```

Iets opvragen van een tabel:

SELECT * FROM public.(tabelnaam)

Ieder tabel heeft 1 primary key.. vaak id of klantnummer etc.
Deze kan je gebruiken om te verwijzen.

Foreign key verwijst naar een primary key.

" * " is alles van een tabel.

Indelen van de volgorde:

ORDER BY (row naam) (sorteren)

DISTINCT = alleen verschillende types opvragen.

ALL = returns true als alle condities kloppen

WHERE = een criterium (is gelijk aan(filter van de rijen)) met AND kan je vergelijkingen samenvoegen, BETWEEN tussen 2 data of OR is een of vergelijking. NOT is zoeken naar iets waar het "NIET" in zit.

met WHERE LIKE P% (zoek naar namen die beginnen met een P daarna maakt het niet uit)
WERE LIKE %p% (zoek naar een naam waar een p in zit.)
Als je wilt zoeken of er een letter inzit gebruik je %, dit geldt als wildcard. P% achter is een P met daar achter maakt niet uit. %p% is een p tussenin, voor en achter de p maakt niks uit.

voorbeeld: WHERE leeftijd > 20 

IN is een vergelijking van namen die in het lijstje moeten staan.

WHERE naam IN ('Bart', 'Peter', 'Nick');

Je kan ze ook combineren (je zoekt nu naar de hoofddocenten in de tabel cursus. )

SELECT *
FROM docent
WHERE id IN (SELECT hoofddocent_id
            FROM cursus)

DELETE statement (verwijdert hele regels uit een tabel)

DELETE FROM docent
WHERE id = 6;

Kan alles zijn ook WHERE naam = 'Rob';

Bewerken van Query's gaat met UPDATE

UPDATE cursus
SET start_datum = '2021-03-01';

daar kan je ook nog een WHERE aan toe voegen dus:

UPDATE cursus
SET start_datum = '2021-03-01'
WHERE id = 6;

en meerdere kan je onder elkaar zetten:

UPDATE cursus
SET start_datum = '2021-03-01'
,   ects = 20
WHERE id = 6;

JOIN STATEMENT

Verschillende tabellen samenvoegen.
Als de voolean op true uitkomt zal de combinatie worden gekoppeld in de output.
```sql
T1 { [INNER] | { LEFT | RIGHT | FULL } [OUTER] } JOIN T2 ON boolean_expression
```


CRUD operaties
C = Creat
R = Read
U = Update
D = Delete