---
title: Ausführen der SSMA-Konsole (SybaseToSQL) | Microsoft-Dokumentation
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
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 602bc0ac1584f9ff369efa8a2484a16a97a92285
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68029154"
---
# <a name="executing-the-ssma-console-sybasetosql"></a>Ausführen der SSMA-Konsole (SybaseToSQL)
Microsoft bietet einen robusten Satz von Skript Befehle zum Ausführen und Steuerungsaktivitäten SSMA Datei. Die folgenden Abschnitte enthalten Informationen identisch.  
  
## <a name="script-file-commands"></a>Datei-Skriptbefehle  
Die Konsolenanwendung verwendet bestimmte standard Skriptbefehle für die Datei als aufgelisteten, in diesem Abschnitt.  
  
## <a name="project-commands"></a>Projektbefehle  
Die Projekt-Befehle verarbeiten, erstellen Projekte öffnen, speichern und Beenden von Projekten.  
  
### <a name="create-new-project"></a>Neues-Projekt erstellen  
Dieser Befehl erstellt ein neues SSMA-Projekt.  
  
-   `project-folder` Gibt den Ordner des Projekts erstellt.  
  
-   `project-name` Gibt den Namen des Projekts. {string}  
  
-   `overwrite-if-exists`Optionales Attribut gibt an, ob ein vorhandenes Projekt überschrieben werden soll. {Boolean}  
  
-   `project-type:`Optionales Attribut. Gibt den Projekttyp, der "Sql Server 2005" Projekt oder "Sql Server 2008" Projekt "Sql Server 2012", Projekt oder "Sql Server 2014", Projekt oder "Sql Azure"-Projekt ist. Standardwert ist "Sql-Server-2008."  
  
**Syntaxbeispiel:**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>" (optional)  
  
   project-type="<sql-server-2008/sql-server-2005/sql-server-2012/sql-server-2014/sql-azure>"  
/>  
```  
Attribut "überschreiben-If-exists" **"false"** standardmäßig.  
  
'Project-Type'-Attribut ist **Sql-Server-2008** standardmäßig.  
  
### <a name="open-project"></a>Open-Projekt  
Mit diesem Befehl wird das Projekt geöffnet.

-   `project-folder` Gibt den Ordner des Projekts erstellt. Der Befehl schlägt fehl, wenn der angegebene Ordner nicht vorhanden ist.  {string}  
  
-   `project-name` Gibt den Namen des Projekts. Der Befehl schlägt fehl, wenn das angegebene Projekt nicht vorhanden ist.  {string}  
  
**Syntaxbeispiel:**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
> [!NOTE]  
> SSMA für SAP ASE-Konsolenanwendung unterstützt die Abwärtskompatibilität zu gewährleisten. Sie können es verwenden, um von früheren Version von SSMA erstellte Projekte zu öffnen.  
  
### <a name="save-project"></a>Save-Projekt  
Dieser Befehl speichert das Migrationsprojekt.  
  
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
'If-modified'-Attribut ist optional, **ignorieren** standardmäßig.  
  
## <a name="database-connection-commands"></a>Datenbankbefehle für Verbindung  
Die Verbindung mit Datenbank-Befehle können mit der Datenbank herstellen.  
  
> [!NOTE]  
> - Die **Durchsuchen** Feature der Benutzeroberfläche wird in der Konsole nicht unterstützt.  
> - Weitere Informationen zu "Erstellen von Skriptdateien", finden Sie unter [Skriptdateien erstellen &#40;SybaseToSQL&#41;](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
### <a name="connect-source-database"></a>Connect-Source-Datenbank  
Mit diesem Befehl wird die Verbindung mit der Quelldatenbank und lädt hochrangige Metadaten von der Quelldatenbank, jedoch nicht alle Metadaten.
  
Wenn die Verbindung mit der Datenquelle hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die Ausführung weiter.
  
Definition des Servers werden aus dem Namensattribut für jede Verbindung im Server-Abschnitt, der die Server-Verbindungsdatei oder die Skriptdatei definiert abgerufen werden.  
  
**Syntaxbeispiel:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="force-load-sourcetarget-database"></a>-Force-Last-Quelle/Ziel-database  
Dieser Befehl lädt die Metadaten der Datenquelle, und ist nützlich für das Migrationsprojekt offline arbeiten.  
  
Wenn die Verbindung mit der Quelle/Ziel kann nicht hergestellt werden, wird ein Fehler generiert, und die Konsolenanwendung beendet die Ausführung weiter.  
  
Dieser Befehl erfordert einen oder mehrere Metabase-Knoten als Befehlszeilenparameter an.  
  
**Syntaxbeispiel:**  
  
```xml  
<force-load metabase="<source/target>" >  
  
  <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
  
### <a name="reconnect-source-database"></a>Verbindung-Source-Datenbank  
Dieser Befehl erneut eine Verbindung herstellt, für die Datenbank jedoch keine Metadaten im Gegensatz zu den Connect-Source-Database-Befehl wird nicht geladen.  
  
Ein Fehler wird generiert, wenn die Verbindung mit der Datenquelle hergestellt werden kann, und die Konsolenanwendung beendet die Ausführung weiter.  
  
**Syntaxbeispiel:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
  
### <a name="connect-target-database"></a>Connect-Zieldatenbank  
Mit diesem Befehl eine Verbindung mit SQL Server-Zieldatenbank her und lädt hochrangige Metadaten der Zieldatenbank, aber nicht die Metadaten vollständig.  
  
Wenn die Verbindung mit dem Ziel hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung weiter beendet die Ausführung.  
  
Definition des Servers werden aus dem Namensattribut für jede Verbindung im Server-Abschnitt, der die Server-Verbindungsdatei oder die Skriptdatei definiert abgerufen werden.  
  
**Syntaxbeispiel:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
  
### <a name="reconnect-target-database"></a>Verbindung-Zieldatenbank  
  
Mit diesem Befehl erneut eine Verbindung herstellt, in die Zieldatenbank aber keine Metadaten, im Gegensatz zu den Connect-Ziel-Database-Befehl wird nicht geladen.  
  
Ein Fehler wird generiert, wenn die (Verbindung mit dem Ziel erneut) hergestellt werden kann, und die Konsolenanwendung beendet die Ausführung weiter.  
  
**Syntaxbeispiel:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-commands"></a>Berichtsbefehle  
Die Berichtsserver-Befehle Generieren von Berichten auf die Leistung der verschiedenen Aktivitäten von SSMA-Konsole.  
  
### <a name="generate-assessment-report"></a>Generieren von Bewertungsbericht  
  
Dieser Befehl generiert Berichte zur Bewertung der Quelldatenbank.  
  
Wenn die Verbindung mit der Quelldatenbank nicht ausgeführt werden, bevor Sie diesen Befehl ausführen, wird ein Fehler generiert, und die Konsolenanwendung wird beendet.  
  
Fehler bei der Ausführung des Befehls, der eine Verbindung mit dem Quellserver für die Datenbank auch führt zum Beenden der Konsolenanwendung.  
  
-   `conversion-report-folder:` Gibt den Ordner, in dem der Bewertungsbericht gespeichert werden kann. (optionales Attribut)  
  
-   `object-name:` Gibt an, die Objekte, die für die Bewertung der berichtgenerierung (unterstützt das einzelne Objektnamen oder einen Gruppennamen für das Objekt) in Betracht gezogen.  
  
-   `object-type:` Gibt den Typ des Objekts (sofern es sich um eine Objektkategorie angegeben wird, dann ist "Category" Objekttyp) im Objekt-Name-Attribut hingewiesen.  
  
-   `conversion-report-overwrite:` Gibt an, ob den Berichtsordner für die Bewertung zu überschreiben, wenn sie bereits vorhanden ist.  
  
    **Standardwert:** "false". (optionales Attribut)  
  
-   `write-summary-report-to:` Gibt den Pfad, an dem der Bericht generiert wird.  
  
    Wenn nur der Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **AssessmentReport&lt;n&gt;. XML** erstellt wird. (optionales Attribut)  
  
    Erstellen von Berichten verfügt über zwei weitere Unterkategorien:  
  
    -   `report-errors` (= "True/False", Standardwert "false" (optionale Attribute))  
  
    -   `verbose` (= "True/False", Standardwert "false" (optionale Attribute))  
  
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
  
## <a name="migration-commands"></a>Migrationsbefehle  
Die migrationsbefehle Schema der Zieldatenbank, die dem Quellschema zu konvertieren und Migrieren von Daten auf dem Zielserver.  
  
### <a name="convert-schema"></a>Convert-schema  
Mit diesem Befehl wird die schemakonvertierung aus der Quelle in das Zielschema.  
  
Wenn die Quelle oder Ziel-datenbankverbindung wird nicht vor dem Ausführen dieses Befehls ausgeführt, oder die Verbindung mit der Quelle oder Ziel-Datenbank-Server ein Fehler, während der Ausführung des Befehls auftritt, wird ein Fehler generiert, und die Konsolenanwendung wird beendet.  
  
-   `conversion-report-folder:` Gibt an, Ordner, in denen der Bewertungsbericht gespeichert werden kann. (optionales Attribut)  
  
-   `object-name:` Gibt an, die Quell-Objekte, die für das Konvertieren eines Schemas (unterstützt das einzelne Objektnamen oder einen Gruppennamen für das Objekt) in Betracht gezogen.  
  
-   `object-type:` Gibt den Typ des Objekts (sofern es sich um eine Objektkategorie angegeben wird, dann ist "Category" Objekttyp) im Objekt-Name-Attribut hingewiesen.  
  
-   `conversion-report-overwrite:` Gibt an, ob den Berichtsordner für die Bewertung zu überschreiben, wenn sie bereits vorhanden ist.  
  
    **Standardwert:** "false". (optionales Attribut)  
  
-   `write-summary-report-to:` Gibt den Pfad, an dem der zusammenfassende Bericht generiert wird.  
  
    Wenn nur der Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **SchemaConversionReport&lt;n&gt;. XML** erstellt wird. (optionales Attribut)  
  
    Erstellen von Berichten verfügt über zwei weitere Unterkategorien:  
  
    -   `report-errors` (= "True/False", Standardwert "false" (optionale Attribute))  
  
    -   `verbose` (= "True/False", Standardwert "false" (optionale Attribute))  
  
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
  
-   `object-name:` Gibt an, die Source-Objekte, die für die Migration als Daten (einzelne unterstützt-Objektnamen oder einen Gruppennamen für das Objekt).  
  
-   `object-type:` Gibt den Typ des Objekts (sofern es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie") im Objekt-Name-Attribut hingewiesen.  
  
-   `write-summary-report-to:` Gibt den Pfad, an dem der Bericht generiert wird.  
  
    Wenn nur der Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **DataMigrationReport&lt;n&gt;. XML** erstellt wird. (optionales Attribut)  
  
    Erstellen von Berichten verfügt über zwei weitere Unterkategorien:  
  
    -   `report-errors` (= "True/False", Standardwert "false" (optionale Attribute))  
  
    -   `verbose` (= "True/False", Standardwert "false" (optionale Attribute))  
  
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
  
## <a name="migration-preparation-command"></a>Vorbereitung der Migrationsbefehl  
Der Befehl Vorbereiten der Migration initiiert schemazuordnung zwischen den Quell- und Zieldatenbanken.  
  
> [!NOTE]  
> Die Ausgabe der Standard-Konsole, die Einstellung für die migrationsbefehle ist 'Full' Ausgabebericht mit keine ausführliche berichterstellung: Nur Zusammenfassung am Stammknoten Source-Objekt-Struktur.  
  
### <a name="map-schema"></a>Map-schema  
Dieser Befehl stellt die schemazuordnung von der Quelldatenbank mit dem Zielschema.  
  
-   `source-schema` Gibt das Quellschema aus, um zu migrieren.  
  
-   `sql-server-schema` Gibt an, das Zielschema auf das Schema der Datenquelle migriert werden.  
  
**Syntaxbeispiel:**  
  
```xml  
<map-schema source-schema="<source-schema>"  
  
sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-commands"></a>Verwaltbarkeit-Befehle  
Die Verwaltbarkeit Befehle helfen, die Ziel-Datenbankobjekte mit der Quelldatenbank zu synchronisieren.  
  
> [!NOTE]  
> Die Ausgabe der Standard-Konsole, die Einstellung für die migrationsbefehle ist 'Full' Ausgabebericht mit keine ausführliche berichterstellung: Nur Zusammenfassung am Stammknoten Source-Objekt-Struktur.  
  
### <a name="synchronize-target"></a>Synchronisieren von Ziel  
Mit diesem Befehl wird die Zielobjekte mit der Zieldatenbank synchronisiert.  
 
Wenn dieser Befehl für die Quelldatenbank ausgeführt wird, wird ein Fehler aufgetreten.  
  
Wenn die Verbindung mit der Zieldatenbank wird nicht ausgeführt, bevor Sie diesen Befehl ausführen oder die Verbindung mit dem Datenbank-Zielserver ein Fehler auftritt, während der Ausführung des Befehls, wird ein Fehler generiert, und die Konsolenanwendung beendet.  
  
-   `object-name:` Gibt an, die Ziel-Objekte, die für die Synchronisierung mit der Zieldatenbank (unterstützt das einzelne Objektnamen oder einen Gruppennamen für das Objekt) in Betracht gezogen.  
  
-   `object-type:` Gibt den Typ des Objekts (sofern es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie") im Objekt-Name-Attribut hingewiesen.  
  
-   `on-error:` Gibt an, ob die Synchronisierungsfehler als Warnungen oder Fehler angegeben. Verfügbare Optionen für in-Fehler:  
  
    -   Bericht insgesamt als Warnung  
  
    -   Bericht-each-als-Warnung  
  
    -   Fehler-Skript  
  
-   `report-errors-to:` Gibt Speicherort der Fehlerbericht für den Synchronisierungsvorgang (optionales Attribut). Wenn nur Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **TargetSynchronizationReport.XML** erstellt wird.  
  
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
  
### <a name="refresh-from-database"></a>Refresh-aus-Datenbank  
Dieser Befehl aktualisiert die Quellobjekte in der Datenbank.  
  
Wenn dieser Befehl für die Zieldatenbank ausgeführt wird, wird ein Fehler generiert.  
  
Dieser Befehl erfordert einen oder mehrere Metabase-Knoten als Befehlszeilenparameter an.  
  
-   `object-name:` Gibt an, die Quell-Objekte, die für die Aktualisierung aus der Quelldatenbank (unterstützt das einzelne Objektnamen oder einen Gruppennamen für das Objekt) in Betracht gezogen.  
  
-   `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
-   `on-error:` Gibt an, ob Aktualisierung Fehler als Warnungen oder Fehler aufgerufen. Verfügbare Optionen für in-Fehler:  
  
    -   Bericht insgesamt als Warnung  
  
    -   Bericht-each-als-Warnung  
  
    -   Fehler-Skript  
  
-   `report-errors-to:` Gibt Speicherort der Fehlerbericht für den Aktualisierungsvorgang (optionales Attribut). Wenn nur Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **SourceDBRefreshReport.XML** erstellt wird.  
  
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
  
## <a name="script-generation-commands"></a>Befehle des Skripts generieren  
Dual-Aufgaben mit die Befehle für die Generierung von Skripts: sie helfen, speichern Sie die Konsolenausgabe in einer Skriptdatei, und notieren Sie die T-SQL-Ausgabe in der Konsole oder eine Datei, die auf Grundlage des Parameters, die Sie angeben.  
  
### <a name="save-as-script"></a>Save-als-script  
Mit diesem Befehl wird zum Speichern der Skripts für die Objekte in eine Datei bereits erwähnt, wenn Metabase = Target. Dies ist eine Alternative zum Befehl zur abonnementsynchronisierung, wir der Skripts abrufen, und führen Sie in der Zieldatenbank identisch.  
  
Dieser Befehl erfordert einen oder mehrere Metabase-Knoten als Befehlszeilenparameter an.  
  
-   `object-name:` Gibt an, die Objekte, deren Skripts werden (unterstützt das einzelne Objektnamen oder einen Gruppennamen für das Objekt) gespeichert werden soll.  
  
-   `object-type:` Gibt den Typ des Objekts (sofern es sich um eine Objektkategorie angegeben wird, dann ist "Category" Objekttyp) im Objekt-Name-Attribut hingewiesen.  
  
-   `metabase:` Gibt an, ob sie die Quelle oder Ziel der Metabasis.  
  
-   `destination:` Gibt den Pfad oder den Ordner, in dem das Skript gespeichert werden muss. Wenn der Dateiname nicht angegeben ist, wird ein Dateiname in der .out Format (Object_name-Attribut-Wert) angegeben werden.
  
-   `overwrite:` True gibt an, überschreibt es die gleiche Dateinamen, falls es vorhanden ist. Sie haben die Werte (True/False).  
  
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
  
### <a name="convert-sql-statement"></a>Convert-Sql-Anweisung
Dieser Befehl konvertiert die SQL-Anweisung.  
  
-   `context` Gibt den Schemanamen an.  
  
-   `destination` Gibt an, ob die Ausgabe in einer Datei gespeichert werden sollen.  
  
    Wenn dieses Attribut nicht angegeben ist, wird die konvertierte T-SQL-Anweisung in der Konsole angezeigt. (optionales Attribut)  
  
-   `conversion-report-folder` Gibt den Ordner, in dem der Bewertungsbericht gespeichert werden kann. (optionales Attribut)  
  
-   `conversion-report-overwrite` Gibt an, ob den Berichtsordner für die Bewertung zu überschreiben, wenn sie bereits vorhanden ist.  
  
    **Standardwert:** "false". (optionales Attribut)  
  
-   `write-converted-sql-to` Gibt an, die Datei Ordnerpfad (oder), die das konvertierte T-SQL gespeichert werden sollen. Wenn ein Pfad angegeben wird, zusammen mit den `sql-files` -Attribut, jede Quelldatei verfügt über eine entsprechende Ziel T-SQL-Datei, die unter den angegebenen Ordner erstellt. Wenn ein Pfad angegeben wird, zusammen mit den `sql` -Attribut, das konvertierte T-SQL wird in einer Datei namens Result.out unter den angegebenen Ordner geschrieben.  
  
-   `sql` Gibt an, die Sybase-Sql-Anweisungen konvertiert werden soll, eine oder mehrere Anweisungen können getrennt werden, mithilfe einer ";"  
  
-   `sql-files` Gibt den Pfad der Sql-Dateien, die in T-SQL-Code konvertiert werden.  
  
-   `write-summary-report-to` Gibt den Pfad, in dem der zusammenfassende Bericht generiert wird. Wenn nur der Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **ConvertSQLReport.XML** erstellt wird. (optionales Attribut)  
  
    Zusammenfassungsbericht erstellen, weist zwei weitere Unterkategorien, nämlich:  
  
    -   Fehlerberichte (= "True/False", mit dem Standardwert "False" (optionale Attribute)).  
  
    -   Verbose (= "True/False", Standardwert "false" (optionale Attribute)).  
  
Dieser Befehl erfordert einen oder mehrere Metabase-Knoten als Befehlszeilenparameter an.  
  
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
Weitere Informationen zu den Befehlszeilenoptionen finden Sie unter [Befehlszeilenoptionen in der SSMA-Konsole (AccessToSQL)](../access/command-line-options-in-ssma-console-accesstosql.md).  
  
Informationen dazu, eine Konsole-Beispielskriptdatei, finden Sie unter [arbeiten mit den Beispielskriptdateien der Konsole &#40;SybaseToSQL&#41;](../../ssma/sybase/working-with-the-sample-console-script-files-sybasetosql.md)  
  
Der nächste Schritt hängt davon ab, auf die Anforderungen Ihres Projekts:  
  
-   Für die Angabe eines Kennworts oder das Exportieren / Importieren von Kennwörtern, finden Sie unter [Verwalten von Kennwörtern &#40;SybaseToSQL&#41;](../../ssma/sybase/managing-passwords-sybasetosql.md).  
  
-   Generieren von Berichten finden Sie unter [Generieren von Berichten &#40;SybaseToSQL&#41;](../../ssma/sybase/generating-reports-sybasetosql.md).  
  
-   Behandlung von Problemen in der Konsole, finden Sie unter [Problembehandlung &#40;SybaseToSQL&#41;](../../ssma/sybase/troubleshooting-sybasetosql.md).  
  
