---
title: Mssqlctl Cluster Speicher-Pool einbinden Verweis
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl Clusterbefehle Speicher-Pool einbinden.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: eb527779cd844064bcabccc91f5356676e06f004
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779306"
---
# <a name="mssqlctl-cluster-storage-pool-mount"></a>Bereitstellen des mssqlctl-Clusterspeicherpools

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **Cluster Speicher-Pool einbinden** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Erstellen Sie Mssqlctl Cluster Speicher-Pool einbinden](#mssqlctl-cluster-storage-pool-mount-create) | Erstellen Sie Bereitstellungen von remote-speichern in HDFS.
[Mssqlctl Cluster Speicherpool Bereitstellung löschen](#mssqlctl-cluster-storage-pool-mount-delete) | Löschen Sie Bereitstellungen von remote-speichern in HDFS.
[Speicher-Pool einbinden des Mssqlctl Clusterstatus](#mssqlctl-cluster-storage-pool-mount-status) | Status des Mount(s).
## <a name="mssqlctl-cluster-storage-pool-mount-create"></a>Erstellen Sie Mssqlctl Cluster Speicher-Pool einbinden
Erstellen Sie Bereitstellungen von remote-speichern in HDFS.
```bash
mssqlctl cluster storage-pool mount create --remote-uri 
                                           --mount-path  
                                           [--credential-file]
```
### <a name="examples"></a>Beispiele
Container "Daten" in ADLS Gen 2-Konto "adlsv2example" auf den gemeinsam verwendeten Schlüssel mit HDFS-Pfad-/mounts/adlsv2/data bereitstellen
```bash
mssqlctl cluster storage-pool mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/
    --mount-path /mounts/adlsv2/data --credentials credential_file
```
Zum Bereitstellen von eines Remotecluster mit HDFS (Hdfs://namenode1:8080 /) auf lokales HDFS Pfad /mounts/Hdfs /
```bash
mssqlctl cluster storage-pool mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--remote-uri`
Der URI der Remotespeicher, die bereitgestellte (Quelle Mount) verwendet werden soll.
#### `--mount-path`
HDFS-Pfad, in denen bereitstellen (Ziel der Bereitstellung) erstellt werden muss.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--credential-file`
Datei mit den Anmeldeinformationen für den Zugriff auf die remote-Speicher. Die Anmeldeinformationen als Schlüssel angegeben werden, müssen = Wert-Paaren mit einem Schlüssel = Wert pro Zeile. Alle entspricht, in dem Schlüssel oder Werte müssen mit Escapezeichen versehen werden. Standardmäßig sind keine Anmeldeinformationen erforderlich. Die erforderlichen Schlüssel hängt davon ab, den Typ des remote-Speicher bereitgestellt wird und den Typ der Autorisierung verwendet.
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
## <a name="mssqlctl-cluster-storage-pool-mount-delete"></a>Mssqlctl Cluster Speicherpool Bereitstellung löschen
Löschen Sie Bereitstellungen von remote-speichern in HDFS.
```bash
mssqlctl cluster storage-pool mount delete --mount-path 
                                           
```
### <a name="examples"></a>Beispiele
Löschen Sie bereitstellen, die auf /mounts/adlsv2/data für ein ADLS-Gen-2-Speicherkonto erstellt.
```bash
mssqlctl cluster storage-pool mount delete --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--mount-path`
Der HDFS-Pfad für die Bereitstellung, die gelöscht werden.
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
## <a name="mssqlctl-cluster-storage-pool-mount-status"></a>Speicher-Pool einbinden des Mssqlctl Clusterstatus
Status des Mount(s).
```bash
mssqlctl cluster storage-pool mount status [--mount-path] 
                                           
```
### <a name="examples"></a>Beispiele
Bereitstellungsstatus anhand des Pfads abrufen
```bash
mssqlctl cluster storage-pool mount status --mount-path /mounts/hdfs
```
Status alle Bereitstellungen zu erhalten.
```bash
mssqlctl cluster storage-pool mount status
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--mount-path`
Der Bereitstellungspfad.
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

Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md). Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).