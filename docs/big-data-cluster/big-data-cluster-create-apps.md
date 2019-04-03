---
title: Bereitstellen von Anwendungen mithilfe von mssqlctl
titleSuffix: SQL Server big data clusters
description: Eine Python- oder R-Skript als eine Anwendung auf SQL Server-2019 big Data-Cluster (Vorschau) bereitstellen.
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: jroth
manager: craigg
ms.date: 03/27/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 6cdedc7eac7b9faa2d266b1a32c299d8b7f5fe73
ms.sourcegitcommit: 1a4aa8d2bdebeb3be911406fc19dfb6085d30b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2019
ms.locfileid: "58872000"
---
# <a name="how-to-deploy-an-app-on-sql-server-big-data-cluster-preview"></a>Gewusst wie: Bereitstellen einer app auf SQL Server-big Data-Cluster (Vorschau)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel beschreibt das Bereitstellen und Verwalten von R und Python-Skript als eine Anwendung in einer SQL Server-2019 big Data-Cluster (Vorschau).

## <a name="whats-new-and-improved"></a>Was ist, neue und verbesserte

- Ein einzelnes Befehlszeilen-Hilfsprogramm zum Verwalten von Cluster und die app.
- Vereinfachte anwendungsbereitstellung und bietet gleichzeitig eine präzise Kontrolle über die Spec-Dateien.
- Hosten von zusätzlichen Typen: SSIS und MLeap (neu in CTP 2.3) unterstützt
- [VS Code-Erweiterung](app-deployment-extension.md) zum Verwalten von anwendungsbereitstellung

Anwendungen werden bereitgestellt und verwaltet mit `mssqlctl` Befehlszeilen-Hilfsprogramm. Dieser Artikel enthält Beispiele dafür, wie zum Bereitstellen von apps über die Befehlszeile an. Erfahren, wie Sie mit diesem Visual Studio Code finden Sie unter [VS Code-Erweiterung](app-deployment-extension.md).

Die folgenden Arten von apps werden unterstützt:
- R und Python-apps ("Funktionen", "Modelle" und "apps")
- MLeap-Bereitstellung
- SQL Server Integration Services (SSIS)

## <a name="prerequisites"></a>Erforderliche Komponenten

- [SQL Server-2019 big Data-cluster](deployment-guidance.md)
- [Mssqlctl-Befehlszeilen-Hilfsprogramm](deploy-install-mssqlctl.md)

## <a name="capabilities"></a>Funktionen

In SQL Server 2019 (Vorschau) CTP 2.4 Sie erstellen, löschen, zu beschreiben, initialisiert werden können, Liste ausgeführt, und aktualisieren Sie Ihre Anwendung. Die folgende Tabelle beschreibt die Befehle der Anwendung-Bereitstellung, mit denen Sie mit **Mssqlctl**.

|Befehl |Description |
|:---|:---|
|`mssqlctl login` | Melden Sie sich bei einer SQL Server-big Data-cluster |
|`mssqlctl app create` | Erstellen Sie die Anwendung. |
|`mssqlctl app delete` | Löschen Sie die Anwendung. |
|`mssqlctl app describe` | Beschreiben Sie die Anwendung. |
|`mssqlctl app init` | KickStart neue Anwendung Gerüst. |
|`mssqlctl app list` | Auflisten von Anwendungen. |
|`mssqlctl app run` | Führen Sie die Anwendung. |
|`mssqlctl app update`| Aktualisieren Sie die Anwendung. |

Erhalten Sie Hilfe bei der `--help` Parameter wie im folgenden Beispiel gezeigt:

```bash
mssqlctl app create --help
```

In den folgenden Abschnitten werden diese Befehle im Detail beschrieben.

## <a name="sign-in"></a>Anmelden

Bevor Sie bereitstellen oder mit Anwendungen interagieren, melden Sie sich beim big Data-cluster mit SQL Server die `mssqlctl login` Befehl. Geben Sie die externe IP-Adresse der `endpoint-service-proxy` Dienst (z. B.: `https://ip-address:30777`) zusammen mit den Benutzernamen und das Kennwort für den Cluster.

```bash
mssqlctl login -e https://<ip-address-of-endpoint-service-proxy>:30777 -u <user-name> -p <password>
```

## <a name="aks"></a>AKS

Wenn Sie ACS verwenden, müssen Sie den folgenden Befehl zum Abrufen der IP-Adresse Ausführen der `endpoint-service-proxy` Dienst mit dem folgenden Befehl in einem nachfolgenden bash- oder Cmd-Fenster:


```bash
kubectl get svc endpoint-service-proxy -n <name of your cluster>
```

## <a name="kubeadm-or-minikube"></a>Kubeadm oder Minikube

Wenn Sie Kubeadm oder Minikube führen Sie den folgenden Befehl verwenden, um die IP-Adresse zur Anmeldung beim Cluster abrufen

```bash
kubectl get node --selector='node-role.kubernetes.io/master'
```

## <a name="create-an-app"></a>Erstellen einer app

Um eine Anwendung zu erstellen, verwenden Sie `mssqlctl` mit der `app create` Befehl. Diese Dateien befinden sich lokal auf dem Computer, dem Sie erstellen die app aus.

Verwenden Sie die folgende Syntax, um eine neue app in big Data-Cluster zu erstellen:

```bash
mssqlctl app create --spec <directory containing spec file>
```

Der folgende Befehl zeigt ein Beispiel für diesen Befehl könnte folgendermaßen aussehen:

```bash
mssqlctl app create --spec ./addpy
```

Dabei wird davon ausgegangen, dass Sie Ihre Anwendung gespeichert, der `addpy` Ordner. Dieser Ordner enthält auch eine Spezifikationsdatei für die Anwendung namens aufgerufene `spec.yaml`. Finden Sie unter [der Anwendungsbereitstellung Seite](concept-application-deployment.md) für Weitere Informationen zu den `spec.yaml` Datei.

Um diese app-Beispiel-app bereitzustellen, erstellen Sie die folgenden Dateien in einem Verzeichnis namens `addpy`:

- `add.py`. Kopieren Sie den folgenden Python-Code in diese Datei ein:
   ```py
   #add.py
   def add(x,y):
        result = x+y
        return result
    result=add(x,y)
   ```
- `spec.yaml`. Kopieren Sie den folgenden Code in diese Datei ein:
   ```yaml
   #spec.yaml
   name: add-app #name of your python script
   version: v1  #version of the app
   runtime: Python #the language this app uses (R or Python)
   src: ./add.py #full path to the location of the app
   entrypoint: add #the function that will be called upon execution
   replicas: 1  #number of replicas needed
   poolsize: 1  #the pool size that you need your app to scale
   inputs:  #input parameters that the app expects and the type
     x: int
     y: int
   output: #output parameter the app expects and the type
     result: int
   ```

Führen Sie dann den folgenden Befehl aus:

```bash
mssqlctl app create --spec ./addpy
```

Sie können überprüfen, ob die app bereitgestellt wurde, mithilfe des List-Befehls:

```bash
mssqlctl app list
```

Wenn die Bereitstellung nicht abgeschlossen ist. Daraufhin sollte die `state` anzeigen `WaitingforCreate` wie im folgenden Beispiel:

```json
[
  {
    "name": "add-app",
    "state": "WaitingforCreate",
    "version": "v1"
  }
]
```

Wenn die Bereitstellung abgeschlossen ist, sollte die `state` ändern in `Ready` Status:

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="list-an-app"></a>App eintragen

Sie können alle apps, die erfolgreich mit erstellte Auflisten der `app list` Befehl.

Der folgende Befehl listet alle verfügbare Anwendungen in Ihrer big Data-Cluster:

```bash
mssqlctl app list
```

Wenn Sie einen Namen und eine Version angeben, werden diese app und den Zustand ("erstellen" oder "Ready") aufgeführt:

```bash
mssqlctl app list --name <app_name> --version <app_version>
```

Das folgende Beispiel zeigt die mit diesem Befehl:

```bash
mssqlctl app list --name add-app --version v1
```

Daraufhin sollte eine Ausgabe ähnlich dem folgenden Beispiel:

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="run-an-app"></a>Ausführen einer app

Wenn die app wird eine `Ready` aufweist, können Sie sie durch eine Ausführung mit der angegebenen Eingabeparameter. Verwenden Sie die folgende Syntax, um eine app auszuführen:

```bash
mssqlctl app run --name <app_name> --version <app_version> --inputs <inputs_params>
```

Der Befehl im folgenden Beispiel wird veranschaulicht, mit dem Befehl "run":

```bash
mssqlctl app run --name add-app --version v1 --inputs x=1,y=2
```

Wenn die Ausführung erfolgreich war, sehen Sie die Ausgabe angegeben wird, wenn Sie die app erstellt. Im Folgenden finden Sie ein Beispiel.

```json
{
  "changedFiles": [],
  "consoleOutput": "",
  "errorMessage": "",
  "outputFiles": {},
  "outputParameters": {
    "result": 3
  },
  "success": true
}
```

## <a name="create-an-app-skeleton"></a>Erstellen Sie ein app-Gerüst

Der Init-Befehl bietet es sich um ein Gerüst mit den entsprechenden Elementen, die zum Bereitstellen einer app erforderlich ist. Das folgende Beispiel erstellt die Hello, die Sie dies tun können, indem Sie den folgenden Befehl ausführen.

```bash
mssqlctl app init --name hello --version v1 --template python
```

Dadurch wird einen Ordner namens Hello erstellt.  Sie können `cd` in das Verzeichnis, und überprüfen Sie die generierten Dateien im Ordner "". spec.yaml definiert die app, wie z. B. Name, Version und Quellcode. Sie können die Spezifikation zum Ändern von Name, Version, Eingaben und Ausgaben bearbeiten.

Hier ist eine Beispielausgabe aus der Init-Befehl, den in den Ordner angezeigt werden

```
hello.py
README.md
run-spec.yaml
spec.yaml

```

## <a name="describe-an-app"></a>Beschreiben Sie eine app

Der Befehl für die Beschreibung bietet ausführliche Informationen über die app, einschließlich der Endpunkt in Ihrem Cluster. Dies wird normalerweise durch ein app-Entwickler verwendet, zum Erstellen einer app mithilfe des Swagger-Clients und mithilfe des Webdiensts für die Interaktion mit der app RESTful-basiert. Finden Sie unter [Anwendungen für big Data-Cluster nutzen](big-data-cluster-consume-apps.md) für Weitere Informationen.

```json
{
  "input_param_defs": [
    {
      "name": "x",
      "type": "int"
    },
    {
      "name": "y",
      "type": "int"
    }
  ],
  "links": {
    "app": "https://10.1.1.3:30777/api/app/add-app/v1",
    "swagger": "https://10.1.1.3:30777/api/app/add-app/v1/swagger.json"
  },
  "name": "add-app",
  "output_param_defs": [
    {
      "name": "result",
      "type": "int"
    }
  ],
  "state": "Ready",
  "version": "v1"
}
```

## <a name="delete-an-app"></a>Löschen einer app

Um eine app aus Ihrer big Data-Cluster zu löschen, verwenden Sie die folgende Syntax:

```bash
mssqlctl app delete --name add-app --version v1
```

## <a name="next-steps"></a>Nächste Schritte

Informationen zur Integration von apps, die auf SQL Server, die in Ihren eigenen Anwendungen auf big Data-Cluster bereitgestellten [Anwendungen für big Data-Cluster nutzen](big-data-cluster-consume-apps.md) für Weitere Informationen. Sie können auch zusätzliche Beispiele Auschecken [Beispiele für das Bereitstellen von Apps](https://aka.ms/sql-app-deploy).

Weitere Informationen zu SQL Server-big Data-Clustern, finden Sie unter [was SQL Server-2019 big Data-Cluster sind?](big-data-cluster-overview.md).
