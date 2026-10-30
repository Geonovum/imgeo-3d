

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

```

## Metadata 



## City Object Hierarchy

