# Symfony 2 Demo Application on OpenShift

This is an example how the [Symfony 2 Demo Application](https://github.com/symfony/symfony-demo) can be deployed on the OpenShift V3 PaaS

## S2I Image

At the moment the [symfony S2i Image](https://github.com/phil-pona/sti-symfony) is used to build this application, due to the following [issue](https://github.com/openshift/sti-php/issues/73) on the official [sti-php image](https://github.com/openshift/sti-php)

## Usage



1. Create a new OpenShift 3 Project

```
$ oc new-project symfony2-demo
```

1.1 Add Builder Image (only needed as long as the official Image does not support [Symfony](https://github.com/openshift/sti-php/issues/73))
```
$ oc new-app  https://github.com/phil-pona/sti-symfony --context-dir=5.6 --strategy=docker
```

2. Run the following command to create the symfony Demo Application

		$ oc create -f https://raw.githubusercontent.com/phil-pona/ose3-symfony2-ex/master/openshift/templates/symfony-demo.json
		$ oc process symfony-demo | oc create -f -

4. start manually the build of the demo application


		$ oc start-build symfony-demo


5. Once the build is running, watch your build progress  

		$ oc build-logs symfony-demo-1

6. Wait for symfony-demo pods to start up (this can take a few minutes):  

		$ oc get pods -w

7. The Symfony Demo Application 

access the application on <route>/web 

Work in Progress:
add missing .htaccess file




# License

Released under the Apache License 2.0. See the [LICENSE](https://github.com/phil-pona/ose3-symfony2-ex/blob/master/LICENSE) file.

