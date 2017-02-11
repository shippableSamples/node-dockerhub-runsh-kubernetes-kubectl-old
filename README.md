![AyeAye](https://github.com/shippableSamples/node-build-push-docker-hub/blob/master/public/resources/images/captain.png)

# Docker Build, Continuous Integration, and Deployment to Kubernetes for a Node JS application
[![Run Status](https://api.shippable.com/projects/5885ecca11c45a1000af5760/badge?branch=master)](https://app.shippable.com/projects/5885ecca11c45a1000af5760)
[![Coverage Badge](https://api.shippable.com/projects/5885ecca11c45a1000af5760/coverageBadge?branch=master)](https://app.shippable.com/projects/5885ecca11c45a1000af5760)


A simple Node JS application with unit tests and coverage reports using mocha
and istanbul. It does a docker build once CI passes and then pushes the image
to Docker Hub. Upon every successful Every time push to Docker Hub, it is 
automatically deployed to a TEST environment in a Kubernetes cluster running 
on Amazon EC2.

## Run CI for this repo on Shippable
* Fork this repo into your source code account (e.g. GitHub)
* Login into [Shippable](wwww.shippable.com) with this account
* Create an [integration](http://docs.shippable.com/integrations/imageRegistries/dockerHub/) on Shippable for your Docker Hub account
* Update the CI configuration in `shippable.yml` file for your integration names (see comments in file)
* Follow these [setup instructions](http://docs.shippable.com/ci/runFirstBuild/) to enable your forked repo for CI and run a build 

## Add Continuous Delivery pipelines to deploy to Kubernetes

* Create an integration for [Kubernetes](http://docs.shippable.com/integrations/containerServices/kubernetes/)
* All pipeline config is in `shippable.resources.yml` and `shippable.jobs.yml`. Check these files and update config wherever the comment asks you to replace with your specific values
* Follow instructions to add your [Continuous Deployment pipeline](http://docs.shippable.com/tutorials/pipelines/howToAddSyncRepos/)
* Right-click on the runSh job in the SPOG view named 'shipdemo-kubectl-deploy-test' and run the job
* Your app should be deployed to your Kubernetes cluster as a Test pod
* Follow instructions to [connect your Continuous Integration project to your Continuous Delivery pipelines](http://docs.shippable.com/tutorials/pipelines/connectingCiPipelines/)
* Right-click on the runSh job in the SPOG view named 'shipdemo-kubectl-deploy-prod' and run the job to deploy to a Prod pod
* Make a change to your forked repo and commit to GitHub - watch your pipeline automatically execute CI with push to Docker Hub and automatic deployment to the Test environment in Kubernetes
* Then right-click to deploy the newest changes to the Prod environment

Your end-to-end pipeline is complete! Now, any change you make to the application will be deployed to your Kubernetes Test pod and be ready to manually deploy a Prod pod, as well.

### CI Console Log
![CI Console Log](https://github.com/shippableSamples/node-build-push-docker-hub-deploy-kubernetes-kubectl/blob/master/public/resources/images/console-log.png)

### CI Integration View
![CI Integration View](https://github.com/shippableSamples/node-build-push-docker-hub-deploy-kubernetes-kubectl/blob/master/public/resources/images/trigger-deploy-kubernetes.png)

### CD Pipeline
![CD Pipeline](https://github.com/shippableSamples/node-build-push-docker-hub-deploy-kubernetes-kubectl/blob/master/public/resources/images/deployment-pipeline-to-kubernetes.png)