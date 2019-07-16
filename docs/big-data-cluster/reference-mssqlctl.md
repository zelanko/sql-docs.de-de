---
title: Referenz zu mssqlctl
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl Befehle.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5567b46376acc5aee6c42cdae19eef133c7af506
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957899"
---
# <a name="mssqlctl"></a>mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **Mssqlctl** tool für [SQL Server-2019 big Data-Clustern (Vorschau)](big-data-cluster-overview.md). Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
|[Mssqlctl-app](reference-mssqlctl-app.md) | Erstellen, löschen, ausführen und Verwalten von Anwendungen. |
|[Mssqlctl bdc](reference-mssqlctl-bdc.md) | Wählen Sie, verwalten und betreiben von SQL Server-Cluster für Big Data. |
|[Mssqlctl hdfs](reference-mssqlctl-hdfs.md) | Das HDFS-Modul bietet, dass die Befehle auf einem HDFS-Dateisystem. |
[Mssqlctl-Anmeldung](#mssqlctl-login) | Melden Sie sich die Endpunkte des Clusters Controller.
[Mssqlctl Abmelden](#mssqlctl-logout) | Melden Sie sich der Cluster.
|[Mssqlctl sql](reference-mssqlctl-sql.md) | Die SQL-DB-CLI ermöglicht den Benutzer für die Interaktion mit SQL Server über T-SQL. |
## <a name="mssqlctl-login"></a>Mssqlctl-Anmeldung
Wenn Ihr Cluster bereitgestellt wird, listet es den controllerendpunkt während der Bereitstellung, die Sie verwenden sollten, die Anmeldung.  Wenn Sie den controllerendpunkt nicht kennen, können Sie Anmeldung, dass Ihres Clusters Kube-Konfigurationsdatei auf Ihrem System in den Standardspeicherort der <user home>/.kube/config oder verwenden Sie die KUBECONFIG Env Var, d. h. KUBECONFIG=path/to/.kube/config zu exportieren.
```bash
mssqlctl login [--cluster-name -n] 
               [--controller-username -u]  
               [--controller-endpoint -e]  
               [--accept-eula -a]
```
### <a name="examples"></a>Beispiele
Melden Sie sich interaktiv an. Clustername wird immer werden aufgefordert, wenn nicht als Argument angegeben. Wenn Sie die CONTROLLER_USERNAME CONTROLLER_PASSWORD und ACCEPT_EULA Env-Variablen, die auf Ihrem System festgelegt haben, werden diese nicht für aufgefordert. Wenn Sie die Kube-Konfigurationsdatei auf Ihrem System haben, oder verwenden die KUBECONFIG Env Var besitzt, um den Pfad zu der Konfigurationsdatei angeben, versucht zunächst die interaktive Umgebung verwenden, verwenden Sie die Konfiguration und fordert Sie dann, wenn die Konfiguration ein Fehler auftritt.
```bash
mssqlctl login
```
Melden Sie sich (nicht interaktiv). Melden Sie sich den Clusternamen, Controller-Benutzername, controllerendpunkt und Endbenutzer-Lizenzvertrag akzeptieren, die als Argumente festgelegt. Die Umgebungsvariable muss CONTROLLER_PASSWORD festgelegt werden.  Wenn Sie nicht, an den controllerendpunkt möchten, bitten Sie die Kube-Konfigurationsdatei ein, auf dem Computer am Standardspeicherort des <user home>/.kube/config oder verwenden Sie die KUBECONFIG Env Var, d. h. KUBECONFIG=path/to/.kube/config zu exportieren.
```bash
mssqlctl login --cluster-name ClusterName --controller-user johndoe@contoso.com  --controller-endpoint https://<ip>:30080 --accept-eula yes
```
Melden Sie sich die Kube-Konfigurationsdatei auf Computer, und legen Sie für die CONTROLLER_USERNAME CONTROLLER_PASSWORD und ACCEPT_EULA Env-Var.
```bash
mssqlctl login -n ClusterName
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--cluster-name -n`
Clustername.
#### `--controller-username -u`
Benutzer des Kontos. Wenn Sie nicht, verwenden Sie dieses Argument möchten, können Sie die Umgebungsvariable CONTROLLER_USERNAME festlegen.
#### `--controller-endpoint -e`
Controller clusterendpunkt "https://host:port". Wenn Sie nicht, verwenden Sie dieses Argument möchten, können Sie die Kube-Konfigurationsdatei auf dem Computer verwenden. Vergewissern Sie sich die Konfigurationsdatei wird, befindet sich der Standardspeicherort der <user home>/.kube/config oder verwenden Sie die KUBECONFIG Env "var".
#### `--accept-eula -a`
Stimmen Sie den Lizenzbedingungen zu? [Yes/No]. Wenn Sie nicht, verwenden Sie dieses Argument möchten, können Sie die Umgebungsvariable ACCEPT_EULA auf "Ja" festlegen.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.
## <a name="mssqlctl-logout"></a>Mssqlctl Abmelden
Melden Sie sich der Cluster.
```bash
mssqlctl logout 
```
### <a name="examples"></a>Beispiele
Melden Sie sich diesen Benutzer.
```bash
mssqlctl logout
```
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).