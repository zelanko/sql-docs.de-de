---
title: 'azdata bdc hdfs mount: Referenz'
titleSuffix: SQL Server big data clusters
description: Verwenden Sie diesen Referenzartikel, um die SQL-Befehle (insbesondere die „bdc hdfs mount“-Befehle) im azdata-Tool zu verstehen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bf0742083b458fb0d8280199a0afaeb44a05958a
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733763"
---
# <a name="azdata-bdc-hdfs-mount"></a>azdata bdc hdfs mount

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

Der folgende Artikel enthält Referenzinformationen zu den `sql`-Befehlen im `azdata`-Tool. Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md).

## <a name="commands"></a>Befehle
| Get-Help | BESCHREIBUNG |
| --- | --- |
[azdata bdc hdfs mount create](#azdata-bdc-hdfs-mount-create) | Erstellen von Einbindungen (Mounts) von Remotespeichern in HDFS.
[azdata bdc hdfs mount delete](#azdata-bdc-hdfs-mount-delete) | Löschen von Einbindungen von Remotespeicher in HDFS.
[azdata bdc hdfs mount status](#azdata-bdc-hdfs-mount-status) | Der Status von Einbindungen (Mounts).
[azdata bdc hdfs mount refresh](#azdata-bdc-hdfs-mount-refresh) | Aktualisieren des Inhalts einer Einbindung in HDFS.
## <a name="azdata-bdc-hdfs-mount-create"></a>azdata bdc hdfs mount create
Erstellen von Einbindungen (Mounts) von Remotespeichern in HDFS. Sofern Anmeldeinformationen für ein Zugreifen auf den Remotespeicher erforderlich sind, müssen diese mit der Umgebungsvariablen MOUNT_CREDENTIALS als eine Liste angegeben werden, die aus Schlüssel=Wert-Paaren mit Kommas als Trennzeichen besteht. Vor jedes Komma in den Schlüsseln oder Werten muss ein Escapezeichen gesetzt werden.
```bash
azdata bdc hdfs mount create --remote-uri -r 
                             --mount-path -m
```
### <a name="examples"></a>Beispiele
So binden Sie den Container „data“ im ADLS Gen 2-Konto „adlsv2example“ in den HDFS-Pfad „/mounts/adlsv2/data“ mit dem gemeinsam verwendeten Schlüssel ein
```bash
Set the MOUNT_CREDENTIALS environment variable as "fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>".
azdata bdc hdfs mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/
    --mount-path /mounts/adlsv2/data
```
So binden Sie einen Remote-HDFS-BDC (hdfs://namenode1:8080/) in den lokalen HDFS-Pfad „/mounts/hdfs/“ ein
```bash
azdata bdc hdfs mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--remote-uri -r`
Der URI des Remotespeichers, der eingebunden werden soll (Quelle der Einbindung).
#### `--mount-path -m`
Der HDFS-Pfad, in dem die Einbindung erstellt werden muss (Ziel der Einbindung).
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.
## <a name="azdata-bdc-hdfs-mount-delete"></a>azdata bdc hdfs mount delete
Löschen von Einbindungen von Remotespeicher in HDFS.
```bash
azdata bdc hdfs mount delete --mount-path -m 
                             
```
### <a name="examples"></a>Beispiele
Löschen Sie die Einbindung (Mount), die unter „/mounts/adlsv2/data“ für ein ADLS Gen 2-Speicherkonto erstellt wurde.
```bash
azdata bdc hdfs mount delete --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--mount-path -m`
Der HDFS-Pfad, der der Einbindung entspricht, die gelöscht werden soll.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.
## <a name="azdata-bdc-hdfs-mount-status"></a>azdata bdc hdfs mount status
Der Status von Einbindungen (Mounts).
```bash
azdata bdc hdfs mount status [--mount-path -m] 
                             
```
### <a name="examples"></a>Beispiele
Rufen Sie den Einbindungsstatus nach Pfad ab.
```bash
azdata bdc hdfs mount status --mount-path /mounts/hdfs
```
Rufen Sie den Status aller Einbindungen ab.
```bash
azdata bdc hdfs mount status
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--mount-path -m`
Einbindungspfad (Mount-Pfad).
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.
## <a name="azdata-bdc-hdfs-mount-refresh"></a>azdata bdc hdfs mount refresh
Aktualisieren des Inhalts einer Einbindung in HDFS.
```bash
azdata bdc hdfs mount refresh --mount-path -m 
                              
```
### <a name="examples"></a>Beispiele
Aktualisieren Sie die Einbindung, die unter „/mounts/adlsv2/data“ erstellt wurde.
```bash
azdata bdc hdfs mount refresh --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--mount-path -m`
Der HDFS-Pfad, der der Einbindung entspricht, die aktualisiert werden soll.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md). Weitere Informationen zur Installation des `azdata`-Tools finden Sie unter [Installieren von azdata zum Verwalten von Big Data-Clustern für SQL Server 2019](../install/deploy-install-azdata.md).
