---
title: 'azdata sql: Referenz'
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata sql-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 794c7be56eaa0591d120b4fea40a725fdeecaac1
ms.sourcegitcommit: 29a2be59c56f8a4b630af47760ef38d2bf56a3eb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92358108"
---
# <a name="azdata-sql"></a>azdata sql

Gilt für [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]e

Der folgende Artikel enthält Referenzinformationen zu den **sql**-Befehlen im **azdata**-Tool. Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md).

## <a name="commands"></a>Befehle

|Get-Help|BESCHREIBUNG|
| --- | --- |
[azdata sql shell](#azdata-sql-shell) | Die SQL-CLI ermöglicht dem Benutzer, über T-SQL mit SQL Server und Azure SQL zu interagieren.
[azdata sql query](#azdata-sql-query) | Die SQL-CLI ermöglicht dem Benutzer, über T-SQL mit SQL Server und Azure SQL zu interagieren.
## <a name="azdata-sql-shell"></a>azdata sql shell
Die SQL-CLI ermöglicht dem Benutzer, über T-SQL mit SQL Server und Azure SQL zu interagieren.
```bash
azdata sql shell [--username -u] 
                 [--database -d]  
                 
[--server -s]  
                 
[--integrated -e]  
                 
[--mssqlclirc]  
                 
[--row-limit]  
                 
[--less-chatty]  
                 
[--auto-vertical-output]  
                 
[--encrypt -n]  
                 
[--trust-server-certificate -c]  
                 
[--connect-timeout -l]  
                 
[--application-intent -k]  
                 
[--multi-subnet-failover -m]  
                 
[--packet-size]  
                 
[--dac-connection -a]  
                 
[--input-file -i]  
                 
[--output-file]  
                 
[--enable-sqltoolsservice-logging]  
                 
[--prompt]
```
### <a name="examples"></a>Beispiele
Beispielbefehlszeile, um die interaktive Umgebung zu starten.
```bash
azdata sql shell
```
Beispielbefehlszeile mit bereitgestelltem Server, Benutzer und bereitgestellter Datenbank
```bash
azdata sql shell --server localhost --username sa --database master         
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--username -u`
Benutzername zum Herstellen einer Verbindung mit der Datenbank.
#### `--database -d`
Name der Datenbank, mit der eine Verbindung hergestellt werden soll.
#### `--server -s`
Name oder Adresse der SQL Server-Instanz.
#### `--integrated -e`
Integrierte Authentifizierung in Windows verwenden.
#### `--mssqlclirc`
Speicherort der mssqlclirc-Konfigurationsdatei.
#### `--row-limit`
Hiermit wird ein Schwellenwert für die Aufforderung für ein Zeilenlimit festgelegt. 0 verwenden, um die Aufforderung zu deaktivieren.
#### `--less-chatty`
Intro beim Start und Beenden überspringen.
#### `--auto-vertical-output`
Hiermit wird automatisch zum vertikalen Ausgabemodus gewechselt, wenn das Ergebnis breiter als die Breite des Terminals ist.
#### `--encrypt -n`
SQL Server verwendet SSL-Verschlüsselung für alle Daten, wenn auf dem Server ein Zertifikat installiert ist.
#### `--trust-server-certificate -c`
Der Kanal wird verschlüsselt, während das Durchlaufen der Zertifikatskette zum Überprüfen der Vertrauensstellung umgangen wird.
#### `--connect-timeout -l`
Wartezeit (in Sekunden) für eine Verbindung mit dem Server, bevor die Anforderung beendet wird.
#### `--application-intent -k`
Deklariert den Arbeitsauslastungstyp der Anwendung beim Herstellen einer Verbindung mit einer Datenbank in einer SQL Server-Verfügbarkeitsgruppe.
#### `--multi-subnet-failover -m`
Wenn die Anwendung in unterschiedlichen Subnetzen eine Verbindung mit der AlwaysOn-Verfügbarkeitsgruppe herstellt, ermöglicht diese Einstellung eine schnellere Erkennung des derzeit aktiven Servers und Verbindung mit ihm.
#### `--packet-size`
Größe der zur Kommunikation mit SQL Server verwendeten Netzwerkpakete in Bytes.
#### `--dac-connection -a`
Herstellen der Verbindung mit SQL Server über eine dedizierte Administratorverbindung.
#### `--input-file -i`
Gibt die Datei an, die einen Batch mit SQL-Anweisungen für die Verarbeitung enthält.
#### `--output-file`
Gibt die Datei an, die die Ausgabe von einer Abfrage empfängt.
#### `--enable-sqltoolsservice-logging`
Aktiviert die Diagnoseprotokollierung für SqlToolsService.
#### `--prompt`
Eingabeaufforderungsformat (Standardwert: \d>
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
## <a name="azdata-sql-query"></a>azdata sql query
Die SQL-CLI ermöglicht dem Benutzer, über T-SQL mit SQL Server und Azure SQL zu interagieren.
```bash
azdata sql query -q 
                 [--database -d]  
                 
[--username -u]  
                 
[--server -s]  
                 
[--integrated -e]
```
### <a name="examples"></a>Beispiele
Beispielbefehlszeile zum Auswählen der Liste der Tabellennamen.
```bash
azdata sql query --server localhost --username sa --database master -q "SELECT name FROM SYS.TABLES"
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `-q`
Die T-SQL-Abfrage, die ausgeführt werden soll.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--database -d`
Name der Datenbank, mit der eine Verbindung hergestellt werden soll.
`master`
#### `--username -u`
Benutzername zum Herstellen einer Verbindung mit der Datenbank.
#### `--server -s`
Name oder Adresse der SQL Server-Instanz.
#### `--integrated -e`
Integrierte Authentifizierung in Windows verwenden.
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

