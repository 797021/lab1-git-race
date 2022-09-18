# Description of the contents of this project

## Which are the technologies used in the code

The technologies that we found in the project are:

* Gradle 7.5.1
* Kotlin 1.7
* HTML 5
* Bootstrap
* Markdown

These technologies can be divided depending on its use:

* To document the project it's being used Markdown. Markdown is a language with plain text syntax for the generation of files that can be accessible for different platforms.
* On the server-side we can found Kotlin with the framework Spring, we use Kotlin here because of its features which can be useful on the develop the app.
* To desing the page has been choosen HTML with Bootstrap which is use to customize the page with Sass.
* Finally for build automation we have Gradle. Gradle is a feature which helps us with the compilation of the code, avoiding overwork.

## Deployment

### How to deploy in a Kubernetes cluster

First of all, ensure you've got a properly configured cluster on your computer.
If you don't have one, you can easily install a local Kubernetes cluster via
[Minikube](https://minikube.sigs.k8s.io/docs/start/).

#### With Minikube

First, start your local cluster if you haven't done so yet:

```bash
minikube start
```

Once you have a running minikube cluster, apply the `deployment.yml` manifest as follows
(ensure your current directory is at the root of the project):

```bash
minikube kubectl -- apply -f .\deployment.yaml
```

**Note:** Wait until the pods are on a `Running` state. You can check your cluster status with the following command:

```bash
minikube kubectl get all
```

Finally, expose the service to the browser with the following command:

```bash
minikube service lab1-git-race
```

This will open a tunnel and print a URL that allows you to open the app with your browser of choice.

#### Without Minikube

First check if you can use kubectl on your cluster:

```bash
kubectl --help
```

Once your cluster is up and running, apply the `deployment.yml` manifest as follows
(ensure your current directory is at the root of the project):

```bash
kubectl apply -f ./deployment.yml
```

**Note:** Wait until the pods are on a `Running` state. You can check your cluster status with the following command:

```bash
kubectl get all
```

After that, the service needs to be exposed via port forwarding, so you can open the app with your browser of choice:

```bash
kubectl port-forward svc/lab1-git-race [forwarded-port]:8080
```

For example, if you choose to forward port 3000, the output of the command should be as follows:

```bash
$ kubectl port-forward svc/lab1-git-race 3000:8080
> Forwarding from 127.0.0.1:3000 -> 8080
> Forwarding from [::1]:3000 -> 8080
...
```

If you want to clean the cluster, enter the following command:

```bash
kubectl delete -f deployment.yml
```
