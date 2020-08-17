---
description: Ausführen der SSMA-Konsole (SybaseToSQL)
title: Ausführen der SSMA-Konsole (sybasedesql) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/27/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sybase Console,Database Connection Commands
- Sybase Console,Manageability Commands
- Sybase Console,Migration Commands
- Sybase Console,Migration Preparation Command
- Sybase Console,Project Commands
- Sybase Console,Report Commands
- Sybase Console,Script File Commands
- Sybase Console,Script Generation Commands
ms.assetid: ea8950b7-fabc-4aa4-89f8-9573a2617d70
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: fee973fdcb79105d5fe7c412c10bdda2cd1bbec5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88372236"
---
# <a name="executing-the-ssma-console-sybasetosql"></a>Ausführen der SSMA-Konsole (SybaseToSQL)
Microsoft bietet Ihnen einen robusten Satz von Skriptdatei Befehlen zum Ausführen und Steuern von SSMA-Aktivitäten. Die nachfolgenden Abschnitte beschreiben die gleichen.  
  
## <a name="script-file-commands"></a>Skriptdatei Befehle  
Die Konsolenanwendung verwendet bestimmte Standard Befehle für Skriptdateien, wie in diesem Abschnitt aufgelistet.  
  
## <a name="project-commands"></a>Projekt Befehle  
Die Projekt Befehle behandeln das Erstellen von Projekten, das Öffnen, speichern und Beenden von Projekten.  
  
### <a name="create-new-project"></a>create-new-project  
Mit diesem Befehl wird ein neues SSMA-Projekt erstellt.  
  
-   `project-folder` Gibt den Ordner des Projekts an, das erstellt wird.  
  
-   `project-name` Gibt den Namen des Projekts an. {string}  
  
-   `overwrite-if-exists`Optionales Attribut gibt an, ob ein vorhandenes Projekt überschrieben werden soll. booleschen  
  
-   `project-type:`Optionales Attribut. Gibt den Projekttyp an, d. h. das Projekt "SQL Server-2005" oder das Projekt "SQL-Server-2008" oder das Projekt "SQL Server-2012" oder das Projekt "SQL-Server-2014" oder das Projekt "SQL-Azure". Der Standardwert ist "SQL Server-2008".  
  
**Syntaxbeispiel:**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>" (optional)  
  
   project-type="<sql-server-2008/sql-server-2005/sql-server-2012/sql-server-2014/sql-azure>"  
/>  
```  
Das Attribut ' überschreiben-if-vorhanden ' ist standardmäßig **false** .  
  
Das Attribut ' Project-Type ' ist standardmäßig **SQL-Server-2008** .  
  
### <a name="open-project"></a>Open-Project  
Dieser Befehl öffnet das Projekt.

-   `project-folder` Gibt den Ordner des Projekts an, das erstellt wird. Der Befehl schlägt fehl, wenn der angegebene Ordner nicht vorhanden ist.  {string}  
  
-   `project-name` Gibt den Namen des Projekts an. Der Befehl schlägt fehl, wenn das angegebene Projekt nicht vorhanden ist.  {string}  
  
**Syntaxbeispiel:**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
> [!NOTE]  
> Die SSMA für SAP ASE-Konsolenanwendung unterstützt die Abwärtskompatibilität. Sie können Sie verwenden, um Projekte zu öffnen, die mit einer früheren Version von SSMA erstellt wurden.  
  
### <a name="save-project"></a>save-project  
Mit diesem Befehl wird das Migrationsprojekt gespeichert.  
  
**Syntaxbeispiel:**  
  
```xml  
<save-project/>  
```  
  
### <a name="close-project"></a>Close-Projekt  
Mit diesem Befehl wird das Migrationsprojekt geschlossen.  
  
**Syntaxbeispiel:**  
  
```xml  
<close-project   
  if-modified="<save/error/ignore>"   (optional)  
/>  
```  
Das Attribut ' If-modified ' ist optional, wird standardmäßig **ignoriert** .  
  
## <a name="database-connection-commands"></a>Daten bankverbindungs Befehle  
Mithilfe der Daten bankverbindungs Befehle können Sie eine Verbindung mit der Datenbank herstellen.  
  
> [!NOTE]  
> - Die Funktion zum **Durchsuchen** der Benutzeroberfläche wird in der-Konsole nicht unterstützt.  
> - Weitere Informationen zum Erstellen von Skriptdateien finden Sie unter [Erstellen von Skriptdateien &#40;sybasetoisql&#41;](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
### <a name="connect-source-database"></a>Connect-Source-Datenbank  
Mit diesem Befehl wird eine Verbindung mit der Quelldatenbank hergestellt, und es werden allgemeine Metadaten der Quelldatenbank geladen, aber nicht alle Metadaten.
  
Wenn die Verbindung mit der Quelle nicht hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung.
  
Die Server Definition wird aus dem Name-Attribut abgerufen, das für jede Verbindung im Server-Abschnitt der Server Verbindungs Datei oder der Skriptdatei definiert ist.  
  
**Syntaxbeispiel:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="force-load-sourcetarget-database"></a>Force-Load-Source/Ziel-Database  
Dieser Befehl lädt die Quell Metadaten und eignet sich für das Offline arbeiten an einem Migrationsprojekt.  
  
Wenn die Verbindung mit der Quelle bzw. dem Ziel nicht hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung.  
  
Dieser Befehl erfordert einen oder mehrere Metabasisknoten als Befehlszeilenparameter.  
  
**Syntaxbeispiel:**  
  
```xml  
<force-load metabase="<source/target>" >  
  
  <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
  
### <a name="reconnect-source-database"></a>reconnect-Quelldatenbank  
Dieser Befehl stellt erneut eine Verbindung mit der Quelldatenbank her, lädt jedoch keine Metadaten im Gegensatz zum Connect-Source-Database-Befehl.  
  
Wenn (erneut) keine Verbindung mit der Quelle hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung.  
  
**Syntaxbeispiel:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="connect-target-database"></a>Connect-Target-Database  
Mit diesem Befehl wird eine Verbindung mit dem Ziel SQL Server Datenbank hergestellt, und es werden allgemeine Metadaten der Zieldatenbank geladen, aber nicht die Metadaten vollständig.  
  
Wenn die Verbindung mit dem Ziel nicht hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung.  
  
Die Server Definition wird aus dem Name-Attribut abgerufen, das für jede Verbindung im Server-Abschnitt der Server Verbindungs Datei oder der Skriptdatei definiert ist.  
  
**Syntaxbeispiel:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
  
### <a name="reconnect-target-database"></a>reconnect-Target-Database  
  
Dieser Befehl stellt erneut eine Verbindung mit der Zieldatenbank her, lädt jedoch keine Metadaten, anders als der Connect-Target-Database-Befehl.  
  
Wenn (erneut) die Verbindung mit dem Ziel nicht hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung.  
  
**Syntaxbeispiel:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-commands"></a>Berichtsbefehle  
Die Berichts Befehle generieren Berichte zur Leistung verschiedener SSMA-Konsolen Aktivitäten.  
  
### <a name="generate-assessment-report"></a>generieren-Assessment-Bericht  
  
Dieser Befehl generiert Bewertungsberichte für die Quelldatenbank.  
  
Wenn die Verbindung der Quelldatenbank vor dem Ausführen dieses Befehls nicht erfolgt, wird ein Fehler generiert, und die Konsolenanwendung wird beendet.  
  
Wenn während der Befehlsausführung keine Verbindung mit dem Quelldaten Bankserver hergestellt werden kann, führt dies auch dazu, dass die Konsolenanwendung beendet wird.  
  
-   `conversion-report-folder:` Gibt den Ordner an, in dem der Bewertungsbericht gespeichert werden kann. (optionales Attribut)  
  
-   `object-name:` Gibt die Objekte an, die für die Bewertungsbericht Generierung berücksichtigt werden (unterstützt einzelne Objektnamen oder einen Gruppen Objektnamen).  
  
-   `object-type:` Gibt den Typ des Objekts an, das im Object-Name-Attribut aufgerufen wird (wenn die Objekt Kategorie angegeben wird, ist der Objekttyp "Category").  
  
-   `conversion-report-overwrite:` Gibt an, ob der Bewertungsberichts Ordner überschrieben werden soll, wenn er bereits vorhanden ist.  
  
    **Standardwert:** false. (optionales Attribut)  
  
-   `write-summary-report-to:` Gibt den Pfad an, in dem der Bericht generiert wird.  
  
    Wenn nur der Ordner Pfad erwähnt wird, dann file **by Name &lt; &gt; XML** wird erstellt. (optionales Attribut)  
  
    Die Berichtserstellung hat zwei weitere Unterkategorien:  
  
    -   `report-errors` (= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
    -   `verbose` (= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
**Syntaxbeispiel:**  
  
```xml  
<generate-assessment-report  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  write-summary-report-to="<file-name/folder-name>"             (optional)  
  
  verbose="<true/false>"                       (optional)  
  
  report-errors="<true/false>"                 (optional)  
  
  assessment-report-folder="<folder-name>"          (optional)  
  
  conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
oder  
  
```xml  
<generate-assessment-report  
  
  assessment-report-folder="<folder-name>"            (optional)  
  
  conversion-report-overwrite="<true/false>"     (optional)  
  
>  
<metabase-object object-name="<object-name>"  
  
        object-type="<object-category>"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration-commands"></a>Migrations Befehle  
Die Migrations Befehle Konvertieren das Ziel Datenbankschema in das Quell Schema und Migrieren Daten auf den Zielserver.  
  
### <a name="convert-schema"></a>Convert-Schema  
Dieser Befehl führt eine Schema Konvertierung von der Quelle in das Ziel Schema durch.  
  
Wenn die Verbindung mit der Quell-oder Zieldatenbank vor dem Ausführen dieses Befehls nicht erfolgt oder wenn die Verbindung mit dem Quell-oder Ziel Datenbankserver während der Ausführung des Befehls fehlschlägt, wird ein Fehler generiert, und die Konsolenanwendung wird beendet.  
  
-   `conversion-report-folder:` Gibt den Ordner an, in dem der Bewertungsbericht gespeichert werden kann. (optionales Attribut)  
  
-   `object-name:` Gibt die für das Schema des Schemas berücksichtigten Quell Objekte an (unterstützt einzelne Objektnamen oder einen Gruppen Objektnamen).  
  
-   `object-type:` Gibt den Typ des Objekts an, das im Object-Name-Attribut aufgerufen wird (wenn die Objekt Kategorie angegeben wird, ist der Objekttyp "Category").  
  
-   `conversion-report-overwrite:` Gibt an, ob der Bewertungsberichts Ordner überschrieben werden soll, wenn er bereits vorhanden ist.  
  
    **Standardwert:** false. (optionales Attribut)  
  
-   `write-summary-report-to:` Gibt den Pfad an, unter dem der Zusammenfassungs Bericht generiert wird.  
  
    Wenn nur der Ordner Pfad erwähnt wird, dann file by Name **schemaconversionreport &lt; n &gt; . XML** wird erstellt. (optionales Attribut)  
  
    Die Berichtserstellung hat zwei weitere Unterkategorien:  
  
    -   `report-errors` (= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
    -   `verbose` (= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
**Syntaxbeispiel:**  
  
```xml  
<convert-schema  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  write-summary-report-to="<file-name/folder-name>"     (optional)  
  
  verbose="<true/false>"                          (optional)  
  
  report-errors="<true/false>"                    (optional)  
  
  conversion-report-folder="<folder-name>"             (optional)  
  
  conversion-report-overwrite="<true/false>"      (optional)  
  
/>  
```  
oder  
  
```xml  
<convert-schema  
  
  conversion-report-folder="<folder-name>"         (optional)  
  
  conversion-report-overwrite="<true/false>"> (optional)  
  
  <metabase-object object-name="<object-name>"  
  
    object-type="<object-category>"/>  
  
</convert-schema>  
```  
  
### <a name="migrate-data"></a>Migrieren von Daten  
Mit diesem Befehl werden die Quelldaten zum Ziel migriert.  
  
-   `object-name:` Gibt die zum Migrieren von Daten berücksichtigten Quell Objekte an (unterstützt einzelne Objektnamen oder einen Gruppen Objektnamen).  
  
-   `object-type:` Gibt den Typ des Objekts an, das im Object-Name-Attribut aufgerufen wird (wenn die Objekt Kategorie angegeben wird, ist der Objekttyp "Category").  
  
-   `write-summary-report-to:` Gibt den Pfad an, in dem der Bericht generiert wird.  
  
    Wenn nur der Ordner Pfad erwähnt wird, dann file by Name **datamigrationreport &lt; n &gt; . XML** wird erstellt. (optionales Attribut)  
  
    Die Berichtserstellung hat zwei weitere Unterkategorien:  
  
    -   `report-errors` (= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
    -   `verbose` (= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
**Syntaxbeispiel:**  
  
```xml  
<migrate-data  
  
  write-summary-report-to="<file-name/folder-name>"  
  
  report-errors="<true/false>" verbose="<true/false>">  
  
    <metabase-object object-name="<object-name>"/>  
  
    <metabase-object object-name="<object-name>"/>  
  
    <metabase-object object-name="<object-name>"/>  
  
    <data-migration-connection  
  
      source-use-last-used="true"/source-server="<server-unique-name>"  
  
      target-use-last-used="true"/target-server="<server-unique-name>"/>  
  
</migrate-data>  
```  
oder  
  
```xml  
<migrate-data  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  write-summary-report-to="<file-name/folder-name>"  
  
  report-errors="<true/false>" verbose="<true/false>"/>  
```  
  
## <a name="migration-preparation-command"></a>Befehl zum Vorbereiten der Migration  
Der Befehl Migrations Vorbereitung initiiert die Schema Zuordnung zwischen den Quell-und Ziel Datenbanken.  
  
> [!NOTE]  
> Die standardmäßige Konsolenausgabe Einstellung für die Migrations Befehle ist der Ausgabebericht "vollständig", ohne dass eine ausführliche Fehlerberichterstattung vorliegt: nur eine Zusammenfassung des Stamm Knotens der Quell Objektstruktur.  
  
### <a name="map-schema"></a>Map-Schema  
Mit diesem Befehl wird die Schema Zuordnung der Quelldatenbank zum Ziel Schema bereitstellt.  
  
-   `source-schema` Gibt das zu migrierende Quell Schema an.  
  
-   `sql-server-schema` Gibt das Ziel Schema an, zu dem das Quell Schema migriert wird.  
  
**Syntaxbeispiel:**  
  
```xml  
<map-schema source-schema="<source-schema>"  
  
sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-commands"></a>Verwaltbarkeitsbefehle  
Mithilfe der verwaltbarkeitsbefehle können die Ziel Datenbankobjekte mit der Quelldatenbank synchronisiert werden.  
  
> [!NOTE]  
> Die standardmäßige Konsolenausgabe Einstellung für die Migrations Befehle ist der Ausgabebericht "vollständig", ohne dass eine ausführliche Fehlerberichterstattung vorliegt: nur eine Zusammenfassung des Stamm Knotens der Quell Objektstruktur.  
  
### <a name="synchronize-target"></a>Synchronisieren-Ziel  
Mit diesem Befehl werden die Zielobjekte mit der Zieldatenbank synchronisiert.  
 
Wenn dieser Befehl für die Quelldatenbank ausgeführt wird, ist ein Fehler aufgetreten.  
  
Wenn die Verbindung mit der Zieldatenbank vor dem Ausführen dieses Befehls nicht erfolgt oder bei der Ausführung des Befehls ein Fehler auftritt, wird ein Fehler generiert, und die Konsolenanwendung wird beendet.  
  
-   `object-name:` Gibt die Zielobjekte an, die für die Synchronisierung mit der Zieldatenbank berücksichtigt werden (unterstützt einzelne Objektnamen oder einen Gruppen Objektnamen).  
  
-   `object-type:` Gibt den Typ des Objekts an, das im Object-Name-Attribut aufgerufen wird (wenn die Objekt Kategorie angegeben wird, ist der Objekttyp "Category").  
  
-   `on-error:` Gibt an, ob Synchronisierungs Fehler als Warnungen oder Fehler angegeben werden sollen. Verfügbare Optionen für "bei Fehler":  
  
    -   Bericht-gesamt-als-Warnung  
  
    -   Bericht-jeder-als-Warnung  
  
    -   Fehler-Skript  
  
-   `report-errors-to:` Gibt den Speicherort des Fehlerberichts für den Synchronisierungs Vorgang an (optionales Attribut). Wenn nur der Ordner Pfad angegeben ist, wird die Datei mit dem Namen **TargetSynchronizationReport.XML** erstellt.  
  
**Syntaxbeispiel:**  
  
```xml  
<synchronize-target  
  
object-name="<object-name>"  
  
on-error="<report-total-as-warning/  
  
report-each-as-warning/  
  
fail-script>" (optional)  
  
  report-errors-to="<file-name/folder-name>"        (optional)  
  
/>  
```  
oder  
  
```xml  
<synchronize-target  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"/>  
```  
oder  
  
```xml  
<synchronize-target>  
  
  <metabase-object object-name="<object-name>"/>  
  
  <metabase-object object-name="<object-name>"/>  
  
  <metabase-object object-name="<object-name>"/>  
  
</synchronize-target>  
```  
  
### <a name="refresh-from-database"></a>Refresh-from-Database  
Mit diesem Befehl werden die Quell Objekte aus der Datenbank aktualisiert.  
  
Wenn dieser Befehl für die Zieldatenbank ausgeführt wird, wird ein Fehler generiert.  
  
Dieser Befehl erfordert einen oder mehrere Metabasisknoten als Befehlszeilenparameter.  
  
-   `object-name:` Gibt die Quell Objekte an, die für die Aktualisierung aus der Quelldatenbank berücksichtigt werden (unterstützt einzelne Objektnamen oder einen Gruppen Objektnamen).  
  
-   `object-type:` Gibt den Typ des Objekts an, das im Object-Name-Attribut angegeben ist (wenn die Objekt Kategorie angegeben wird, wird der Objekttyp "Category" genannt).  
  
-   `on-error:` Gibt an, ob Aktualisierungs Fehler als Warnungen oder Fehler aufgerufen werden. Verfügbare Optionen für "bei Fehler":  
  
    -   Bericht-gesamt-als-Warnung  
  
    -   Bericht-jeder-als-Warnung  
  
    -   Fehler-Skript  
  
-   `report-errors-to:` Gibt den Speicherort des Fehlerberichts für den Aktualisierungs Vorgang an (optionales Attribut). Wenn nur der Ordner Pfad angegeben ist, wird die Datei mit dem Namen **SourceDBRefreshReport.XML** erstellt.  
  
**Syntaxbeispiel:**  
  
```xml  
<refresh-from-database  
  
  object-name="<object-name>"  
  
  on-error="<report-total-as-warning/  
  
             report-each-as-warning/  
  
             fail-script>"              (optional)  
  
  report-errors-to="<file-name/folder-name>"        (optional)  
  
/>  
```  
oder  
  
```xml  
<refresh-from-database  
  
  object-name="<object-name>"  
  
  object-type="<object-category>" />  
```  
oder  
  
```xml  
<refresh-from-database>  
  
  <metabase-object object-name="<object-name>"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-commands"></a>Skript Generierungs Befehle  
Die Skript Generierungs Befehle führen duale Aufgaben aus: Sie helfen dabei, die Konsolenausgabe in einer Skriptdatei zu speichern und die T-SQL-Ausgabe in der Konsole oder in einer Datei auf Grundlage des angegebenen Parameters aufzuzeichnen.  
  
### <a name="save-as-script"></a>als Skript speichern  
Dieser Befehl wird verwendet, um die Skripts der Objekte in einer Datei zu speichern, die bei Metabase = target angegeben wird. Dies ist eine Alternative zum Synchronisierungs Befehl darin, dass die Skripts erhalten und in der Zieldatenbank gleich ausgeführt werden.  
  
Dieser Befehl erfordert einen oder mehrere Metabasisknoten als Befehlszeilenparameter.  
  
-   `object-name:` Gibt die Objekte an, deren Skripts gespeichert werden sollen (unterstützt einzelne Objektnamen oder einen Gruppen Objektnamen).  
  
-   `object-type:` Gibt den Typ des Objekts an, das im Object-Name-Attribut aufgerufen wird (wenn die Objekt Kategorie angegeben wird, ist der Objekttyp "Category").  
  
-   `metabase:` Gibt an, ob es sich um die Quell-oder Ziel Metabase handelt.  
  
-   `destination:` Gibt den Pfad oder den Ordner an, in dem das Skript gespeichert werden muss. Wenn der Dateiname nicht angegeben wird, wird ein Dateiname im Format (object_name Attribut Wert). out bereitgestellt.
  
-   `overwrite:` Wenn der Wert true ist, wird derselbe Dateiname überschrieben, sofern er vorhanden ist. Sie kann die Werte (true/false) enthalten.  
  
**Syntaxbeispiel:**  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  object-name="<object-name>"  
  
  object-type="<object-category>"  
  
  destination="<file-name/folder-name>"  
  
  overwrite="<true/false>"   (optional)  
  
/>  
```  
oder  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  destination="<file-name/folder-name>"  
  
    <metabase-object object-name="<object-name>"  
  
                     object-type="<object-category>"/>  
  
</save-as-script>  
```  
  
### <a name="convert-sql-statement"></a>Convert-SQL-Anweisung
Mit diesem Befehl wird die SQL-Anweisung konvertiert.  
  
-   `context` Gibt den Schema Namen an.  
  
-   `destination` Gibt an, ob die Ausgabe in einer Datei gespeichert werden soll.  
  
    Wenn dieses Attribut nicht angegeben wird, wird die konvertierte T-SQL-Anweisung in der Konsole angezeigt. (optionales Attribut)  
  
-   `conversion-report-folder` Gibt den Ordner an, in dem der Bewertungsbericht gespeichert werden kann. (optionales Attribut)  
  
-   `conversion-report-overwrite` Gibt an, ob der Bewertungsberichts Ordner überschrieben werden soll, wenn er bereits vorhanden ist.  
  
    **Standardwert:** false. (optionales Attribut)  
  
-   `write-converted-sql-to` Gibt den Datei Ordner Pfad (oder) an, in dem die konvertierte T-SQL-Datei gespeichert werden soll. Wenn ein Ordner Pfad zusammen mit dem-Attribut angegeben wird `sql-files` , verfügt jede Quelldatei über eine entsprechende Ziel-T-SQL-Datei, die im angegebenen Ordner erstellt wurde. Wenn ein Ordner Pfad zusammen mit dem-Attribut angegeben wird `sql` , wird die konvertierte T-SQL-Datei in eine Datei mit dem Namen "result. out" unter dem angegebenen Ordner geschrieben.  
  
-   `sql` Gibt die zu konvertierenden Sybase-SQL-Anweisungen an. eine oder mehrere Anweisungen können mithilfe von ";" getrennt werden.  
  
-   `sql-files` Gibt den Pfad der SQL-Dateien an, die in T-SQL-Code konvertiert werden sollen.  
  
-   `write-summary-report-to` Gibt den Pfad an, in dem der Zusammenfassungs Bericht generiert wird. Wenn nur der Ordner Pfad erwähnt wird, wird die Datei mit dem Namen **ConvertSQLReport.XML** erstellt. (optionales Attribut)  
  
    Die Erstellung eines Zusammenfassungs Berichts umfasst zwei weitere Unterkategorien:  
  
    -   Report-Errors (= "true/false", mit dem Standardwert "false" (optionale Attribute)).  
  
    -   Ausführliche (= "true/false", mit dem Standardwert "false" (optionale Attribute)).  
  
Dieser Befehl erfordert einen oder mehrere Metabasisknoten als Befehlszeilenparameter.  
  
**Syntaxbeispiel:**  
  
```  
<convert-sql-statement  
  
       context="<database-name>.<schema-name>"  
  
        conversion-report-folder="<folder-name>"  
  
        conversion-report-overwrite="<true/false>"  
  
        write-summary-report-to="<file-name/folder-name>"   (optional)  
  
        verbose="<true/false>"   (optional)  
  
        report-errors="<true/false>"   (optional)  
  
        destination="<stdout/file>"   (optional)  
  
        write-converted-sql-to ="<file-name/folder-name>"  
  
        sql="SELECT 1 FROM DUAL;">  
  
    <output-window suppress-messages="<true/false>" />  
  
</convert-sql-statement>  
```  
oder  
  
```  
<convert-sql-statement  
  
         context="<database-name>.<schema-name>"  
  
         conversion-report-folder="<folder-name>"  
  
         conversion-report-overwrite="<true/false>"  
  
         write-summary-report-to="<file-name/folder-name>"   (optional)  
  
         verbose="<true/false>"   (optional)  
  
         report-errors="<true/false>"   (optional)  
  
         destination="<stdout/file>"   (optional)  
  
         write-converted-sql-to ="<file-name/folder-name>"  
  
         sql-files="<folder-name>\*.sql"  
  
/>  
```  
oder  
  
```  
<convert-sql-statement  
  
         context="<database-name>.<schema-name>"  
  
         conversion-report-folder="<folder-name>"  
  
         conversion-report-overwrite="<true/false>"  
  
         sql-files="<folder-name>\*.sql"  
  
/>  
```  
  
## <a name="next-steps"></a>Nächste Schritte  
Weitere Informationen zu Befehlszeilenoptionen finden Sie unter [Befehlszeilenoptionen in der SSMA-Konsole (accesstosql)](../access/command-line-options-in-ssma-console-accesstosql.md).  
  
Informationen zu einer Beispiel-Konsolen Skriptdatei finden Sie unter [Arbeiten mit den Beispiel Konsolen Skriptdateien &#40;sybasetoisql&#41;](../../ssma/sybase/working-with-the-sample-console-script-files-sybasetosql.md)  
  
Der nächste Schritt hängt von Ihren Projektanforderungen ab:  
  
-   Informationen zum Angeben eines Kennworts oder zum Exportieren/Importieren von Kenn Wörtern finden Sie unter Verwalten von Kenn [Wörtern &#40;Sybase&#41;](../../ssma/sybase/managing-passwords-sybasetosql.md).  
  
-   Informationen zum Erstellen von Berichten finden Sie unter [Erstellen von Berichten &#40;sybasedesql&#41;](../../ssma/sybase/generating-reports-sybasetosql.md).  
  
-   Informationen zur Behebung von Problemen in der-Konsole finden Sie unter [Problembehandlung &#40;sybasedesql&#41;](../../ssma/sybase/troubleshooting-sybasetosql.md).  
  
