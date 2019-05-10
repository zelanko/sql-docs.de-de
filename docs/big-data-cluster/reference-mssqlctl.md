---
title: Referenz zu mssqlctl
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl Befehle.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ebd3b63d641c77dae1afbff21264ec4fe34df4d0
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64775502"
---
# <a name="mssqlctl"></a>mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **Mssqlctl** tool für [SQL Server-2019 big Data-Clustern (Vorschau)](big-data-cluster-overview.md). Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
|[Mssqlctl-app](reference-mssqlctl-app.md) | Erstellen, löschen, ausführen und Verwalten von Anwendungen. |
|[Mssqlctl-cluster](reference-mssqlctl-cluster.md) | Wählen Sie, verwalten Sie und betreiben Sie Cluster. |
[mssqlctl login](#mssqlctl-login) | Melden Sie sich an den Cluster.
[mssqlctl logout](#mssqlctl-logout) | Melden Sie sich der Cluster.
|[Mssqlctl-Speicher](reference-mssqlctl-storage.md) | Verwalten von Clusterspeicher. |
## <a name="mssqlctl-login"></a>Mssqlctl-Anmeldung
Melden Sie sich an den Cluster.
```bash
mssqlctl login [--username -u] 
               [--password -p]  
               [--endpoint -e]
```
### <a name="examples"></a>Beispiele
Melden Sie sich interaktiv an.
```bash
mssqlctl login
```
Melden Sie sich mit Benutzername und Kennwort.
```bash
mssqlctl login -u johndoe@contoso.com -p VerySecret
```
Melden Sie sich den Benutzernamen, Kennwort und clusterendpunkt.
```bash
mssqlctl login -u johndoe@contoso.com -p VerySecret --endpoint https://host.com:12800
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--username -u`
Benutzer des Kontos.
#### `--password -p`
Kennwortanmeldeinformationen.
#### `--endpoint -e`
Cluster-Host und Port (z. b) "http://host:port".
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