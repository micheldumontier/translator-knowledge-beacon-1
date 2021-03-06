# Purpose #

## Overview ##

This project documents the Knowledge Beacon Application Programming Interface (KBAPI). 

Specifically, this repository holds the OpenAPI ("Swagger") definition of the **KBAPI** archived in the 'api' subfolder: https://github.com/NCATS-Tangerine/translator-knowledge-beacon/blob/develop/api/knowledge-beacon-api.yaml

Check out our [Knowledge Beacon Wiki](https://github.com/NCATS-Tangerine/translator-knowledge-beacon/wiki) for additional documentation on the status of Knowledge Beacon API implementations and some additional notes on how to build your own.

# Knowledge Beacons Workflow

The **KBAPI** is primarily designed to support a simple knowledge discovery workflow, as illustrated in following diagram:

![alt text](https://github.com/NCATS-Tangerine/translator-knowledge-beacon/blob/develop/docs/KB_Workflow.png "Knowledge Beacon Workflow")

Aside from the concept and statement accessing endpoints, the **KBAPI** also provides access to the list of concept (*/types*) and relationship (*/predicates*) data types used by the beacon. 

In fact, concept instances returned by various calls (*/concepts?keywords=..*, */concepts/{conceptId}* and the subject/object concepts in knowledge assertions returned by the */statements* endpoint) are specified by the API to be tagged by the semantic concept types (i.e. "gene", "drug", "disease", etc.) reported by the */types* endpoint, which is assumed to be based on a semantic data type controlled vocabulary (originally based on the [UMLS Metamap concept categories](https://metamap.nlm.nih.gov/Docs/SemGroups_2013.txt), but which is now undergoing NCATS Translator curation to a richer ontology).

The **KBAPI** also provides endpoints (*/exactmatches*) to report CURIE identifiers which are deemed to globally identify the functionally equivalent (*sensa*-[SKOS exactMatch](http://www.w3.org/2004/02/skos/core#exactMatch) or [OWL sameAs](https://www.w3.org/2002/07/owl)).

# Knowledge Beacons in Action!

An initial prototype web application client "Translator Knowledge.Bio" accessing Knowledge Beacons is implemented and running at **http://tkbio.ncats.io.**, the code for which is available **[here](https://github.com/NCATS-Tangerine/tkbio)**. 

The pool of known beacons is currently documented in a **[master YAML-formatted catalog of beacons](https://github.com/NCATS-Tangerine/translator-knowledge-beacon/blob/develop/api/knowledge-beacon-list.yaml)**. REST clients may also access aggregate data via the API from all these registered beacons, through a [Knowledge Beacon Aggregator](https://github.com/NCATS-Tangerine/beacon-aggregator), a public version for which is hosted online at **https://kba.ncats.io**. 

Some of these KBAPI wrappers are locally published in other repositories within the NCATS-Tangerine organization, as follows:

* [Reference Beacon](https://github.com/NCATS-Tangerine/reference-beacon): a Java Spring Boot KBAPI accessing a Neo4j server containing [Semantic Medline Database](https://skr3.nlm.nih.gov/SemMedDB/) concepts and relationships text-mined from PubMed abstracts
* [Monarch Database "Biolink" Beacon](https://github.com/NCATS-Tangerine/biolink-beacon): a Python KSAPI accessing the Biolink API of the [Monarch Initiative Biomedical Resource](https://monarchinitiative.org/)
* [nDex Beacon](https://github.com/NCATS-Tangerine/ndex-beacon): a Java wrapper accessing the [nDex biomedical graph archive](http://www.home.ndexbio.org/index/) biomedical network data exchange archive.
* [StringDb Beacon](https://github.com/NCATS-Tangerine/stringdb-beacon) : a Python wrapper for the [STRING Protein-Protein interactions database](https://string-db.org/).

Other beacon wrappers (e.g. Wikidata) are hosted in other repositories elsewhere (see the [catalog of beacons](https://github.com/NCATS-Tangerine/translator-knowledge-beacon/blob/develop/api/knowledge-beacon-list.yaml)).


