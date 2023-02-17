# INSPIRE Good Practice: GeoJSON encoding of INSPIRE datasets
## Name of the GP
*GeoJSON encoding of INSPIRE datasets*
## Description of the GP
This Good Practice (GP) describes a mechanism to create INSPIRE data sets encoded using the GeoJSON encoding standard. 

GeoJSON is an open standard format for geospatial data interchange, designed to represent simple geographical features and their non-spatial attributes. It is based on JSON, the JavaScript Object Notation.
GeoJSON uses a geographic coordinate reference system, World Geodetic System 1984, and units of decimal degrees.
GeoJSON Geometry Objects may be points (which can be used for features like addresses and locations), line strings (e.g. for streets, highways, boundaries), polygons (countries, provinces, tracts of land), and multi-part collections of these types. GeoJSON features are not only used to represent entities of the physical world. For example, mobile routing and navigation apps may describe their service coverage using GeoJSON.

The GeoJSON format has originally been defined by an Internet working group of developers who needed a solution to encode geometries for use in web applications. It has since been formalised by the IETF, a standards organisation which develops specifications concerning the Internet as [RFC 7946](https://tools.ietf.org/html/rfc7946).

Within INSPIRE, the GeoJSON encoding can be used to encode data from several themes in order to improve data sharing via APIs and the usability of the data in web clients such as ArcMap, QGIS, OpenLayers, Leaflet and in mobile applications.

It can serve as an *alternative encoding* that can be used instead of the default encoding for simple data, where there is no information loss. In other cases, this GeoJSON encoding may serve as an *additional* encoding only.

When it is used as alternative encoding, the dataset shall be compliant with the INSPIRE Implementing Rules (IR), and technical compliance will be demonstrated through transformation to the default encoding (GML). 

The GeoJSON encoding can be used on core INSPIRE data specifications, or on extensions, and can also be use-case specific. This means that even for one INSPIRE theme, multiple logical schemas could, over time, become available.
GeoJSON models related to the different data themes/use cases need be described in the INSPIRE-MIF [repository for the GeoJSON encoding](https://github.com/INSPIRE-MIF/gp-GeoJSON-encodings). 

For any GeoJSON logical schema to be accepted as specific implementation of this GP, the following resources must be created:

- A description of the logical model, its relevance and expected benefits, its implementations and its limitations compared to the default encoding
- A JSON schema
- A formal, executable specification of the *UML-to-GeoJSON* model transformation or the *GML-to-GeoJSON* model transformation referencing and conforming to the generic INSPIRE model transformation rules in the INSPIRE-MIF [model-transformation-rules](https://github.com/INSPIRE-MIF/model-transformation-rules) repository. These generic INSPIRE model transformation rules are encoding-agnostic and will/may be underpinning the development of different encodings for INSPIRE data. These will in turn be described in their own, encoding-specific INSPIRE-MIF repositories. The [gp-GeoJSON-encodings](https://github.com/INSPIRE-MIF/gp-GeoJSON-encodings) repository is the encoding-specific repository for this GP. The executable specification can be delivered in any form that takes a computer-readable model as input and creates a computer-readable model as output. These specifications can be programs. They need to be documented in such a way that the mapping is human-readable. Examples include an annotated ShapeChange configuration, an XSLT, or a hale studio model transformation.

- A formal, executable model for data transformation that allows to transform a data set encoded as GeoJSON to the default encoding. This can be delivered as an ETL workbench (e.g. hale studio transformation project, FME workbench), as a standalone program or as a service. In all cases, the executable model must be documented in a human-readable form.


## INSPIRE component(s)
**Data:** this GP describes how data falling under any INSPIRE theme can be encoded in GeoJSON format in such a way that the abstract requirements from related specifications are met. The GP relies on INSPIRE code lists, and transformation services.

**Note:** This document does not describe a formal mechanism to publish data sets as a network service. 

## References
### Normative reference
- [GeoJSON - IETF RFC 7946](https://tools.ietf.org/html/rfc7946)
- [Common Model Transformation Rules](https://github.com/INSPIRE-MIF/model-transformation-rules)


### Other references
The Good Practice is based on the [INSPIRE UML-to-GeoJSON encoding rule](https://github.com/INSPIRE-MIF/gp-GeoJSON-encodings/blob/main/spec/GeoJSON-encoding-rule.md))

## Relevance & expected benefits
Enhance the usability of INSPIRE data in web and mobile applications and data sharing via APIs.

#### Optimal Use Case

- Consumption in web & mobile applications
- Small Payloads (< 10MB)
- Simple geometries 
- Limited Precision geometries


## Intended Outcome
The expected outcome is that the various communities of INSPIRE implementers create logical data models for GeoJSON for a wide range of INSPIRE themes and use cases. To make sure interoperability and compliance are guaranteed, all these implementers rely on the common process and set of rules described in this good practice.

## Evidence of implementation & support
The good practice does not require any specific tool support beyond basic support for the GeoJSON specification. The GeoJSON is supported by all major GIS tools such as ArcGIS and QGIS, ETL tools such as hale studio and FME, and libraries such as GDAL/OGR. 

The Good Practice also requires the submission of formal model transformation and data transformation rules for each data model. A simple mapping table is not considered sufficient. To create these formal rules, model transformation tools such as ShapeChange as well as data transformation tools such as hale studio and FME can be used.

*Concrete implementations*

Concrete implementations of the good practice are provided as issues in the in the [repository for the GeoJSON encoding](https://github.com/INSPIRE-MIF/gp-GeoJSON-encodings) using the [ad-hoc template](https://github.com/INSPIRE-MIF/gp-geojson-encodings/issues/new?assignees=&labels=&template=share_implementation_evidence.md). 


# Limitations
This Good Practice only describes the framework in which specific GeoJSON logical models for INSPIRE data sets are created. The theme-specific or use-case specific encoding rules will be made available in the INSPIRE-MIF [GeoJSON repository](https://github.com/INSPIRE-MIF/gp-GeoJSON-encodings). 

### Technical limitations
GeoJSON uses a geographic coordinate reference system, World Geodetic System 1984, and units of decimal degrees.
In some cases, such as the handling of high-cardinality properties, the GeoJSON encoding rule underlying this GP makes a trade-off, so that implementers might need additional model and instance transformation rules to make adjustments for specific data sets and environments.
The GeoJSON format cannot deal with 3D geometries and coverage/raster data, therefore this GP cannot be used for those types of data.

