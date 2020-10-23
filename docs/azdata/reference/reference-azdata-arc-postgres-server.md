---
title: Referenz zu „azdata arc postgres server“
titleSuffix: SQL Server big data clusters
description: Dies ist der Referenzartikel zu azdata arc postgres server-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 0a28ba44dfbeb2b0ef1b5191e6e3bfba5352d540
ms.sourcegitcommit: 29a2be59c56f8a4b630af47760ef38d2bf56a3eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92358728"
---
# <a name="azdata-arc-postgres-server"></a>azdata arc postgres server

Gilt für [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]e

Der folgende Artikel enthält Referenzinformationen zu den **sql**-Befehlen im **azdata**-Tool. Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md).

## <a name="commands"></a>Befehle

|Get-Help|Beschreibung|
| --- | --- |
[azdata arc postgres server create](#azdata-arc-postgres-server-create) | Hiermit wird eine PostgreSQL-Servergruppe erstellt.
[azdata arc postgres server edit](#azdata-arc-postgres-server-edit) | Hiermit bearbeiten Sie die Konfiguration einer PostgreSQL-Servergruppe.
[azdata arc postgres server delete](#azdata-arc-postgres-server-delete) | Hiermit löschen Sie eine PostgreSQL-Servergruppe.
[azdata arc postgres server show](#azdata-arc-postgres-server-show) | Hiermit zeigen Sie Details zu einer PostgreSQL-Servergruppe an.
[azdata arc postgres server list](#azdata-arc-postgres-server-list) | Hiermit listen Sie die PostgreSQL-Servergruppen auf.
[azdata arc postgres server config](reference-azdata-arc-postgres-server-config.md) | Konfigurationsbefehle
[azdata arc postgres server backup](reference-azdata-arc-postgres-server-backup.md) | Hiermit verwalten Sie PostgreSQL-Servergruppensicherungen.
## <a name="azdata-arc-postgres-server-create"></a>azdata arc postgres server create
Legen Sie die Umgebungsvariable „AZDATA_PASSWORD“ fest, um das Kennwort für die Servergruppe festzulegen.
```bash
azdata arc postgres server create --name -n 
                                  [--path]  
                                  
[--cores-limit -cl]  
                                  
[--cores-request -cr]  
                                  
[--memory-limit -ml]  
                                  
[--memory-request -mr]  
                                  
[--storage-class-data -scd]  
                                  
[--storage-class-logs -scl]  
                                  
[--storage-class-backups -scb]  
                                  
[--extensions]  
                                  
[--volume-size-data -vsd]  
                                  
[--volume-size-logs -vsl]  
                                  
[--volume-size-backups -vsb]  
                                  
[--workers -w]  
                                  
[--engine-version -ev]  
                                  
[--no-external-endpoint]  
                                  
[--dev]  
                                  
[--port]  
                                  
[--no-wait]  
                                  
[--engine-settings -e]
```
### <a name="examples"></a>Beispiele
Hiermit wird eine PostgreSQL-Servergruppe erstellt.
```bash
azdata arc postgres server create -n pg1
```
Hiermit erstellen Sie eine PostgreSQL-Servergruppe mit Engine-Einstellungen. Beide unten aufgeführten Beispiele sind gültig.
```bash
azdata arc postgres server create -n pg1 --engine-settings "key1=val1"
azdata arc postgres server create -n pg1 --engine-settings "key2=val2"
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Der Name der Instanz.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--path`
Dies ist der Pfad zur JSON-Quelldatei für die PostgreSQL-Servergruppe. Diese ist optional.
#### `--cores-limit -cl`
Dies ist die maximale Anzahl an CPU-Kernen für Postgres-Instanzen, die pro Knoten verwendet werden können. Teilkerne werden unterstützt.
#### `--cores-request -cr`
Dies ist die Mindestanzahl von CPU-Kernen, die pro Knoten verfügbar sein müssen, um den Dienst zu planen. Teilkerne werden unterstützt.
#### `--memory-limit -ml`
Dies ist die Arbeitsspeicherbegrenzung der Postgres-Instanz als Zahl, gefolgt von Ki (Kilobyte), Mi (Megabyte) oder Gi (Gigabyte).
#### `--memory-request -mr`
Dies ist die Arbeitsspeicheranforderung der Postgres-Instanz als Zahl, gefolgt von Ki (Kilobyte), Mi (Megabyte) oder Gi (Gigabyte).
#### `--storage-class-data -scd`
Dies ist die für persistente Datenvolumes zu verwendende Speicherklasse.
#### `--storage-class-logs -scl`
Dies ist die für persistente Protokollvolumes zu verwendende Speicherklasse.
#### `--storage-class-backups -scb`
Dies ist die für persistente Sicherungsvolumes zu verwendende Speicherklasse.
#### `--extensions`
Dies ist eine durch Trennzeichen getrennte Liste der Postgres-Erweiterungen, die beim Start geladen werden sollen. Unterstützte Werte finden Sie in der Postgres-Dokumentation.
#### `--volume-size-data -vsd`
Dies ist die Größe des Speichervolumes, das für Daten verwendet werden soll, als positive Zahl, gefolgt von Ki (Kilobyte), Mi (Megabyte) oder Gi (Gigabyte).
#### `--volume-size-logs -vsl`
Dies ist die Größe des Speichervolumes, das für Datenprotokolle verwendet werden soll, als positive Zahl, gefolgt von Ki (Kilobyte), Mi (Megabyte) oder Gi (Gigabyte).
#### `--volume-size-backups -vsb`
Dies ist die Größe des Speichervolumes, das für Sicherungen verwendet werden soll, als positive Zahl, gefolgt von Ki (Kilobyte), Mi (Megabyte) oder Gi (Gigabyte).
#### `--workers -w`
Dies ist die Anzahl der bereitzustellenden Workerknoten in einem Shardcluster, oder 0 (Standardwert) für Postgres mit einem Knoten.
#### `--engine-version -ev`
Dieser Wert muss 11 oder 12 sein. Der Standardwert ist 12.
#### `--no-external-endpoint`
Falls ein Wert angegeben ist, wird kein externer Dienst erstellt. Andernfalls wird ein externer Dienst mit demselben Diensttyp wie dem des Datencontrollers erstellt.
#### `--dev`
Wenn dieser Wert angegeben wird, gilt die Instanz als Entwicklungsinstanz, und es fallen keine Kosten dafür an.
#### `--port`
Dies ist optional.
#### `--no-wait`
Wenn dieser Wert vorhanden ist, wartet der Befehl nicht darauf, dass die Instanz bereit ist, bis eine Rückgabe erfolgt.
#### `--engine-settings -e`
Dies ist eine durch Kommas getrennte Liste der Postgres-Engine-Einstellungen im Format „key1=val1, key2=val2“.
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
## <a name="azdata-arc-postgres-server-edit"></a>azdata arc postgres server edit
Hiermit bearbeiten Sie die Konfiguration einer PostgreSQL-Servergruppe.
```bash
azdata arc postgres server edit --name -n 
                                [--path]  
                                
[--workers -w]  
                                
[--engine-version -ev]  
                                
[--cores-limit -cl]  
                                
[--cores-request -cr]  
                                
[--memory-limit -ml]  
                                
[--memory-request -mr]  
                                
[--extensions]  
                                
[--dev]  
                                
[--port]  
                                
[--no-wait]  
                                
[--engine-settings -e]  
                                
[--replace-engine-settings -re]  
                                
[--admin-password]
```
### <a name="examples"></a>Beispiele
Hiermit bearbeiten Sie die Konfiguration einer PostgreSQL-Servergruppe.
```bash
azdata arc postgres server edit --src ./spec.json -n pg1
```
Hiermit bearbeiten Sie eine PostgreSQL-Servergruppe mit Engine-Einstellungen.
```bash
azdata arc postgres server edit -n pg1 --engine-settings "key2=val2"
```
Hiermit wird eine PostgreSQL-Servergruppe bearbeitet, und vorhandene Engine-Einstellungen werden durch die neue Einstellung „key1=val1“ ersetzt.
```bash
azdata arc postgres server edit -n pg1 --engine-settings "key1=val1" --replace-engine-settings
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Dies ist der Name der bearbeiteten PostgreSQL-Servergruppe. Der Name, unter dem Ihre Instanz bereitgestellt wird, kann nicht geändert werden.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--path`
Dies ist der Pfad zur JSON-Quelldatei für die PostgreSQL-Servergruppe. Diese ist optional.
#### `--workers -w`
Dies ist die Anzahl der bereitzustellenden Workerknoten in einem Shardcluster, oder 0 (Standardwert) für Postgres mit einem Knoten.
#### `--engine-version -ev`
Die Engine-Version kann nicht geändert werden. --engine-version kann zusammen mit --name verwendet werden, um eine PostgreSQL Hyperscale-Servergruppe zu identifizieren, wenn zwei Servergruppen mit unterschiedlicher Engine-Version denselben Namen haben. Der Parameter --engine-version ist optional und muss den Wert 11 oder 12 aufweisen, wenn er zum Identifizieren einer Servergruppe verwendet wird.
#### `--cores-limit -cl`
Dies ist die maximale Anzahl an CPU-Kernen für Postgres-Instanzen, die pro Knoten verwendet werden können. Teilkerne werden unterstützt. Geben Sie den entsprechenden Wert als leere Zeichenfolge an, um cores_limit zu entfernen.
#### `--cores-request -cr`
Dies ist die Mindestanzahl von CPU-Kernen, die pro Knoten verfügbar sein müssen, um den Dienst zu planen. Teilkerne werden unterstützt. Geben Sie den entsprechenden Wert als leere Zeichenfolge an, um cores_request zu entfernen.
#### `--memory-limit -ml`
Dies ist die Arbeitsspeicherbegrenzung für die Postgres-Instanz als Zahl, gefolgt von Ki (Kilobyte), Mi (Megabyte) oder Gi (Gigabyte). Geben Sie den entsprechenden Wert als leere Zeichenfolge an, um memory_limit zu entfernen.
#### `--memory-request -mr`
Dies ist die Arbeitsspeicheranforderung für die Postgres-Instanz als Zahl, gefolgt von Ki (Kilobyte), Mi (Megabyte) oder Gi (Gigabyte). Geben Sie den entsprechenden Wert als leere Zeichenfolge an, um memory_request zu entfernen.
#### `--extensions`
Dies ist eine durch Trennzeichen getrennte Liste der Postgres-Erweiterungen, die beim Start geladen werden sollen. Unterstützte Werte finden Sie in der Postgres-Dokumentation.
#### `--dev`
Wenn dieser Wert angegeben wird, gilt die Instanz als Entwicklungsinstanz, und es fallen keine Kosten dafür an.
#### `--port`
Dies ist optional.
#### `--no-wait`
Wenn dieser Wert vorhanden ist, wartet der Befehl nicht darauf, dass die Instanz bereit ist, bis eine Rückgabe erfolgt.
#### `--engine-settings -e`
Dies ist eine durch Kommas getrennte Liste der Postgres-Engine-Einstellungen im Format „key1=val1, key2=val2“. Die angegebenen Einstellungen werden mit den vorhandenen Einstellungen zusammengeführt. Geben Sie einen leeren Wert wie „removedKey=“ an, um eine Einstellung zu entfernen. Wenn Sie eine Engine-Einstellung ändern, die einen Neustart erfordert, wird der Dienst neu gestartet, um die Einstellung sofort anzuwenden.
#### `--replace-engine-settings -re`
Bei einer Angabe mit --engine-settings werden alle vorhandenen benutzerdefinierten Engine-Einstellungen durch neue Einstellungen und Werte ersetzt.
#### `--admin-password`
Bei angegebenem Wert wird das Administratorkennwort des Postgres-Servers auf den Wert der AZDATA_PASSWORD-Umgebungsvariablen (falls vorhanden) bzw. einen angeforderten Wert festgelegt.
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
## <a name="azdata-arc-postgres-server-delete"></a>azdata arc postgres server delete
Hiermit löschen Sie eine PostgreSQL-Servergruppe.
```bash
azdata arc postgres server delete --name -n 
                                  [--engine-version -ev]
```
### <a name="examples"></a>Beispiele
Hiermit löschen Sie eine PostgreSQL-Servergruppe.
```bash
azdata arc postgres server delete -n pg1
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Dies ist der Name der PostgreSQL-Servergruppe.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--engine-version -ev`
--engine-version kann zusammen mit --name verwendet werden, um eine PostgreSQL Hyperscale-Servergruppe zu identifizieren, wenn zwei Servergruppen mit unterschiedlicher Engine-Version denselben Namen haben. Der Parameter --engine-version ist optional und muss den Wert 11 oder 12 aufweisen, wenn er zum Identifizieren einer Servergruppe verwendet wird.
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
## <a name="azdata-arc-postgres-server-show"></a>azdata arc postgres server show
Hiermit zeigen Sie Details zu einer PostgreSQL-Servergruppe an.
```bash
azdata arc postgres server show --name -n 
                                [--engine-version -ev]  
                                
[--path -p]
```
### <a name="examples"></a>Beispiele
Hiermit zeigen Sie Details zu einer PostgreSQL-Servergruppe an.
```bash
azdata arc postgres server show -n pg1
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Dies ist der Name der PostgreSQL-Servergruppe.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--engine-version -ev`
--engine-version kann zusammen mit --name verwendet werden, um eine PostgreSQL Hyperscale-Servergruppe zu identifizieren, wenn zwei Servergruppen mit unterschiedlicher Engine-Version denselben Namen haben. Der Parameter --engine-version ist optional und muss den Wert 11 oder 12 aufweisen, wenn er zum Identifizieren einer Servergruppe verwendet wird.
#### `--path -p`
Dies ist ein Pfad, unter dem die vollständige Spezifikation für die PostgreSQL-Servergruppe geschrieben werden sollen. Wenn keine Angabe erfolgt, wird die Spezifikation in die Standardausgabe geschrieben.
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
## <a name="azdata-arc-postgres-server-list"></a>azdata arc postgres server list
Hiermit listen Sie die PostgreSQL-Servergruppen auf.
```bash
azdata arc postgres server list 
```
### <a name="examples"></a>Beispiele
Hiermit listen Sie die PostgreSQL-Servergruppen auf.
```bash
azdata arc postgres server list
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

