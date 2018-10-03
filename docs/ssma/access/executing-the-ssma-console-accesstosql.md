---
title: Executing the SSMA Console ausführen (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: aa1bf665-8dc0-4259-b36f-46ae67197a43
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 402416503f927f74dcb711ac3bffb3c901f10e79
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47737818"
---
# <a name="executing-the-ssma-console-accesstosql"></a>Executing the SSMA Console ausführen (AccessToSQL)
Microsoft bietet Ihnen eine Reihe zuverlässiger Skriptbefehle für die Datei "und"-Befehlszeilenoptionen zum Ausführen und Steuern von SSMA-Aktivitäten. Die folgenden Abschnitte enthalten Informationen identisch.  
  
## <a name="project--script-file-commands"></a>Project-Datei-Skriptbefehle  
Die Projekt-Befehle verarbeiten, erstellen Projekte öffnen, speichern und Beenden von Projekten.  
  
**Befehl**  
  
Neues-Projekt erstellen: erstellt ein neues SSMA-Projekt.  
  
**Skript**  
  
-   `project-folder` Gibt den Ordner des Projekts erstellt.  
  
-   `project-name` Gibt den Namen des Projekts. {string}  
  
-   `overwrite-if-exists`Optionales Attribut gibt an, ob ein vorhandenes Projekt überschrieben werden soll. {Boolean}  
  
-   `project-type` ist ein optionales Attribut.  Die folgenden Optionen sind für den Projekttyp verfügbar:  
  
    -   SQL Server 2005  
  
    -   SQL-Server-2008  
  
    -   SQL-Server-2012  
  
    -   SQL-Server – 2014  
  
    -   SQL Server 2016  
  
    -   sql-azure  
  
    Standardwert ist "Sql Server 2008".  
  
**Beispiel:**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>"  
  
  project-type=”<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014 | sql-azure>”  
  
/>  
```  
Attribut "überschreiben-If-exists" **"false"** standardmäßig.  
  
'Project-Type'-Attribut ist **Sql-Server-2008** standardmäßig.  
  
**Befehl**  
  
Open-Projekt: Öffnet ein vorhandenes Projekt.  
  
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
**Hinweis:** SSMA für Access-Konsole-Anwendung unterstützt die Abwärtskompatibilität zu gewährleisten. Sie werden können zum Öffnen von Projekten, die mit früheren Version von SSMA erstellt.  
  
**Befehl**  
  
Projekt speichern: speichert das Migrationsprojekt.  
  
**Skript**  
  
**Syntaxbeispiel:**  
  
```xml  
<save-project/>  
```  
**Befehl**  
  
Close-Projekt: Schließt das Migrationsprojekt.  
  
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
  
Die **Durchsuchen** Feature der Benutzeroberfläche wird in der Konsole nicht unterstützt.  
  
Die **Windows-Authentifizierung** und **Port** Parameter sind nicht anwendbar, Herstellen der Verbindung mit SQL Azure.  
  
Weitere Informationen zu "Erstellen von Skriptdateien", finden Sie unter [Skriptdateien erstellen &#40;AccessToSQL&#41;](../../ssma/access/creating-script-files-accesstosql.md).  
  
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
  
Load-Access-Datenbank: zum Laden von Access-Datenbankdateien verwendet  
  
**Skript**  
  
**Syntaxbeispiel:**  
  
```xml  
<load-access-database  database-file="<Access-database>"/>  
```  
oder  
  
```xml  
<load-access-database>  
  
  <access-database database-file="<Access-database1>"/>  
  
  <access-database database-file="<Access-database2>"/>  
  
</load-access-database>  
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
<force-load  
  
  object-name="<object-name>"  
  
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
  
-   Stellt eine Verbindung her, in die Zieldatenbank für SQL Server oder SQL Azure und high Level Metadaten der Zieldatenbank, aber nicht die Metadaten vollständig geladen.  
  
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
  
-   `assessment-report-folder:` Gibt an, Ordner, in dem der Bewertungsbericht kann gespeichert werden. (optionales Attribut)  
  
-   `object-name:` Gibt an, die Objekte, die für die Bewertung der berichtgenerierung (es kann zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt haben) in Betracht gezogen.  
  
-   `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
-   `assessment-report-overwrite:` Gibt an, ob den Berichtsordner für die Bewertung zu überschreiben, wenn sie bereits vorhanden ist.  
  
    **Standardwert:** "false". (optionales Attribut)  
  
-   `write-summary-report-to:` Gibt den Pfad, in dem der Bericht generiert wird.  
  
    Wenn nur der Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **AssessmentReport&lt;n&gt;. XML** erstellt wird. (optionales Attribut)  
  
    Erstellen von Berichten verfügt über zwei weitere Unterkategorien:  
  
    -   `report-errors` (= "True/False", Standardwert "false" (optionale Attribute))  
  
    -   `verbose` (= "True/False", Standardwert "false" (optionale Attribute))  
  
**Syntaxbeispiel:**  
  
```xml  
<generate-assessment-report  
  
  object-name="ssma.Procedures"  
  
  object-type="category"  
  
  write-summary-report-to="<file>"             (optional)  
  
  verbose="<true/false>"                       (optional)  
  
  report-errors="<true/false>"                 (optional)  
  
  conversion-report-folder="<folder>"          (optional)  
  
  conversion-report-overwrite="<true/false>"   (optional)  
  
/>  
```  
oder  
  
```xml  
<generate-assessment-report  
  
  conversion-report-folder="<folder>"            (optional)  
  
  conversion-report-overwrite="<true/false>"     (optional)  
  
>  
    <metabase-object object-name="ssma.Procedures"  
  
        object-type="category"/>  
  
</generate-assessment-report>  
```  
  
## <a name="migration-script-file-commands"></a>Skript-Datei-Migrationsbefehle  
Die migrationsbefehle Schema der Zieldatenbank, die dem Quellschema zu konvertieren und Migrieren von Daten auf dem Zielserver.  
  
Die Ausgabe der Standard-Konsole, die Einstellung für die migrationsbefehle ist 'Full' Ausgabebericht mit keine ausführliche berichterstellung: nur Zusammenfassung am Stammknoten Source-Objekt-Struktur.  
  
**Befehl**  
  
Convert-schema  
  
-   Führt die schemakonvertierung aus der Quelle in das Zielschema.  
  
-   Wenn die Quelle oder Ziel-datenbankverbindung wird nicht vor dem Ausführen dieses Befehls ausgeführt, oder die Verbindung mit der Quelle oder Ziel-Datenbank-Server ein Fehler, während der Ausführung des Befehls auftritt, wird ein Fehler generiert, und die Konsolenanwendung wird beendet.  
  
**Skript**  
  
-   `conversion-report-folder:` Gibt an, Ordner, in dem der Bewertungsbericht gespeichert werden können. (optionales Attribut)  
  
-   `object-name:` Gibt an, die Quell-Objekte, die für das Konvertieren eines Schemas (es kann zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt haben) in Betracht gezogen.  
  
-   `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
-   `conversion-report-overwrite:` Gibt an, ob den Berichtsordner für die Bewertung zu überschreiben, wenn sie bereits vorhanden ist.  
  
    **Standardwert:** "false". (optionales Attribut)  
  
-   `write-summary-report-to:` Gibt den Pfad, in dem der Bericht generiert wird.  
  
    Wenn nur der Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **SchemaConversionReport&lt;n&gt;. XML** erstellt wird. (optionales Attribut)  
  
    Erstellen von Berichten verfügt über zwei weitere Unterkategorien:  
  
    -   `report-errors` (= "True/False", Standardwert "false" (optionale Attribute))  
  
    -   `verbose` (= "True/False", Standardwert "false" (optionale Attribute))  
  
**Syntaxbeispiel:**  
  
```xml  
<convert-schema  
  
  object-name="ssma.Procedures"  
  
  object-type="category"  
  write-summary-report-to="<filepath/folder>"     (optional)  
  
  verbose="<true/false>"                          (optional)  
  
  report-errors="<true/false>"                    (optional)  
  
  conversion-report-folder="<folder>"             (optional)  
  
  conversion-report-overwrite="<true/false>"      (optional)  
  
/>  
```  
oder  
  
```xml  
<convert-schema  
  
  conversion-report-folder="<folder>"         (optional)  
  
  conversion-report-overwrite="<true/false>"  (optional)  
  
  <metabase-object object-name="ssma.Procedures"  
  
    object-type="category"/>  
  
</convert-schema>  
```  
**Befehl**  
  
Migrieren von Daten  
  
1.  Werden die Quelldaten zum Ziel migriert.  
  
**Skript**  
  
-   `object-name:` Gibt an, die Source-Objekte, die für die Migration als Daten (es kann zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt).  
  
-   `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
-   `write-summary-report-to:` Gibt den Pfad, in dem der Bericht generiert wird.  
  
    Wenn nur der Ordnerpfad angegeben wird, klicken Sie dann anhand des Namens Datei **DataMigrationReport&lt;n&gt;. XML** erstellt wird. (optionales Attribut)  
  
    Erstellen von Berichten verfügt über zwei weitere Unterkategorien:  
  
    -   `report-errors` (= "True/False", Standardwert "false" (optionale Attribute))  
  
    -   `verbose` (= "True/False", Standardwert "false" (optionale Attribute))  
  
**Syntaxbeispiel:**  
  
```xml  
<migrate-data  
  
  write-summary-report-to="<filepath/folder>"  
  
  report-errors="true" verbose="true">  
  
    <metabase-object object-name="ssma.TT1"/>  
  
    <metabase-object object-name="ssma.TT2"/>  
  
    <metabase-object object-name="ssma.TT3"/>  
  
    <data-migration-connection  
  
      source-use-last-used="true"/source-server="<server-unique-name>"  
  
      target-use-last-used="true"/target-server="<server-unique-name>"/>  
  
</migrate-data>  
```  
oder  
  
```xml  
<migrate-data  
  
  object-name="ssma.Tables"  
  
  object-type="category"  
  
  write-summary-report-to="<filepath/folder>"  
  
  report-errors="true" verbose="true"/>  
```  
**Befehl**  
  
Tabellen verknüpfen: mit diesem Befehl verknüpft die Quelltabelle (Zugriff) mit der Zieltabelle.  
  
**Skript**  
  
**Syntaxbeispiel:**  
  
```xml  
<link-tables>  
  
  <metabase-object object-name="AccessDatabase.table1" object-type="Tables"/>  
  
  <metabase-object object-name="AccessDatabase.table2" object-type="Tables"/>  
  
</link-tables>  
```  
oder  
  
```xml  
<link-tables>  
  
  <metabase-object object-name="AccessDatabase.Tables" object-type="category"/>  
  
</link-tables>  
```  
**Befehl**  
  
Aufheben der Verknüpfung-Tabellen: Dieser Befehl hebt die Verknüpfung mit der Quelltabelle (Zugriff) aus der Zieltabelle.  
  
**Skript**  
  
**Beispiele für die Abfrageausdruckssyntax:**  
  
```xml  
<unlink-tables>  
  
  <metabase-object object-name="AccessDatabase.table1" object-type="Tables"/>  
  
  <metabase-object object-name="AccessDatabase.table2" object-type="Tables"/>  
  
</unlink-tables>  
```  
oder  
  
```xml  
<unlink-tables>  
  
  <metabase-object object-name="AccessDatabase.Tables" object-type="category"/>  
  
</unlink-tables>  
```  
  
## <a name="migration-preparation-script-file-commands"></a>Vorbereitung der Skript-Datei Migrationsbefehle  
Der Befehl Vorbereiten der Migration initiiert schemazuordnung zwischen den Quell- und Zieldatenbanken.  
  
**Befehl**  
  
Map-Schema: schemazuordnung der Quelldatenbank mit dem Zielschema.  
  
**Skript**  
  
-   `source-schema` Gibt das Schema der Datenquelle, die, das wir migrieren möchten.  
  
-   `sql-server-schema` Gibt das Zielschema, das sie migriert werden soll.  
  
**Syntaxbeispiel:**  
  
```xml  
<map-schema source-schema="source-schema"  
  
            sql-server-schema="target-schema"/>  
```  
  
## <a name="manageability-commands"></a>Verwaltbarkeit-Befehle  
Die Verwaltbarkeit Befehle helfen, die Ziel-Datenbankobjekte mit der Quelldatenbank zu synchronisieren.  
  
Die Ausgabe der Standard-Konsole, die Einstellung für die migrationsbefehle ist 'Full' Ausgabebericht mit keine ausführliche berichterstellung: nur Zusammenfassung am Stammknoten Source-Objekt-Struktur.  
  
**Befehl**  
  
Synchronisieren von Ziel  
  
1.  Synchronisiert die Zielobjekte mit der Zieldatenbank an.  
  
2.  Wenn dieser Befehl für die Quelldatenbank ausgeführt wird, wird ein Fehler aufgetreten.  
  
3.  Wenn die Verbindung mit der Zieldatenbank wird nicht ausgeführt, bevor Sie diesen Befehl ausführen oder die Verbindung mit dem Datenbank-Zielserver ein Fehler auftritt, während der Ausführung des Befehls, wird ein Fehler generiert, und die Konsolenanwendung beendet.  
  
**Skript**  
  
1.  `object-name:` Gibt an, die Ziel-Objekte, die für die Synchronisierung mit der Zieldatenbank (es kann zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt haben) in Betracht gezogen.  
  
2.  `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
3.  `on-error:` Gibt an, ob die Synchronisierungsfehler als Warnungen oder Fehler angegeben. Verfügbare Optionen für in-Fehler:  
  
    -   Bericht insgesamt als Warnung  
  
    -   Bericht-each-als-Warnung  
  
    -   Fehler-Skript  
  
4.  `report-errors-to:` Speicherort der Fehlerbericht angibt, für der Synchronisierungsvorgang (optionales Attribut), wenn nur Ordnerpfad angegeben wird, klicken Sie dann Datei anhand des Namens **TargetSynchronizationReport.XML** erstellt wird.  
  
**Syntaxbeispiel:**  
  
```xml  
<synchronize-target  
  
  object-name="ots_triggers.dbo"  
  
  on-error="<report-total-as-warning|  
  
             report-each-as-warning|  
  
             fail-script>"              (optional)  
  
  report-errors-to="<file-name>"        (optional)  
  
/>  
```  
oder  
  
```xml  
<synchronize-target  
  
  object-name="ssma.dbo.Procedures"  
  
  object-type="category"/>  
```  
oder  
  
```xml  
<synchronize-target>  
  
  <metabase-object object-name="ssma.dbo.TT1"/>  
  
  <metabase-object object-name="ssma.dbo.TT2"/>  
  
  <metabase-object object-name="ssma.dbo.TT3"/>  
  
</synchronize-target>  
```  
**Befehl**  
  
Refresh-aus-Datenbank  
  
-   Aktualisiert die Source-Objekte aus der Datenbank.  
  
-   Wenn dieser Befehl für die Zieldatenbank ausgeführt wird, wird ein Fehler generiert.  
  
**Skript**  
  
Ist eine oder mehrere Metabase-Knoten als Befehlszeilenparameter erforderlich.  
  
1.  `object-name:` Gibt an, die Quell-Objekte, die für die Aktualisierung aus der Quelldatenbank (es kann zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt haben) in Betracht gezogen.  
  
2.  `object-type:` Gibt den Typ des Objekts im Objekt-Name-Attribut angegeben ist (falls es sich um eine Objektkategorie angegeben ist, dann Objekttyp "Kategorie").  
  
3.  `on-error:` Gibt an, ob die datenaktualisierung Fehler als Warnungen oder Fehler angegeben. Verfügbare Optionen für in-Fehler:  
  
    -   Bericht insgesamt als Warnung  
  
    -   Bericht-each-als-Warnung  
  
    -   Fehler-Skript  
  
4.  `report-errors-to:` Speicherort der Fehlerbericht angibt, für der Aktualisierungsvorgang (optionales Attribut), wenn nur Ordnerpfad angegeben wird, klicken Sie dann Datei anhand des Namens **SourceDBRefreshReport.XML** erstellt wird.  
  
**Syntaxbeispiel:**  
  
```xml  
<refresh-from-database  
  
  object-name="ssma.TT1"  
  
  on-error="<report-total-as-warning|  
  
             report-each-as-warning|  
  
             fail-script>"              (optional)  
  
  report-errors-to="<file-name>"        (optional)  
  
/>  
```  
oder  
  
```xml  
<refresh-from-database  
  
  object-name="ssma.Procedures"  
  
  object-type="category"/>  
```  
oder  
  
```xml  
<refresh-from-database>  
  
  <metabase-object object-name="ssma.TT_1"/>  
  
</refresh-from-database>  
```  
  
## <a name="script-generation-script-file-commands"></a>Skript generieren-Skriptbefehle für Datei  
Die Generierung von Skripts, die Befehle hilft beim Speichern der Konsolenausgabe in einer Skriptdatei.  
  
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
  
  object-name="ssma.dbo.Procedures"  
  
  object-type="category"  
  
  destination="<file/folder>"  
  
  overwrite="<true/false>"             (optional)  
  
/>  
```  
oder  
  
```xml  
<save-as-script  
  
  metabase="<source/target>"  
  
  destination="<file/folder>"  
  
    <metabase-object object-name="ssma.dbo.Procedures"  
  
                     object-type="category"/>  
  
</save-as-script>  
```  
  
## <a name="next-step"></a>Nächster Schritt  
Weitere Informationen zu Befehlszeilenoptionen, finden Sie unter [Command Line Options in SSMA-Konsole &#40;AccessToSQL&#41; ](../../ssma/access/command-line-options-in-ssma-console-accesstosql.md) .  
  
Weitere Informationen zu den beispielskriptdateien der Konsole, finden Sie unter [arbeiten mit der Beispiel-Konsole Skript FilesExecuting der SSMA-Konsole &#40;AccessToSQL&#41;](../../ssma/access/working-sample-console-script-filesexecuting-ssma-console-accesstosql.md)  
  
Der nächste Schritt hängt davon ab, auf die Anforderungen Ihres Projekts:  
  
-   Für die Angabe eines Kennworts oder das Exportieren / Importieren von Kennwörtern, finden Sie unter [Verwalten von Kennwörtern &#40;AccessToSQL&#41;](../../ssma/access/managing-passwords-accesstosql.md).  
  
-   Generieren von Berichten finden Sie unter [Generieren von Berichten &#40;AccessToSQL&#41;](../../ssma/access/generating-reports-accesstosql.md).  
  
-   Behandlung von Problemen in der Konsole, finden Sie unter [Problembehandlung &#40;AccessToSQL&#41;](../../ssma/access/troubleshooting-accesstosql.md).  
  
