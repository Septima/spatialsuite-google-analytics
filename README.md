spatialsuite-google-analytics
=============================

Google Analytics modul

Septima v/ Klavs P. Christensen. klavsATseptima.dk www.septima.dk

Før installation

I Google Analytics oprettes og konfigureres en konto. Informationer fra opsætningen af denne konto skal bruges i konfigurationen af modulet. Se nedenfor

--------------------
INSTALLATION
--------------------

1:    Download modulet https://github.com/Septima/spatialsuite-google-analytics/archive/2.0.1.zip
1.a:  Kopiér modulet "google-analytics" til [cbinfo.config.dir]/modules/thirdparty/septima/google-analytics.
1.b:  Skriv følgende i modules.xml:
```xml
<module name="google-analytics" dir="thirdparty/septima/google-analytics"/>.
```

2  :  Inkludér toolet i profile.xml. (Evt i include-fil så det automatisk kommer med i alle profiler)
```xml
<tool module="google-analytics" name="ga-plugin"/>
```

3  :  Inkludér cbinfo-parametre

3.a:  ID'et på korrekt ejendom:
```xml
<!-- =================================== -->
<!-- GOOGLE ANALYTICS                    -->
<!-- =================================== -->
<param name="module.google-analytics.id">UA-XXXXXXX-XX</param>
```
3.b:  Skal oplysninger om brugeren gemmes?:
```xml
<param name="module.google-analytics.storeprincipal">true</param>
```

--------------------
Forberedelse af Google Anlytics
--------------------

Det tager noget tid at blive fortrolig med Google Analytics. Her gives en vejledning i hvordan Analytics skal konfigureres og en overordnet gennemgang af mulighederne for analyse.  

Google Analytics er struktureret i Konto -> Ejendomme -> Visninger  
* En konto er oprettet og ejet af et Google-bruger-id.
* Adgangen til kontoen kan deles med andre brugere.

#### Opsætning:

##### Konto  
Opret en konto i Analytics ( http://www.google.com/analytics/ )
* Hvis du IKKE er logget ind i Analytics så er der en knap på forsiden "Opret konto"
* Hvis du ER logget skal du gå til administration-menuen.
* Opret en konto. Navnet er valgfrit, men jeg anbefaler noget i stil med SpatialMap.[DINKOMMUNE] (feks: SpatialMap.Favrskov)  

##### Ejendomme  
Under kontoen oprettes to ejendomme, en intern og en ekstern
* Giv ejendommene de navne som du bruger om dine sites, feks. WebGIS og Borgersite
* Hver ejendom har et Sporings-id, UA-XXXXX-X; Det er dette id, der skal skrives i cbinfo.xml for hhv. det interne og eksterne site.

##### Visninger  
Hver ejendom er blevet oprettet med en standard-visning
* Omdøb denne visning til SITENAVN-Alle Profiler. (Feks.: WebGIS - Alle Profiler). Denne visning bliver bruget til at dataopsamle på tværs af alle profiler på dit site.
* For hver profil som du ønsker at måle særskilt skal du oprette en visning. Jeg anbefaler at kalde visningen SITENAVN-PROFILNAVN (Feks. WebGIS - Byg). Konfigurer visningen således:
 * Opret filter med navn: profilid (feks byg)
 * Filtertype: tilpasset->Inkludér
 * Filterfelt: "Brugerdefineret"
 * Filtreringsmønster: profilid (byg)
 * Forskel på små og store bogstaver: Nej
 * Gem filter og visning

#### Analyse

Der logges ind i Google Analytics. Forsiden viser en træstruktur, Konti -> Ejendomme -> Visninger, over det man har adgang til.

Vælg en visning feks. "WebGIS - Alle Profiler".

Man kan nu navigere i forskellige visninger og det anbefales, at man gør sig fortrolig med den anvendte terminologi. Vær specielt opmærksom på det aktive dato-interval øverst til højre. Der vises kun håndelser for det aktive interval.

Brugere på siden (Hvor mange brugere, hvorfra og hvornår)
* Realtid - Oversigt
* Målgruppe -> Oversigt Oversigt, som viser overordnede tal om antal sidevisninger og brugere. Fra denne oversigt kan der klikkes ned i forskellige aspekter af data.
* Målgruppe -> Demografi -> Geografisk Område viser hvor brugere er lokaliseret
* Målgruppe -> Teknologi -> Browser og OS giver oversigt over hvilke typer browsere, der anvendes. Der leveres statistik på skærmopløsninger, operativsystem og meget andet.

Håndelser (Hvad laver brugerne)
Der dataopsamles på hvilke temaer, der vælges, hvilke knapper, der trykkes på og zoomlevels i kortet
* Realtid -> Hændelser. Viser håndelser indenfor de seneste tredive minutter. Anvendes til at finde ud af, hvad der sker lige nu.
* Indhold -> Hændelser -> Oversigt. Nederst til højre klikkes på "Vis fuld rapport". Nu vises en liste over hændelser.

Hvis ikke Kategori for hændelse er valgt som primære dimension så vælg den.
Som sekundær dimension vælges Hændelser -> Hændelsesetiket. Nu vises alle hændelser med information. Det kan eksempelvis ses hvor mange gange de enkelte temaer er blevet tændt.
Lister i Google Analytics kan eksporteres til diverse formater, hvor regnearksformater er gode til efterfølgende filtrering, sortering og analyse.

