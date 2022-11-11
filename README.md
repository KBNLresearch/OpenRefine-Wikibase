# OpenRefine-Wikibase
Files for interaction between OpenRefine and KB Wikibases. 

Purpose: reconciling and uploading data to Wikibases of the KB, using Openfine 
 
## Wikibases of the KB 
* https://kbtestwikibase.wikibase.cloud/wiki/Main_Page (informal test/prototyping WB instance, not part of the KB IT infrastructure)
* http://kbga-wiki-test.westeurope.azurecontainer.io/wiki/Main_Page (formal test WB instance, part of the IT-infra of the KB)

## Setting up a reconciliation service for a Wikibase instance

**General**
* Installing the reconciliation service : https://openrefine-wikibase.readthedocs.io/en/latest/install.html
* You will also need to install two extensions in your Wikibase: [UniversalLanguageSelector](https://www.mediawiki.org/wiki/Special:MyLanguage/Extension:UniversalLanguageSelector) and (optionally) [CirrusSearch](https://www.mediawiki.org/wiki/Extension:CirrusSearch).

**KB specific**
* [kb-test-wikibase-cloud-config.py](kb-test-wikibase-cloud-config.py) is an example configuration file for making a Dockerized Wikibase reconciliation service for https://kbtestwikibase.wikibase.cloud, as described in https://openrefine-wikibase.readthedocs.io/en/latest/install.html#installing-with-docker. 
  * This file must be renamed to config.py when used in the actual Docker setup 
  * This will expose the recon service at http://localhost:8000 (as specified in the *this_host* parameter).
  * This file has been succesfully tested with a service run on a local Windows10 machine. See [these two](https://twitter.com/ookgezellig/status/1569720757009403905) [tweets](https://twitter.com/ookgezellig/status/1569732763678277638). 
* For making this work for other WB instances, change *https://kbtestwikibase.wikibase.cloud* into the URL of the specific KB Wikibase you are dealing with, and don't forget to change the *this_host*, *wikibase_name*, the *fallback_image_url* and other relevent parameters accordingly.
  * [kbga-test-azure-config.py](kbga-test-azure-config.py) is the custom configuration file for http://kbga-wiki-test.westeurope.azurecontainer.io. This file must be renamed to config.py when used in the actual Docker setup.

## Connecting OpenRefine to a Wikibase instance
Once you have a working reconciliation service for your Wikibase instance, you can connect OpenRefine to it. All you need is a so-called manifest for that instance, which provides some metadata and links required for the connection to work.

**General**
* Connecting OpenRefine to a Wikibase instance: https://docs.openrefine.org/manual/wikibase/configuration
* Example manifests: https://github.com/OpenRefine/wikibase-manifests

**KB specific**
* A (basic) manifest for connecting OpenRefine to https://kbtestwikibase.wikibase.cloud is available on [kb-test-wikibase-cloud-manifest.json](kb-test-wikibase-cloud-manifest.json).
* For making this work for other WB instances, change *https://kbtestwikibase.wikibase.cloud* into the URL of the specific KB Wikibase you are dealing with, and don't forget to specify the base URL of the KB reconcilation service (g. http://localhost:8000 in the above example).
  * [kbga-test-azure-manifest.json](kbga-test-azure-manifest.json ) is the (basic) manifest for connecting OpenRefine to http://kbga-wiki-test.westeurope.azurecontainer.io
  
** Special:Tags
When using OpenRefine to write to your Wikibase, make sure that (using the Admin account) you add the tags “openrefine-3.x” (x=3,4,5,6,7,..) to the Special:Tags page of your Wikibase, depending on which versions (v3.3, 3.4.. 3.7) of OpenRefine you want to allow to write to your wikibase. See for instance https://www.wikidata.org/wiki/Special:Tags 
<image scr="images/special-tags.jpg">

 

Als je die labels nog niet in je WB toegevoegd hebt, dan geeft OR (in dit geval v3.7) de volgende foutmeldingen

 

Je moet er dan ook voor zorgen dat in de manifest.json die je aan OR toevoegt (https://github.com/KBNLresearch/OpenRefine-Wikibase/blob/main/kbga-test-azure-manifest.json), je in het veld “tag” precies de waarde "openrefine-${version}" hebt staan, overeenkomstig de syntax die je in de Special:Tags hebt opgenomen

 

