# eva-app
eva app and related helm charts


## Installation

### Preparing the Helm client for eva-app installation

```sh
helm repo add eva-app https://mellerikat.github.io/eva-app
helm repo update
```

<br>

### Installing the eva-app version

Update the list of available charts from the chart repository.

```sh
helm repo update
```

<br>
Save the chart's default values to a file, then customize the contents to match your environment's configuration.

Caution, please be aware that the default value template can change with each new version of the chart.

```sh
helm show values eva-app/eva-app > my-values.yaml
```

<br>
Update eva-app.

```sh
helm upgrade --install eva-app --namespace eva-app eva-app/eva-app --values my-values.yaml
```

<br>
For deployments outside of the AWS cloud (such as on-premise or NPC), the following command may be required to pull the eva-app image from its repository in AWS ECR.

```sh
region=ap-northeast-2
eva_app_ecr_password=$(aws ecr get-login-password --region ${region})
helm upgrade --install eva-app --values ./values.2.2.3.eva-app.yaml --namespace eva-app eva-app/eva-app --set imagePullSecrets.password="${eva_app_ecr_password}"
```
