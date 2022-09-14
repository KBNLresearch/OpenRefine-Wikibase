# OpenRefine-Wikibase
Files for interaction between OpenRefine and KB Wikibases. 

Purpose: reconciling and uploading of data against KB Wikibases using Openfine 
 
## Wikibases of the KB 
* https://kbtestwikibase.wikibase.cloud/wiki/Main_Page (informal test/prototyping WB instance, not part of the KB IT infrastructure)
* http://kbga-wiki-test.westeurope.azurecontainer.io/wiki/Main_Page (formal test WB instance, part of the IT-infra of the KB)

## Setting up a reconciliation service for a Wikibase instance

**General**
* Installing the reconciliation service : https://openrefine-wikibase.readthedocs.io/en/latest/install.html
* You will also need to install two extensions in your Wikibase: [UniversalLanguageSelector](https://www.mediawiki.org/wiki/Special:MyLanguage/Extension:UniversalLanguageSelector) and (optionally) [CirrusSearch](https://www.mediawiki.org/wiki/Extension:CirrusSearch).

**KB specific**
* [config.py](config.py) is an example configuration file for making a Dockerized Wikibase reconciliation service as described in https://openrefine-wikibase.readthedocs.io/en/latest/install.html#installing-with-docker. 
  * This will expose the recon service at http://localhost:8000 (as specified in the *this_host* parameter).
  * This file has been succesfully tested with a service run on a local Windows10 machine. See [these two](https://twitter.com/ookgezellig/status/1569720757009403905) [tweets](https://twitter.com/ookgezellig/status/1569732763678277638). 
* For making this work for other WB instances, change *https://kbtestwikibase.wikibase.cloud* into the URL of the specific KB Wikibase you are dealing with, and don't forget to change the *wikibase_name*, the *fallback_image_url* and other relevent parameters accordingly.

## Connecting OpenRefine to a Wikibase instance
Once you have a working reconciliation service for your Wikibase instance, you can connect OpenRefine to it. All you need is a so-called manifest for that instance, which provides some metadata and links required for the connection to work.

**General**
* Connecting OpenRefine to a Wikibase instance: https://docs.openrefine.org/manual/wikibase/configuration
* Example manifests: https://github.com/OpenRefine/wikibase-manifests

**KB specific**
* A manifest for connecting OpenRefine to *https://kbtestwikibase.wikibase.cloud* is available on [kb-test-wikibase-cloud-manifest.json](kb-test-wikibase-cloud-manifest.json).
* For making this work for other WB instances, change *https://kbtestwikibase.wikibase.cloud* into the URL of the specific KB Wikibase you are dealing with, and don't forget to specify the base URL of the KB reconcilation service (g. http://localhost:8000 in the above example).
