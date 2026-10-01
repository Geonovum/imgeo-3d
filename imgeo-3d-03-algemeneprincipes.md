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

Het functioneel gebied in de BGT kent het object Kering. In IMGeo-3D valt functioneel gebied onder het concept Virtuele ruimte. Dit sluit aan op CityGML3.0 die onderscheid maakt in Ingenomen Ruimte(OccupiedSpace) en Vrije Ruimte (UnoccupiedSpace) waarbij de ruimte met de properties class, functie en gebruik gespecificeerd kunnen worden. <mark> Wordt nu hetzelfde bedoeld in IMGEO? Is het LandUse? Hoe wordt dit nu gebruikt? Voor nu buiten scope. </mark> 

## Coördinaat-referentiesysteem

Het toegepaste coördinaatsysteem voor IMGEO-3D is een samengesteld CRS voor Nederland met de naam RDNAP(EPSG:7415). Dit coördinaatsysteem is een samenstelling van het Geprojecteerd CRS Rijksdriehoeksmeting (RD-stelsel (EPSG:28992)), waarmee men de x en y coördinaten kan duiden, en het Vertikaal CRS Normaal Amsterdams Peil (NAP (EPSG:5709)).

De coördinaatgetallen zijn daarbij op millimeternauwkeurigheid met als eenheid meters. Het coördinaatgetal heeft maximaal drie cijfers achter de komma. <mark>(Waarom?!?! Onhandig met BIM of vergelijkingen)</mark> Zo nodig wordt daarvoor afgerond,zodanig dat als het vierde cijfer achter de komma de waarde 1 t/m 4 bedraagt, het derde cijfer achter de komma niet wijzigt en als het vierde cijfer achter de komma de waarde 5 t/m 9 bedraagt, het derde cijfer achter de komma met één wordt
verhoogd, met mogelijk ook implicaties voor de voorliggende cijfers, waarbij dezelfde regel geldt.

Het RD-stelsel voldoet aan de eisen van de Europese richtlijn INSPIRE. Deze
stelt dat binnen de Europese continentale aardschol, waartoe ook Nederland en
het Nederlandse deel van de Noordzee behoort, geldt dat coördinaten herleidbaar
moeten zijn tot het European Terrestrial Reference System 1989 (ETRS89) voor de
horizontale component. <mark> Hoe dan? ER is toch geen z? </mark>

## Geometrietypen

Het BGT-informatiemodel beschrijft het geometrietype als een associatie van een
object met een geometrie-object. Daarbij maakt de BGT onderscheid in vlak-,
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

wordt:

| *Object*                                                    | *BGT classificatie*            | *Plus classificatie*                       | *Geometrie*            |*Ruimte*        |
|-------------------------------------------------------------|--------------------------------|--------------------------------------------|------------------------|----------------|
| *Bouwwerk*                                                  |                                |                                            |                        |              |
| **Pand**                                                    | Grondvlaksituatie van BAG-pand |                                            | LOD0 2D Multivlak              | 3D             |
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

