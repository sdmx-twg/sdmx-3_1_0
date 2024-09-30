# SDMX 3.1.0 Public Review

## Overview

A draft version of the SDMX 3.1.0 specifications have been prepared by the TWG.

Comments are invited on the changes and improvements proposed. 

Comments may be submitted as GitHub issues using the following link https://github.com/sdmx-twg/sdmx-3_1_0/issues. 

The closing date for comments is 24 Dec 2024. General questions and requests for help should be e-mailed to the TWG twg@sdmx.org.

Please raise all issues and comments in the issues section of this repository

[https://github.com/sdmx-twg/sdmx-3_1_0/issues](https://github.com/sdmx-twg/sdmx-3_1_0/issues)

**The public review will close on December 24th 2024**


## Location

### Technical Specifications

[Section 1](https://github.com/sdmx-twg/sdmx-3_1_0/raw/refs/heads/main/specifications/SDMX_3-1-0_SECTION_1_DRAFT-1_0.docx) FRAMEWORK FOR SDMX TECHNICAL STANDARDS

[Section 2](https://github.com/sdmx-twg/sdmx-3_1_0/raw/refs/heads/main/specifications/SDMX_3-1-0_SECTION_2_DRAFT-1_0.docx) INFORMATION MODEL: UML CONCEPTUAL DESIGN

[Section 5](https://github.com/sdmx-twg/sdmx-3_1_0/raw/refs/heads/main/specifications/SDMX_3-1-0_SECTION_5_DRAFT-1_0.docx) SDMX REGISTRY SPECIFICATION: LOGICAL FUNCTIONALITY AND LOGICAL INTERFACES

[Section 6](https://github.com/sdmx-twg/sdmx-3_1_0/raw/refs/heads/main/specifications/SDMX_3-1-0_SECTION_6_DRAFT-1_0.docx) TECHNICAL NOTES

**Note**  The UML Model has not been updated to reflect the changes, and as such some of the diagrams in the technical specifications are not up to date with the 3.1.0 changes.
 
### Git Repositories - SDMX 3.1.0   

[XML Schema](https://github.com/sdmx-twg/sdmx-ml/tree/develop)

[JSON Schema](https://github.com/sdmx-twg/sdmx-json/tree/develop)

[REST API](https://github.com/sdmx-twg/sdmx-rest/tree/develop)

## SDMX 3.1.0 Major Changes

SDMX 3.1.0 introduces a new Structure type ‘Dimension Constraint’ to satisfy the use case for a DSD to evolve over time, without breaking existing data collections.  

In satisfying this use case it is proposed to simplify the general SDMX Constraint mechanism by reversing the direction of reference; In SDMX 3.1.0 it is the Constrainable (DSD, Dataflow, Provision Agreement, MSD, Metadataflow, Metadata Provision Agreement) that references the Data Constraint, whilst in SDMX 3.0.0 and lower it was the Constraint that referenced the Constrainable.

The changes are listed below, along with the Rationale:

### Dimension Constraint: New Structure

This structure enables Dataflows to fix their Dimensions to all or a subset of those defined by the DSD to which they adhere.  

This structure is only required if it is foreseen that the DSD will have additional Dimensions added without undergoing a major version change. 

### Data Constraint: Reference reversed

This change simplifies constraint management, and creates a consistency between the new Dimension Constraint, which constrains Dimensions, and the Data Constraint which constrains content.

### Advanced Release Calendar: Removed

The Data Constraint for version 3.0.0 contained an Advanced Release calendar, which was documented to serve two functions; to document to data consumers when publications are due, and to restrict when a data provide can report data.  

It was noted that keeping this structure in place can create ambiguities with both purpose, i.e. is it there to report or to restrict, and outcome i.e. it is possible to reference multiple.  

### Cube Region: Dimension and Attribute distinction removed

The cube region provides a means to create subsets of Codelists; this feature should not be coupled to the context of how the Codelist is used. 

### Metadata Constraint: Removed

It is possible to create the same restrictions in a Data Constraint. By reusing the DataConstraint as a way to restrict content, the same content restrictions can be shared between structure types. 

### Availability Constraint: no longer Maintainable

The Availability Constraint is the only Constraint which keeps its reference to a DSD, Dataflow, or Provision Agreement.  It reports data that exists for a point in time, based on the data query context and content; as such is is not a structure type that can be maintained in a system, and therefore should not have a URN, and the mandatory properties of a Maintainable such as Name and Agency are not relevant.
 
### Categorisation: Fixed version to 1.0

There is no use case for supporting multiple versions of a Categorisation.
  
###  Metadata Registration: Removed references to this in the documentation

Whilst it is documented that this is possible, it is not possible with the current schema to registry a Metadata Provision Agreement. A Registration can only reference a Provision Agreement (data).  Furthermore, the REST API only describes Registration retrieval with data queries, not metadata queries - so no work has been done in the schema or web service to support this.  





