# GeoIoT Main Ontology

## Overview

The GeoIoT Ontology is a modular OWL 2 ontology for integrating geospatial and IoT knowledge in smart city and smart campus systems. It provides a shared semantic layer for data integration, reasoning, and SPARQL querying across heterogeneous sources such as GIS, BIM, sensor streams, and operational asset data.

- Base ontology IRI: http://www.geoiot.org/ontology
- Namespace: http://www.geoiot.org/ontology#
- Current version IRI: http://www.geoiot.org/ontology/2.0
- Preferred prefix: `giot`

## Core Modules

### 1. Spatial Module

Extends GeoSPARQL and BOT-aligned spatial modeling.

Key ideas:

- Hierarchical spatial containment (for example: Site -> Building -> Zone)
- Transitive location reasoning via `giot:isLocatedIn`
- Symmetric adjacency via `giot:isAdjacentTo`
- Geometry linkage via `giot:hasGeometry`

### 2. Observation Module

Extends SOSA/SSN with IoT-specific stream and quality concepts.

Key ideas:

- Device-to-stream relation via `giot:hasStream`
- Feature/property observation alignment via `giot:observesProperty` and `giot:observesLocation`
- Quality attachment via `giot:hasQualityAnnotation`

### 3. Asset Module

Bridges physical assets to IoT monitoring and observation streams.

Key ideas:

- Cross-domain bridge: `giot:isMonitoredBy` (Asset -> IoTDevice)
- Asset and device organization via `giot:hasAsset`, `giot:hasDevice`, and related properties

## External Standards and Imports

The ontology imports and aligns with key standards:

- GeoSPARQL
- SOSA / SSN
- BOT
- QUDT
- PROV-O (used in provenance-aligned modeling)

## Why This Ontology

The main ontology enables:

- Interoperable data integration across heterogeneous systems
- Rule-based inference over spatial and IoT relationships
- Reusable, standards-aligned query patterns in SPARQL
- Clear separation of core semantic structures from domain-specific extensions

## Notes

- The ontology was developed using an iterative methodology and evaluated with reasoner-based checks.
- Domain extensions can build on `giot:` while preserving a stable core namespace.
