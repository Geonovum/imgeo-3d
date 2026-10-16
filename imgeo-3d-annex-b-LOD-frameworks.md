# LOD Frameworks

Een LOD representeert een specifieke geometrische abstractie van een object in de werkelijkheid. Deze bijlage toont verschillende geometrische LOD-definities en LOD-abstracties. Deze LOD's zijn gestandaardiseerd door OGC [[CityGML3]], het verfijnd LOD-framework van de TU Delft [[Biljecki16c]] en de LOD-uitbreiding voor BIM-modellen [[vanderVaart2026]].

## CityGML 3.0 LOD niveaus
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

## Verfijnd LOD-framework
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

## BIM LOD uitbreiding

![BIM LOD uitbreiding](media/LOD/BIM-ondersteunende_LOD.png "Uitbreiding van de LOD-niveaus ten behoeve van een goede aansluiting op de conversie van BIM naar GEO)")

**LODa** is een multi-surface, bestaande uit 3D vlakken die de voetprint, verdiepingen en dakstructuur van een object representeren. Dit is een uitbreiding op LOD 0.3. Het staat niet-horizontale-vlakken toe. 

**LODb** is een aggregatie bestaande uit een solid van een geextrudeerde voetprint en een dakstructuur, en een multi-surface van de overhangende dakstructuur. 

**LODc.1** is een solid, gemaakt door het extruderen van horizontale doorsnede op elke verdieping en hier één solid van maken. 

**LODc.2** is het LODc.1 level, aangevuld met een verfijnde dakstructuur. 

**LODd.1** Horizontale vlakken worden gefilterd, gebaseerd op of deze buiten een gevel (balkon/overhang) of binnen een gevel (vloeren, muren) liggen. Alleen de interne objecten worden opwaards geextrudeerd, externe objecten worden gerepresenteerd met multisurfaces. 

**LODd.2** is het LODd.1 level, aangevuld met een verfijnde dakstructuur. 

De BIM-LOD's zijn ontwikkeld in onderzoek en kunnen verfijnd worden zodat de behoefte voor een 3D BGT volledig gedekt wordt.  

## Niveau van Semantische decompositie
Een semantische decompositie is een opdeling van een model in betekenisvolle objecten. Dit kan men doen op verschillende manieren en verschillend niveau. Een partonomie geeft de hiërarchische deel-geheelrelaties tussen deze onderdelen weer. De verschillende decompositieniveaus geven aan hoe ver de brug is opgedeeld in onderdelen. Hieronder wordt de partonomie van een brug met de bijbehorende decompositieniveaus weergegeven.

![Partonomie van een brug met verschillende decompositieniveaus](media/LOD/Voorbeeld_semantische_decompositie_brug.png "(Partonomie van een brug met verschillende decompositieniveaus)")

Een semantische decompositie kan ten onrechte worden geïnterpreteerd als een toename in detailniveau, terwijl dit betrekking heeft op het opdelen van een model. 

Onderstaand voorbeeld laat één keer een boomstam en een boomkroon zien in LOD 1.0 en in het tweede voorbeeld één totale boom in LOD 1.0. Ondanks dat de LOD's overeenkomen lijkt het object gemodelleerd met meer semantische decompositie, gedetaileerder. 

![Semantische decomopositie boom](media/LOD/Boom_LOD_en_Semantische_decompositie.png "(Semantische decomopositie boom)")

Met BGT 1.2 en IMGEO 2.2 is decompositie mogelijk door bijvoorbeeld voor Wegdelen een macro-object Weg te creëren en met weginrichtingselementen de onderdelen van een weg te modelleren.  

## Semantische decompositie en LOD's
Binnen de CityGML 3.0 standaard mogelijk is om een gebouw in een LOD2 te modelleren, de muren die onderdeel zijn van dit gebouw conform LOD3 en de ruimten binnen dit gebouw als LOD0.  

![Verschillend LOD gebruik in semantische decompositie gebouw](media/LOD/CityGML30_LOD_2.png "(Verschillend LOD gebruik in de semantische decompositie van een gebouw)")




