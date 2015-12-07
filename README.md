# Symfony 2 Demo Application on OpenShift

This is an example how the [Symfony 2 Demo Application](https://github.com/symfony/symfony-demo) can be deployed on the OpenShift V3 PaaS

## Usage


1. Create a new OpenShift 3 Project

```
$ oc new-project symfony2-demo
```

2. Run the following command to create the symfony Demo Application

		$ oc create -f https://raw.githubusercontent.com/phil-pona/ose3-symfony2-ex/master/openshift/templates/symfony-demo.json

4. Depending on the state of your system, and whether additional items need to be downloaded, it may take around a minute for your build to be started automatically.  If you do not want to wait, run

		$ oc start-build symfony-demo

5. Once the build is running, watch your build progress  

		$ oc build-logs symfony-demo-1

6. Wait for symfony-demo pods to start up (this can take a few minutes):  

		$ oc get pods -w

# License

Released under the Apache License 2.0. See the [LICENSE](https://github.com/phil-pona/ose3-symfony2-ex/blob/master/LICENSE) file.

