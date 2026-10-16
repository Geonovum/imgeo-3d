# Ontwerpprincipes

Voor de inhoud van de IMGeo-3D zijn de volgende ontwerpprincipes gehanteerd.

## Topografie

De IMGeo-3D bestaat uit 3D-abstracties van objecten in de werkelijkheid, gelimiteerd tot
de be­schre­ven, fysieke en functionele, to­po­grafische objecten met een duidelijk meervoudig gebruik,
samengevat onder de term 3D-basistopografie.

## Schaalbereik
De bestaande 2D-topografische gegevens zijn geschikt voor een schaalbereik van 1:500 tot 1:5.000. De IMGeo-3D voegt een derde ruimtelijke dimensie toe. Dit behoudt dezelfde schaalnauwkeurigheid.

## Reële en virtuele objecten
De domeinmodellen BGT 1.2 en IMGEO 2.2 bevatten voornamelijk fysieke, concrete topografische objecten. Deze objecten zijn binnen het NEN3610-2011 raamwerk gepositioneerd. Aangezien nieuwere versies van BGT en IMGEO zich gaan baseren op NEN3610-2022 ([[NEN3610]]) zal deze versie ook als topmodel gebruikt worden voor IMGeo-3D. Een belangrijk verschil tussen de NEN3610:2011 en NEN3610:2022 is het onderscheid dat gemaakt is in de NEN3610:2022 tussen een [Reëel Object](https://definities.geostandaarden.nl/nen3610-2022/nl/page/reeel_object) en een [Virtuele ruimte](https://definities.geostandaarden.nl/nen3610-2022/nl/page/virtuele_ruimte). Ook in CityGML 3.0 wordt een duidelijk onderscheid gemaakt in ruimte en in fysiek object dat de ruimte begrenst. Hiermee wordt het mogelijk om bijvoorbeeld asfalt (Reëel object) te modelleren als horizontale begrenzing van de onderkant van een weg (Virtuele ruimte) of daken (Reëel object) als horizontale begrenzing aan de bovenkant van een verblijfsobject (Virtuele ruimte). Het laatste voorbeeld vergt een uitbreiding van BGT/IMGEO Objecten.   

![Voorstelling van objecttypen BGT en IMGEO onder de NEN3610:2022](media/BGT-NEN3610-2022-mapping.png "Voorstelling van hoe een mapping van (deels toekomstig) BGT en IMGEO zou kunnen zijn onder het NEN3610:2022 raamwerk")

## 3D Dekking
IMGeo 3D kent dezelfde dekking als IMGEO en BGT in het horizontale vlak. In het verticale vlak is de dekking zowel bovengronds als ondergronds. Deze dekking beschrijft de ruimtelijke scope van het 3D model en impliceert niet dat binnen deze gehele ruimte daadwerkelijk objecten zijn gemodelleerd.

## IMGeo-objecten in de BGT
nvt...?

## Modellering
IMGeo-3D hanteert het Basismodel Geo-informatie (NEN 3610:2022) voor de
modellering. NEN 3610:2011 conformeert zich aan de ISO 19100 standaarden voor
geo-informatie. Deze gelden daarom ook voor de BGT. IMGeo-3D bouwt voort op CityGML en sluit aan bij het CityGML 3.0 Conceptual Model. Daarmee wordt de bestaande relatie met CityGML voortgezet, en gebruikt het model de vernieuwde conceptuele modellering van CityGML 3.0. Het is mogelijk om bestaande CityGML 1.0 en 2.0 data up te graden naar CityGML3.0. 

### Level Of Detail (LOD)
Een belangrijk concept in 3D-modellering is het Level Of Detail <a>LOD</a>. Een LOD representeert daarbij een specifieke geometrische abstractie van een object in de werkelijkheid. Door deze abstracties op gestandaardiseerde wijze te definiëren, is het mogelijk om datasets op verschillende detailniveaus te gebruiken en kunnen gegevens uit verschillende bronnen beter worden gecombineerd. De LOD's zijn daarmee niet verschillende objecten, maar verschillende geometrische representaties van hetzelfde object.  

Het verplicht te gebruiken LOD in de 3D BGT is LOD 0.1. Aanvullend hierop kunnen objectgroepen in LOD 1.2, LOD 1.3, LOD2.2 gerepresenteerd worden. Voor inwinning van BIM-modellen is het mogelijk om LODC.1 en LODD.2 te gebruiken. Zie [Bijlage 2 LOD Frameworks](#lod-frameworks) voor toelichting op deze LOD's. 

### Niveau van Semantishe Decompositie
Een belangrijke verandering in CityGML 3.0 is het onderscheid tussen en het loskoppelen van Level Of Detail en semantische decompositie. 

### 3D Coordinaten 
Ongeacht het Level Of Detail dat gebruikt wordt voor de geometrische representatie van de objecten in de werkelijkheid zal de geometrie opgebouwd worden in driedimensionale ruimte. Dit betekent dat de geometrie (punten- lijnen - vlakken - volumes) van objecten opgesteld is met (X, Y, Z) coordinaten.   

## Geen inhoud van de BGT: macro-objecten en micro-objecten

nader te bepalen

