---
title: azdata-Referenz
titleSuffix: SQL Server big data clusters
description: Referenz Artikel zu azdata-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a8136c85f8c32e08423f3d199a021d4f60353b39
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68425990"
---
# <a name="azdata"></a>azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält eine Referenz für das **azdata** -Tool für [SQL Server 2019 Big Data Cluster (Vorschau)](big-data-cluster-overview.md). Weitere Informationen zum Installieren des Tools **azdata** finden [Sie unter Install azdata to Manage SQL Server 2019 Big Data Clusters](deploy-install-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
|[azdata-App](reference-azdata-app.md) | Erstellen, löschen, ausführen und Verwalten von Anwendungen. |
|[azdata-BDC](reference-azdata-bdc.md) | Wählen Sie SQL Server Big Data-Cluster aus, und führen Sie Sie aus. |
|[azdata-Notebook](reference-azdata-notebook.md) | Befehle zum Anzeigen, ausführen und Verwalten von Notebooks von einem Terminal. |
[azdata-Anmeldung](#azdata-login) | Melden Sie sich beim Controller Endpunkt des Clusters an.
[azdata-Abmeldung](#azdata-logout) | Melden Sie sich beim Cluster ab.
|[azdata-SQL](reference-azdata-sql.md) | Die SQL-Datenbank-CLI ermöglicht dem Benutzer die Interaktion mit SQL Server über T-SQL. |
## <a name="azdata-login"></a>azdata-Anmeldung
Wenn Ihr Cluster bereitgestellt wird, wird der Controller Endpunkt während der Bereitstellung aufgelistet, den Sie für die Anmeldung verwenden sollten.  Wenn Sie den Controller Endpunkt nicht kennen, können Sie sich anmelden, indem Sie die Kube-Konfiguration Ihres Clusters auf Ihrem System am Standard Speicherort von <user home>/.Kube/config "haben, oder Sie verwenden den kubeconfig env-var, d. h. Export kubeconfig = path/to/. Kube/config.
```bash
azdata login [--cluster-name -n] 
             [--controller-username -u]  
             [--controller-endpoint -e]  
             [--accept-eula -a]
```
### <a name="examples"></a>Beispiele
Melden Sie sich interaktiv an. Der Cluster Name wird immer angefordert, wenn er nicht als Argument angegeben ist. Wenn Sie die CONTROLLER_USERNAME-, CONTROLLER_PASSWORD-und ACCEPT_EULA ENV-Variablen auf Ihrem System festgelegt haben, werden diese nicht zur Eingabe von aufgefordert. Wenn Sie über die Kube-Konfiguration auf Ihrem System verfügen oder den Pfad zur Konfiguration mithilfe von kubeconfig-ERV-var angeben, wird zunächst versucht, die Konfiguration zu verwenden, und Sie werden aufgefordert, wenn die Konfiguration fehlschlägt.
```bash
azdata login
```
Melden Sie sich an (nicht interaktiv). Melden Sie sich mit Cluster Name, Controller Benutzername, Controller Endpunkt und EULA-Akzeptanz Satz als Argumente an. Die Umgebungsvariable CONTROLLER_PASSWORD muss festgelegt werden.  Wenn Sie den Controller Endpunkt nicht angeben möchten, verwenden Sie die Kube-Konfiguration auf Ihrem Computer am Standard Speicherort von <user home>/.Kube/config ", oder verwenden Sie kubeconfig env var, d. h. Export kubeconfig = path/to/. Kube/config.
```bash
azdata login --cluster-name ClusterName --controller-user johndoe@contoso.com  --controller-endpoint https://<ip>:30080 --accept-eula yes
```
Melden Sie sich mit der Kube-Konfiguration auf dem Computer an, und env var ist für CONTROLLER_USERNAME, CONTROLLER_PASSWORD und ACCEPT_EULA festgelegt.
```bash
azdata login -n ClusterName
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--cluster-name -n`
Der Cluster Name.
#### `--controller-username -u`
Kontobenutzer. Wenn Sie dieses arg nicht verwenden möchten, können Sie die Umgebungsvariable CONTROLLER_USERNAME festlegen.
#### `--controller-endpoint -e`
Cluster Controller-Endpunkt https://host:port "". Wenn Sie dieses arg nicht verwenden möchten, können Sie die Kube-Konfiguration auf Ihrem Computer verwenden. Stellen Sie sicher, dass sich die Konfiguration am Standard Speicherort von <user home>/.Kube/config "befindet, oder verwenden Sie kubeconfig-ERV var.
#### `--accept-eula -a`
Akzeptieren Sie die Lizenzbedingungen? [Ja/Nein]. Wenn Sie dieses arg nicht verwenden möchten, können Sie die Umgebungsvariable ACCEPT_EULA auf "yes" festlegen. Die Lizenzbedingungen für dieses Produkt können unter https://aka.ms/azdata-eula angezeigt werden.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-logout"></a>azdata-Abmeldung
Melden Sie sich beim Cluster ab.
```bash
azdata logout 
```
### <a name="examples"></a>Beispiele
Melden Sie sich für diesen Benutzer an.
```bash
azdata logout
```
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Installieren des Tools **azdata** finden [Sie unter Install azdata to Manage SQL Server 2019 Big Data Clusters](deploy-install-azdata.md).
