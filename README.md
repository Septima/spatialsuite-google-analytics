spatialsuite-google-analytics
=============================

Google Analytics modul

Septima v/ Klavs P. Christensen. klavsATseptima.dk www.septima.dk

F�r installation

I Google Analytics oprettes og konfigureres en konto. Informationer fra ops�tningen af denne konto skal bruges i konfigurationen af modulet. Se nedenfor

--------------------
INSTALLATION
--------------------

1:    Download modulet https://github.com/Septima/spatialsuite-google-analytics/archive/1.0.zip    
1.a:  Kopi�r modulet "google-analytics" til [cbinfo.config.dir]/modules/thirdparty/septima/google-analytics.  
1.b:  Skriv f�lgende i modules.xml:  
```xml
	 <module name="google-analytics" dir="thirdparty/septima/google-analytics"/>.
```

2  :  Inklud�r toolet i profile.xml. (Evt i include-fil s� det automatisk kommer med i alle profiler)  
```xml
<tool module="google-analytics" name="ga-plugin"/>
```

3.b:  Inklud�r en cbinfo-parameter med id'et p� korrekt ejendom:
```xml
    <!-- =================================== -->
    <!-- GOOGLE ANALYTICS                    -->
    <!-- =================================== -->   
    <param name="module.google-analytics.id">UA-XXXXXXX-XX</param>
```

--------------------
Forberedelse af Google Anlytics
--------------------

Det tager noget tid at blive fortrolig med Google Analytics. Her gives en vejledning i hvordan Analytics skal konfigureres og en overordnet gennemgang af mulighederne for analyse.  

Google Analytics er struktureret i Konto -> Ejendomme -> Visninger  
* En konto er oprettet og ejet af et Google-bruger-id.
* Adgangen til kontoen kan deles med andre brugere.

#### Ops�tning:  

##### Konto  
Opret en konto i Analytics ( http://www.google.com/analytics/ )
* Hvis du IKKE er logget ind i Analytics s� er der en knap p� forsiden "Opret konto"
* Hvis du ER logget skal du g� til administration-menuen.
* Opret en konto. Navnet er valgfrit, men jeg anbefaler noget i stil med SpatialMap.[DINKOMMUNE] (feks: SpatialMap.Favrskov)  

##### Ejendomme  
Under kontoen oprettes to ejendomme, en intern og en ekstern
* Giv ejendommene de navne som du bruger om dine sites, feks. WebGIS og Borgersite
* Hver ejendom har et Sporings-id, UA-XXXXX-X; Det er dette id, der skal skrives i cbinfo.xml for hhv. det interne og eksterne site.

##### Visninger  
Hver ejendom er blevet oprettet med en standard-visning
* Omd�b denne visning til SITENAVN-Alle Profiler. (Feks.: WebGIS - Alle Profiler). Denne visning bliver bruget til at dataopsamle p� tv�rs af alle profiler p� dit site.
* For hver profil som du �nsker at m�le s�rskilt skal du oprette en visning. Jeg anbefaler at kalde visningen SITENAVN-PROFILNAVN (Feks. WebGIS - Byg). Konfigurer visningen s�ledes:
 * Opret filter med navn: profilid (feks byg)
 * Filtertype: tilpasset->Inklud�r
 * Filterfelt: "Brugerdefineret"
 * Filtreringsm�nster: profilid (byg)
 * Forskel p� sm� og store bogstaver: Nej
 * Gem filter og visning

#### Analyse

Der logges ind i Google Analytics. Forsiden viser en tr�struktur, Konti -> Ejendomme -> Visninger, over det man har adgang til.

V�lg en visning feks. �WebGIS - Alle Profiler�.

Man kan nu navigere i forskellige visninger og det anbefales, at man g�r sig fortrolig med den anvendte terminologi. V�r specielt opm�rksom p� det aktive dato-interval �verst til h�jre. Der vises kun h�ndelser for det aktive interval. 

Brugere p� siden (Hvor mange brugere, hvorfra og hvorn�r)
* Realtid - Oversigt
* M�lgruppe -> Oversigt Oversigt, som viser overordnede tal om antal sidevisninger og brugere. Fra denne oversigt kan der klikkes ned i forskellige aspekter af data.
* M�lgruppe -> Demografi -> Geografisk Omr�de viser hvor brugere er lokaliseret
* M�lgruppe -> Teknologi -> Browser og OS giver oversigt over hvilke typer browsere, der anvendes. Der leveres statistik p� sk�rmopl�sninger, operativsystem og meget andet.

H�ndelser (Hvad laver brugerne)  
Der dataopsamles p� hvilke temaer, der v�lges, hvilke knapper, der trykkes p� og zoomlevels i kortet
* Realtid -> H�ndelser. Viser h�ndelser indenfor de seneste tredive minutter. Anvendes til at finde ud af, hvad der sker lige nu.
* Indhold -> H�ndelser -> Oversigt. Nederst til h�jre klikkes p� �Vis fuld rapport�. Nu vises en liste over h�ndelser.

Hvis ikke Kategori for h�ndelse er valgt som prim�re dimension s� v�lg den.  
Som sekund�r dimension v�lges H�ndelser -> H�ndelsesetiket. Nu vises alle h�ndelser med information. Det kan eksempelvis ses hvor mange gange de enkelte temaer er blevet t�ndt.  
Lister i Google Analytics kan eksporteres til diverse formater, hvor regnearksformater er gode til efterf�lgende filtrering, sortering og analyse.

