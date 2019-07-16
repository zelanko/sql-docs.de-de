---
title: Mssqlctl BDC-Speicherpool bereitstellen-Referenz
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl BDC-Speicherpool einbindebefehle.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b6a412c6d7cab9fb869a9aa8ee1b62ae0ed3f717
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958004"
---
# <a name="mssqlctl-bdc-storage-pool-mount"></a>Mssqlctl BDC-Speicherpool Bereitstellung

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **BDC-Speicher-Pool einbinden** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Mssqlctl BDC-Speicherpool Bereitstellung erstellen](#mssqlctl-bdc-storage-pool-mount-create) | Erstellen Sie Bereitstellungen von remote-speichern in HDFS.
[Mssqlctl BDC-Speicherpool Bereitstellung löschen](#mssqlctl-bdc-storage-pool-mount-delete) | Löschen Sie Bereitstellungen von remote-speichern in HDFS.
[Mssqlctl BDC-Speicherpool Bereitstellungsstatus](#mssqlctl-bdc-storage-pool-mount-status) | Status des Mount(s).
## <a name="mssqlctl-bdc-storage-pool-mount-create"></a>Mssqlctl BDC-Speicherpool Bereitstellung erstellen
Erstellen Sie Bereitstellungen von remote-speichern in HDFS. Die Anmeldeinformationen für den Zugriff auf die remote-Speicher, sofern vorhanden, sollte angegeben werden, verwenden die Umgebungsvariable MOUNT_CREDENTIALS als durch Trennzeichen getrennte Liste von Schlüssel = Wert-Paaren. Alle Kommas in den Schlüssel oder Werte müssen mit Escapezeichen versehen werden.
```bash
mssqlctl bdc storage-pool mount create --remote-uri 
                                       --mount-path
```
### <a name="examples"></a>Beispiele
Container "Daten" in ADLS Gen 2-Konto "adlsv2example" auf den gemeinsam verwendeten Schlüssel mit HDFS-Pfad-/mounts/adlsv2/data bereitstellen
```bash
Set the MOUNT_CREDENTIALS environment variable as "fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>".
mssqlctl bdc storage-pool mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/
    --mount-path /mounts/adlsv2/data
```
Bereitstellen eines remote HDFS BDCS (Hdfs://namenode1:8080 /) auf lokales HDFS Pfad /mounts/Hdfs /
```bash
mssqlctl bdc storage-pool mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--remote-uri`
Der URI der Remotespeicher, die bereitgestellte (Quelle Mount) verwendet werden soll.
#### `--mount-path`
HDFS-Pfad, in denen bereitstellen (Ziel der Bereitstellung) erstellt werden muss.
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
## <a name="mssqlctl-bdc-storage-pool-mount-delete"></a>Mssqlctl BDC-Speicherpool Bereitstellung löschen
Löschen Sie Bereitstellungen von remote-speichern in HDFS.
```bash
mssqlctl bdc storage-pool mount delete --mount-path 
                                       
```
### <a name="examples"></a>Beispiele
Löschen Sie bereitstellen, die auf /mounts/adlsv2/data für ein ADLS-Gen-2-Speicherkonto erstellt.
```bash
mssqlctl bdc storage-pool mount delete --mount-path /mounts/adlsv2/data
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
## <a name="mssqlctl-bdc-storage-pool-mount-status"></a>Mssqlctl BDC-Speicherpool Bereitstellungsstatus
Status des Mount(s).
```bash
mssqlctl bdc storage-pool mount status [--mount-path] 
                                       
```
### <a name="examples"></a>Beispiele
Bereitstellungsstatus anhand des Pfads abrufen
```bash
mssqlctl bdc storage-pool mount status --mount-path /mounts/hdfs
```
Status alle Bereitstellungen zu erhalten.
```bash
mssqlctl bdc storage-pool mount status
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