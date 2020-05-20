## Sphaera App

## About 

This is the app for the [Sphaera](http://sphaera.mpiwg-berlin.mpg.de) project database.

It contains templates and configurations for the metaphacts platform for building a declarative knowledge graph application, which enables end-users to capture, curate, trace and visualise knowledge in the history around a specific text: the Tractatus De sphaera by Johannes de Sacrobosco. 

The [Sphaera](http://sphaera.mpiwg-berlin.mpg.de) project based at the [Max Planck Institute for the History of Science](https://www.mpiwg-berlin.mpg.de) and is led by [Matteo Valleriani](http://www.mpiwg-berlin.mpg.de/en/users/valleriani). [Florian Kräutli](http://www.mpiwg-berlin.mpg.de/en/users/fkraeutli) leads the digital development and is responsible for the design of the app.

The app and project was initially developed in 2017. This version of the app has been migrated in April 2020 by metaphacts to be compatible with newer versions (>= 3.2) for public usage and demonstration purpose.

![Database Home Screen](https://sphaera.mpiwg-berlin.mpg.de/Department-I/sphaera/sphaera-jekyll-site/assets/img/sphaera-db-home.jpg)

## Technology

### Data Model

The Sphaera database is based on open standards and Semantic Web technologies:

* The data model is based on the formal ontology [CIDOC-CRM](http://www.cidoc-crm.org/) and the [FRBRoo](https://www.ifla.org/publications/node/11240) extension for bibliographic records. This ensures that the data is compatible to other sources and remains usable in the foreseeable  future. Please note that the [Erlangen](http://erlangen-crm.org/) OWL implementation of CIDOC-CRM was used and extened by FRBRoo.

* Person and place records we include links to [Wikidata](http://www.wikidata.org/), making the dataset part of the growing web of Linked Data. Wikidata  provides links to other authority records such as VIAF and allows  to add new persons or other entities that we discover in our records.

  

### Platform Functionality

The Sphaera app makes use of the following platform components:

* authoring forms including field definitions over complex CIDOC CRM and FRBRoo pattern
* different visualization components (semantic maps, lists, carousels, graphs)
* IIIF image viewer for deep zoom image viewing and annotations (e.g. of scanned book pages)
* components for knowledge graph administration

## How to deploy

The following instructions can be utilized to setup your own instance of Sphaera:

1. Checkout this project and create a zip of the sphaera folder
   `git clone https://github.com/metaphacts/sphaera-app.git` 
   `cd sphaera-app/ && zip -r sphaera.zip sphaera`
2. Install the platform version 3.2 or newer (c.f. [public help](https://help.metaphacts.com/resource/Help:Installation) or help in your version/distribution) with Blazegraph as database. **Please assign sufficient memory** (for example, using `--memory=2g --memory-reservation=2g` in the docker run command) to the platform as well as blazegraph container. 
3. Login to the platform as administrator with root permission and got to Admin -> Apps & Storages -> Upload the `sphaera.zip` via drag&drop and restart the platform (c.f. also [app deployment help]( https://help.metaphacts.com/resource/Help:AppDeployment))
4. Download the existing Sphaera database dump from [MPIWG Dataverse](https://dataverse.mpiwg-berlin.mpg.de/dataverse/sphaera) as NQuads (.nq). Load the file in through the platform Data Import&Export interface using the *"Perserve Contexts"* in the "Advanced Options" tab.



## Changelog

### April 2020

* Decoupled app from infrastructure scripts
* Migrated the app structure to platform version 3.2 and newer
* Tuned/fixed some visualisation queries, for example, on the start page to be more performant and not break blazegraph
* Use the wikidata hyprid lookup from metaphacts for lookups / autosuggestion pattern in person fields (old wdqas hosting with blazegraph text index has been retired).