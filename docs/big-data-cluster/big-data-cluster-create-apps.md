---
title: 'Gewusst wie: Bereitstellen einer app auf SQL Server-big Data-Cluster | Microsoft-Dokumentation'
description: Eine Python- oder R-Skript als eine Anwendung auf SQL Server-2019 big Data-Cluster (Vorschau) bereitstellen.
author: TheBharath
ms.author: bharaths
manager: craigg
ms.date: 11/07/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: dd24b4379f50a5b974e7a0a90412d1e13bf6db22
ms.sourcegitcommit: 87fec38a515a7c524b7c99f99bc6f4d338e09846
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/08/2018
ms.locfileid: "51272558"
---
# <a name="how-to-deploy-an-app-on-sql-server-2019-big-data-cluster-preview"></a>Gewusst wie: Bereitstellen einer app auf SQL Server-2019 big Data-Cluster (Vorschau)

Dieser Artikel beschreibt das Bereitstellen und Verwalten von R und Python-Skript als eine Anwendung in einer SQL Server-2019 big Data-Cluster (Vorschau).

R und Python-Anwendungen bereitgestellt und verwaltet mit der **Mssqlctl-Pre-** Befehlszeilen-Hilfsprogramms die in CTP 2.1 enthalten ist. Dieser Artikel enthält Beispiele für die Bereitstellung dieser R und Python-Skripts wie apps, die von der Befehlszeile aus.

## <a name="prerequisites"></a>Erforderliche Komponenten

Sie benötigen einen SQL Server-2019 big Data-Cluster konfiguriert. Weitere Informationen finden Sie unter [Gewusst wie: Bereitstellen von SQL Server, big Data-in Kubernetes Cluster](deployment-guidance.md). 

## <a name="installation"></a>Installation

Die **Mssqlctl-Pre-** Befehlszeilen-Hilfsprogramm wird bereitgestellt, um die Funktion zur Python- und R-Bereitstellung (Vorschau). Verwenden Sie den folgenden Befehl aus, um das Hilfsprogramm zu installieren:

```cmd
pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.1 mssqlctlpre
```

## <a name="capabilities"></a>Funktionen

Löschen Sie in CTP 2.1 an, die Sie erstellen können, auflisten, und führen Sie eine R- oder Python-Anwendung. Die folgende Tabelle beschreibt die Befehle der Anwendung-Bereitstellung, mit denen Sie mit **Mssqlctl-Pre-**.

| Befehl | Description |
|---|---|
| `mssqlctl-pre login` | Melden Sie sich bei einer SQL Server-big Data-cluster |
| `mssqlctl-pre app create` | Erstellen einer app |
| `mssqlctl-pre app list` | Liste von bereitgestellten apps |
| `mssqlctl-pre app delete` | Löschen einer app |
| `mssqlctl-pre app run` | Auflisten der ausgeführten apps |

Erhalten Sie Hilfe bei der `--help` Parameter wie im folgenden Beispiel gezeigt:

```bash
mssqlctl-pre app create --help
```

In den folgenden Abschnitten werden diese Befehle im Detail beschrieben.

## <a name="log-in"></a>Anmelden

Vor dem Konfigurieren von R und Python-Anwendungen, zuerst melden Sie sich bei Ihrer big Data-cluster mit SQL-Server die `mssqlctl-pre login` Befehl. Geben Sie die IP-Adresse (extern) die `service-proxy-lb` (z. B.: `https://ip-address:30777`) zusammen mit den Benutzernamen und das Kennwort für den Cluster.

Sie können die IP-Adresse des Dienst-Proxy-lb-Diensts abrufen, mit dem folgenden Befehl in einem nachfolgenden bash- oder Cmd-Fenster:
```bash 
kubectl get svc service-proxy-lb -n <name of your cluster>
```

```bash
mssqlctl-pre login -e https://<ip-address-of-service-proxy-lb> -u <user-name> -p <password>
```

## <a name="create-an-app"></a>Erstellen einer app

Um eine Anwendung zu erstellen, übergeben Sie die Python- oder R-Codedateien an **Mssqlctl-Pre-** mit der `app create` Befehl. Diese Dateien befinden sich lokal auf dem Computer, dem Sie erstellen die app aus.

Verwenden Sie die folgende Syntax, um eine neue app in Ihre big Data-Cluster zu erstellen:

```bash
mssqlctl-pre app create -n <app_name> -v <version_number> -r <runtime> -i <path_to_code_init> -c <path_to_code> --inputs <input_params> --outputs <output_params> 
```

Der folgende Befehl zeigt ein Beispiel für diesen Befehl könnte folgendermaßen aussehen:

```py
#add.py
def add(x,y):
        result = x+y
        return result;
result=add(x,y)
```
Um dies zu testen, speichern Sie die oben genannten Codezeilen in Ihr lokales Verzeichnis als `add.py` , und führen Sie den folgenden Befehl aus

```bash
mssqlctl-pre app create --name add-app --version v1 --runtime Python --code ./add.py  --inputs x=int,y=int --outputs result=int 
```

Sie können überprüfen, ob die app bereitgestellt wurde, mithilfe des List-Befehls:

```bash
mssqlctl-pre app list
```

Wenn die Bereitstellung nicht abgeschlossen ist. sehen Sie die "State" "Erstellen" angezeigt: 

```
[
  {
    "name": "add-app",
    "state": "Creating",
    "version": "v1"
  }
]
```

Nachdem die Bereitstellung erfolgreich durchgeführt wurde. Daraufhin sollte die "State" in "Ready" Status ändern:

```
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
mssqlctl-pre app list
```

Wenn Sie einen Namen und eine Version angeben, werden diese app und den Zustand ("erstellen" oder "Ready") aufgelistet:

```bash
mssqlctl-pre app list --name <app_name> --version <app_version>
```

Das folgende Beispiel zeigt die mit diesem Befehl:

```bash
mssqlctl-pre app list --name add-app --version v1
```

Daraufhin sollte eine Ausgabe ähnlich dem folgenden Beispiel:

```
[
  {
    "name": "add-app",
    "state": "Ready",
    "version": "v1"
  }
]
```

## <a name="run-an-app"></a>Ausführen einer app

Wenn die app im Zustand "Bereit" befindet, können Sie es durch eine Ausführung mit der angegebenen Eingabeparameter verwenden. Verwenden Sie die folgende Syntax, um eine app auszuführen:

```bash
mssqlctl-pre app run --name <app_name> --version <app_version> --inputs <inputs_params>
```

Der Befehl im folgenden Beispiel wird veranschaulicht, mit dem Befehl "run":

```bash
mssqlctl-pre app run --name add-app --version v1 --inputs x=1,y=2
```

Wenn die Ausführung erfolgreich war, sehen Sie die Ausgabe angegeben wird, wenn Sie die app erstellt. Im Folgenden finden Sie ein Beispiel.

```
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

## <a name="delete-an-app"></a>Löschen einer app

Um eine app aus Ihrer big Data-Cluster zu löschen, verwenden Sie die folgende Syntax:

```bash
mssqlctl-pre app delete --name add-app --version v1
```

## <a name="next-steps"></a>Nächste Schritte

Sie können auch zusätzliche Beispiele Auschecken [ https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster). 

Weitere Informationen zu SQL Server-big Data-Clustern, finden Sie unter [was SQL Server-2019 big Data-Cluster sind?](big-data-cluster-overview.md).
