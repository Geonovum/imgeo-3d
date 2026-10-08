# LOD Pand

**LOD 0.0** De meest grove representatie. Gebouwen groter dan 6 m worden opgenomen en aangrenzende gebouwen mogen worden samengevoegd tot één geometrische entiteit.  
**LOD 0.1** Gebouwen worden individueel gemodelleerd en grote gebouwonderdelen worden opgenomen.  
**LOD 0.2** Naast grote gebouwonderdelen worden ook kleinere gebouwonderdelen en uitbreidingen, zoals erkers, opgenomen. De footprint wordt op één hoogte weergegeven en ook het dakrandvlak wordt opgenomen.  
**LOD 0.3** Gelijk aan LOD0.2, maar met de mogelijkheid om meerdere horizontale oppervlakken op verschillende hoogtes te modelleren wanneer het hoogteverschil groter is dan een bepaalde drempel (bijvoorbeeld 2 m).  

**LOD 1.0** De meest grove 3D-representatie. Gebouwen groter dan 6 m worden opgenomen en aangrenzende gebouwen mogen worden geaggregeerd.    
**LOD 1.1** Gebouwen worden individueel gemodelleerd en grote gebouwonderdelen worden opgenomen.  
**LOD 1.2**: Ook kleinere gebouwonderdelen en uitbreidingen, zoals erkers, worden gemodelleerd. Het gebouw wordt daarbij in principe tot één hoogte geëxtrudeerd.  
**LOD 1.3**: Gelijk aan LOD1.2, maar meerdere horizontale bovenvlakken zijn toegestaan wanneer het hoogteverschil groter is dan een bepaalde drempel (bijvoorbeeld 2 m). Hierdoor kunnen bijvoorbeeld verschillende bouwhoogtes of grote inspringingen afzonderlijk worden gemodelleerd.  

**LOD2.0** is een grofmazig model met standaard dakstructuren, waarin mogelijk ook grote gebouwonderdelen, zoals garages, worden opgenomen (groter dan 4 m en 10 m²).  
**LOD2.1** is vergelijkbaar met LOD2.0, met als verschil dat ook kleinere gebouwonderdelen en uitbreidingen, zoals erkers, grote uitsparingen in gevels en externe rookkanalen, moeten worden opgenomen (groter dan 2 m en 2 m²). In vergelijking met het grovere model kan het modelleren van dergelijke kenmerken in deze LOD voordelen bieden voor toepassingen zoals het schatten van de energiebehoefte, omdat het muuroppervlak nauwkeuriger in kaart wordt gebracht.  
**LOD2.2** voldoet aan de eisen van LOD2.0 en LOD2.1, met als toevoeging dat ook dakopbouwen (groter dan 2 m en 2 m²) moeten worden opgenomen. Dit betreft voornamelijk dakkapellen, maar ook andere relatief grote dakconstructies, zoals zeer grote schoorsteenconstructies.   
**LOD2.3** vereist dat dakoverstekken expliciet worden gemodelleerd wanneer deze groter zijn dan 0,2 m. Hierdoor bevinden de dakrand en de gebouwcontouren zich altijd op hun werkelijke locatie. Dit biedt voordelen voor toepassingen waarbij het volume van het gebouw van belang is.  

**LOD 3.0** Een model waarbij dakstructuren gedetailleerder zijn dan in LOD2.2, terwijl overige onderdelen, zoals gevels en muren, op het niveau van LOD2.2 zijn gemodelleerd. Dakdetails kunnen bijvoorbeeld dakramen bevatten. Ramen van dakkapellen hoeven niet te worden gemodelleerd.  
**LOD 3.1** Een hybride model dat specifiek aansluit bij terrestrische acquisitietechnieken, zoals Mobile Mapping Systems. Alle elementen onder het dak worden op het niveau van LOD3.2 gemodelleerd, terwijl het dak op het niveau van LOD2.3 wordt gemodelleerd. Hierdoor kunnen bijvoorbeeld dakoverstekken expliciet worden weergegeven, terwijl moeilijk vanaf de grond waarneembare dakdetails minder gedetailleerd zijn.  
**LOD 3.2** Een architectonisch gedetailleerd model waarin elementen groter dan 1,0 m worden gemodelleerd. Dit omvat onder andere ramen, deuren, balkons en andere relevante gevel- en dakdetails.  
**LOD 3.3** Een zeer gedetailleerd architectonisch model waarin elementen groter dan 0,2 m worden gemodelleerd. Dit omvat onder andere raamneggen/raamopeningen in 3D, luifels en vergelijkbare kleine architectonische details. 