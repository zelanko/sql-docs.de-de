---
title: Ausführen der SSMA-Konsole (mysqldesql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Script file commands, Database connection commands
- Script file commands, Manageability commands
- Script file commands, Migration commands
- Script file commands, Migration preparation commands
- Script file commands, project commands
- Script file commands, Report commands
- Script file commands, Script generation commands
ms.assetid: e3e9f7e4-0619-4861-a202-3d5d39953b26
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 239ba5021363be583572d5d24887233261e359cc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "76909690"
---
# <a name="executing-the-ssma-console-mysqltosql"></a>Ausführen der SSMA-Konsole (MySqlToSql)
Microsoft bietet Ihnen einen robusten Satz von Skriptdatei Befehlen zum Ausführen und Steuern von SSMA-Aktivitäten.  
  
Die Konsolenanwendung verwendet bestimmte Standard Befehle für Skriptdateien, wie in diesem Abschnitt aufgelistet.  
  
## <a name="project--script-file-commands"></a>Befehle der Projekt Skriptdatei  
**Befehl**  
  
Create-New-Project:   
                   Erstellt ein neues SSMA-Projekt.  
  
Die Projekt Befehle behandeln das Erstellen von Projekten, das Öffnen, speichern und Beenden von Projekten.  
  
**Skript**  
  
1.  `project-folder`Gibt den Ordner des Projekts an, das erstellt wird.  
  
2.  `project-name`Gibt den Namen des Projekts an. {string}  
  
3.  `overwrite-if-exists`Optionales Attribut gibt an, ob ein vorhandenes Projekt überschrieben werden soll. booleschen  
  
4.  `project-type:`Optionales Attribut. Gibt den Projekttyp an, d. h. das Projekt "SQL-Server-2005" oder das Projekt "SQL Server-2008" oder das Projekt "SQL-Server-2012" oder das Projekt "SQL-Server-2014" oder das Projekt "SQL-Azure". Der Standardwert ist "SQL Server-2008".  
  
**Syntax Beispiel:**  
  
```xml  
<create-new-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
   overwrite-if-exists="<true/false>"   (optional)  
  
   project-type=="<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014 | sql-azure>"   (optional)  
  
/>  
```  
Das Attribut ' überschreiben-if-vorhanden ' ist standardmäßig **false** .  
  
Das Attribut ' Project-Type ' ist standardmäßig **SQL-Server-2008** .  
  
**Befehl**  
  
Open-Project:   
                  Öffnet ein vorhandenes Projekt.  
  
**Skript**  
  
1.  `project-folder`Gibt den Ordner des Projekts an, das erstellt wird. Der Befehl schlägt fehl, wenn der angegebene Ordner nicht vorhanden ist.  {string}  
  
2.  `project-name`Gibt den Namen des Projekts an. Der Befehl schlägt fehl, wenn das angegebene Projekt nicht vorhanden ist.  {string}  
  
**Syntax Beispiel:**  
  
```xml  
<open-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
/>  
```  
> [!IMPORTANT]  
> Die SSMA für MySQL-Konsolenanwendung unterstützt die Abwärtskompatibilität. Sie können Projekte öffnen, die mit einer früheren Version von SSMA erstellt wurden.  
  
**Befehl**  
  
Save-Project: speichert das Migrationsprojekt.  
  
**Skript**  
  
**Syntax Beispiel:**  
  
```xml  
<save-project/>  
```  
**Befehl**  
  
Close-Projekt  
                  : Schließt das Migrationsprojekt.  
  
**Skript**  
  
**Syntax Beispiel:**  
  
```xml  
<save-project/>  
```  
**Befehl**  
  
Close-Projekt  
                  : Schließt das Migrationsprojekt.  
  
**Skript**  
  
**Syntax Beispiel:**  
  
```xml  
<close-project  
  
   if-modified="<save/error/ignore>"   (optional)  
  
/>  
```  
Das Attribut ' If-modified ' ist optional, wird standardmäßig **ignoriert** .  
  
## <a name="database-connection-script-file-commands"></a>Befehle der Datenbank-Verbindungs Skriptdatei  
Mithilfe der Daten bankverbindungs Befehle können Sie eine Verbindung mit der Datenbank herstellen.  
  
1.  Die Funktion zum **Durchsuchen** der Benutzeroberfläche wird in der-Konsole nicht unterstützt.  
  
2.  Die **Windows-Authentifizierungs-und-** **Port** Parameter sind beim Herstellen einer Verbindung mit SQL Azure nicht anwendbar.  
  
3.  Weitere Informationen zum Erstellen von Skriptdateien finden Sie unter [Erstellen von Skriptdateien &#40;mysqltoisql&#41;](../../ssma/mysql/creating-script-files-mysqltosql.md).  
  
**Befehl**  
  
Connect-Source-Datenbank  
  
-   Führt eine Verbindung mit der Quelldatenbank aus und lädt auf hoher Ebene Metadaten der Quelldatenbank, aber nicht alle Metadaten.  
  
-   Wenn die Verbindung mit der Quelle nicht hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung.  
  
**Skript**  
  
Die Server Definition wird aus dem Name-Attribut abgerufen, das für jede Verbindung im Server Abschnitt der Server Verbindungs Datei oder der Skriptdatei definiert ist.  
  
**Syntax Beispiel:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
**Befehl**  
  
Force-Load-Source/Ziel-Database  
  
-   Lädt die Quell Metadaten.  
  
-   Nützlich für das Offline arbeiten an einem Migrationsprojekt.  
  
-   Wenn die Verbindung mit der Quelle bzw. dem Ziel nicht hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung.  
  
**Skript**  
  
Erfordert einen oder mehrere Metabasisknoten als Befehlszeilenparameter.  
  
**Syntax Beispiel:**  
  
```xml  
<force-load metabase="<source/target>"  
  
      <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Befehl**  
  
reconnect-Quelldatenbank  
  
1.  Stellt eine erneute Verbindung mit der Quelldatenbank her, lädt jedoch keine Metadaten im Gegensatz zum Connect-Source-Database-Befehl.  
  
2.  Wenn (erneut) keine Verbindung mit der Quelle hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung.  
  
**Skript**  
  
**Syntax Beispiel:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Befehl**  
  
Connect-Target-Database  
  
1.  Stellt eine Verbindung mit dem Ziel SQL Server oder SQL Azure Datenbank her und lädt auf hoher Ebene Metadaten der Zieldatenbank, jedoch nicht vollständig auf die Metadaten.  
  
2.  Wenn die Verbindung mit dem Ziel nicht hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung.  
  
**Skript**  
  
Die Server Definition wird aus dem Name-Attribut abgerufen, das für jede Verbindung im Server Abschnitt der Server Verbindungs Datei oder der Skriptdatei definiert ist.  
  
**Syntax Beispiel:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Befehl**  
  
reconnect-Target-Database  
  
1.  Stellt eine erneute Verbindung mit der Zieldatenbank her, lädt jedoch im Gegensatz zum Connect-Target-Database-Befehl keine Metadaten.  
  
2.  Wenn (erneut) die Verbindung mit dem Ziel nicht hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung.  
  
**Skript**  
  
**Syntax Beispiel:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file-commands"></a>Befehle für Berichts Skriptdateien  
Die Berichts Befehle generieren Berichte zur Leistung verschiedener SSMA-Konsolen Aktivitäten.  
  
**Befehl**  
  
generieren-Assessment-Bericht  
  
1.  Generiert Bewertungsberichte für die Quelldatenbank.  
  
2.  Wenn die Verbindung der Quelldatenbank vor dem Ausführen dieses Befehls nicht erfolgt, wird ein Fehler generiert, und die Konsolenanwendung wird beendet.  
  
3.  Wenn während der Befehlsausführung keine Verbindung mit dem Quelldaten Bankserver hergestellt werden kann, führt dies auch dazu, dass die Konsolenanwendung beendet wird.  
  
**Skript**  
  
1.  `assessment-report-folder:`Gibt den Ordner an, in dem der Bewertungsbericht gespeichert werden kann. (optionales Attribut)  
  
2.  `object-name:`Gibt die Objekte an, die für die Bewertungsbericht Generierung berücksichtigt werden (Sie kann einzelne Objektnamen oder einen Gruppen Objektnamen aufweisen).  
  
3.  `object-type:`Gibt den Typ des Objekts an, das im Object-Name-Attribut angegeben ist (wenn die Objekt Kategorie angegeben wird, wird der Objekttyp "Category" genannt).  
  
4.  `assessment-report-overwrite:`Gibt an, ob der Bewertungsberichts Ordner überschrieben werden soll, wenn er bereits vorhanden ist.  
  
    **Standardwert:** false. (optionales Attribut)  
  
5.  `write-summary-report-to:`Gibt den Pfad an, in dem der Zusammenfassungs Bericht generiert wird.  
  
    Wenn nur der Ordner Pfad erwähnt wird, dann file **by Name&lt;&gt; XML** wird erstellt. (optionales Attribut)  
  
    Die Berichterstellung hat zwei weitere Unterkategorien:  
  
    -   `report-errors`(= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
    -   `verbose`(= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
**Syntax Beispiel:**  
  
```xml  
<generate-assessment-report  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
oder  
  
```xml  
<generate-assessment-report  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
>  
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration--script-file-commands"></a>Befehle der Migrations Skriptdatei  
Die Migrations Befehle Konvertieren das Ziel Datenbankschema in das Quell Schema und migriert Daten auf den Zielserver.  
  
Die standardmäßige Konsolenausgabe Einstellung für die Migrations Befehle ist der Ausgabebericht "vollständig", ohne dass eine ausführliche Fehlerberichterstattung vorliegt: nur eine Zusammenfassung des Stamm Knotens der Quell Objektstruktur.  
  
**Befehl**  
  
Convert-Schema  
  
1.  Führt eine Schema Konvertierung von der Quelle in das Ziel Schema durch.  
  
2.  Wenn die Verbindung mit der Quell-oder Zieldatenbank vor dem Ausführen dieses Befehls nicht erfolgt oder wenn die Verbindung mit dem Quell-oder Ziel Datenbankserver während der Ausführung des Befehls fehlschlägt, wird ein Fehler generiert, und die Konsolenanwendung wird beendet.  
  
**Skript**  
  
1.  `conversion-report-folder:`Gibt den Ordner an, in dem der Bewertungsbericht gespeichert werden kann. (optionales Attribut)  
  
2.  `object-name:`Gibt die Objekte an, die für das Umrechnen des Schemas berücksichtigt werden (es kann sich um indivduale Objektnamen oder einen Gruppen Objektnamen).  
  
3.  `object-type:`Gibt den Typ des Objekts an, das im Object-Name-Attribut angegeben ist (wenn die Objekt Kategorie angegeben wird, wird der Objekttyp "Category" genannt).  
  
4.  `conversion-report-overwrite:`Gibt an, ob der Bewertungsberichts Ordner überschrieben werden soll, wenn er bereits vorhanden ist.  
  
    **Standardwert:** false. (optionales Attribut)  
  
5.  `write-summary-report-to:`Gibt den Pfad an, in dem der Zusammenfassungs Bericht generiert wird.  
  
    Wenn nur der Ordner Pfad erwähnt wird, dann file by Name **schemaconversionreport&lt;n&gt;. XML** wird erstellt. (optionales Attribut)  
  
    Die Erstellung eines Zusammenfassungs Berichts umfasst zwei weitere Unterkategorien:  
  
    -   `report-errors`(= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
    -   `verbose`(= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
**Syntax Beispiel:**  
  
```xml  
<convert-schema  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
oder  
  
```xml  
<convert-schema  
  
   conversion-report-folder="<folder-name>"   (optional)  
  
   conversion-report-overwrite="<true/false>"   (optional)  
  
      <metabase-object object-name="<object-names>"  
  
         object-type="<object-category>"/>  
  
</convert-schema>  
```  
**Befehl**  
  
Migrieren von Daten  
  
1.  Migriert die Quelldaten zum Ziel.  
  
**Skript**  
  
1.  `object-name:`Gibt die zum Migrieren von Daten berücksichtigten Quell Objekte an (es kann sich um indivduale Objektnamen oder einen Gruppen Objektnamen).  
  
2.  `object-type:`Gibt den Typ des Objekts an, das im Object-Name-Attribut angegeben ist (wenn die Objekt Kategorie angegeben wird, wird der Objekttyp "Category" genannt).  
  
3.  `write-summary-report-to:`Gibt den Pfad an, in dem der Zusammenfassungs Bericht generiert wird.  
  
    Wenn nur der Ordner Pfad erwähnt wird, dann file by Name **datamigrationreport&lt;n&gt;. XML** wird erstellt. (optionales Attribut)  
  
    Die Berichterstellung hat zwei weitere Unterkategorien:  
  
    -   `report-errors`(= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
    -   `verbose`(= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
**Syntax Beispiel:**  
  
```xml  
<migrate-data  
  
   write-summary-report-to="<file-name/folder-name>"  
  
   report-errors="true" verbose="true">  
  
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
  
   report-errors="true" verbose="true"/>  
```  
  
## <a name="migration-preparation-script-file-command"></a>Skriptdatei Befehl zur Vorbereitung der Migration  
Der Befehl Migrations Vorbereitung initiiert die Schema Zuordnung zwischen den Quell-und Ziel Datenbanken.  
  
**Befehl**  
  
Map-Schema  
  
Schema Zuordnung der Quelldatenbank zum Ziel Schema.  
  
**Skript**  
  
1.  `source-schema`Gibt das Quell Schema an, das migriert werden soll.  
  
2.  `sql-server-schema`Gibt das Ziel Schema an, in dem Sie migriert werden soll.  
  
**Syntax Beispiel:**  
  
```xml  
<map-schema  
  
   source-schema="<source-schema>"  
  
   sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-script-file-commands"></a>Verwaltbarkeitsskript-Datei Befehle  
Mithilfe der verwaltbarkeitsbefehle können die Ziel Datenbankobjekte mit der Quelldatenbank synchronisiert werden.  
  
> [!NOTE]  
> Die standardmäßige Konsolenausgabe Einstellung für die Migrations Befehle ist der Ausgabebericht "vollständig", ohne dass eine ausführliche Fehlerberichterstattung vorliegt: nur eine Zusammenfassung des Stamm Knotens der Quell Objektstruktur.  
  
**Befehl**  
  
Synchronisieren-Ziel  
  
1.  Synchronisiert die Zielobjekte mit der Zieldatenbank.  
  
2.  Wenn dieser Befehl für die Quelldatenbank ausgeführt wird, ist ein Fehler aufgetreten.  
  
3.  Wenn die Verbindung mit der Zieldatenbank vor dem Ausführen dieses Befehls nicht erfolgt oder bei der Ausführung des Befehls ein Fehler auftritt, wird ein Fehler generiert, und die Konsolenanwendung wird beendet.  
  
**Skript**  
  
1.  `object-name:`Gibt die Objekte an, die für die Synchronisierung mit der Zieldatenbank berücksichtigt werden (Sie kann über indivduale Objektnamen oder einen Gruppen Objektnamen verfügen).  
  
2.  `object-type:`Gibt den Typ des Objekts an, das im Object-Name-Attribut angegeben ist (wenn die Objekt Kategorie angegeben wird, wird der Objekttyp "Category" genannt).  
  
3.  `on-error:`Gibt an, ob Synchronisierungs Fehler als Warnungen oder Fehler angegeben werden sollen. Verfügbare Optionen für "bei Fehler":  
  
    -   Bericht-gesamt-als-Warnung  
  
    -   Bericht-jeder-als-Warnung  
  
    -   Fehler-Skript  
  
4.  `report-errors-to:`Gibt den Speicherort des Fehlerberichts für den Synchronisierungs Vorgang an (optionales Attribut), wenn nur der Ordner Pfad angegeben ist, dann wird die Datei mit dem Namen " **targetsynchronizationreport. XML** " erstellt.  
  
**Syntax Beispiel:**  
  
```xml  
<synchronize-target  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name>"   (optional)  
  
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
**Befehl**  
  
Refresh-from-Database  
  
1.  Aktualisiert die Quell Objekte aus der Datenbank.  
  
2.  Wenn dieser Befehl für die Zieldatenbank ausgeführt wird, wird ein Fehler generiert.  
  
**Skript**  
  
1.  `object-name:`Gibt die Quell Objekte an, die für die Aktualisierung aus der Quelldatenbank berücksichtigt werden (Sie können über indivduale Objektnamen oder einen Gruppen Objektnamen verfügen).  
  
2.  `object-type:`Gibt den Typ des Objekts an, das im Object-Name-Attribut angegeben ist (wenn die Objekt Kategorie angegeben wird, wird der Objekttyp "Category" genannt).  
  
3.  `on-error:`Gibt an, ob Synchronisierungs Fehler als Warnungen oder Fehler angegeben werden sollen. Verfügbare Optionen für "bei Fehler":  
  
    -   Bericht-gesamt-als-Warnung  
  
    -   Bericht-jeder-als-Warnung  
  
    -   Fehler-Skript  
  
4.  `report-errors-to:`Gibt den Speicherort des Fehlerberichts für den Synchronisierungs Vorgang an (optionales Attribut), wenn nur der Ordner Pfad angegeben wird. Anschließend wird die Datei mit dem Namen " **sourcedbrefreshreport. XML** " erstellt.  
  
Erfordert einen oder mehrere Metabasisknoten als Befehlszeilenparameter.  
  
**Syntax Beispiel:**  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name>"   (optional)  
  
/>  
```  
oder  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"/>  
```  
oder  
  
```xml  
<refresh-from-database>  
  
   <metabase-object object-name="<object-name>"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-script-file-commands"></a>Skripterstellung Skriptdatei Befehle  
Die Skript Generierungs Befehle führen duale Aufgaben aus: Sie helfen dabei, die Konsolenausgabe in einer Skriptdatei zu speichern. und notieren Sie die T-SQL-Ausgabe in der Konsole oder in einer Datei, die auf dem von Ihnen angegebenen Parameter basiert.  
  
**Befehl**  
  
als Skript speichern  
  
Wird verwendet, um die Skripts der Objekte in einer Datei zu speichern, die bei Metabase = Target erwähnt wird. Dies ist eine Alternative zum Synchronisierungs Befehl, bei dem die Skripts in der Zieldatenbank ausgeführt werden.  
  
**Skript**  
  
Erfordert einen oder mehrere Metabasisknoten als Befehlszeilenparameter.  
  
1.  `object-name:`Gibt die Objekte an, deren Skripts gespeichert werden sollen. (Er kann über indivduale Objektnamen oder einen Gruppen Objektnamen verfügen)  
  
2.  `object-type:`Gibt den Typ des Objekts an, das im Object-Name-Attribut angegeben ist (wenn die Objekt Kategorie angegeben wird, wird der Objekttyp "Category" genannt).  
  
3.  `metabase:`Gibt an, ob es sich um die Quell-oder Ziel Metabase handelt.  
  
4.  `destination:`Gibt den Pfad oder den Ordner an, in dem das Skript gespeichert werden muss. wenn der Dateiname nicht angegeben ist, wird ein Dateiname im Format (object_name Attribut Wert). out angegeben.  
  
5.  `overwrite:`true gibt an, dass der Dateiname überschrieben wird Sie kann die Werte (true/false) enthalten.  
  
**Syntax Beispiel:**  
  
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
**Befehl**  
  
Convert-SQL-Anweisung  
  
1.  `context`Gibt den Schema Namen an.  
  
2.  `destination`Gibt an, ob die Ausgabe in einer Datei gespeichert werden soll.  
  
    Wenn dieses Attribut nicht angegeben wird, wird die konvertierte T-SQL-Anweisung in der Konsole angezeigt. (optionales Attribut)  
  
3.  `conversion-report-folder`Gibt den Ordner an, in dem der Bewertungsbericht gespeichert werden kann. (optionales Attribut)  
  
4.  `conversion-report-overwrite`Gibt an, ob der Bewertungsberichts Ordner überschrieben werden soll, wenn er bereits vorhanden ist.  
  
    **Standardwert:** false. (optionales Attribut)  
  
5.  `write-converted-sql-to`Gibt den Datei Ordner Pfad (oder) an, in dem die konvertierte T-SQL-Datei gespeichert werden soll. Wenn ein Ordner Pfad zusammen mit dem `sql-files` -Attribut angegeben wird, verfügt jede Quelldatei über eine entsprechende Ziel-T-SQL-Datei, die im angegebenen Ordner erstellt wurde. Wenn ein Ordner Pfad zusammen mit dem `sql` -Attribut angegeben wird, wird die konvertierte T-SQL-Datei in eine Datei mit dem Namen "result. out" unter dem angegebenen Ordner geschrieben.  
  
6.  `sql`Gibt die zu konvertierenden MySQL-SQL-Anweisungen an. eine oder mehrere Anweisungen können mithilfe von ";" getrennt werden.  
  
7.  `sql-files`Gibt den Pfad der SQL-Dateien an, die in T-SQL-Code konvertiert werden müssen.  
  
8.  `write-summary-report-to`Gibt den Pfad an, in dem der Zusammenfassungs Bericht generiert wird. Wenn nur der Ordner Pfad erwähnt wird, wird die Datei mit dem Namen **converzqlreport. XML** erstellt. (optionales Attribut)  
  
    Die Berichtserstellung hat zwei weitere Unterkategorien, nämlich:  
  
    -   Report-Errors (= "true/false", mit dem Standardwert "false" (optionale Attribute)).  
  
    -   Ausführliche (= "true/false", mit dem Standardwert "false" (optionale Attribute)).  
  
**Skript**  
  
Erfordert einen oder mehrere Metabasisknoten als Befehlszeilenparameter.  
  
**Syntax Beispiel:**  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   destination="stdout/file"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
   sql="SELECT 1 FROM DUAL;">  
  
      <output-window suppress-messages="<true/false>" />  
  
</convert-sql-statement>  
```  
oder  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   destination="<stdout/file>"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
   sql-files="<folder-name>\*.sql"  
  
/>  
```  
oder  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   sql-files="<folder-name>\*.sql"  
  
/>  
```  
  
## <a name="next-step"></a>Nächster Schritt  
Weitere Informationen zu Befehlszeilenoptionen finden Sie unter [Befehlszeilenoptionen in der SSMA-Konsole &#40;mysqlto SQL&#41;](../../ssma/mysql/command-line-options-in-ssma-console-mysqltosql.md) .  
  
Weitere Informationen zu Beispiel-Konsolen Skriptdateien finden Sie unter [Arbeiten mit den Beispiel Konsolen Skriptdateien &#40;mysqltoisql&#41;](../../ssma/mysql/working-with-the-sample-console-script-files-mysqltosql.md)  
  
Der nächste Schritt hängt von Ihren Projektanforderungen ab:  
  
1.  Informationen zum Angeben eines Kennworts oder zum Exportieren/Importieren von Kenn Wörtern finden Sie unter Verwalten von Kenn [Wörtern &#40;MySQL&#41;](../../ssma/mysql/managing-passwords-mysqltosql.md).  
  
2.  Informationen zum Erstellen von Berichten finden Sie unter [Erstellen von Berichten &#40;mysqldesql&#41;](../../ssma/mysql/generating-reports-mysqltosql.md).  
  
3.  Informationen zur Behebung von Problemen in der-Konsole finden Sie unter [Problembehandlung &#40;mysqldesql&#41;](../../ssma/mysql/troubleshooting-mysqltosql.md).  
  
