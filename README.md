# OpenRefine-Wikibase
Files for interaction between OpenRefine and KB Wikibases. 

Allowing 
* uploading of data to KB Wikibases via OpenRefine
* reconciling data against KB Wikibases using Openfine  

## OpenRefine documentation
* Connecting OpenRefine to a Wikibase instance : https://docs.openrefine.org/manual/wikibase/configuration
  * Example manifests: https://github.com/OpenRefine/wikibase-manifests
* Reconciling with Wikibase: https://docs.openrefine.org/manual/wikibase/reconciling + https://openrefine-wikibase.readthedocs.io/en/latest/

[config.py](config.py) is an example configuration file for the reconciliation service as described in https://openrefine-wikibase.readthedocs.io/en/latest/install.html#installing-with-docker
Change 'https://kbtestwikibase.wikibase.cloud' into the Wikibase you are dealing with and don't forget to change the *wikibase_name* 


## Wikibases of the KB 
* https://kbtestwikibase.wikibase.cloud/wiki/Main_Page (external test/prototyping WB-instance)
* http://kbga-wiki-test.westeurope.azurecontainer.io/wiki/Main_Page (internal test WB-instance)
