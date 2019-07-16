---
title: Executing the SSMA Console ausführen (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ce63f633-067d-4f04-b8e9-e1abd7ec740b
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 64348e33502e8407e567b8901890246344765f4f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989684"
---
# <a name="executing-the-ssma-console-db2tosql"></a>Executing the SSMA Console ausführen (DB2ToSQL)
Microsoft bietet einen robusten Satz von Skript Befehle zum Ausführen und Steuerungsaktivitäten SSMA Datei. Die folgenden Abschnitte enthalten Informationen identisch. Die Konsolenanwendung verwendet bestimmte standard Skriptbefehle für die Datei als aufgelisteten, in diesem Abschnitt.  
  
## <a name="project-script-file-commands"></a>Project-Datei-Skriptbefehle  
Die Projekt-Befehle verarbeiten, erstellen Projekte öffnen, speichern und Beenden von Projekten.  
  
**Befehl**  
  
Neues-Projekt erstellen  
  
Erstellt ein neues SSMA-Projekt an.  
  
**Skript**  
  
-   `project-folder` Gibt den Ordner des Projekts erstellt.  
  
-   `project-name` Gibt den Namen des Projekts. {string}  
  
-   `overwrite-if-exists`Optionales Attribut gibt an, ob ein vorhandenes Projekt überschrieben werden soll. {Boolean}  
  
-   `project-type:`Optionales Attribut. Gibt den Projekttyp z. B. "Sql Server 2005" Projekt oder "Sql Server 2008", Projekt oder "Sql Server 2012", Projekt oder "Sql Server 2014", Projekt oder "Sql Azure". Der Standardwert ist "Sql Server 2014".  
  
**Beispiel:**  
  
```xml  
<create-new-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
   overwrite-if-exists="<true/false>"   (optional)  
  
   project-type="<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014>"   (optional)  
  
/>  
```  
Attribut "überschreiben-If-exists" **"false"** standardmäßig.  
  
'Project-Type'-Attribut ist **Sql-Server-2008** standardmäßig.  
  
**Befehl**  
  
Open-Projekt  
  
Öffnet ein vorhandenes Projekt.  
  
**Skript**  
  
-   `project-folder` Gibt den Ordner des Projekts erstellt. Der Befehl schlägt fehl, wenn der angegebene Ordner nicht vorhanden ist.  {string}  
  
-   `project-name` Gibt den Namen des Projekts. Der Befehl schlägt fehl, wenn das angegebene Projekt nicht vorhanden ist.  {string}  
  
**Syntaxbeispiel:**  
  
```xml  
<open-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
/>  
```  
SSMA für DB2-Konsolenanwendung unterstützt die Abwärtskompatibilität zu gewährleisten. Sie werden können zum Öffnen von Projekten, die mit früheren Version von SSMA erstellt.  
  
**Befehl**  
  
Save-Projekt  
  
Speichert das Migrationsprojekt.  
  
**Skript**  
  
**Syntaxbeispiel:**  
  
```xml  
<save-project/>  
```  
**Befehl**  
  
Close-Projekt  
  
Schließt das Migrationsprojekt.  
  
**Skript**  
  
**Syntaxbeispiel:**  
  
```xml  
<close-project  
  
   if-modified="<save/error/ignore>"   (optional)  
  
/>  
```  
  
## <a name="database-connection-script-file-commands"></a>Datenbank-Verbindung Datei Skriptbefehle  
Die Verbindung mit Datenbank-Befehle können mit der Datenbank herstellen.  
  
-   Die **Durchsuchen** Feature der Benutzeroberfläche wird in der Konsole nicht unterstützt.  
  
-   Weitere Informationen zu "Erstellen von Skriptdateien", finden Sie unter [Skriptdateien erstellen &#40;OracleToSQL&#41;](../../ssma/oracle/creating-script-files-oracletosql.md).  
  
**Befehl**  
  
Connect-Source-Datenbank  
  
-   Führt die Verbindung mit der Quelldatenbank und lädt die Metadaten für die hohe auf die Quelldatenbank, aber nicht alle Metadaten.  
  
-   Wenn die Verbindung mit der Datenquelle hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung  
  
**Skript**  
  
Server-Definition wird aus dem Namensattribut für jede Verbindung im Server-Abschnitt, der die Server-Verbindungsdatei oder die Skriptdatei definiert abgerufen.  
  
**Syntaxbeispiel:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
**Befehl**  
  
-Force-Last-Quelle/Ziel-database  
  
-   Lädt die Metadaten der Datenquelle.  
  
-   Nützlich für das Migrationsprojekt offline arbeiten.  
  
-   Wenn die Verbindung mit der Quelle/Ziel kann nicht hergestellt werden, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung  
  
**Skript**  
  
Ist eine oder mehrere Metabase-Knoten als Befehlszeilenparameter erforderlich.  
  
**Syntaxbeispiel:**  
  
```xml  
<force-load object-name="<object-name>"  
  
  metabase="<source/target>"/>  
```  
oder  
  
```xml  
<force-load>  
  
   <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Befehl**  
  
Verbindung-Source-Datenbank  
  
-   Verbindung mit der Quelldatenbank, aber keine Metadaten im Gegensatz zu den Connect-Source-Database-Befehl wird nicht geladen.  
  
-   Ein Fehler wird generiert, wenn die Verbindung mit der Datenquelle hergestellt werden kann, und die Konsolenanwendung beendet die Ausführung weiter.  
  
**Skript**  
  
**Syntaxbeispiel:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Befehl**  
  
Connect-Zieldatenbank  
  
-   SQL Server-Zieldatenbank her, und high Level Metadaten der Zieldatenbank, aber nicht die Metadaten vollständig geladen.  
  
-   Wenn die Verbindung mit dem Ziel hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung weiter beendet die Ausführung.  
  
**Skript**  
  
Definition des Servers wird aus dem Namensattribut für jede Verbindung im Server-Abschnitt, der die Server-Verbindungsdatei oder die Skriptdatei definiert abgerufen werden.  
  
**Syntaxbeispiel:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Befehl**  
  
Verbindung-Zieldatenbank  
  
-   Verbindung mit der Zieldatenbank, aber alle Metadaten, im Gegensatz zu den Connect-Ziel-Database-Befehl wird nicht geladen.  
  
-   Ein Fehler wird generiert, wenn die (Verbindung mit dem Ziel erneut) hergestellt werden kann, und die Konsolenanwendung beendet die Ausführung weiter.  
  
**Skript**  
  
**Syntaxbeispiel:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file-commands"></a>Berichtsbefehle Skript-Datei  
Die Berichtsserver-Befehle Generieren von Berichten auf die Leistung der verschiedenen Aktivitäten von SSMA-Konsole.  
  
**Befehl**  
  
Generieren von Bewertungsbericht  
  
-   Der Bewertungsberichte für die Quelldatenbank erstellt.  
  
-   Wenn die Verbindung mit der Quelldatenbank nicht ausgeführt werden, bevor Sie diesen Befehl ausführen, wird ein Fehler generiert, und die Konsolenanwendung wird beendet.  
  
-   Fehler bei der Ausführung des Befehls, der eine Verbindung mit dem Quellserver für die Datenbank auch führt zum Beenden der Konsolenanwendung.  
  
**Skript**  
  
-   `conversion-report-folder:` Gibt an, Ordner, in dem der Bewertungsbericht kann gespeichert werden. (optionales Attribut)  
  
-   `object-name:` Gibt an, die Objekte, die für die Bewertung der berichtgenerierung (es kann zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt haben) in Betracht gezogen.  
  
-   `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
-   `conversion-report-overwrite:` Gibt an, ob den Berichtsordner für die Bewertung zu überschreiben, wenn sie bereits vorhanden ist.  
  
    **Standardwert:** "false". (optionales Attribut)  
  
-   `write-summary-report-to:` Gibt den Pfad, in dem der zusammenfassende Bericht generiert wird.  
  
    Wenn nur der Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **AssessmentReport&lt;n&gt;. XML** erstellt wird. (optionales Attribut)  
  
    Erstellen von Berichten verfügt über zwei weitere Unterkategorien:  
  
    -   `report-errors` (= "True/False", Standardwert "false" (optionale Attribute))  
  
    -   `verbose` (= "True/False", Standardwert "false" (optionale Attribute))  
  
**Syntaxbeispiel:**  
  
```xml  
<generate-assessment-report  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   write-summary-report-to="<file>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   assessment-report-folder="<folder-name>"   (optional)  
  
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
  
## <a name="migration-script-file-commands"></a>Skript-Datei-Migrationsbefehle  
Die migrationsbefehle Schema der Zieldatenbank, die dem Quellschema zu konvertieren und Migrieren von Daten auf dem Zielserver. Die Ausgabe der Standard-Konsole, die Einstellung für die migrationsbefehle ist 'Full' Ausgabebericht mit keine ausführliche berichterstellung: Nur Zusammenfassung am Stammknoten Source-Objekt-Struktur.  
  
**Befehl**  
  
Convert-schema  
  
-   Führt die schemakonvertierung aus der Quelle in das Zielschema.  
  
-   Wenn die Quelle oder Ziel-datenbankverbindung wird nicht vor dem Ausführen dieses Befehls ausgeführt, oder die Verbindung mit der Quelle oder Ziel-Datenbank-Server ein Fehler, während der Ausführung des Befehls auftritt, wird ein Fehler generiert, und die Konsolenanwendung wird beendet.  
  
**Skript**  
  
-   `conversion-report-folder:` Gibt an, Ordner, in dem der Bewertungsbericht kann gespeichert werden. (optionales Attribut)  
  
-   `object-name:` Gibt an, die Quell-Objekte, die für das Konvertieren eines Schemas (es kann zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt haben) in Betracht gezogen.  
  
-   `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
-   `conversion-report-overwrite:` Gibt an, ob den Berichtsordner für die Bewertung zu überschreiben, wenn sie bereits vorhanden ist.  
  
    **Standardwert:** "false". (optionales Attribut)  
  
-   `write-summary-report-to:` Gibt den Pfad, in dem der zusammenfassende Bericht generiert wird.  
  
    Wenn nur der Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **SchemaConversionReport&lt;n&gt;. XML** erstellt wird. (optionales Attribut)  
  
    Erstellen von Berichten verfügt über zwei weitere Unterkategorien:  
  
    -   `report-errors` (= "True/False", Standardwert "false" (optionale Attribute))  
  
    -   `verbose` (= "True/False", Standardwert "false" (optionale Attribute))  
  
**Syntaxbeispiel:**  
  
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
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</convert-schema>  
```  
**Befehl**  
  
Migrieren von Daten: Werden die Quelldaten zum Ziel migriert.  
  
**Skript**  
  
-   `conversion-report-folder:` Gibt an, Ordner, in dem der Bewertungsbericht kann gespeichert werden. (optionales Attribut)  
  
-   `object-name:` Gibt an, die Source-Objekte, die für die Migration als Daten (es kann zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt).  
  
-   `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
-   `conversion-report-overwrite:` Gibt an, ob den Berichtsordner für die Bewertung zu überschreiben, wenn sie bereits vorhanden ist.  
  
    **Standardwert:** "false". (optionales Attribut)  
  
-   `write-summary-report-to:` Gibt den Pfad, in dem der zusammenfassende Bericht generiert wird.  
  
    Wenn nur der Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **DataMigrationReport&lt;n&gt;. XML** erstellt wird. (optionales Attribut)  
  
    Erstellen von Berichten verfügt über zwei weitere Unterkategorien:  
  
    -   `report-errors` (= "True/False", Standardwert "false" (optionale Attribute))  
  
    -   `verbose` (= "True/False", Standardwert "false" (optionale Attribute))  
  
**Syntaxbeispiel:**  
  
```xml  
<migrate-data  
  
   write-summary-report-to="<file-name/folder-name>"  
  
   report-errors="<true/false>"  
  
   verbose="<true/false>">  
  
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
  
   report-errors="<true/false>"  
  
   verbose="<true/false>"/>  
```  
  
## <a name="migration-preparation-script-file-commands"></a>Vorbereitung der Skript-Datei Migrationsbefehle  
Der Befehl Vorbereiten der Migration initiiert schemazuordnung zwischen den Quell- und Zieldatenbanken.  
  
**Befehl**  
  
Map-schema  
  
Schemazuordnung der Quelldatenbank mit dem Zielschema.  
  
**Skript**  
  
-   `source-schema` Gibt das Schema der Datenquelle, die, das wir migrieren möchten.  
  
-   `sql-server-schema` Gibt das Zielschema, das sie migriert werden soll.  
  
**Syntaxbeispiel:**  
  
```xml  
<map-schema  
  
   source-schema="<source-schema>"  
  
   sql-server-schema="<target-schema>"/>  
```  
**Befehl**  
  
Map-schema  
  
Schemazuordnung der Quelldatenbank mit dem Zielschema.  
  
**Skript**  
  
`source-schema` Gibt das Schema der Datenquelle, die, das wir migrieren möchten.  
  
`sql-server-schema` Gibt das Zielschema, das sie migriert werden soll.  
  
**Syntaxbeispiel:**  
  
```xml  
<map-schema  
  
   source-schema="<source-schema>"  
  
   sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-script-file-commands"></a>Datei-Skriptbefehle Verwaltbarkeit  
Die Verwaltbarkeit Befehle helfen, die Ziel-Datenbankobjekte mit der Quelldatenbank zu synchronisieren.  
  
Die Ausgabe der Standard-Konsole, die Einstellung für die migrationsbefehle ist 'Full' Ausgabebericht mit keine ausführliche berichterstellung: Nur Zusammenfassung am Stammknoten Source-Objekt-Struktur.  
  
**Befehl**  
  
Synchronisieren von Ziel  
  
-   Synchronisiert die Zielobjekte mit der Zieldatenbank an.  
  
-   Wenn dieser Befehl für die Quelldatenbank ausgeführt wird, wird ein Fehler aufgetreten.  
  
-   Wenn die Verbindung mit der Zieldatenbank wird nicht ausgeführt, bevor Sie diesen Befehl ausführen oder die Verbindung mit dem Datenbank-Zielserver ein Fehler auftritt, während der Ausführung des Befehls, wird ein Fehler generiert, und die Konsolenanwendung beendet.  
  
**Skript**  
  
-   `object-name:` Gibt an, die Ziel-Objekte, die für die Synchronisierung mit der Zieldatenbank (es kann zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt haben) in Betracht gezogen.  
  
-   `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
-   `on-error:` Gibt an, ob die Synchronisierungsfehler als Warnungen oder Fehler angegeben. Verfügbare Optionen für in-Fehler:  
  
    -   Bericht insgesamt als Warnung  
  
    -   Bericht-each-als-Warnung  
  
    -   Fehler-Skript  
  
-   `report-errors-to:` Speicherort der Fehlerbericht angibt, für der Synchronisierungsvorgang (optionales Attribut), wenn nur Ordnerpfad angegeben wird, klicken Sie dann Datei anhand des Namens **TargetSynchronizationReport.XML** erstellt wird.  
  
**Syntaxbeispiel:**  
  
```xml  
<synchronize-target  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name/folder-name>"   (optional)  
  
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
  
Refresh-aus-Datenbank  
  
-   Aktualisiert die Source-Objekte aus der Datenbank.  
  
-   Wenn dieser Befehl für die Zieldatenbank ausgeführt wird, wird ein Fehler generiert.  
  
**Skript**  
  
Ist eine oder mehrere Metabase-Knoten als Befehlszeilenparameter erforderlich.  
  
-   `object-name:` Gibt an, die Quell-Objekte, die für die Aktualisierung aus der Quelldatenbank (es kann zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt haben) in Betracht gezogen.  
  
-   `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
-   `on-error:` Gibt an, ob die datenaktualisierung Fehler als Warnungen oder Fehler angegeben. Verfügbare Optionen für in-Fehler:  
  
    -   Bericht insgesamt als Warnung  
  
    -   Bericht-each-als-Warnung  
  
    -   Fehler-Skript  
  
-   `report-errors-to:` Speicherort der Fehlerbericht angibt, für der Aktualisierungsvorgang (optionales Attribut), wenn nur Ordnerpfad angegeben wird, klicken Sie dann Datei anhand des Namens **SourceDBRefreshReport.XML** erstellt wird.  
  
**Syntaxbeispiel:**  
  
```xml  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   on-error="<report-total-as-warning/  
  
               report-each-as-warning/  
  
               fail-script>"   (optional)  
  
   report-errors-to="<file-name/folder-name>"   (optional)  
  
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
  
## <a name="script-generation-script-file-commands"></a>Skript generieren-Skriptbefehle für Datei  
Die Generierung des Datenupdateskripts-Befehle führen zwei Aufgaben aus: Sie helfen, speichern Sie die Konsolenausgabe in einer Skriptdatei; und zeichnen Sie die T-SQL-Ausgabe in der Konsole oder eine Datei, die auf Grundlage des Parameters, die Sie angeben.  
  
**Befehl**  
  
Save-als-script  
  
Speichern die Skripts für die Objekte in einer Datei, die bereits erwähnt, wenn zum Metabase = Ziel, dies ist eine Alternative zum Befehl zur abonnementsynchronisierung in wir Abrufen der Skripts und führen Sie in der Zieldatenbank identisch.  
  
**Skript**  
  
Ist eine oder mehrere Metabase-Knoten als Befehlszeilenparameter erforderlich.  
  
-   `object-name:` Gibt an, die Objekte, deren Skripts sind, gespeichert werden soll. (sie können einzelne Objektnamen oder einen Gruppennamen für das Objekt haben)  
  
-   `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
-   `metabase:` Gibt an, ob sie die Quelle oder Ziel der Metabasis.  
  
-   `destination:` Gibt den Pfad oder den Ordner, in dem das Skript muss gespeichert werden, wenn der Dateiname nicht klicken Sie dann einen Dateinamen in das Format (Attributwert Object_name) .out angegeben ist  
  
-   `overwrite:` Bei "true" überschreibt es Wenn gleichen Dateinamen vorhanden. Sie haben die Werte (True/False).  
  
**Syntaxbeispiel:**  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   object-name="<object-name>"  
  
   object-type="<object-category>"  
  
   destination="<file/folder>"  
  
   overwrite="<true/false>"   (optional)  
  
/>  
```  
oder  
  
```xml  
<save-as-script  
  
   metabase="<source/target>"  
  
   destination="<file/folder>"  
  
      <metabase-object object-name="<object-name>"  
  
         object-type="<object-category>"/>  
  
</save-as-script>  
```  
**Befehl**  
  
Convert-Sql-Anweisung  
  
-   `context` Gibt den Schemanamen an.  
  
-   `destination` Gibt an, ob die Ausgabe in einer Datei gespeichert werden sollen.  
  
    Wenn dieses Attribut nicht angegeben ist, wird die konvertierte T-SQL-Anweisung in der Konsole angezeigt. (optionales Attribut)  
  
-   `conversion-report-folder` Gibt an, Ordner, in dem der Bewertungsbericht kann gespeichert werden. (optionales Attribut)  
  
-   `conversion-report-overwrite` Gibt an, ob den Berichtsordner für die Bewertung zu überschreiben, wenn sie bereits vorhanden ist.  
  
    **Standardwert:** "false". (optionales Attribut)  
  
-   `write-converted-sql-to` Gibt an, die Datei Ordnerpfad, in dem das konvertierte T-SQL ist, gespeichert werden (oder). Wenn ein Pfad angegeben wird, zusammen mit den `sql-files` -Attribut, wird jede Quelldatei eine entsprechende Ziel T-SQL-Datei, die unter den angegebenen Ordner erstellt haben. Wenn ein Pfad angegeben wird, zusammen mit den `sql` Attribut, das konvertierte T-SQL geschrieben, in eine Datei namens **Result.out** unter den angegebenen Ordner.  
  
-   `sql` Gibt an, die DB2-Sql-Anweisungen konvertiert werden soll, eine oder mehrere Anweisungen können getrennt werden, mithilfe einer ";"  
  
-   `sql-files` Gibt den Pfad der Sql-Dateien, die in T-SQL-Code konvertiert werden.  
  
-   `write-summary-report-to` Gibt den Pfad, in dem der Bericht generiert wird. Wenn nur der Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **ConvertSQLReport.XML** erstellt wird. (optionales Attribut)  
  
    Bericht Erstellung hat 2 Unterkategorien, viz weiter..,:  
  
    -   Fehlerberichte (= "True/False", mit dem Standardwert "False" (optionale Attribute)).  
  
    -   Verbose (= "True/False", Standardwert "false" (optionale Attribute)).  
  
**Skript**  
  
Ist eine oder mehrere Metabase-Knoten als Befehlszeilenparameter erforderlich.  
  
**Syntaxbeispiel:**  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>"   (optional)  
  
   verbose="<true/false>"   (optional)  
  
   report-errors="<true/false>"   (optional)  
  
   destination="<stdout/file>"   (optional)  
  
   file-name="<file-name>"  
  
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
  
   write-summary-report-to="<file-name/folder-name>" (optional)  
  
   verbose="<true/false>" (optional)  
  
   report-errors="<true/false>"  
  
   destination="<stdout/file>"   (optional)  
  
   write-converted-sql-to="<file-name/folder-name>"  
  
   sql-files="<folder-name>\*.sql" />  
```  
oder  
  
```  
<convert-sql-statement  
  
   context="<schema-name>"  
  
   conversion-report-folder="<folder-name>"  
  
   conversion-report-overwrite="<true/false>"  
  
   sql-files="<folder-name>\*.sql" />  
```  
  
## <a name="next-step"></a>Nächster Schritt  
Weitere Informationen zu Befehlszeilenoptionen, finden Sie unter [Command Line Options in SSMA-Konsole &#40;DB2ToSQL&#41; ](../../ssma/db2/command-line-options-in-ssma-console-db2tosql.md) .  
  
Weitere Informationen zu den beispielskriptdateien der Konsole, finden Sie unter [arbeiten mit den Beispielskriptdateien der Konsole &#40;DB2ToSQL&#41;](../../ssma/db2/working-with-the-sample-console-script-files-db2tosql.md)  
  
Der nächste Schritt hängt davon ab, auf die Anforderungen Ihres Projekts:  
  
-   Für die Angabe eines Kennworts oder das Exportieren / Importieren von Kennwörtern, finden Sie unter [Verwalten von Kennwörtern &#40;DB2ToSQL&#41;](../../ssma/db2/managing-passwords-db2tosql.md).  
  
-   Generieren von Berichten finden Sie unter [Generieren von Berichten &#40;DB2ToSQL&#41;](../../ssma/db2/generating-reports-db2tosql.md).  
  
-   Behandlung von Problemen in der Konsole, finden Sie unter [Problembehandlung &#40;DB2ToSQL&#41;](../../ssma/db2/troubleshooting-db2tosql.md).  
  
