---
title: Ausführen der SSMA-Konsole (MySQLToSQL)) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 761cb5368c0b586b63f92952f3938d8708daaf86
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63183059"
---
# <a name="executing-the-ssma-console-mysqltosql"></a>Ausführen der SSMA-Konsole (MySqlToSql)
Microsoft bietet einen robusten Satz von Skript Befehle zum Ausführen und Steuerungsaktivitäten SSMA Datei.  
  
Die Konsolenanwendung verwendet bestimmte standard Skriptbefehle für die Datei als aufgelisteten, in diesem Abschnitt.  
  
## <a name="project--script-file-commands"></a>Project-Datei-Skriptbefehle  
**Befehl**  
  
create-new-project:   
                   Erstellt ein neues SSMA-Projekt an.  
  
Die Projekt-Befehle verarbeiten, erstellen Projekte öffnen, speichern und Beenden von Projekten.  
  
**Skript**  
  
1.  `project-folder` Gibt den Ordner des Projekts erstellt.  
  
2.  `project-name` Gibt den Namen des Projekts. {string}  
  
3.  `overwrite-if-exists`Optionales Attribut gibt an, ob ein vorhandenes Projekt überschrieben werden soll. {boolean}  
  
4.  `project-type:`Optionales Attribut. Gibt an, das z. B. "Sql Server 2005" Projekt "Projekttyp" oder "Sql Server 2008" Projekt oder "Sql Server 2012" oder "Sql Server 2014" Projekt oder "Sql Azure". Standardwert ist "Sql Server 2008".  
  
**Syntaxbeispiel:**  
  
```xml  
<create-new-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
   overwrite-if-exists="<true/false>"   (optional)  
  
   project-type=="<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014 | sql-azure>"   (optional)  
  
/>  
```  
Attribut "überschreiben-If-exists" **"false"** standardmäßig.  
  
'Project-Type'-Attribut ist **Sql-Server-2008** standardmäßig.  
  
**Befehl**  
  
Open-Projekt:   
                  Öffnet ein vorhandenes Projekt.  
  
**Skript**  
  
1.  `project-folder` Gibt den Ordner des Projekts erstellt. Der Befehl schlägt fehl, wenn der angegebene Ordner nicht vorhanden ist.  {string}  
  
2.  `project-name` Gibt den Namen des Projekts. Der Befehl schlägt fehl, wenn das angegebene Projekt nicht vorhanden ist.  {string}  
  
**Syntaxbeispiel:**  
  
```xml  
<open-project  
  
   project-folder="<project-folder>"  
  
   project-name="<project-name>"  
  
/>  
```  
> [!IMPORTANT]  
> SSMA für MySQL-Konsolenanwendung unterstützt die Abwärtskompatibilität zu gewährleisten. Sie werden können zum Öffnen von Projekten, die mit früheren Version von SSMA erstellt.  
  
**Befehl**  
  
Save-Projekt: Speichert das Migrationsprojekt.  
  
**Skript**  
  
**Syntaxbeispiel:**  
  
```xml  
<save-project/>  
```  
**Befehl**  
  
Close-Projekt  
                  decodiert werden: Schließt das Migrationsprojekt.  
  
**Skript**  
  
**Syntaxbeispiel:**  
  
```xml  
<save-project/>  
```  
**Befehl**  
  
Close-Projekt  
                  decodiert werden: Schließt das Migrationsprojekt.  
  
**Skript**  
  
**Syntaxbeispiel:**  
  
```xml  
<close-project  
  
   if-modified="<save/error/ignore>"   (optional)  
  
/>  
```  
'If-modified'-Attribut ist optional, **ignorieren** standardmäßig.  
  
## <a name="database-connection-script-file-commands"></a>Datenbank-Verbindung Datei Skriptbefehle  
Die Verbindung mit Datenbank-Befehle können mit der Datenbank herstellen.  
  
1.  Die **Durchsuchen** Feature der Benutzeroberfläche wird in der Konsole nicht unterstützt.  
  
2.  Die **Windows-Authentifizierung** und **Port** Parameter sind nicht anwendbar, Herstellen der Verbindung mit SQL Azure.  
  
3.  Weitere Informationen zu "Erstellen von Skriptdateien", finden Sie unter [Skriptdateien erstellen &#40;MySQLToSQL&#41;](../../ssma/mysql/creating-script-files-mysqltosql.md).  
  
**Befehl**  
  
connect-source-database  
  
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
<force-load metabase="<source/target>"  
  
      <metabase-object object-name="<object-name>"/>  
  
</force-load>  
```  
**Befehl**  
  
reconnect-source-database  
  
1.  Verbindung mit der Quelldatenbank, aber keine Metadaten im Gegensatz zu den Connect-Source-Database-Befehl wird nicht geladen.  
  
2.  Ein Fehler wird generiert, wenn die Verbindung mit der Datenquelle hergestellt werden kann, und die Konsolenanwendung beendet die Ausführung weiter.  
  
**Skript**  
  
**Syntaxbeispiel:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```  
**Befehl**  
  
connect-target-database  
  
1.  Stellt eine Verbindung her, in die Zieldatenbank für SQL Server oder SQL Azure und high Level Metadaten der Zieldatenbank, aber nicht die Metadaten vollständig geladen.  
  
2.  Wenn die Verbindung mit dem Ziel hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung weiter beendet die Ausführung.  
  
**Skript**  
  
Definition des Servers wird aus dem Namensattribut für jede Verbindung im Server-Abschnitt, der die Server-Verbindungsdatei oder die Skriptdatei definiert abgerufen werden.  
  
**Syntaxbeispiel:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  
**Befehl**  
  
reconnect-target-database  
  
1.  Verbindung mit der Zieldatenbank, aber alle Metadaten, im Gegensatz zu den Connect-Ziel-Database-Befehl wird nicht geladen.  
  
2.  Ein Fehler wird generiert, wenn die (Verbindung mit dem Ziel erneut) hergestellt werden kann, und die Konsolenanwendung beendet die Ausführung weiter.  
  
**Skript**  
  
**Syntaxbeispiel:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  
  
## <a name="report-script-file-commands"></a>Berichtsbefehle Skript-Datei  
Die Berichtsserver-Befehle Generieren von Berichten auf die Leistung der verschiedenen Aktivitäten von SSMA-Konsole.  
  
**Befehl**  
  
Generieren von Bewertungsbericht  
  
1.  Der Bewertungsberichte für die Quelldatenbank erstellt.  
  
2.  Wenn die Verbindung mit der Quelldatenbank nicht ausgeführt werden, bevor Sie diesen Befehl ausführen, wird ein Fehler generiert, und die Konsolenanwendung wird beendet.  
  
3.  Fehler bei der Ausführung des Befehls, der eine Verbindung mit dem Quellserver für die Datenbank auch führt zum Beenden der Konsolenanwendung.  
  
**Skript**  
  
1.  `assessment-report-folder:` Gibt an, Ordner, in dem der Bewertungsbericht kann gespeichert werden. (optionales Attribut)  
  
2.  `object-name:` Gibt an, die Objekte, die für die Bewertung der berichtgenerierung (sie können einzelne Objektnamen oder einen Gruppennamen für das Objekt haben) in Betracht gezogen.  
  
3.  `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
4.  `assessment-report-overwrite:` Gibt an, ob den Berichtsordner für die Bewertung zu überschreiben, wenn sie bereits vorhanden ist.  
  
    **Standardwert:** "false". (optionales Attribut)  
  
5.  `write-summary-report-to:` Gibt den Pfad, in dem der zusammenfassende Bericht generiert wird.  
  
    Wenn nur der Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **AssessmentReport&lt;n&gt;. XML** erstellt wird. (optionales Attribut)  
  
    Erstellen von Berichten verfügt über zwei weitere Unterkategorien:  
  
    -   `report-errors` (= "True/False", Standardwert "false" (optionale Attribute))  
  
    -   `verbose` (= "True/False", Standardwert "false" (optionale Attribute))  
  
**Syntaxbeispiel:**  
  
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
  
## <a name="migration--script-file-commands"></a>Skript-Datei-Migrationsbefehle  
Die migrationsbefehle Schema der Zieldatenbank, die dem Quellschema zu konvertieren und Migrieren von Daten auf dem Zielserver.  
  
Die Ausgabe der Standard-Konsole, die Einstellung für die migrationsbefehle ist 'Full' Ausgabebericht mit keine ausführliche berichterstellung: Nur Zusammenfassung am Stammknoten Source-Objekt-Struktur.  
  
**Befehl**  
  
convert-schema  
  
1.  Führt die schemakonvertierung aus der Quelle in das Zielschema.  
  
2.  Wenn die Quelle oder Ziel-datenbankverbindung wird nicht vor dem Ausführen dieses Befehls ausgeführt, oder die Verbindung mit der Quelle oder Ziel-Datenbank-Server ein Fehler, während der Ausführung des Befehls auftritt, wird ein Fehler generiert, und die Konsolenanwendung wird beendet.  
  
**Skript**  
  
1.  `conversion-report-folder:` Gibt an, Ordner, in dem der Bewertungsbericht kann gespeichert werden. (optionales Attribut)  
  
2.  `object-name:` Gibt an, die Objekte, die für das Konvertieren eines Schemas (es kann zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt haben) in Betracht gezogen.  
  
3.  `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
4.  `conversion-report-overwrite:` Gibt an, ob den Berichtsordner für die Bewertung zu überschreiben, wenn sie bereits vorhanden ist.  
  
    **Standardwert:** "false". (optionales Attribut)  
  
5.  `write-summary-report-to:` Gibt den Pfad, in dem der zusammenfassende Bericht generiert wird.  
  
    Wenn nur der Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **SchemaConversionReport&lt;n&gt;. XML** erstellt wird. (optionales Attribut)  
  
    Zusammenfassung der berichtserstellung verfügt über zwei weitere Unterkategorien:  
  
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
  
      <metabase-object object-name="<object-names>"  
  
         object-type="<object-category>"/>  
  
</convert-schema>  
```  
**Befehl**  
  
migrate-data  
  
1.  Werden die Quelldaten zum Ziel migriert.  
  
**Skript**  
  
1.  `object-name:` Gibt an, die Source-Objekte, die für die Migration als Daten (es kann zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt).  
  
2.  `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
3.  `write-summary-report-to:` Gibt den Pfad, in dem der zusammenfassende Bericht generiert wird.  
  
    Wenn nur der Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **DataMigrationReport&lt;n&gt;. XML** erstellt wird. (optionales Attribut)  
  
    Erstellen von Berichten verfügt über zwei weitere Unterkategorien:  
  
    -   `report-errors` (= "True/False", Standardwert "false" (optionale Attribute))  
  
    -   `verbose` (= "True/False", Standardwert "false" (optionale Attribute))  
  
**Syntaxbeispiel:**  
  
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
  
## <a name="migration-preparation-script-file-command"></a>Vorbereitung der Skript-Datei Migrationsbefehl  
Der Befehl Vorbereiten der Migration initiiert schemazuordnung zwischen den Quell- und Zieldatenbanken.  
  
**Befehl**  
  
map-schema  
  
Schemazuordnung der Quelldatenbank mit dem Zielschema.  
  
**Skript**  
  
1.  `source-schema` Gibt das Schema der Datenquelle, die, das wir migrieren möchten.  
  
2.  `sql-server-schema` Gibt das Zielschema, das sie migriert werden soll.  
  
**Syntaxbeispiel:**  
  
```xml  
<map-schema  
  
   source-schema="<source-schema>"  
  
   sql-server-schema="<target-schema>"/>  
```  
  
## <a name="manageability-script-file-commands"></a>Datei-Skriptbefehle Verwaltbarkeit  
Die Verwaltbarkeit Befehle helfen, die Ziel-Datenbankobjekte mit der Quelldatenbank zu synchronisieren.  
  
> [!NOTE]  
> Die Ausgabe der Standard-Konsole, die Einstellung für die migrationsbefehle ist 'Full' Ausgabebericht mit keine ausführliche berichterstellung: Nur Zusammenfassung am Stammknoten Source-Objekt-Struktur.  
  
**Befehl**  
  
Synchronisieren von Ziel  
  
1.  Synchronisiert die Zielobjekte mit der Zieldatenbank an.  
  
2.  Wenn dieser Befehl für die Quelldatenbank ausgeführt wird, wird ein Fehler aufgetreten.  
  
3.  Wenn die Verbindung mit der Zieldatenbank wird nicht ausgeführt, bevor Sie diesen Befehl ausführen oder die Verbindung mit dem Datenbank-Zielserver ein Fehler auftritt, während der Ausführung des Befehls, wird ein Fehler generiert, und die Konsolenanwendung beendet.  
  
**Skript**  
  
1.  `object-name:` Gibt an, die Objekte, die für die Synchronisierung mit der Zieldatenbank (es kann zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt haben) in Betracht gezogen.  
  
2.  `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
3.  `on-error:` Gibt an, ob die Synchronisierungsfehler als Warnungen oder Fehler angegeben. Verfügbare Optionen für in-Fehler:  
  
    -   Bericht insgesamt als Warnung  
  
    -   report-each-as-warning  
  
    -   fail-script  
  
4.  `report-errors-to:` Speicherort der Fehlerbericht angibt, für der Synchronisierungsvorgang (optionales Attribut), wenn nur Ordnerpfad angegeben wird, klicken Sie dann Datei anhand des Namens **TargetSynchronizationReport.XML** erstellt wird.  
  
**Syntaxbeispiel:**  
  
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
  
refresh-from-database  
  
1.  Aktualisiert die Source-Objekte aus der Datenbank.  
  
2.  Wenn dieser Befehl für die Zieldatenbank ausgeführt wird, wird ein Fehler generiert.  
  
**Skript**  
  
1.  `object-name:` Gibt an, die Quell-Objekte, die für die Aktualisierung aus der Quelldatenbank (es kann zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt haben) in Betracht gezogen.  
  
2.  `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
3.  `on-error:` Gibt an, ob die Synchronisierungsfehler als Warnungen oder Fehler angegeben. Verfügbare Optionen für in-Fehler:  
  
    -   Bericht insgesamt als Warnung  
  
    -   report-each-as-warning  
  
    -   fail-script  
  
4.  `report-errors-to:` Speicherort der Fehlerbericht angibt, für der Synchronisierungsvorgang (optionales Attribut), wenn nur Ordnerpfad angegeben wird, klicken Sie dann Datei anhand des Namens **SourceDBRefreshReport.XML** erstellt wird.  
  
Ist eine oder mehrere Metabase-Knoten als Befehlszeilenparameter erforderlich.  
  
**Syntaxbeispiel:**  
  
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
  
## <a name="script-generation-script-file-commands"></a>Skript generieren-Skriptbefehle für Datei  
Die Generierung des Datenupdateskripts-Befehle führen zwei Aufgaben aus: Sie helfen, speichern Sie die Konsolenausgabe in einer Skriptdatei; und zeichnen Sie die T-SQL-Ausgabe in der Konsole oder eine Datei, die auf Grundlage des Parameters, die Sie angeben.  
  
**Befehl**  
  
save-as-script  
  
Speichern die Skripts für die Objekte in einer Datei, die bereits erwähnt, wenn zum Metabase = Ziel, dies ist eine Alternative zum Befehl zur abonnementsynchronisierung in wir Abrufen der Skripts und führen Sie in der Zieldatenbank identisch.  
  
**Skript**  
  
Ist eine oder mehrere Metabase-Knoten als Befehlszeilenparameter erforderlich.  
  
1.  `object-name:` Gibt an, die Objekte, deren Skripts sind, gespeichert werden soll. (Es kann zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt haben)  
  
2.  `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
3.  `metabase:` Gibt an, ob sie die Quelle oder Ziel der Metabasis.  
  
4.  `destination:` Gibt den Pfad oder den Ordner, in dem das Skript muss gespeichert werden, wenn der Dateiname nicht klicken Sie dann einen Dateinamen in das Format (Attributwert Object_name) .out angegeben ist  
  
5.  `overwrite:` Bei "true" überschreibt es Wenn gleichen Dateinamen vorhanden. Sie haben die Werte (True/False).  
  
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
**Befehl**  
  
convert-sql-statement  
  
1.  `context` Gibt den Schemanamen an.  
  
2.  `destination` Gibt an, ob die Ausgabe in einer Datei gespeichert werden sollen.  
  
    Wenn dieses Attribut nicht angegeben ist, wird die konvertierte T-SQL-Anweisung in der Konsole angezeigt. (optionales Attribut)  
  
3.  `conversion-report-folder` Gibt an, Ordner, in dem der Bewertungsbericht kann gespeichert werden. (optionales Attribut)  
  
4.  `conversion-report-overwrite` Gibt an, ob den Berichtsordner für die Bewertung zu überschreiben, wenn sie bereits vorhanden ist.  
  
    **Standardwert:** "false". (optionales Attribut)  
  
5.  `write-converted-sql-to` Gibt an, die Datei Ordnerpfad, in dem das konvertierte T-SQL ist, gespeichert werden (oder). Wenn ein Pfad angegeben wird, zusammen mit den `sql-files` -Attribut, wird jede Quelldatei eine entsprechende Ziel T-SQL-Datei, die unter den angegebenen Ordner erstellt haben. Wenn ein Pfad angegeben wird, zusammen mit den `sql` -Attribut, das konvertierte T-SQL wird in einer Datei namens Result.out unter den angegebenen Ordner geschrieben.  
  
6.  `sql` Gibt an, die MySQL-Sql-Anweisungen konvertiert werden, wird eine oder mehrere Anweisungen kann getrennte verwenden ein ";"  
  
7.  `sql-files` Gibt den Pfad der Sql-Dateien, die in T-SQL-Code konvertiert werden.  
  
8.  `write-summary-report-to` Gibt den Pfad, in dem der zusammenfassende Bericht generiert wird. Wenn nur der Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **ConvertSQLReport.XML** erstellt wird. (optionales Attribut)  
  
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
Weitere Informationen zu Befehlszeilenoptionen, finden Sie unter [Command Line Options in SSMA-Konsole &#40;MySQLToSQL&#41; ](../../ssma/mysql/command-line-options-in-ssma-console-mysqltosql.md) .  
  
Weitere Informationen zu den beispielskriptdateien der Konsole, finden Sie unter [arbeiten mit den Beispielskriptdateien der Konsole &#40;MySQLToSQL&#41;](../../ssma/mysql/working-with-the-sample-console-script-files-mysqltosql.md)  
  
Der nächste Schritt hängt davon ab, auf die Anforderungen Ihres Projekts:  
  
1.  Für die Angabe eines Kennworts oder das Exportieren / Importieren von Kennwörtern, finden Sie unter [Verwalten von Kennwörtern &#40;MySQLToSQL&#41;](../../ssma/mysql/managing-passwords-mysqltosql.md).  
  
2.  Generieren von Berichten finden Sie unter [Generieren von Berichten &#40;MySQLToSQL&#41;](../../ssma/mysql/generating-reports-mysqltosql.md).  
  
3.  Behandlung von Problemen in der Konsole, finden Sie unter [Problembehandlung &#40;MySQLToSQL&#41;](../../ssma/mysql/troubleshooting-mysqltosql.md).  
  
