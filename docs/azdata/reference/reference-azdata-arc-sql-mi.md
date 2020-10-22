---
title: Referenz zu azdata arc sql mi
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata arc sql mi-Befehlen
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 234a990cde52a6fd051410d30000413b9acfa3a0
ms.sourcegitcommit: 29a2be59c56f8a4b630af47760ef38d2bf56a3eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92358678"
---
# <a name="azdata-arc-sql-mi"></a>azdata arc sql mi

Gilt für [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]e

Der folgende Artikel enthält Referenzinformationen zu den **sql**-Befehlen im **azdata**-Tool. Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md).

## <a name="commands"></a>Befehle

|Get-Help|Beschreibung|
| --- | --- |
[azdata arc sql mi create](#azdata-arc-sql-mi-create) | Hiermit wird eine verwaltete SQL-Instanz erstellt.
[azdata arc sql mi edit](#azdata-arc-sql-mi-edit) | Hiermit wird die Konfiguration einer verwalteten SQL-Instanz bearbeitet.
[azdata arc sql mi delete](#azdata-arc-sql-mi-delete) | Hiermit wird eine verwaltete SQL-Instanz gelöscht.
[azdata arc sql mi show](#azdata-arc-sql-mi-show) | Hiermit werden die Details einer verwalteten SQL-Instanz angezeigt.
[azdata arc sql mi list](#azdata-arc-sql-mi-list) | Hiermit werden verwaltete SQL-Instanzen aufgelistet.
[azdata arc sql mi config](reference-azdata-arc-sql-mi-config.md) | Konfigurationsbefehle
## <a name="azdata-arc-sql-mi-create"></a>azdata arc sql mi create
Legen Sie die Umgebungsvariable AZDATA_PASSWORD fest, wenn Sie ein Kennwort für die verwaltete SQL-Instanz festlegen möchten.
```bash
azdata arc sql mi create --name -n 
                         [--path]  
                         
[--cores-limit -cl]  
                         
[--cores-request -cr]  
                         
[--memory-limit -ml]  
                         
[--memory-request -mr]  
                         
[--storage-class-data -scd]  
                         
[--storage-class-logs -scl]  
                         
[--storage-class-data-logs -scdl]  
                         
[--storage-class-backups -scb]  
                         
[--volume-size-data -vsd]  
                         
[--volume-size-logs -vsl]  
                         
[--volume-size-data-logs -vsdl]  
                         
[--volume-size-backups -vsb]  
                         
[--no-external-endpoint]  
                         
[--dev]  
                         
[--no-wait]
```
### <a name="examples"></a>Beispiele
Hiermit wird eine verwaltete SQL-Instanz erstellt.
```bash
azdata arc sql mi create -n sqlmi1
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Der Name der verwalteten SQL-Instanz.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--path`
Der Pfad zur src-Datei für die JSON-Datei der verwalteten SQL-Instanz.
#### `--cores-limit -cl`
Das Limit für Kerne der verwalteten Instanz als Integer.
#### `--cores-request -cr`
Die Anforderung für Kerne der verwalteten Instanz als Integer.
#### `--memory-limit -ml`
Das Limit für die Kapazität der verwalteten Instanz als Integer.
#### `--memory-request -mr`
Die Anforderung der Kapazität der verwalteten Instanz als ganzzahliger Betrag des Arbeitsspeichers in GB.
#### `--storage-class-data -scd`
Die für Daten zu verwendende Speicherklasse (.mdf). Wenn kein Wert angegeben wird, wird keine Speicherklasse angegeben, was dazu führt, dass Kubernetes die Standardspeicherklasse nutzt.
#### `--storage-class-logs -scl`
Die für Protokolle zu verwendende Speicherklasse (/var/log). Wenn kein Wert angegeben wird, wird keine Speicherklasse angegeben, was dazu führt, dass Kubernetes die Standardspeicherklasse nutzt.
#### `--storage-class-data-logs -scdl`
Die für Datenbankprotokolle zu verwendende Speicherklasse (.ldf). Wenn kein Wert angegeben wird, wird keine Speicherklasse angegeben, was dazu führt, dass Kubernetes die Standardspeicherklasse nutzt.
#### `--storage-class-backups -scb`
Die für Sicherungen zu verwendende Speicherklasse (/var/opt/mssql/backups). Wenn kein Wert angegeben wird, wird keine Speicherklasse angegeben, was dazu führt, dass Kubernetes die Standardspeicherklasse nutzt.
#### `--volume-size-data -vsd`
Dies ist die Größe des Speichervolumes, das für Daten verwendet werden soll, als positive Zahl, gefolgt von Ki (Kilobyte), Mi (Megabyte) oder Gi (Gigabyte).
#### `--volume-size-logs -vsl`
Dies ist die Größe des Speichervolumes, das für Datenprotokolle verwendet werden soll, als positive Zahl, gefolgt von Ki (Kilobyte), Mi (Megabyte) oder Gi (Gigabyte).
#### `--volume-size-data-logs -vsdl`
Dies ist die Größe des Speichervolumes, das für Datenprotokolle verwendet werden soll, als positive Zahl, gefolgt von Ki (Kilobyte), Mi (Megabyte) oder Gi (Gigabyte).
#### `--volume-size-backups -vsb`
Dies ist die Größe des Speichervolumes, das für Sicherungen verwendet werden soll, als positive Zahl, gefolgt von Ki (Kilobyte), Mi (Megabyte) oder Gi (Gigabyte).
#### `--no-external-endpoint`
Falls ein Wert angegeben ist, wird kein externer Dienst erstellt. Andernfalls wird ein externer Dienst mit demselben Diensttyp wie dem des Datencontrollers erstellt.
#### `--dev`
Wenn dieser Wert angegeben wird, gilt die Instanz als Entwicklungsinstanz, und es fallen keine Kosten dafür an.
#### `--no-wait`
Wenn dieser Wert vorhanden ist, wartet der Befehl nicht darauf, dass die Instanz bereit ist, bis eine Rückgabe erfolgt.
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
## <a name="azdata-arc-sql-mi-edit"></a>azdata arc sql mi edit
Hiermit wird die Konfiguration einer verwalteten SQL-Instanz bearbeitet.
```bash
azdata arc sql mi edit --name -n 
                       [--path]  
                       
[--cores-limit -cl]  
                       
[--cores-request -cr]  
                       
[--memory-limit -ml]  
                       
[--memory-request -mr]  
                       
[--dev]  
                       
[--no-wait]
```
### <a name="examples"></a>Beispiele
Hiermit wird die Konfiguration einer verwalteten SQL-Instanz bearbeitet.
```bash
azdata arc sql mi edit --path ./spec.json -n sqlmi1
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Der Name der verwalteten SQL-Instanz, die bearbeitet wird. Der Name, unter dem Ihre Instanz bereitgestellt wird, kann nicht geändert werden.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--path`
Der Pfad zur src-Datei für die JSON-Datei der verwalteten SQL-Instanz.
#### `--cores-limit -cl`
Das Limit für Kerne der verwalteten Instanz als Integer.
#### `--cores-request -cr`
Die Anforderung für Kerne der verwalteten Instanz als Integer.
#### `--memory-limit -ml`
Das Limit für die Kapazität der verwalteten Instanz als Integer.
#### `--memory-request -mr`
Die Anforderung der Kapazität der verwalteten Instanz als ganzzahliger Betrag des Arbeitsspeichers in GB.
#### `--dev`
Wenn dieser Wert angegeben wird, gilt die Instanz als Entwicklungsinstanz, und es fallen keine Kosten dafür an.
#### `--no-wait`
Wenn dieser Wert vorhanden ist, wartet der Befehl nicht darauf, dass die Instanz bereit ist, bis eine Rückgabe erfolgt.
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
## <a name="azdata-arc-sql-mi-delete"></a>azdata arc sql mi delete
Hiermit wird eine verwaltete SQL-Instanz gelöscht.
```bash
azdata arc sql mi delete --name -n 
                         
```
### <a name="examples"></a>Beispiele
Hiermit wird eine verwaltete SQL-Instanz gelöscht.
```bash
azdata arc sql mi delete -n sqlmi1
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Der Name der verwalteten SQL-Instanz, die gelöscht werden soll.
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
## <a name="azdata-arc-sql-mi-show"></a>azdata arc sql mi show
Hiermit werden die Details einer verwalteten SQL-Instanz angezeigt.
```bash
azdata arc sql mi show --name -n 
                       [--path -p]
```
### <a name="examples"></a>Beispiele
Hiermit werden die Details einer verwalteten SQL-Instanz angezeigt.
```bash
azdata arc sql mi show -n sqlmi1
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Der Name der verwalteten SQL-Instanz, die angezeigt werden soll.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--path -p`
Ein Pfad, unter den die vollständige Spezifikation der verwalteten SQL-Instanz geschrieben werden soll. Wenn keine Angabe erfolgt, wird die Spezifikation in die Standardausgabe geschrieben.
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
## <a name="azdata-arc-sql-mi-list"></a>azdata arc sql mi list
Hiermit werden verwaltete SQL-Instanzen aufgelistet.
```bash
azdata arc sql mi list 
```
### <a name="examples"></a>Beispiele
Hiermit werden verwaltete SQL-Instanzen aufgelistet.
```bash
azdata arc sql mi list
```
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

Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md). 

Weitere Informationen zur Installation des Tools **azdata** finden Sie unter [Installieren von azdata](..\install\deploy-install-azdata.md).

