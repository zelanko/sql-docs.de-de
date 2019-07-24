---
title: azdata BDC-HDFS-Einstellungsreferenz
titleSuffix: SQL Server big data clusters
description: Referenz Artikel zu azdata BDC-HDFS-Einstellungsbefehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7f0b259a3ac4ac0850fa05de3867e928b035307b
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426270"
---
# <a name="azdata-bdc-hdfs-mount"></a>azdata BDC-HDFS-einbinden

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält eine Referenz für die **BDC-HDFS** -Einstellungsbefehle im **azdata** -Tool. Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata BDC HDFS Mount Create](#azdata-bdc-hdfs-mount-create) | Erstellen Sie bereit Stellungen von Remote speichern in HDFS.
[azdata BDC HDFS Mount DELETE](#azdata-bdc-hdfs-mount-delete) | Löschen Sie die Bereitstellung von Remote speichern in HDFS.
[azdata BDC HDFS Mount Status](#azdata-bdc-hdfs-mount-status) | Status der einreistellung (en).
[azdata BDC HDFS-Einstellungsaktualisierung](#azdata-bdc-hdfs-mount-refresh) | Aktualisieren Sie den Inhalt einer Festlegung in HDFS.
## <a name="azdata-bdc-hdfs-mount-create"></a>azdata BDC HDFS Mount Create
Erstellen Sie bereit Stellungen von Remote speichern in HDFS. Die Anmelde Informationen für den Zugriff auf den Remote Speicher sollten ggf. mit der Umgebungsvariablen MOUNT_CREDENTIALS als eine durch Trennzeichen getrennte Liste von Key = Value-Paaren angegeben werden. Alle Kommas in den Schlüsseln oder Werten müssen mit Escapezeichen versehen werden.
```bash
azdata bdc hdfs mount create --remote-uri -r 
                             --mount-path -m
```
### <a name="examples"></a>Beispiele
So stellen Sie Container "Data" in ADLS Gen 2-Konto "adlsv2example" im HDFS-Pfad/Mounts/adlsv2/Data mit dem gemeinsam verwendeten Schlüssel einbinden
```bash
Set the MOUNT_CREDENTIALS environment variable as "fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>".
azdata bdc hdfs mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/
    --mount-path /mounts/adlsv2/data
```
So einbinden Sie einen Remote-HDFS-BDC (HDFS://namenode1:8080/) auf dem lokalen HDFS-Pfad/Mounts/HDFS/
```bash
azdata bdc hdfs mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--remote-uri -r`
Der URI des Remote Speicher, der eingebunden werden soll (Quelle der Bereitstellung).
#### `--mount-path -m`
HDFS-Pfad, in dem die einreilegung erstellt werden muss (Ziel der einreilegung).
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
## <a name="azdata-bdc-hdfs-mount-delete"></a>azdata BDC HDFS Mount DELETE
Löschen Sie die Bereitstellung von Remote speichern in HDFS.
```bash
azdata bdc hdfs mount delete --mount-path -m 
                             
```
### <a name="examples"></a>Beispiele
Löschen Sie die unter/Mounts/adlsv2/Data erstellte für ein ADLS Gen 2-Speicherkonto.
```bash
azdata bdc hdfs mount delete --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--mount-path -m`
der HDFS-Pfad, der der zu löschenden Festlegung entspricht.
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
## <a name="azdata-bdc-hdfs-mount-status"></a>azdata BDC HDFS Mount Status
Status der einreistellung (en).
```bash
azdata bdc hdfs mount status [--mount-path -m] 
                             
```
### <a name="examples"></a>Beispiele
Einstellungsstatus nach Pfad
```bash
azdata bdc hdfs mount status --mount-path /mounts/hdfs
```
Hiermit wird der Status aller bereit Stellungen angezeigt.
```bash
azdata bdc hdfs mount status
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--mount-path -m`
Einstellungspfad.
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
## <a name="azdata-bdc-hdfs-mount-refresh"></a>azdata BDC HDFS-Einstellungsaktualisierung
Aktualisieren Sie den Inhalt einer Festlegung in HDFS.
```bash
azdata bdc hdfs mount refresh --mount-path -m 
                              
```
### <a name="examples"></a>Beispiele
Aktualisieren der auf/Mounts/adlsv2/Data. erstellten Mount
```bash
azdata bdc hdfs mount refresh --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--mount-path -m`
Der HDFS-Pfad, der der zu aktualisierenden Festlegung entspricht.
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

Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md). Weitere Informationen zum Installieren des Tools **azdata** finden [Sie unter Install azdata to Manage SQL Server 2019 Big Data Clusters](deploy-install-azdata.md).
