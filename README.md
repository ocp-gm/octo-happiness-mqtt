[Contribute via OpenShift Dev Spaces](https://devspaces.apps.ocp.ocp-gm.de/#https://github.com/sa-mw-dach/octo-happiness-template-java?che-editor=eclipse/che-theia/latest)

# octo-happiness-template-java# octo-happiness-template-java Project

This project shows an easy to use and full install of an application pipeline and deployment via helm.

## Running the application in dev mode

You can run your application in dev mode that enables live coding using:

```bash
docker-compose up
./mvnw compile quarkus:dev
```

or via quarkus cli, just run

```bash
docker-compose up
quarkus dev
```

> **_NOTE:_**  Quarkus now ships with a Dev UI, which is available in dev mode only at http://localhost:8080/q/dev/.

## Packaging and running the application

1. Login to your oc cli
2. Navigate to the repo root and run
3. ```helm upgrade -i octo-happiness-template-java infra/helm```

## Packaging and running the application via quarkus build

1. Login to your oc cli
2. Navigate to the repo root and run
3. ```quarkus build -Dquarkus.kubernetes.deploy=true -DskipTests=true -DskipITs=true```

The skip of the test is used, because we set connection urls to a not exposed service which can not be used at build
time.

## Uninstall

You can uninstall the installed helm chart via

```bash
helm uninstall octo-happiness-template-java 
```

Afterwards you will have do delete the pvc manually

```bash
oc delete pvc builder-pvc
```