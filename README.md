# Microservices-Blog
## Andreea Nenciu och Tijana Ilić

### Laboration 4: Skapa arkitektur

#### Motivation

Vi skapade en blogg där man kan logga in som vanlig användare eller administratör. Alla som är inloggade kan läsa blogginlägg, men bara admin kan skriva nya blogginlägg som sparas i databasen. 

Vi valde att bygga 3 mikrotjänster i ASP.NET Core med EF Core: en frontend-del med statiska filer (AppClient), ett Rest-API med SQL-databas för användare (Identity) och ett till Rest-API med egen SQL-databas för bloggen (Blog). 


Vi valde att separera projektet i 3 delar så att man kan lätt använda de separat i andra projekt om det skulle behövas, på det sättet får man flexibilitet och mer skalbarhet. API-erna handlar om två olika resurser (användare för login och blogginlägg för själva bloggen).
Vi byggde projektet med Docker-compose och där har vi 5 containers:
* 1 container för frontend-delen (appclient) som beror på de 2 API-erna 
* 2 enskilda containers för API-er (identity och blog) som beror på respektive databaser
* 2 enskilda containers för SQL-databaserna (identitydb och blogdb)

#### Instruktioner
Man ska köra projektet med Docker-compose.
Login:
* som användare: Username:User, Password:User
* som admin: Username:Admin, Password:Admin

#### Introduktion och syfte
Målet är att skapa en modern arkitektur för en applikation

#### Uppgift
Systemet ska utvecklas testdrivet från grunden. Testerna ska täcka en rimlig mängd av
programmet för att underlätta för er.
Systemet ska ha ett användargränssnitt (CLI, Desktop, webb eller app). UX eller design av
användargränssnittet kommer inte att bedömas. Det är helt okey att använda en vit sida med
knappar som aktiverar funktioner.
Systemet ska ha någon form av persistens, databas, textfiler eller lagring i extern tjänst.
Systemet ska vara utvecklat med en mikroservicearkitektur. Systemet ska innehålla minst tre
stycken tjänster. Samtliga tjänster ska motiverat användas från användargränssnittet (de är
okey att de kallas på genom andra tjänster).
Systemet kommer att användas även i den sista labben.

#### Exempel på system att välja
* Ett enkelt buggrapporteringssystem. Lägga till, läsa och sätta status på buggar.
* En väldigt enkel twitterklon, användare loggar in och postar meddelanden som alla
kan läsa.
* En dagbok/blogg, logga in skriv inlägg och läsa dem.
* En meddelandetjänst, skicka meddelanden mellan två personer, spara dessa i en
databas och visa dem via CLI eller hemsida.
* En beräkningstjänst, skicka in något som ska beräknas via UI och få tillbaka detta
när det är klart.
* Ett litet onlinespel (avancerat).

#### Redovisning
Källkoden ska vara pushad till ett eget publikt repository på GitHub. Uppgiften ska
genomföras parvis och fullständiga namn ska finnas med i README.md i repots
main-branch (master). I README.md ska också innehålla en kortfattad beskrivning av er
arkitektur och motivation kring de val ni gjort.
