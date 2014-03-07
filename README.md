spatialsuite-google-analytics
=============================

Google Analytics modul

Septima v/ Klavs P. Christensen. klavsATseptima.dk www.septima.dk

Før installation

I Google Analytics oprettes en Web App, som svarer til Spatial Map-urlen, eks. kort.ishoej.dk. Se nedenfor.  

Web Appens Egenskabs-id noteres og skal bruges i opsætningen af modulet.  

Vigtigt: Den profil, der automatisk oprettes under den nye Web App skal omdøbes til “*ditcbkortsite* Alt”  

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
Kontoejer kan oprette Web Apps. Registrering af hændelser sker på Web App-niveau. Web Apps kaldes også Ejendom og Egenskab
Under en Web App oprettes et antal profiler. Profiler anvendes til at filtrere i hvilke hændelser man ønsker at analysere. Som default oprettes en profil “All Web Site data”, som ikke filtrerer.

Uhensigtsmæssighed ved GA: Hvis man ikke omdøber default-profilen for en Web App er det umuligt at skelne dem fra hinanden.  

Administration af rettigheder foregår på profil-niveau og det er selvfølgelig vigtigt, at kunne skelne dem fra hinanden. Derfor; omdøb straks default-profilen til noget sigende når en Wep App er oprettet.

Analyse

Der logges ind i Google Analytics. Forsiden viser en træstruktur, Konti -> Web Apps -> Profiler, over det man har adgang til.
Vælg profilen “SpatialMapUrl Alle hændelser”.
Man kan nu navigere i forskellige visninger og det anbefales, at man gør sig fortrolig med den anvendte terminologi. Vær specielt opmærksom på det aktive dato-interval øverst til højre. Der vises kun hændelser for det aktive interval. 

Analyse af hændelser

I menuen til venstre er specielt to menupunkter interessante til analyse af hændelser:
Standardrapporter -> Realtid -> Hændelser. Viser hændelser indenfor de seneste tredive minutter. Anvendes til at finde ud af, hvad der sker lige nu.
Standardrapporter -> Indhold -> Hændelser -> Oversigt.
Nederst til højre klikkes på “Vis fuld rapport”. Nu vises en liste over hændelser.
Hvis ikke Kategori for hændelse er valgt som primære dimension så vælg den.
Som sekundær dimension vælges Hændelser -> Hændelsesetiket. Nu vises alle hændelser med information. Det kan eksempelvis ses hvor mange gange de enkelte temaer er blevet tændt.
Lister i Google Analytics kan eksporteres til diverse formater, hvor regnearksformater er gode til efterfølgende filtrering, sortering og analyse.

Analyse af sidevisninger og brugere

I menuen til venstre er følgende menupunkter specielt interessante:
Standardrapport -> Målgruppe -> Oversigt, som viser overordnede tal om antal sidevisninger og brugere. Fra denne oversigt kan der klikkes ned i forskellige aspekter af data.
Standardrapport -> Målgruppe -> Demografi -> Geografisk Område viser hvor brugere er lokaliseret
Standardrapport -> Målgruppe -> Teknologi -> Browser og OS giver oversigt over hvilke typer browsere, der anvendes. Der leveres statistik på skærmopløsninger, operativsystem og meget andet.

