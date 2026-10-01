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
geo-informatie. Deze gelden daarom ook voor de BGT.

De BGT is een tweedimensionale objectenverzameling. Om de stap naar 3D op een
later moment te kunnen maken, is het BGT-model gebaseerd op CityGML 2.0. 

IMGeo-3D bouwt voort op CityGML en sluit aan bij het CityGML 3.0 Conceptual Model. Daarmee wordt de bestaande relatie met CityGML voortgezet, en gebruikt het model de vernieuwde conceptuele modellering van CityGML 3.0. Het is mogelijk om bestaande CityGML 1.0 en 2.0 data up te graden naar CityGML3.0. 

### Level Of Detail (LOD)
Een belangrijk concept in 3D-modellering is het Level Of Detail <a>LOD</a>. Een LOD representeert daarbij een specifieke geometrische abstractie van een object in de werkelijkheid. Door deze abstracties op gestandaardiseerde wijze te definiëren, is het mogelijk om datasets op verschillende detailniveaus te gebruiken en kunnen gegevens uit verschillende bronnen beter worden gecombineerd. De LOD's zijn daarmee niet verschillende objecten, maar verschillende geometrische representaties van hetzelfde object.   

Als basis voor IMGeo-3D kunnen de vier Levels of Details (LOD-0, -1, -2 en 3) van de CityGML standaard gebruikt worden.  

![CityGML3.0 LOD hoofdniveaus](media/LOD/CityGML30_LOD.png "(CityGML3.0 LOD hoofdniveaus)")

De volgende definities worden in de CityGML specificatie gegeven voor het voorbeeld gebouw:

<table>
  <caption> LoD van een gebouw zoals beschreven in de CityGML3.0 standaard </caption>
  <tr>
    <th> Level </th>
    <th> Beschrijving </th>
  </tr>
  <tr>
    <td> LoD0 </td>
    <td> Een representatie van een gebouw of vertrek met niet volumetrische geometrie zoals een punt, vlak (polygoon) of meerdere vlakken (voor bijvoorbeeld de 'footprint' of 'roofprint'). </td>    
  </tr>
   <tr>
    <td> LoD1 </td>
    <td>  Een representatie van een gebouw of vertrek als een blok/prisma vorm. </td>    
  </tr>
   <tr>
    <td> LoD2 </td>
    <td> Een representatie van een gebouw of vertrek als een volume met (meestal) verticale muren, waarbij de vlakken die het dak representeren zijn verfijnd. </td>    
  </tr>
   <tr>
    <td> LoD3 </td>
    <td> Een representatie van een gebouw of vertrek als een schil of een collectie van constructieve elementen. Dit is de enige LoD die gevelopeningen ondersteunt. </td>    
  </tr>
</table>

De documentatie van CityGML 3.0 over de LOD's is algemeen en conceptueel. Dit biedt flexibiliteit om verschillende soorten 3D-modellen binnen het CityGML-framework te modelleren, maar maakt het tegelijkertijd lastig om eenduidig vast te stellen hoe een bepaalde LOD de werkelijkheid representeert. Zo is niet altijd vastgelegd welke geometrische vereenvoudigingen moeten worden toegepast en welke onderdelen van een gebouw bij een bepaald LOD moeten worden gemodelleerd.

Om hier verbetering in te brengen heeft [[Biljecki16c]] in 2016 een verfijning gemaakt die voortbouwt op het toen ter tijd actuele CityGML2.0 LoD framework. Dit is gedaan door iedere CityGML LoD op te splitsen in 4 sub groepen. Zo is LoD1 opgesplitst in LoD1.0, 1.1, 1.2 en 1.3. Het eerste nummer van de verfijnde LoD komt overeen met de CityGML LoD. Het tweede nummer geeft de verdere verfijning aan. De documentatie van de verfijnde LoD is uitgebreider dan die van de CityGML standaard. 

<figure id="refined-lods">
  <img
    src="media/LOD/TUDeflt_Refined_LODs_for_CityGML_Buildings.png"
    alt="Refined LoDs for CityGML Buildings">

  <figcaption>
    Refined LoDs for CityGML Buildings. Bron: [[Biljecki16c]].
  </figcaption>
</figure>

### Niveau van Semantishe Decompositie
Een belangrijke verandering in CityGML 3.0 is het onderscheid tussen en het loskoppelen van Level Of Detail en semantische decompositie. Dit betekent dat het binnen de CityGML 3.0 standaard mogelijk is om een gebouw in een LOD2 te modelleren, de muren die onderdeel zijn van dit gebouw conform LOD3 en de ruimten binnen dit gebouw als LOD0.  

![Verschillend LOD gebruik in semantische decompositie gebouw](media/LOD/CityGML30_LOD_2.png "(Verschillend LOD gebruik in de semantische decompositie van een gebouw)")

### 3D Coordinaten 
Ongeacht het Level Of Detail dat gebruikt wordt voor de geometrische representatie van de objecten in de werkelijkheid zal de geometrie opgebouwd worden in driedimensionale ruimte. Dit betekent dat de geometrie (punten- lijnen - vlakken - volumes) van objecten opgesteld is met (X, Y, Z) coordinaten.   

## Geen inhoud van de BGT: macro-objecten

Geen verandering t.o.v. BGT/IMGEO. 

