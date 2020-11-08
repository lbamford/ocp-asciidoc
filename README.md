# ocp-asciidoc
Experiment with Docker, OpenShift, Apache and Asciidoc 

From asciidoc to published web content, pdf etc.

The aim is to trigger re-deployments when the source code changes. So content is automatically updated with latest asciidoc generated output.

## Steps

* login to OpenShift
** oc project ocp-directory

* add asciidoctor/docker-asciidoctor to openshift internal register
** oc import-image asciidoctor/docker-asciidoctor --confirm

* run deploy yaml, this has a couple of init containers that pull the code then run asciidoctor
** oc apply -f deploy.yml 

* check all good in openshift

* open route in web browser check the output


## Init Containers

https://docs.openshift.com/container-platform/4.1/nodes/containers/nodes-containers-init.html

Init containers are useful for checking certain preconditions are met before starting the main container, for example you might want to know a database is available before starting a web service. 

They can also be used for injecting content into the main container by using temporary shared storage, that is mounted and available to all containers (withing the pod) during initialisation.