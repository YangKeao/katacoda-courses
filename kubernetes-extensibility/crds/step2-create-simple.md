Let's begin by inspecting a small example YAML file that declares a simple Thermometer:

`ccat thermometer-crd-minimal.yaml`{{execute}}

In this CRD definition, the Kind is CustomResourceDefinition and the CRD is scoped to namespaces. We also provide the plural and short alias names for the same resource. Later we will define features that we can add to this specification. In its current form, it's the most simplistic.

> In this scenario we are using Kubernetes v1.18, so in the CRD definition we use `apiVersion: apiextensions.k8s.io/v1`. If you are using Kubernetes v1.16 or newer, you can use v1, which has a [slightly improved CRD format](https://kubernetes.io/docs/tasks/extend-kubernetes/custom-resources/custom-resource-definition-versioning/).

Before we give this declaration to your cluster, let's see what is currently on the cluster. There should be no preexisting CRDs:

`kubectl get crds`{{execute}}

And of course, Kubernetes lacks any definition of a Thermometer, so a small error ensues if your try to get them:

`kubectl get thermometers`{{execute}}

Now, submit the Thermometer CRD to Kubernetes:

`kubectl apply -f thermometer-crd-minimal.yaml`{{execute}}

Notice the `apply` command was used instead of the `create` because we will be applying additional upgrades to the CRD in the subsequent steps. Kubernetes is now aware of this new resource type:

`kubectl get crds`{{execute}}

Thermometer resources are now listed as a cluster api-resource:

`kubectl api-resources --api-group='d2iq.com' -o wide`{{execute}}

The resource REST management is also added as */apis/d2iq/* to the Kubernetes API:

`kubectl get --raw / | jq . | grep -C3 d2iq`{{execute}}

The REST API URL reveals the Thermometer resource:

`kubectl get -v=9 --raw /apis/d2iq.com/v1beta1/thermometers/ | jq`{{execute}}

Notice that in the last command, we added a [verbosity request](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#kubectl-output-verbosity-and-debugging) `-v=9`. With it set to level 9 (the highest) we get a bit more insight into how the `kubectl` command is obtaining the resource information.

The command also pipes the output to `jq` to pretty-print the JSON with syntax highlights.

The CRD definition just defines the resource type and while Kubernetes recognizes the type, there are no instances of the Thermometer resource type:

`kubectl get trms`{{execute}}

In the next step, let's add a Thermometer based on this type.
