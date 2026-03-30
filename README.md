# GeoIoT Ontology

GeoIoT is a modular ontology for integrating geospatial and IoT knowledge in smart campus and smart city systems. It provides a shared semantic layer for data integration, reasoning, and SPARQL querying across GIS, BIM, sensors, and operational asset data.

## Scope

The ontology is designed to:
1. Represent spatial entities such as sites, buildings, and zones.
2. Represent IoT devices, observation streams, and quality annotations.
3. Bridge physical assets and monitoring devices.
4. Support interoperable querying and inference using standards-aligned semantics.

## Namespace and Version

1. Ontology IRI: https://www.geoiot.org/ontology
2. Namespace: https://www.geoiot.org/ontology#
3. Preferred prefix: giot
4. Current version IRI: https://www.geoiot.org/ontology/2.0
GeoIoT Ontology (v2.0) Diagram, a modular ontology integrating geospatial context, IoT observations, and physical assets for smart campus/smart city use cases.

## Core Modules

### Spatial Module

Main concepts:
1. SpatialEntity
2. Site
3. Building
4. Zone
5. Boundary

Main properties:
1. isLocatedIn
2. isAdjacentTo
3. hasGeometry
4. contains

### Observation Module

Main concepts:
1. IoTDevice
2. ObservationStream
3. ObservableProperty
4. QualityAnnotation
5. Trend

Main properties:
1. hasStream
2. hasQualityAnnotation
3. observesProperty
4. observesLocation
5. hasTrend

### Asset Module

Main concepts:
1. Asset
2. IoTAgent
3. UsageGroup

Main properties:
1. isMonitoredBy
2. hasAsset
3. hasDevice
4. hasUsageGroup
5. hasEntity

## Imported and Aligned Standards

The ontology aligns with:
1. GeoSPARQL
2. SOSA
3. SSN
4. BOT
5. QUDT
6. PROV-O

## Competency Questions and Example SPARQL

### CQ1
Which sensors are located within a given building?

SPARQL:
PREFIX giot: <https://www.geoiot.org/ontology#>

SELECT ?sensor ?stream WHERE {
  ?sensor a giot:IoTDevice ;
          giot:isLocatedIn ?zone ;
          giot:hasStream ?stream .
  ?zone giot:isLocatedIn <https://example.org/entity/building/ENG-B> .
}

### CQ2
Which assets are monitored by devices whose streams have quality flags?

SPARQL:
PREFIX giot: <https://www.geoiot.org/ontology#>

SELECT ?asset ?device ?qa WHERE {
  ?asset a giot:Asset ;
         giot:isMonitoredBy ?device .
  ?device giot:hasStream ?stream .
  ?stream giot:hasQualityAnnotation ?qa .
}

### CQ3
How can a location assertion be traced to its provenance activity?

SPARQL:
PREFIX giot: <https://www.geoiot.org/ontology#>
PREFIX prov: <http://www.w3.org/ns/prov#>

SELECT ?graph ?activity ?time WHERE {
  GRAPH ?graph {
    <https://example.org/entity/zone/ENG-B-201> giot:isLocatedIn ?b .
  }
  ?graph prov:wasGeneratedBy ?activity .
  ?activity prov:endedAtTime ?time .
}

## Repository Contents

1. geoiot-ontology.owl
2. Optional serializations: geoiot-ontology.ttl, geoiot-ontology.jsonld
3. Documentation files
4. Catalog files for ontology tooling (optional)

## Release and Versioning Policy

1. Semantic versioning is used for ontology releases.
2. Every release is tagged in GitHub.
3. The changelog records added, changed, and deprecated terms.
4. Previous versions remain accessible for reproducibility.

## Validation and Quality Assurance

Before each release:
1. Syntax validation for RDF/OWL serialization.
2. Reasoner consistency check.
3. Namespace consistency check.
4. Example SPARQL query check.
