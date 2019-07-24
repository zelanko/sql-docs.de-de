---
title: Bereitstellen von Anwendungen mit azdata
titleSuffix: SQL Server big data clusters
description: Stellen Sie ein Python-oder R-Skript als Anwendung auf SQL Server 2019 Big Data Cluster (Vorschauversion) bereit.
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 06b76e7eb8eec8db1993ca558a1f57355457c4ad
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419493"
---
# <a name="how-to-deploy-an-app-on-sql-server-big-data-cluster-preview"></a>Bereitstellen einer APP auf SQL Server Big Data Cluster (Vorschau)

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie R-und python-Skripts als Anwendung in einem SQL Server 2019 Big Data-Cluster (Vorschauversion) bereitstellen und verwalten.

## <a name="whats-new-and-improved"></a>Neuerungen und Verbesserungen

- Ein einzelnes Befehlszeilen-Hilfsprogramm zum Verwalten von Cluster und App.
- Vereinfachte App-Bereitstellung bei gleichzeitiger Bereitstellung einer differenzierten Steuerung durch spec-Dateien.
- Unterstützung für das Hosting zusätzlicher Anwendungs Typen: SSIS und msprung (neu in CTP 2,3)
- [Vs Code Erweiterung](app-deployment-extension.md) zum Verwalten der Anwendungs Bereitstellung

Anwendungen werden mit `azdata` dem Befehlszeilen-Hilfsprogramm bereitgestellt und verwaltet. Dieser Artikel enthält Beispiele für die Bereitstellung von apps über die Befehlszeile. Weitere Informationen zur Verwendung dieses in Visual Studio Code finden Sie unter [vs Code Erweiterung](app-deployment-extension.md).

Die folgenden App-Typen werden unterstützt:
- R-und python-Apps (Funktionen, Modelle und Apps)
- Msprung-Dienst
- SQL Server Integration Services (SSIS)

## <a name="prerequisites"></a>Vorraussetzungen

- [SQL Server 2019 Big Data Cluster](deployment-guidance.md)
- [azdata-Befehlszeilenprogramm](deploy-install-azdata.md)

## <a name="capabilities"></a>Funktionen

In SQL Server 2019 (Vorschau) können Sie die Anwendung erstellen, löschen, beschreiben, initialisieren, auflisten und aktualisieren. In der folgenden Tabelle werden die Befehle für die Anwendungs Bereitstellung beschrieben, die Sie mit **azdata**verwenden können.

|Befehl |Beschreibung |
|:---|:---|
|`azdata login` | Anmelden bei einem SQL Server Big Data-Cluster |
|`azdata app create` | Erstellen Sie eine Anwendung. |
|`azdata app delete` | Löschen Sie die Anwendung. |
|`azdata app describe` | Beschreiben Sie die Anwendung. |
|`azdata app init` | Starten Sie ein neues Anwendungs Skelett. |
|`azdata app list` | Listet die Anwendung (en) auf. |
|`azdata app run` | Anwendung ausführen. |
|`azdata app update`| Aktualisieren Sie die Anwendung. |

Sie können wie im folgenden Beispiel `--help` mit dem-Parameter Hilfe erhalten:

```bash
azdata app create --help
```

In den folgenden Abschnitten werden diese Befehle ausführlicher beschrieben.

## <a name="sign-in"></a>Anmelden

Bevor Sie Anwendungen bereitstellen oder mit ihnen interagieren, melden Sie sich zunächst mit dem `azdata login` Befehl bei Ihrem SQL Server Big Data-Cluster an. Geben Sie die externe IP-Adresse `controller-svc-external` des Dienstanbieter ( `https://ip-address:30080`z. b.) zusammen mit dem Benutzernamen und dem Kennwort für den Cluster an.

```bash
azdata login --controller-endpoint https://<ip-address-of-controller-svc-external>:30080 --controller-username <user-name>
```

## <a name="aks"></a>EINDRINGT

Wenn Sie AKS verwenden, müssen Sie den folgenden Befehl ausführen, um die IP-Adresse des `mgmtproxy-svc-external` Dienstanbieter zu erhalten, indem Sie diesen Befehl in einem bash-oder CMD-Fenster ausführen:


```bash
kubectl get svc mgmtproxy-svc-external -n <name of your big data cluster>
```

## <a name="kubeadm-or-minikube"></a>Kubeadm oder minikube

Wenn Sie kubeadm oder minikube verwenden, führen Sie den folgenden Befehl aus, um die IP-Adresse für die Anmeldung beim Cluster zu erhalten.

```bash
kubectl get node --selector='node-role.kubernetes.io/master'
```

## <a name="create-an-app"></a>Erstellen einer APP

Verwenden `azdata` Sie zum Erstellen einer Anwendung mit dem `app create` Befehl. Diese Dateien befinden sich lokal auf dem Computer, auf dem Sie die APP erstellen.

Verwenden Sie die folgende Syntax, um eine neue app in Big Data Cluster zu erstellen:

```bash
azdata app create --spec <directory containing spec file>
```

Der folgende Befehl zeigt ein Beispiel dafür, wie dieser Befehl aussehen könnte:

```bash
azdata app create --spec ./addpy
```

Dabei wird davon ausgegangen, dass die `addpy` Anwendung im Ordner gespeichert ist. Dieser Ordner sollte auch eine Spezifikations Datei für die Anwendung mit dem `spec.yaml`Namen enthalten. Weitere Informationen zur `spec.yaml` Datei finden Sie auf [der Seite "Anwendungs Bereitstellung](concept-application-deployment.md) ".

Um diese APP-Beispiel-App bereitzustellen, erstellen Sie die folgenden Dateien `addpy`in einem Verzeichnis mit dem Namen:

- `add.py`. Kopieren Sie den folgenden Python-Code in diese Datei:
   ```py
   #add.py
   def add(x,y):
        result = x+y
        return result
    result=add(x,y)
   ```
- `spec.yaml`. installiert haben. Kopieren Sie den folgenden Code in diese Datei:
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

Führen Sie anschließend den folgenden Befehl aus:

```bash
azdata app create --spec ./addpy
```

Mithilfe des List-Befehls können Sie überprüfen, ob die APP bereitgestellt wurde:

```bash
azdata app list
```

Wenn die Bereitstellung nicht fertiggestellt ist, sollte `state` die `WaitingforCreate` Anzeige wie im folgenden Beispiel angezeigt werden:

```json
[
  {
    "name": "add-app",
    "state": "WaitingforCreate",
    "version": "v1"
  }
]
```

Nachdem die Bereitstellung erfolgreich war, sollte die `state` `Ready` Statusänderung angezeigt werden:

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="list-an-app"></a>Auflisten einer APP

Sie können alle apps auflisten, die erfolgreich mit dem `app list` Befehl erstellt wurden.

Der folgende Befehl listet alle verfügbaren Anwendungen in Ihrem Big Data Cluster auf:

```bash
azdata app list
```

Wenn Sie einen Namen und eine Version angeben, werden diese spezifische APP und deren Status (erstellen oder bereit) aufgelistet:

```bash
azdata app list --name <app_name> --version <app_version>
```

Das folgende Beispiel veranschaulicht diesen Befehl:

```bash
azdata app list --name add-app --version v1
```

Es sollte eine Ausgabe angezeigt werden, die dem folgenden Beispiel ähnelt:

```json
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="run-an-app"></a>Ausführen einer APP

Wenn sich die app in einem `Ready` Status befindet, können Sie Sie verwenden, indem Sie Sie mit den angegebenen Eingabe Parametern ausführen. Verwenden Sie die folgende Syntax, um eine APP auszuführen:

```bash
azdata app run --name <app_name> --version <app_version> --inputs <inputs_params>
```

Der folgende Beispiel Befehl veranschaulicht den Run-Befehl:

```bash
azdata app run --name add-app --version v1 --inputs x=1,y=2
```

Wenn die Ausführung erfolgreich war, sollte die Ausgabe wie angegeben angezeigt werden, als Sie die App erstellt haben. Nachfolgend finden Sie ein Beispiel:

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

## <a name="create-an-app-skeleton"></a>Erstellen eines App-Skeleton

Der Befehl init bietet ein Gerüst mit den relevanten Artefakten, die für die Bereitstellung einer APP erforderlich sind. Im folgenden Beispiel wird Hello erstellt, indem der folgende Befehl ausgeführt wird.

```bash
azdata app init --name hello --version v1 --template python
```

Dadurch wird ein Ordner mit dem Namen Hello erstellt.  Sie können `cd` das Verzeichnis in das Verzeichnis überprüfen und die generierten Dateien im Ordner überprüfen. "spec. YAML" definiert die APP, z. b. Name, Version und Quellcode. Sie können die Spezifikation bearbeiten, um den Namen, die Version, die Eingabe und die Ausgaben zu ändern.

Im folgenden finden Sie eine Beispielausgabe des Befehls "init", die im Ordner angezeigt wird.

```
hello.py
README.md
run-spec.yaml
spec.yaml

```

## <a name="describe-an-app"></a>Beschreiben einer APP

Der beschreibe Befehl enthält ausführliche Informationen über die APP, einschließlich des Endpunkts in Ihrem Cluster. Dies wird in der Regel von einem App-Entwickler verwendet, um eine APP mit dem Swagger-Client zu erstellen und den Webdienst zu verwenden, um auf eine restliche Weise mit der APP zu interagieren. Weitere Informationen finden Sie [unter Verwenden von Anwendungen auf Big Data Clustern](big-data-cluster-consume-apps.md) .

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

## <a name="delete-an-app"></a>Löschen einer APP

Verwenden Sie die folgende Syntax, um eine APP aus Ihrem Big Data Cluster zu löschen:

```bash
azdata app delete --name add-app --version v1
```

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie Sie apps, die auf SQL Server Big Data Clustern in ihren eigenen Anwendungen bereitgestellt werden, unter Verwenden von [Anwendungen auf Big Data Clustern](big-data-cluster-consume-apps.md) für weitere Informationen integrieren. Weitere Beispiele finden Sie unter Beispiele für die [App](https://aka.ms/sql-app-deploy)-Bereitstellung.

Weitere Informationen zu SQL Server Big Data Clustern finden Sie unter [Was sind SQL Server 2019 Big Data Cluster?](big-data-cluster-overview.md).
