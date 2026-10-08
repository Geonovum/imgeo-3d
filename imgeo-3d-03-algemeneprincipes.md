# Algemene principes

Voor de inhoud van de IMGeo-3D  zijn de volgende algemene principes gehanteerd.

## Bronhouders

Het bronhoudersprincipe blijft in 3D ongewijzigd t.o.v. BGT/IMGEO. 

## Manier van 3D inwinning

Er zijn verschillende methoden om 3D-gegevens voor IMGeo-3D in te winnen en te verwerken. Er zijn drie belangrijke routes om tot 3D-geoinformatie voor IMGeo-3D te komen. Dit zijn: 

- **Directe 3D inwinning:** 3D gegevens worden rechtstreeks in de werkelijkheid ingewonnen met bijvoorbeeld LiDAR, fotogrammetrie of landmeetkundige metingen. 
- **3D-verrijking van bestaande 2D registraties:** Bestaande 2D IMGeo-/BGT-gegevens worden aangevuld met hoogte- en andere 3D-informatie en vervolgens verwerkt tot 3D-geoinformatie.  
- **Van 3D-BIM naar 3D-Geo:** bestaande 3D BIM-modellen worden getransformeerd naar 3D-Geoinformatie. 

IMGeo-3D houdt rekening met verschillende methoden waarop 3D-gegevens kunnen worden ingewonnen en opgebouwd. De wijze waarop gegevens zijn ingewonnen, bepaalt welke informatie beschikbaar is en welke mogelijkheden en beperkingen dit met zich meebrengt voor de verdere verwerking en modellering.

## Talud

Kruinlijngeometrie vervalt in IMGeo-3D. 

## Functioneel gebied

In IMGeo-3D valt functioneel gebied onder het concept Virtuele ruimte. Dit sluit aan op CityGML3.0  die onderscheid maakt in Ruimte die kan worden geclassificeerd als Ingenomen Ruimte(OccupiedSpace) en Vrije Ruimte (UnoccupiedSpace) waarbij de ruimte met de properties class, functie en gebruik gespecificeerd kunnen worden.

## Coördinaat-referentiesysteem
Het toegepaste coördinaatsysteem voor IMGEO-3D is een samengesteld CRS voor Nederland met de naam RDNAP(EPSG:7415). Dit coördinaatsysteem is een samenstelling van het Geprojecteerd CRS Rijksdriehoeksmeting (RD-stelsel (EPSG:28992)), waarmee men de x en y coördinaten kan duiden, en het Vertikaal CRS Normaal Amsterdams Peil (NAP (EPSG:5709)).

De coördinaatgetallen zijn daarbij op millimeternauwkeurigheid met als eenheid meters. Het coördinaatgetal heeft maximaal drie cijfers achter de komma. <mark>(Waarom?!?! Onhandig met BIM of vergelijkingen)</mark> Zo nodig wordt daarvoor afgerond,zodanig dat als het vierde cijfer achter de komma de waarde 1 t/m 4 bedraagt, het derde cijfer achter de komma niet wijzigt en als het vierde cijfer achter de komma de waarde 5 t/m 9 bedraagt, het derde cijfer achter de komma met één wordt
verhoogd, met mogelijk ook implicaties voor de voorliggende cijfers, waarbij dezelfde regel geldt.

Het RD-stelsel voldoet aan de eisen van de Europese richtlijn INSPIRE. Deze
stelt dat binnen de Europese continentale aardschol, waartoe ook Nederland en
het Nederlandse deel van de Noordzee behoort, geldt dat coördinaten herleidbaar
moeten zijn tot het European Terrestrial Reference System 1989 (ETRS89) voor de
horizontale component. <mark> Hoe dan? Er is toch geen z? </mark>

## Geometrietypen

Het BGT-informatiemodel beschrijft het geometrietype als een associatie van een
object met een geometrie-object. Daarbij maakt de BGT onderscheid in solid-, vlak-,
lijn- en puntgeometrie. Tot de BGT-inhoud behoren de volgende objecten.

| *Object*                                                    | *BGT classificatie*            | *Plus classificatie*                       | *Geometrie*            |*Ruimte*        |
|-------------------------------------------------------------|--------------------------------|--------------------------------------------|------------------------|----------------|
| *Bouwwerk*                                                  |                                |                                            |                        |              |
| **Pand**                                                    | Grondvlaksituatie van BAG-pand |                                            | 2D Multivlak              | 2D             |
|                                                             |                                |                                            |                        |              |
| **Overig bouwwerk**                                         | *Type:*                        |                                            |                        |              |
|                                                             | overkapping                    |                                            | 2D Multivlak              | 2D             |
|                                                             | open loods                     |                                            | 2D Vlak                   | 2D             |
|                                                             | opslagtank                     |                                            | 2D Vlak                   | 2D             |
|                                                             | bezinkbak                      |                                            | 2D Vlak                   | 2D             |
|                                                             | windturbine                    |                                            | 2D Vlak                   | 2D             |
|                                                             | lage trafo                     |                                            | 2D Vlak                   | 2D             |
|                                                             | bassin                         |                                            | 2D Vlak                   | 2D             |
|                                                             | niet-bgt                       | bunker                                     | 2D Vlak                   | 2D             |
|                                                             | niet-bgt                       | voedersilo                                 | 2D Vlak                   | 2D             |
|                                                             | niet-bgt                       | schuur                                     | 2D Vlak                   | 2D             |
|                                                             |                                |                                            |                        |              |

Dit wordt in Imgeo-3D:

| *Object*                                                    | *BGT classificatie*            | *Plus classificatie*                       | *Geometrie*            |*Ruimte*        |
|-------------------------------------------------------------|--------------------------------|--------------------------------------------|------------------------|----------------|
| *Bouwwerk*                                                  |                                |                                            |                        |              |
| **Pand**                                                    | Grondvlaksituatie van BAG-pand |                                            | LOD 0.1 3D TriangulatedSurface    | 3D             |
|                                                             | 3D blokmodel boven maaiveld van BAG-pand met 1 hoogte|                      | LOD 1.2 3D Solid met 2D grondvlak      | 3D             |
|                                                             | 3D blokmodel boven maaiveld van BAG-pand met meerdere hoogte|               | LOD 1.3 3D Solid met 2D grondvlak      | 3D             |
|                                                             | 3D blokmodel boven maaiveld van BAG-pand met meerdere hoogte|               | LOD 2.2 3D Solid       | 3D             |
|                                                             |                                |                                            |                        |              |
| **Overig bouwwerk**                                         | *Type:*                        |                                            |                        |              |
|                                                             | overkapping                    |                                            | LOD0 2D Multivlak               | 3D             |
|                                                             | open loods                     |                                            | LOD0 2D Vlak                   | 3D             |
|                                                             | opslagtank                     |                                            | LOD0 2D Vlak                   | 3D             |
|                                                             | bezinkbak                      |                                            | LOD0 2D Vlak                   | 3D             |
|                                                             | windturbine                    |                                            | LOD0 2D Vlak                   | 3D             |
|                                                             | lage trafo                     |                                            | LOD0 2D Vlak                   | 3D             |
|                                                             | bassin                         |                                            | LOD0 2D Vlak                   | 3D             |
|                                                             | niet-bgt                       | bunker                                     | LOD0 2D Vlak                   | 3D             |
|                                                             | niet-bgt                       | voedersilo                                 | LOD0 2D Vlak                   | 3D             |
|                                                             | niet-bgt                       | schuur                                     | LOD0 2D Vlak                   | 3D             |
|                                                             |                                |                                            |                        |              |




Objecten die virtuele ruimte zijn, doen, in tegenstelling tot alle objecten die Reeël object zijn én BGT-vlakobjecten, niet mee in de topologische structuur. Virtuele ruimte objecten liggen als een overlay over andere BGT-objecten. De begrenzing van virtuele ruimte hoeft niet samen te vallen met de begrenzing van
reeële objecten.

<mark> Wat moeten we hiermee? een nen2660:RuimtelijkGebied nen2660:isBegrensdDoor een nen2660:ReeelObject en een nen2660:RuimtelijkGebied nen2660:bevat een nen2660:ReeelObject. Kunnen we hier wat mee?  
nen2660-term:SpatialRegion 
 a skos:Concept ;
 skos:broader nen2660-term:PhysicalObject ;
 skos:definition "A physical object that encloses a particular area, such as a room, roadway and river, 
that is bounded by real objects or other spatial areas (e.g., by usage or convention) and that contains 
primarily liquid or gaseous amount of matter"@en ;
 skos:definition "Een fysiek object dat een bepaald gebied omsluit, zoals een vertrek, rijbaan en rivier,
en dat wordt begrensd door reële objecten of andere ruimtelijke gebieden (bijvoorbeeld op basis van 
gebruik of conventie) en dat voornamelijk vloeibare of gasvormige hoeveelheid materie bevat"@nl ;

https://w3id.org/nen2660/term#SpatialRegion
</mark>

Voor de beschrijving van geometrieën geldt het ISO 19107 Spatial Schema. Voor de uitwisseling wordt gebruik gemaakt van Geography Markup Language (GML) 3.1.1. 


In de LOD 0-serie van IMGeo-3D zijn de geometrieën uit het GML 3.1.1 Simple Features Profile v1.0 toegestaan, aangevuld met cirkelbogen (GM_Arc).

In de LOD 1-, LOD 2- en LOD 3-serie van IMGeo-3D wordt voor volumetrische geometrieën GM_Solid gebruikt. De begrenzing van deze solids wordt opgebouwd uit oppervlakken die gebruikmaken van de geometrieën die binnen het GML 3.1.1 Simple Features Profile v1.0 zijn toegestaan, aangevuld met cirkelbogen (GM_Arc)


De geometrie-objecten worden in het informatiemodel met hun ISO 19107 naam,
zoals GM_Surface, aangeduid. Bij objecten die een lijn- of een vlakgeometrie
kunnen hebben, is een associatie met GM_Object gelegd. Een GM_Object mag een ISO
punt, lijn, of volume zijn. In de praktijk betekent dit voor BGT objecten dat lijn-
of vlakgeometrie is toegestaan. Bij hetzelfde objecttype kan in het optionele
IMGeo-deel mogelijk wel puntgeometrie voorkomen.

| Geometrietype      | ISO aanduiding  |
|--------------------|-----------------|
| Vlak               | GM_Surface      |
| Lijn               | GM_Curve        |
| Punt               | GM_Point        |
| Multivlak          | GM_MultiSurface |
| Multipunt          | GM_MultiPoint   |
| Solid              | GM_Solid        | 
| MultiSolid         | GM_MultiSolid   |
| Geometrie algemeen | GM_Object       |

Zowel lijn-, vlak- als solidvormige objecten kunnen bestaan uit een boogvorm. Voor de
representatie van boogvormen zijn er twee mogelijkheden in de BGT toegestaan,
namelijk benadering van de boog met:

-   lineaire lijnsegmenten, de zogenaamde gestrookte boog;

-   beschrijving van de boog met drie punten (GM_Arc).

Voor het weergeven van cirkels kan men gebruik maken van twee bogen. Gebruik van
GM_Circle is niet toegestaan.





































Topologie in 3D
=========


<mark> Bij de LOD 0.0 En LOD 0.1 objecten blijft de topologie hetzelfde  </mark> 

De vlakobjecten in de BGT op maaiveldniveau (niveau 0) partitioneren de ruimte.
Dat betekent dat:

-   elk van deze objecten topologisch gestructureerd moet zijn;

-   deze objecten naadloos op elkaar aan moeten sluiten, zodat er op
    maaiveldniveau geen gaten voorkomen;

-   deze objecten elkaar niet mogen overlappen.

Op maaiveldniveau is het grondgebied van Nederland volledig gebiedsdekkend. Het
totaal oppervlak van alle objecten op maaiveldniveau is gelijk aan het
dekkingsgebied (zie paragraaf 2.4).

Bij niveauverschillen kunnen objecten elkaar wel overlappen. Objecten op een
niveau anders dan het maaiveld doen echter niet mee in de topologische
structuur. Dit houdt onder meer in dat wanneer men dit object verwijdert er
minimaal één ander object op niveau 0 overblijft.

Elk objecttype bevat één geometrie op één niveau. Dit betekent bijvoorbeeld dat
een weg zich opsplitst in meerdere wegdelen met eigen identificaties als deze
over een brug loopt, ook al zijn de rest van de kenmerken gelijk.


In het 3D geval dat elk object een 3D Solid is: 
-> Elke Solid is Geldig 
-> Solids mogen niet ongewenst overlappen  


-> 3D topologie is nog niet opgelost (nog geen oplossing voor). Wiskundigen (computational geometry)
        -> computation fluid dynamics (Github City for CFD (TU Delft)) stad en terrein als een waterdichte mesh. 
        -> Finite element modelling (FEM) voor aardbevegingen op gebouwen (gebied in voxels -> kracht op loslaten, wat doet dit met een gebouw)
-> het gebouw is een intersectionsurface ( City GML, daar bovenop een gebouw als Solid).

zie de productbeschrijving 3D Basisvoorziening https://3d.kadaster.nl/productbeschrijving/


Closure Surfaces kunnen gebruikt worden om Solid Objecten deel te laten zijn van de kwaliteitscheck op kaartdichtheid. zie: https://docs.ogc.org/guides/20-066.html#_closure_surfaces

Terrain Intersection Curves https://docs.ogc.org/guides/20-066.html#_terrain_intersection_curves kunnen interessant zijn voor uitgiftepeil/bouwpeil afspraken.


Voorbeeld: 

<bldg:Building gml:id="building_001">

    <!-- LOD0 -->
    <core:lod0MultiSurface>
        <!-- LOD0 geometry -->
    </core:lod0MultiSurface>

    <!-- LOD1 -->
    <core:lod1Solid>
        <!-- LOD1 geometry -->
    </core:lod1Solid>

    <!-- LOD2 -->
    <core:lod2Solid>
        <!-- LOD2 geometry -->
    </core:lod2Solid>

    <!-- LOD3 -->
    <core:lod3Solid>
        <!-- LOD3 geometry -->
    </core:lod3Solid>

    <!-- Closure Surface -->
    <core:boundary>
        <core:ClosureSurface gml:id="closure_001">

            <core:lod3MultiSurface>
                <!-- ClosureSurface geometry -->
            </core:lod3MultiSurface>

        </core:ClosureSurface>
    </core:boundary>

        <!-- Terrain Intersection Curve -->
    <core:lod1TerrainIntersectionCurve>
   
                <!-- Terrain Intersection Curve Geometry -->
    </core:lod1TerrainIntersectionCurve>

</bldg:Building>


Voor eventuele Solids kan gebruik gemaakt worden van de kennis die is opgedaan in het val3dity https://github.com/tudelft3d/val3dity intitiatief en de 3D BAG https://docs.3dbag.nl/en/schema/concepts/


Kennis te gebruiken uit: https://docs.geostandaarden.nl/3dbv/basis-al-prod-20201009/


https://www.pdok.nl/-/verbetering-kwaliteit-3d-basisvoorziening



Alles wat bindend is, in de standaard. Alles wat uitleg is daarbuiten. 

-> Standaard IMGEO-3D 
-> Praktijkrichtlijn of een handreiking (nagaan welke dit wordt)