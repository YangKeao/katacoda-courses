# Kubeless on Kubernetes #

[Kubeless](https://github.com/kubeless/kubeless) is a Kubernetes-native serverless framework that lets you deploy small bits of code without having to worry about the underlying infrastructure plumbing. It leverages Kubernetes resources to provide auto-scaling, API routing, monitoring, troubleshooting and more.

_Kubeless_ is purely open-source and non-affiliated to any commercial organization. Help and feedback is welcomed.

Exploring _Kubeless_ is a great way to explore this Kubernetes architectural pattern of using a CLI tool, a controller and some Custom Resource Definition ([CRDs](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/)) optionally along with [Kafka](https://kafka.apache.org/) to achieve a fundamental serverless solution.

_Kubeless_ relies on a command line tool called 'kubeless' to submit functions and perform controlling operations with the Kubeless controller. There is also a user interface to parallel the CLI tool features. A dedicated Kafka system is also added to allow functions to be trigger via publish/subscribe.

You will learn how:

- to install Kubeless on Kubernetes
- functions are deployed and removed
- functions are named, exposed, and invoked
- functions are listed, inspected and monitored

More about the Kubeless architecture is described in the [Kubeless documentation](https://kubeless.io/docs/architecture/).