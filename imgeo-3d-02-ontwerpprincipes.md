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
  <caption> LOD van een gebouw zoals beschreven in de CityGML3.0 standaard </caption>
  <tr>
    <th> Level </th>
    <th> Beschrijving </th>
  </tr>
  <tr>
    <td> LOD0 </td>
    <td> Ruimtes van objecten in de werkelijkheid (ruimtelijke objecten), kan men representeren door een punt, een verzameling lijnen of een verzameling vlakken. Fysieke objecten in de werkelijkheid (Reeële objecten) kan men representeren in LOD0 met behulp van een verzameling lijnen of verzameling vlakken. LOD0 vlakrepresentaties zijn vaak het resultaat van de projectie van het volume van het object op maaiveld. Dit kan een footprint zijn. Bijvoorbeeld van een gebouw of een kamer. LOD0 lijn representaties zijn vaak het resultaat van de projectie van verticale vlakken. Bijvoorbeeld een muur. Ook representeert het vaak de centrale as van netwerken, zoals weg- of rivierassen.  </td>    
  </tr>
   <tr>
    <td> LOD1 </td>
    <td> Ruimtes van objecten in de werkelijkheid (ruimtelijke objecten), kan men representeren door een verticale extrusie te maken van een horizontale footprint.  kan men in LOD1 weergeven met horizontale of verticale vlakken. </td>    
  </tr>
   <tr>
    <td> LOD2 </td>
    <td> Ruimtes van objecten in de werkelijkheid (ruimtelijke objecten), kan men representeren door een verzameling lijnen, een verzameling vlakken, of een enkele solid geometrie. Fysieke objecten in de werkelijkheid (Reeële objecten) kan men maken met een set vlakken. De vorm van de objecten in de werkelijkheid is gegeneraliseerd. Details als bijvoorbeeld uitstulpingen, inkepingen, vensterbanken, en ook structuren als balkonnen of dakkapelen worden vaak genegeerd. LOD2 lijn representaties kan men gebruik voor centrale as representaties van bijvoorbeeld een antenne of een schoorsteen. 
 </tr>
   <tr>
    <td> LOD3 </td>
    <td> Ruimtes van objecten in de werkelijkheid (ruimtelijke objecten), kan men representeren door een verzameling lijnen, vlakken of een enkele solid. (Reeële objecten) kan men maken met een set vlakken. LOD3 is het hoogste detailniveau, waarbij de geometrieën alle beschikbare vormdetails bevatten.  </td>    
  </tr>
</table>

De bovenstaande beschrijving van CityGML 3.0 over de LOD's is algemeen en conceptueel. Dit biedt flexibiliteit om verschillende soorten 3D-modellen en verschillende soorten geometrie binnen één LOD-niveau te modelleren. Dit maakt het lastig om eenduidig vast te stellen hoe een men een object in de werkelijkheid in een bepaalde LOD representeert. 

Om hier verbetering in te brengen heeft [[Biljecki16c]] in 2016 een verfijning gemaakt die voortbouwt op het toen ter tijd actuele CityGML2.0 LOD framework. Dit is gedaan door iedere CityGML LOD op te splitsen in 4 sub groepen. Zo is LOD1 opgesplitst in LOD1.0, 1.1, 1.2 en 1.3. Het eerste nummer van de verfijnde LOD komt overeen met de CityGML LOD. Het tweede nummer geeft de verdere verfijning aan. De documentatie van de verfijnde LOD is uitgebreider dan die van de CityGML standaard. 

<figure id="refined-LoDs">
  <img
    src="media/LoD/TUDeflt_Refined_LoDs_for_CityGML_Buildings.png"
    alt="Refined LoDs for CityGML Buildings">

  <figcaption>
    Refined LoDs for CityGML Buildings. Bron: [[Biljecki16c]].
  </figcaption>
</figure>


Voortbouwend op deze benadering is een generiek verfijnd LOD-raamwerk definitie opgesteld. Dit raamwerk biedt een algemene basis voor het eenduidiger beschrijven van het detailniveau van verschillende assets. Omdat de kenmerken en geometrische eigenschappen per asset kunnen verschillen, is het generieke raamwerk vervolgens per asset verder geconcretiseerd. Deze specifieke uitwerkingen worden in het objectenhandboek behandeld.

**LOD 0.0** De meest grove 2D representatie. Objecten groter dan X m worden opgenomen en aangrenzende objecten mogen worden samengevoegd tot één geometrische entiteit.  
**LOD 0.1** Objecten worden individueel gemodelleerd en grote objectonderdelenwonderdelen worden opgenomen.  
**LOD 0.2** Naast grote objectonderdelen worden ook kleinere objectonderdelen en uitbreidingen opgenomen. De footprint wordt op één hoogte weergegeven en ook de bovenkant van het object wordt opgenomen.  
**LOD 0.3** Gelijk aan LOD0.2, maar met de mogelijkheid om meerdere horizontale oppervlakken op verschillende hoogtes te modelleren wanneer het hoogteverschil groter is dan een bepaalde drempel (bijvoorbeeld 2 m).  

**LOD 1.0** De meest grove 3D-representatie. Objecten groter dan X m worden opgenomen en aangrenzende objecten mogen worden geaggregeerd.    
**LOD 1.1** Objecten worden individueel gemodelleerd en grote objectonderdelen worden opgenomen.  
**LOD 1.2**: Ook kleinere objectonderdelen en uitbreidingen worden gemodelleerd. Het object wordt daarbij in principe tot één hoogte geëxtrudeerd.  
**LOD 1.3**: Gelijk aan LOD1.2, maar meerdere horizontale bovenvlakken zijn toegestaan wanneer het hoogteverschil groter is dan een bepaalde drempel (bijvoorbeeld 2 m). Hierdoor kunnen bijvoorbeeld verschillende objecthoogtes of grote inspringingen afzonderlijk worden gemodelleerd.  

**LOD2.0** is een grofmazig model met standaard vormstructuren, waarin mogelijk ook grote objectonderdelen worden opgenomen (groter dan 4 m en 4 m²).  
**LOD2.1** is vergelijkbaar met LOD2.0, met als verschil dat ook kleinere objectonderdelen en uitbreidingen, worden opgenomen (groter dan 2 m en 2 m²).   
**LOD2.2** voldoet aan de eisen van LOD2.0 en LOD2.1, met als toevoeging dat ook objecten op de bovenkant van het object (groter dan 2 m en 2 m²) moeten worden opgenomen. 
**LOD2.3** vereist het vorig niveau plus dat objecten die "overstekken/overhangen" expliciet worden gemodelleerd wanneer deze groter zijn dan 0,2 m. 

**LOD 3.0** Een model waarbij objectstructuren gedetailleerder zijn dan in LOD2.2.  
**LOD 3.1** Een detailinveau waarin elementen groter dan 1,0 m worden gemodelleerd. Bovenvlakken, die vanaf de grond lastig waarneembaar zijn modelleert men conform LOD 2.3  
**LOD 3.2** Een gedetailleerd model waarin elementen groter dan 1,0 m worden gemodelleerd.  
**LOD 3.3** Een zeer gedetailleerd model waarin elementen groter dan 0,2 m worden gemodelleerd en eventueel kleine details.  

### Niveau van Semantishe Decompositie
Een belangrijke verandering in CityGML 3.0 is het onderscheid tussen en het loskoppelen van Level Of Detail en semantische decompositie. Dit betekent dat het binnen de CityGML 3.0 standaard mogelijk is om een gebouw in een LOD2 te modelleren, de muren die onderdeel zijn van dit gebouw conform LOD3 en de ruimten binnen dit gebouw als LOD0.  

![Verschillend LOD gebruik in semantische decompositie gebouw](media/LOD/CityGML30_LOD_2.png "(Verschillend LOD gebruik in de semantische decompositie van een gebouw)")


Een semantische decompositie kan gezien worden als toename in detail. 
Onderstaand voorbeeld laat 1 keer een boomstam en een boomkroon zien in LOD 1.0 en in het tweede voorbeeld een boom in LOD 1.0. Ondanks dat de LOD's overeenkomen lijkt een object gemodelleerd met meer semantische decompositie gedetaileerder. 

![Semantische decomopositie en LOD](media/LOD/Boom_LOD_en_Semantische_decompositie.png "(Semantische decomopositie en LOD)")

### 3D Coordinaten 
Ongeacht het Level Of Detail dat gebruikt wordt voor de geometrische representatie van de objecten in de werkelijkheid zal de geometrie opgebouwd worden in driedimensionale ruimte. Dit betekent dat de geometrie (punten- lijnen - vlakken - volumes) van objecten opgesteld is met (X, Y, Z) coordinaten.   

## Geen inhoud van de BGT: macro-objecten

Geen verandering t.o.v. BGT/IMGEO. 

