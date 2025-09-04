# eva-app
eva app and related helm charts


## Installation

### Clone eva-app helm repository

It includes values templates in addition to charts.

```sh
git clone https://github.com/mellerikat/eva-app.git
cd eva-app
```

### Install eva-app

```sh
cp -r values.tpl/app-{chart version} .values-{postfix you want}
```

Modify values in .values-{postfix you want} to your environment.

```sh
helm repo add eva-app https://mellerikat.github.io/eva-app
helm repo update
```

```sh
helm upgrade --install eva-app --namespace eva-app eva-app/eva-app --values values.yaml
```


If the service account doesn't have ECR Pull access, you might need to force the Helm client to pull the eva-app docker mage like this,
```sh
$ aws ecr get-login-password --region ap-northeast-2 | sudo docker login --username AWS --password-stdin 339713051385.dkr.ecr.ap-northeast-2.amazonaws.com
$ docker pull 339713051385.dkr.ecr.ap-northeast-2.amazonaws.com/mellerikat/release/eva-app:{{version}}   # <= 2.1.2)
```
