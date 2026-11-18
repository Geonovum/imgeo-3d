
Bronnen: 

https://github.com/3DGI/cityjson2jsonfg/
https://github.com/Geonovum/ogc-api-workshops/tree/main/JSON-FG
https://github.com/3DGI/cityjson2jsonfg/

Below is a mapping of the CityJSON concepts to JSON-FG as it is implemented in *cityjson2jsonfg*.


In GeoJSON is de geomtrie beschreven in het "geometry" attribuut. Geometrieën zijn gecodeerd volgens de OGC Simple Features Standaard (in 2D of 2.5D punten, line strings, polygons or aggregaties daarvan). Standaard coordinatiereferentiestelsel is WGS 84 CRS (OGC:CRS84 for 2D or OGC:CRS84h for 2.5D).

Een van de motivaties voor het ontwikkelen van JSON-FG is de ondersteuning voor het representen van geometrie in andere CRS-en en met andere geometry-types. 

Om conflicten met bestaande GeoJSON-readers te voorkomen is het mogelijk deze geometrieen te beschrijven in een nieuw attribuut "place".  


| CityJSON                                                                         | JSON-FG                                                                                                                                                                                                                                                           |
|----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Meerdere geometrieën in één CityObject mogelijk. Elk van een ander LevelOfDetail (0, 1.2, 1.3, 2.2) | Waar een CityObject een LoD < 0.2 geometrie heeft wordt ervan uitgegaan dat dit 2.5D geometrie is. Dit wordt toegevoegd in het GeoJSON-attribuut `"geometry"`. Wanneer de overige attributen een LOD groter of gelijk aan 1 hebben, dan wordt de geometrie met het hoogste Level Of Detail toegevoegd in het JSON-FG-attribuut `"place"`. |
| Meerdere LoDs in een CityObject, elk van een familie wordt toegevoegd (1.1, 1.3).       | De geometrie van het hoogste LOD wordt toegevoegd aan de feature.                                                                                                                                                                                                  |
| City model creatie datum in `CityJSON.metadata.referenceDate`.                   |Worden toegevoegd als een "tijdstip" (time instant) to `time.date` as `full-date`.                                                                                                                                                                                                        |
| Semantic surfaces                                                                | Not converted.                                                                                                                                                                                                                                                    |
| Appearances                                                                      | Not converted.                                                                                                                                                                                                                                                    |
| Metadata (other than `referenceDate` and `referenceSystem`)                      | Not converted.                                                                                                                                                                                                                                                    |
| CityObject hierarchy (parent and children relations)                             | Not converted.                                                                                                                                                                                                                                                    |


## Semantic Surfaces

bron: https://www.cityjson.org/specs/2.0.2/#semantics-of-geometric-primitives

Semantic surface: 

Een Semantic Object is een JSON object die het de betekenis van een primitive van een geometrie representeert. Bijvoorbeeld een vlak van de totaalgeometrie van een gebouw dat een muur is. Een semantic Object kan ook andere attributen representeren zoals dakhelling, potentie voor zonne-energie etc. Wanneer de hoofdgeometrie een Solid, multisurface of multisolid is, dan is de primitive een surface. Wanneer de de hoofdgeometrie een multipoint of multilinestring is dan is de primitive een punt of linestring. 

Per CityGML object kan dit andere sematic surfaces hebben. Bijvoorbeeld: 

"Building", "BuildingPart", "BuildingRoom", "BuildingStorey", "BuildingUnit", and "BuildingInstallation" kunnen onderstaande vlakken hebben: 

"RoofSurface", "GroundSurface", "WallSurface", "ClosureSurface", "OuterCeilingSurface", "OuterFloorSurface", "Window", 
"Door", "InteriorWallSurface", "CeilingSurface", "FloorSurface".

In de CityGML 3.0 standaard wordt dit Thematic Surface genoemd: 

Thematic surfaces: https://docs.ogc.org/is/20-010/20-010.html#toc49
Levels of Detail are no longer associated with the degree of semantic decomposition of city objects and refer to the spatial representations only. This means that, for example, buildings can have thematic surfaces (like WallSurface, GroundSurface) also in LODs 0 and 1 and windows and doors can be represented in all LODs 0-3. In CityGML 2.0 or earlier thematic surfaces were only allowed starting from LOD2, openings like doors and windows starting from LOD3, and interior rooms and furniture only in LOD4.

## Appearances 
Both textures and materials are supported in CityJSON. And the same mechanisms used in CityGML are reused: 

Voor materiaal geldt het volgende: 
``` json 
Material : X3DMaterialNode { 
  SFFloat [in,out] ambientIntensity 0.2         [0,1]
  SFColor [in,out] diffuseColor     0.8 0.8 0.8 [0,1]
  SFColor [in,out] emissiveColor    0 0 0       [0,1]
  SFNode  [in,out] metadata         NULL        [X3DMetadataObject]
  SFFloat [in,out] shininess        0.2         [0,1]
  SFColor [in,out] specularColor    0 0 0       [0,1]
  SFFloat [in,out] transparency     0           [0,1]
}
```

Voor texture geldt het volgende: 


``` xml
<app:appearanceMember>
    <app:Appearance gml:id="ID_22f377b6-5a68-4dde-985b-d11b5491ab69">
      <app:theme>Rotterdam</app:theme>
      <app:surfaceDataMember>
        <app:ParameterizedTexture gml:id="ID_940d0f51-539c-412f-82f6-2718efc1e8ab">
          <app:imageURI>citygml_textures/tex_5951656.jpg</app:imageURI>
          <app:mimeType>image/jpg</app:mimeType>
          <app:target uri="#ID_173bb43a-3d8f-4e8e-a029-5ee08ed5e8ae">
            <app:TexCoordList>
              <app:textureCoordinates ring="#ID_173bb43a-3d8f-4e8e-a029-5ee08ed5e8ae_0_">0.366449 0.471743 0.305409 0.496171 0.300001 0.482651 0.297363 0.476056 0.369303 0.447266 0.372185 0.45447 0.379315 0.472295 0.368411 0.476655 0.366449 0.471743
              </app:textureCoordinates>
            </app:TexCoordList>
          </app:target>
```

``` xml
    <bldg:Building gml:id="BAG_0599100000669457">
               <bldg:BuildingPart gml:id="ID_75798d5a-c3eb-4edb-8648-63587f3d2274"> 
                          <bldg:lod2Solid>
                                <gml:Solid gml:id="ID_e94f0073-bcce-442f-81ef-cf382a928034">
                                    <gml:exterior>
                                        <gml:CompositeSurface gml:id="ID_6582cf13-3520-4cd9-b363-8b03539f4d86">
                                            <gml:surfaceMember xlink:href="#RCID_91ef277d-9eb8-4efa-8667-ec51e08dd072"/>

                                                     <bldg:outerBuildingInstallation>
            <bldg:BuildingInstallation gml:id="UUID_e6e005f4-47b9-4063-b6fb-f55c3ae1748f">
              <creationDate>2024-10-29</creationDate>
              <bldg:boundedBy>
                <bldg:RoofSurface gml:id="UUID_95799910-224c-461a-befc-f878ae7f929a">
                  <creationDate>2024-10-29</creationDate>
                  <bldg:lod2MultiSurface>
                    <gml:MultiSurface gml:id="UUID_d8380f5b-cadc-4f1e-87ef-2474a0469cec">

                        <bldg:boundedBy>
            <bldg:ClosureSurface gml:id="UUID_8d84ece2-3843-4664-bff0-010ad8143b8d">
                <bldg:boundedBy>
            <bldg:ClosureSurface gml:id="UUID_8d84ece2-3843-4664-bff0-010ad8143b8d">

               <bldg:boundedBy>
               
            <bldg:RoofSurface gml:id="UUID_a18d99db-1309-4477-97d2-bd76d724483d">
              <creationDate>2024-10-29</creationDate>
              <bldg:lod2MultiSurface>
                <gml:MultiSurface gml:id="UUID_589c27dc-8819-44da-a1f6-1f91b29cc0f8">
                  <gml:surfaceMember>
                    <gml:Polygon gml:id="ID_173bb43a-3d8f-4e8e-a029-5ee08ed5e8ae">
                      <gml:exterior>
                        <gml:LinearRing gml:id="ID_173bb43a-3d8f-4e8e-a029-5ee08ed5e8ae_0_">
                          <gml:posList srsDimension="3">94953.54868 437983.611415 14.226183 94955.583067 437988.691849 14.226183 94954.457977 437989.142375 14.226183 94953.909215 437989.362118 14.226183 94951.511535 437983.374438 14.226183 94952.111049 437983.134371 14.226183 94953.594257 437982.540442 14.226183 94953.957551 437983.447688 14.23071 94953.54868 437983.611415 14.226183</gml:posList>
                        </gml:LinearRing>
                      </gml:exterior>
                    </gml:Polygon>
                  </gml:surfaceMember>
                </gml:MultiSurface>
              </bldg:lod2MultiSurface>
            </bldg:RoofSurface>
          </bldg:boundedBy>

```

## Metadata 
bron: https://www.cityjson.org/specs/2.0.1/#metadata
Een CityJSON-bestand kan op het hoogste niveau één optioneel `"metadata"`-object hebben. Dat beschrijft de dataset als geheel, niet de afzonderlijke objecten. CityJSON 2.0 kent daarvoor een klein vast setje velden:

| Veld | Betekenis |
|---|---|
| `identifier` | Unieke identificatie van de dataset |
| `title` | Naam van de dataset |
| `referenceDate` | Datum van de dataset (bijv. datum van inwinning of creatie) |
| `referenceSystem` | Coördinaatreferentiesysteem als URL, bijv. `https://www.opengis.net/def/crs/EPSG/0/7415` (RDNAP) |
| `geographicalExtent` | Bounding box `[minx, miny, minz, maxx, maxy, maxz]` |
| `pointOfContact` | Contactgegevens (naam, e-mail, rol, organisatie, adres, website) |

Uitgebreidere metadata, zoals herkomst (lineage) of kwaliteit, valt buiten de kernspecificatie. Daarvoor zijn er Extensions, zoals de MetadataExtended-extensie.

Hiermee kan onderstaande gemaakt worden: 

```json 
  {
    "type": "CityJSON",
    "version": "2.0",
    "extensions":
    {
        "Metadata-Extended":
        {
            "url": "https://raw.githubusercontent.com/cityjson/metadata-extended/0.6/metadata-extended.ext.json",
            "version": "0.6"
        }        
    },
    "metadata":
    {
      "geographicalExtent": [ 84710.1, 446846.0, -5.3, 84757.1, 446944.0, 40.9 ],
      "identifier": "eaeceeaa-3f66-429a-b81d-bbc6140b8c1c",
      "pointOfContact": {
        "contactName": "3D geoinformation group, Delft University of Technology",
        "contactType": "organization",
        "role": "owner",
        "phone": "+31-6666666666",
        "emailAddress": "3dgeoinfo-bk@tudelft.nl",
        "website": "https://3d.bk.tudelft.nl",
        "address": {
          "details": "Julianalaan 134, Delft 2628BL, the Netherlands"
        }
      },
      "referenceDate": "1977-02-28",
      "referenceSystem": "https://www.opengis.net/def/crs/EPSG/0/2355",
      "title": "Buildings in LoD2.3 of Chibougamau, Québec"
    },
    "+metadata-extended": {
        "isTriangulated": false,
        "metadataDateStamp": "2021-07-12",
        "datasetTopicCategory": "geoscientificInformation",
        "spatialRepresentationType": ["vector"],
        "fileIdentifier": "delft.json",
        "metadataStandard": "ISO 19115 - Geographic Information - Metadata",
        "metadataStandardVersion": "ISO 19115:2014(E)",
        "metadataCharacterSet": "UTF-8",
        "datasetCharacterSet": "UTF-8",
        "textures": "absent",
        "materials": "absent"
    },
    "CityObjects": {},
    "vertices": [],
    "transform": {
      "scale": [1.0, 1.0, 1.0],
      "translate": [0.0, 0.0, 0.0]
    }
  }
```

**JSON-FG**

JSON-FG heeft geen eigen metadata-object. Het voegt wel een aantal members toe die gedeeltelijk overlappen met de CityJSON-metadata:

| CityJSON | JSON-FG | Opmerking |
|---|---|---|
| `referenceSystem` | `"coordRefSys"` (op collectie- of featureniveau) | Wordt geconverteerd. Daardoor hoeft niet te worden teruggevallen op CRS84, zodat RD/NAP (EPSG:7415) behouden blijft. |
| `referenceDate` | `"time": { "date": ... }` | Wordt geconverteerd, maar met een verschuiving in betekenis (zie hieronder). |
| `geographicalExtent` | `"bbox"` (GeoJSON) | Wordt niet geconverteerd, maar kan wel. GeoJSON ondersteunt een 3D-bbox met 6 waarden. |
| `identifier`, `title`, `pointOfContact` | — | Geen plek in JSON-FG. Kan als vrije `"properties"` op de FeatureCollection of via de collectiemetadata van een OGC API (`/collections/{id}`), eventueel met een link naar een ISO 19115-metadatarecord (`rel="describedby"`). |

**Aandachtspunt `time`:** in JSON-FG beschrijft `"time"` het *tijdstip of de periode waarop het feature betrekking heeft*: een eigenschap van het object in de werkelijkheid. De CityJSON-`referenceDate` is een eigenschap van de *dataset*. Als de `referenceDate` naar `time.date` van elk feature wordt overgenomen, verandert dus de betekenis van "datum van het bestand" naar "datum van het object". Voor IMGeo-3D ligt het meer voor de hand om `time` te vullen met de objectspecifieke tijdsgegevens, zoals `tijdstipRegistratie` of `objectBeginTijd`, en de datasetdatum als metadata van de collectie op te nemen.

**Aanvullend:** JSON-FG kent ook `"featureType"`, `"featureSchema"` en `"conformsTo"`. Die hebben geen equivalent in de CityJSON-metadata, maar zijn wel bruikbaar om het objecttype (bijv. `Building`) en het bijbehorende schema vast te leggen.

## City Object Hierarchy

bron: https://www.cityjson.org/specs/2.0.1/#the-different-city-objects

**CityJSON**

In CityJSON staan alle CityObjects in één platte lijst (`"CityObjects"`), elk met een eigen sleutel (id). Het nesten zoals in CityGML gebeurt niet. De samenhang wordt in plaats daarvan met verwijzingen vastgelegd:

- `"children"`: lijst met id's van onderliggende objecten
- `"parents"`: lijst met id's van bovenliggende objecten

CityJSON maakt onderscheid tussen:

- **1st-level City Objects**: kunnen zelfstandig bestaan, bijv. `Building`, `Bridge`, `Road`, `SolitaryVegetationObject`, `CityFurniture`, `TINRelief`.
- **2nd-level City Objects**: bestaan alleen als onderdeel van een 1st-level object en *moeten* een `"parents"` hebben, bijv. `BuildingPart`, `BuildingInstallation`, `BuildingStorey`, `BuildingRoom`, `BuildingUnit`, `BridgePart`, `TunnelPart`.

```json
"CityObjects": {
  "BAG_0599100000669457": {
    "type": "Building",
    "children": ["ID_75798d5a", "UUID_e6e005f4"]
  },
  "ID_75798d5a": {
    "type": "BuildingPart",
    "parents": ["BAG_0599100000669457"],
    "geometry": [ ... ]
  },
  "UUID_e6e005f4": {
    "type": "BuildingInstallation",
    "parents": ["BAG_0599100000669457"],
    "geometry": [ ... ]
  }
}
```

Daarnaast is er `CityObjectGroup`, waarmee objecten zonder hiërarchische relatie gegroepeerd kunnen worden. Thematische vlakken (RoofSurface, WallSurface e.d.) zijn in CityJSON géén CityObjects, anders dan in CityGML (`boundedBy`). Ze zijn semantics binnen de geometrie (zie [Semantic Surfaces](#semantic-surfaces)).

**JSON-FG**

JSON-FG (en GeoJSON) kent geen hiërarchie tussen features. Elk feature in een FeatureCollection staat op zichzelf, en een standaardmanier om parent/child-relaties uit te drukken ontbreekt. In *cityjson2jsonfg* worden `parents` en `children` daarom niet geconverteerd. Dat zorgt voor de volgende problemen:

- De relatie tussen een `Building` en zijn `BuildingPart`s of `BuildingInstallation`s gaat verloren.
- Wordt alleen het 1st-level object omgezet, dan verdwijnt de geometrie van de onderdelen.
- Wordt elk object een los feature, dan is niet meer te zien welke delen bij elkaar horen.

**Mogelijke oplossingen:**

1. **Relaties als properties:** neem `parents`/`children` op als gewone attributen met id's in `"properties"`. Dat is eenvoudig, maar zonder vastgelegde semantiek.
2. **Links:** gebruik de `links`-member met een eigen `rel`, bijv. `"rel": "parent"` / `"rel": "child"` met een `href` naar het andere feature in de OGC API. Dat sluit aan bij hoe OGC API's relaties uitdrukken.
3. **Samenvoegen:** voeg de geometrie van alle onderdelen samen in `"place"` van het 1st-level feature (bijv. een `MultiPolyhedron` of `Polyhedron` per part). De geometrie blijft dan behouden, maar de identiteit en attributen van de onderdelen gaan verloren.
4. **`featureType` gebruiken** om het CityJSON-type (`Building`, `BuildingPart`, …) per feature vast te leggen, in combinatie met optie 1 of 2.

**Relevantie voor IMGeo-3D:** de BAG-pand-id zit op het `Building`, terwijl de 3D-geometrie vaak op `BuildingPart`-niveau zit, zoals in het Rotterdamse voorbeeld hierboven. Bij een uitwisseling via JSON-FG moet dus expliciet gekozen worden hoe die relatie behouden blijft. Anders is de koppeling met de BAG niet meer te leggen.


## Conclusie 

JSON-FG maakt 3D-data toegankelijk, CityJSON maakt 3D-data volledig. Voor IMGeo-3D is CityJSON de basis, en JSON-FG een afgesproken, vereenvoudigde weergave ernaast. beide hebben voordelen en nadelen: 

 Aspect | CityJSON | JSON-FG |
|---|---|---|
| Meerdere LoD's per object | Ja | Nee, één geometrie in `place` (plus 2D/2.5D in `geometry`) |
| Semantische/thematische vlakken (dak, muur, grond) | Ja | Nee |
| Appearances (texturen, materialen) | Ja | Nee |
| Hiërarchie (Building → BuildingPart, Installation) | Ja | Nee, alleen via eigen afspraken (properties, links) |
| Metadata van de dataset | Ja | Alleen CRS en (met een verschuiving in betekenis) datum |
| Werkt met standaard GeoJSON-tools en GIS-clients | Nee, vraagt specifieke software | Ja |
| Past op OGC API Features (per feature) | Via CityJSONFeature / CityJSONSeq | Ja, van nature |

### Gevolgen voor IMGeo-3D

1. **Het IMGeo-3D informatiemodel los van het formaat vastleggen.** IMGeo-3D beschrijft wat er is: objecten, LoD's, thematische vlakken, relaties met BAG en BGT. Dat volgt het conceptuele model van CityGML 3.0. CityGML en CityJSON zijn daar volledige uitwerkingen van, JSON-FG is een vereenvoudiging hiervan.
2. **CityJSON (2.0) is het volledige uitwisselformaat** voor bestanden en levering, met CityGML (GML) als alternatief waar dat nodig is, bijvoorbeeld bij aanbestedingen.
3. **Voor JSON-FG komt er een profiel** Dat profiel legt de keuzes vast die *cityjson2jsonfg* nu impliciet maakt, of juist laat liggen:
   - welke LoD in `place` komt (de hoogste, of een vaste LoD zoals 2.2)
   - dat `geometry` de 2D-footprint bevat, etc.
   - dat `featureType` het objecttype bevat.
   - dat relaties via `links` lopen (parent/child, BAG-pand-id).
   - dat `time` de objecttijden bevat en niet de datasetdatum.
   - dat `coordRefSys` EPSG:7415 (RD + NAP) is.
   - een expliciete melding dat semantiek en texturen niet in dit profiel zitten.

### Gevolgen voor API's

Bied meerdere formaten aan via content negotiation op dezelfde OGC API Features-endpoints:

- **`application/city+json` (CityJSONFeature / CityJSONSeq):** de volledige 3D-informatie per feature, voor 3D-analyse, BIM/GIS-integratie en wie het complete model nodig heeft. De 3DBAG-API werkt al zo.
- **`application/fg+json` (JSON-FG):** voor brede bruikbaarheid in GIS-tools, viewers en eenvoudige toepassingen die "een 3D-vorm per object" genoeg vinden. Dit sluit ook goed aan bij de GeoJSON-lijn van de Nederlandse API-strategie (Geo-module van de API Design Rules).
- **Voor visualisatie (optioneel):** 3D Tiles of I3S via OGC API 3D GeoVolumes. Geen van beide JSON-formaten is gemaakt voor het snel tonen van grote gebieden.


### Cloud Native Imgeo 3D

CityJSON en JSON-FG zijn tekstformaten voor uitwisseling per bestand of per feature via een API. Voor grote, landsdekkende datasets wordt steeds vaker een *cloud-native* formaat gebruikt. Zo'n bestand staat op object storage (bijv. S3 of Azure Blob). Een client haalt via HTTP range requests alleen de delen op die nodig zijn, zonder server of API ertussen. Daarvoor heeft het bestand een index, zodat de client weet waar in het bestand welke objecten staan. Voor IMGeo-3D zijn twee formaten relevant.

**GeoParquet** (bron: https://geoparquet.org/)

Apache Parquet is een kolomgeoriënteerd, gecomprimeerd tabelformaat. GeoParquet is een OGC-standaard die vastlegt hoe geometrie daarin wordt opgeslagen (als WKB, met het CRS en de bbox in de bestandsmetadata). Het wordt breed ondersteund: GDAL/QGIS, DuckDB, GeoPandas en cloud-datawarehouses. Overture Maps publiceert zijn gebouwen wereldwijd als GeoParquet.

- **Voordelen:** compact en snel, vooral bij analyse op attributen (een gebruiker die alleen `bouwjaar` wil, leest de geometrie niet in). Meerdere geometriekolommen zijn toegestaan, dus meerdere LoD's per object kunnen naast elkaar staan.
- **Nadelen:** het is een vereenvoudiging van het model, net als JSON-FG. Er is geen solid-type: volumes worden `MultiPolygon Z`. Semantische vlakken en hiërarchie kunnen alleen via eigen afspraken, en appearances worden niet ondersteund.

**FlatCityBuf** (bron: https://www.cityjson.org/flatcitybuf/)

FlatCityBuf is een binaire, cloud-geoptimaliseerde codering van **CityJSON zelf**, ontwikkeld aan de TU Delft. Het bestand bestaat uit een header (CRS, transform, appearances), een ruimtelijke index (packed Hilbert R-tree, 2D), een attribuutindex (B+tree, bijv. op BAG-pand-id) en de features als CityJSONFeatures. Conversie van en naar CityJSONSeq gaat met de CLI `fcb`.

- **Voordelen:** het volledige CityJSON-model blijft behouden: solids, LoD's, semantische vlakken, appearances en hiërarchie. Volgens de makers is één object uit de volledige 3DBAG (circa 70 GB) met een handvol requests op te halen.
- **Nadelen:** de makers noemen het nog *beta* en het is geen vastgestelde standaard. Het wordt vooral met de eigen bibliotheken gebruikt (Rust, C++, Python, TypeScript) en niet door GDAL/QGIS. Bestanden zijn onveranderlijk, dus het is een distributieformaat en geen bronformaat.

**Afweging voor IMGeo-3D**

| Aspect | GeoParquet | FlatCityBuf |
|---|---|---|
| Volledig CityJSON-model | Nee, vereenvoudiging | Ja |
| Toolondersteuning | Breed (GIS, data-analyse) | Beperkt (eigen bibliotheken) |
| Status | OGC-standaard | Beta |
| Geschikt voor | Analyse en bulkdownload van objecten en attributen | Gerichte opvraging van het volledige 3D-model uit een grote dataset |

De twee formaten vullen elkaar aan en vervangen CityJSON niet. Ze worden uit dezelfde bron gegenereerd als de API en de CityJSON-levering, zodat ze inhoudelijk gelijk blijven. Voor GeoParquet is een profiel nodig, net als bij JSON-FG. Dat profiel legt vast welke LoD's als geometriekolom worden opgenomen, dat solids als `MultiPolygon Z` worden opgeslagen, welke kolom de relatie met het ouderobject en de BAG-pand-id bevat, en dat het CRS EPSG:7415 (RD + NAP) is. FlatCityBuf is gezien de status vooral iets om te volgen en mee te experimenteren. Als het stabiel wordt, is het de meest logische cloud-native vorm van CityJSON.