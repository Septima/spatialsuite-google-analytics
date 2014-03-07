spatialsuite-google-analytics
=============================

Google Analytics modul

Septima v/ Klavs P. Christensen. klavsATseptima.dk www.septima.dk

F�r installation

I Google Analytics oprettes en Web App, som svarer til Spatial Map-urlen, eks. kort.ishoej.dk. Se nedenfor.  

Web Appens Egenskabs-id noteres og skal bruges i ops�tningen af modulet.  

Vigtigt: Den profil, der automatisk oprettes under den nye Web App skal omd�bes til �*ditcbkortsite* Alt�  

--------------------
INSTALLATION
--------------------

1:    Install the module
1.a:  Copy the standard module "google-analytics" to [cbinfo.config.dir]/modules/standard.
1.b:  Write the following entry in [cbinfo.modules]: <module name="google-analytics" dir="thirdparty/septima/google-analytics"/>.

2  :  Add tool to profile.
         <tool module="google-analytics" name="ga-plugin"/>

3.b:  Add a cbinfo parameter with the ID of the Google Analytics account:
```xml
    <!-- =================================== -->
    <!-- GOOGLE ANALYTICS                    -->
    <!-- =================================== -->   
    <param name="module.google-analytics.id">UA-XXXXXXX-XX</param>
```

Om Google Analytics  

Struktur  

GA er struktureret i Konto -> Web Apps -> Profiler  

En konto er oprettet og ejet af et Google-bruger-id. Adgangen til kontoen kan deles med andre brugere. Bruger har adgang til specifikke profiler. Administrator har adgang til alle profiler
Kontoejer kan oprette Web Apps. Registrering af h�ndelser sker p� Web App-niveau. Web Apps kaldes ogs� Ejendom og Egenskab
Under en Web App oprettes et antal profiler. Profiler anvendes til at filtrere i hvilke h�ndelser man �nsker at analysere. Som default oprettes en profil �All Web Site data�, som ikke filtrerer.

Uhensigtsm�ssighed ved GA: Hvis man ikke omd�ber default-profilen for en Web App er det umuligt at skelne dem fra hinanden.  

Administration af rettigheder foreg�r p� profil-niveau og det er selvf�lgelig vigtigt, at kunne skelne dem fra hinanden. Derfor; omd�b straks default-profilen til noget sigende n�r en Wep App er oprettet.

Analyse

Der logges ind i Google Analytics. Forsiden viser en tr�struktur, Konti -> Web Apps -> Profiler, over det man har adgang til.
V�lg profilen �SpatialMapUrl Alle h�ndelser�.
Man kan nu navigere i forskellige visninger og det anbefales, at man g�r sig fortrolig med den anvendte terminologi. V�r specielt opm�rksom p� det aktive dato-interval �verst til h�jre. Der vises kun h�ndelser for det aktive interval. 

Analyse af h�ndelser

I menuen til venstre er specielt to menupunkter interessante til analyse af h�ndelser:
Standardrapporter -> Realtid -> H�ndelser. Viser h�ndelser indenfor de seneste tredive minutter. Anvendes til at finde ud af, hvad der sker lige nu.
Standardrapporter -> Indhold -> H�ndelser -> Oversigt.
Nederst til h�jre klikkes p� �Vis fuld rapport�. Nu vises en liste over h�ndelser.
Hvis ikke Kategori for h�ndelse er valgt som prim�re dimension s� v�lg den.
Som sekund�r dimension v�lges H�ndelser -> H�ndelsesetiket. Nu vises alle h�ndelser med information. Det kan eksempelvis ses hvor mange gange de enkelte temaer er blevet t�ndt.
Lister i Google Analytics kan eksporteres til diverse formater, hvor regnearksformater er gode til efterf�lgende filtrering, sortering og analyse.

Analyse af sidevisninger og brugere

I menuen til venstre er f�lgende menupunkter specielt interessante:
Standardrapport -> M�lgruppe -> Oversigt, som viser overordnede tal om antal sidevisninger og brugere. Fra denne oversigt kan der klikkes ned i forskellige aspekter af data.
Standardrapport -> M�lgruppe -> Demografi -> Geografisk Omr�de viser hvor brugere er lokaliseret
Standardrapport -> M�lgruppe -> Teknologi -> Browser og OS giver oversigt over hvilke typer browsere, der anvendes. Der leveres statistik p� sk�rmopl�sninger, operativsystem og meget andet.

