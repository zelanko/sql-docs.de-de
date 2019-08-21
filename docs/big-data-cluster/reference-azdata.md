---
title: Referenz zu azdata
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 33cc3070647c58e6ae57c8bff3d587a76ae0a28d
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653100"
---
# <a name="azdata"></a>azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält einen Verweis auf das **azdata** -Tool für [ [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (Vorschau)](big-data-cluster-overview.md). Weitere Informationen zum Installieren des Tools **azdata** finden Sie unter Installieren von [azdata [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]zur Verwaltung ](deploy-install-azdata.md)von.

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
|[azdata app](reference-azdata-app.md) | Erstellen, Löschen, Ausführen und Verwalten von Anwendungen. |
|[azdata bdc](reference-azdata-bdc.md) | Auswählen, Verwalten und Betreiben von SQL Server-Big Data-Clustern. |
|[azdata login](#azdata-login) | Anmelden beim Controllerendpunkt des Clusters.
|[azdata logout](#azdata-logout) | Abmelden beim Cluster.

## <a name="azdata-login"></a>azdata login
Wenn Ihr Cluster bereitgestellt wird, wird der Controller Endpunkt während der Bereitstellung aufgelistet, den Sie für die Anmeldung verwenden sollten.  Wenn Sie den Controller Endpunkt nicht kennen, können Sie sich anmelden, indem Sie die Kube-Konfiguration Ihres Clusters auf Ihrem System am Standard Speicherort <user home>von/.Kube/config "verwenden, oder Sie verwenden den kubeconfig-env-var, d. h. Export kubeconfig = path/to/. Kube/config.
```bash
azdata login [--cluster-name -n] 
             [--controller-username -u]  
             [--controller-endpoint -e]  
             [--accept-eula -a]
```
### <a name="examples"></a>Beispiele
Melden Sie sich interaktiv an. Der Clustername wird immer angefordert, wenn er nicht als Argument angegeben ist. Wenn Sie die Umgebungsvariablen CONTROLLER_USERNAME, CONTROLLER_PASSWORD und ACCEPT_EULA auf Ihrem System festgelegt haben, wird nicht deren Eingabe angefordert. Wenn sich die Kube-Konfiguration auf Ihrem System befindet, oder Sie mit der KUBECONFIG-Umgebungsvariablen den Pfad zur Konfiguration angeben, versucht die interaktive Benutzeroberfläche zunächst, die Konfiguration zu verwenden, und fordert Sie dann zur Eingabe auf, wenn bei der Konfiguration ein Fehler auftritt.
```bash
azdata login
```
Melden Sie sich an (nicht interaktiv). Melden Sie sich mit Clustername, Controllerbenutzername, Controllerendpunkt und EULA-Akzeptanzsatz als Argumente an. Die Umgebungsvariable CONTROLLER_PASSWORD muss festgelegt werden.  Wenn Sie den Controller Endpunkt nicht angeben möchten, stellen Sie die Kube-Konfiguration auf Ihrem Computer am Standard Speicherort von <user home>/.Kube/config "her, oder verwenden Sie kubeconfig env var, d. h. Export kubeconfig = path/to/. Kube/config.
```bash
azdata login --cluster-name ClusterName --controller-user johndoe@contoso.com  --controller-endpoint https://<ip>:30080 --accept-eula yes
```
Melden Sie sich mit der Kube-Konfiguration auf dem Computer an, und legen Sie die Umgebungsvariablen CONTROLLER_USERNAME, CONTROLLER_PASSWORD und ACCEPT_EULA fest.
```bash
azdata login -n ClusterName
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--cluster-name -n`
Clustername.
#### `--controller-username -u`
Kontobenutzer. Wenn Sie dieses Argument nicht verwenden möchten, können Sie die Umgebungsvariable CONTROLLER_USERNAME festlegen.
#### `--controller-endpoint -e`
Clustercontroller-Endpunkt „https://host:port“. Wenn Sie dieses Argument nicht verwenden möchten, können Sie die Kube-Konfiguration auf Ihrem Computer verwenden. Stellen Sie sicher, dass sich die Konfiguration am Standard <user home>Speicherort von/.Kube/config "befindet, oder verwenden Sie kubeconfig-ERV var.
#### `--accept-eula -a`
Stimmen Sie den Lizenzbedingungen zu? [yes/no]. Wenn Sie dieses Argument nicht verwenden möchten, können Sie die Umgebungsvariable ACCEPT_EULA auf „yes“ festlegen. 
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden [http://jmespath.org/](http://jmespath.org/]) Sie unter.
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.
## <a name="azdata-logout"></a>azdata logout
Abmelden beim Cluster.
```bash
azdata logout 
```
### <a name="examples"></a>Beispiele
Abmelden dieses Benutzers.
```bash
azdata logout
```
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden [http://jmespath.org/](http://jmespath.org/]) Sie unter.
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Installieren des Tools **azdata** finden Sie unter Installieren von [azdata [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]zur Verwaltung ](deploy-install-azdata.md)von.
