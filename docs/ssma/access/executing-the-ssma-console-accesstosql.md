---
description: Ausführen der SSMA-Konsole (accesstosql)
title: Ausführen der SSMA-Konsole (accesstosql) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: aa1bf665-8dc0-4259-b36f-46ae67197a43
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 655b6f64391ebf8c7fd28d179000753ed4f95faa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492513"
---
# <a name="executing-the-ssma-console-accesstosql"></a>Ausführen der SSMA-Konsole (accesstosql)
Microsoft bietet Ihnen einen robusten Satz von Skriptdatei Befehlen und Befehlszeilenoptionen zum Ausführen und Steuern von SSMA-Aktivitäten. Die nachfolgenden Abschnitte beschreiben die gleichen.  
  
## <a name="project--script-file-commands"></a>Befehle der Projekt Skriptdatei  
Die Projekt Befehle behandeln das Erstellen von Projekten, das Öffnen, speichern und Beenden von Projekten.  
  
**Befehl**  
  
Create-New-Project: erstellt ein neues SSMA-Projekt.  
  
**Skript**  
  
-   `project-folder` Gibt den Ordner des Projekts an, das erstellt wird.  
  
-   `project-name` Gibt den Namen des Projekts an. {string}  
  
-   `overwrite-if-exists`Optionales Attribut gibt an, ob ein vorhandenes Projekt überschrieben werden soll. booleschen  
  
-   `project-type` ist ein optionales Attribut.  Die folgenden Optionen sind für den Projekttyp verfügbar:  
  
    -   SQL Server-2005  
  
    -   SQL Server-2008  
  
    -   SQL Server-2012  
  
    -   SQL Server-2014  
  
    -   SQL Server-2016  
  
    -   SQL-Azure  
  
    Der Standardwert ist "SQL Server-2008".  
  
**Beispiel:**  
  
```xml  
<create-new-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
  overwrite-if-exists="<true/false>"  
  
  project-type="<sql-server-2008 | sql-server-2005 | sql-server-2012 | sql-server-2014 | sql-azure>"  
  
/>  
```  
Das Attribut ' überschreiben-if-vorhanden ' ist standardmäßig **false** .  
  
Das Attribut ' Project-Type ' ist standardmäßig **SQL-Server-2008** .  
  
**Befehl**  
  
Open-Project: öffnet ein vorhandenes Projekt.  
  
**Skript**  
  
-   `project-folder` Gibt den Ordner des Projekts an, das erstellt wird. Der Befehl schlägt fehl, wenn der angegebene Ordner nicht vorhanden ist.  {string}  
  
-   `project-name` Gibt den Namen des Projekts an. Der Befehl schlägt fehl, wenn das angegebene Projekt nicht vorhanden ist.  {string}  
  
**Syntax Beispiel:**  
  
```xml  
<open-project  
  
  project-folder="<project-folder>"  
  
  project-name="<project-name>"  
  
/>  
```  
**Hinweis:** SSMA für die Access-Konsolenanwendung unterstützt die Abwärtskompatibilität. Sie können Projekte öffnen, die mit einer früheren Version von SSMA erstellt wurden.  
  
**Befehl**  
  
Save-Project: speichert das Migrationsprojekt.  
  
**Skript**  
  
**Syntax Beispiel:**  
  
```xml  
<save-project/>  
```  
**Befehl**  
  
Close-Project: schließt das Migrationsprojekt.  
  
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
  
Die Funktion zum **Durchsuchen** der Benutzeroberfläche wird in der Konsole nicht unterstützt.  
  
Die **Windows-Authentifizierungs-und-** **Port** Parameter sind beim Herstellen einer Verbindung mit SQL Azure nicht anwendbar.  
  
Weitere Informationen zum Erstellen von Skriptdateien finden Sie unter [Erstellen von Skriptdateien &#40;Access Token&#41;](../../ssma/access/creating-script-files-accesstosql.md).  
  
**Befehl**
  
Connect-Source-Datenbank  
  
- Führt eine Verbindung mit der Quelldatenbank durch und lädt allgemeine Metadaten der Quelldatenbank, jedoch nicht alle Metadaten.  
  
- Wenn die Verbindung mit der Quelle nicht hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung.  
  
**Skript**
  
Die Server Definition wird aus dem Name-Attribut abgerufen, das für jede Verbindung im Server Abschnitt der Server Verbindungs Datei oder der Skriptdatei definiert ist.  
  
**Syntax Beispiel:**  
  
```xml  
<connect-source-database  server="<server-unique-name>"/>  
```  
**Befehl**  
  
Load-Access-Database: dient zum Laden von Access-Datenbankdateien  
  
**Skript**  
  
**Syntax Beispiel:**  
  
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
  
Force-Load-Source/Ziel-Database  
  
-   Lädt die Quell Metadaten.  
  
-   Nützlich für das Offline arbeiten an einem Migrationsprojekt.  
  
-   Wenn die Verbindung mit der Quelle bzw. dem Ziel nicht hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung.  
  
**Skript**  
  
Erfordert einen oder mehrere Metabasisknoten als Befehlszeilenparameter.  
  
**Syntax Beispiel:**  
  
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
  
reconnect-Quelldatenbank  
  
- Stellt eine erneute Verbindung mit der Quelldatenbank her, lädt jedoch keine Metadaten im Gegensatz zum Connect-Source-Database-Befehl.  
  
- Wenn (erneut) keine Verbindung mit der Quelle hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung.  
  
**Skript**
  
**Syntax Beispiel:**  
  
```xml  
<reconnect-source-database  server="<server-unique-name>"/>  
```

**Befehl**
  
Connect-Target-Database  
  
- Stellt eine Verbindung mit dem Ziel SQL Server oder SQL Azure Datenbank her und lädt allgemeine Metadaten der Zieldatenbank, jedoch nicht vollständig die Metadaten.  
  
- Wenn die Verbindung mit dem Ziel nicht hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung.  
  
**Skript**
  
Die Server Definition wird aus dem Name-Attribut abgerufen, das für jede Verbindung im Server Abschnitt der Server Verbindungs Datei oder der Skriptdatei definiert ist.  
  
**Syntax Beispiel:**  
  
```xml  
<connect-target-database  server="<server-unique-name>"/>  
```  

**Befehl**
  
reconnect-Target-Database  
  
- Stellt eine erneute Verbindung mit der Zieldatenbank her, lädt jedoch im Gegensatz zum Connect-Target-Database-Befehl keine Metadaten.  
  
- Wenn (erneut) die Verbindung mit dem Ziel nicht hergestellt werden kann, wird ein Fehler generiert, und die Konsolenanwendung beendet die weitere Ausführung.  
  
**Skript**
  
**Syntax Beispiel:**  
  
```xml  
<reconnect-target-database  server="<server-unique-name>"/>  
```  

## <a name="report-script-file-commands"></a>Befehle für Berichts Skriptdateien

Die Berichts Befehle generieren Berichte zur Leistung verschiedener SSMA-Konsolen Aktivitäten.

**Befehl**
  
generieren-Assessment-Bericht  
  
- Generiert Bewertungsberichte für die Quelldatenbank.  
  
- Wenn die Verbindung der Quelldatenbank vor dem Ausführen dieses Befehls nicht erfolgt, wird ein Fehler generiert, und die Konsolenanwendung wird beendet.  
  
- Wenn während der Befehlsausführung keine Verbindung mit dem Quelldaten Bankserver hergestellt werden kann, führt dies auch dazu, dass die Konsolenanwendung beendet wird.  
  
**Skript**

- `assessment-report-folder:` Gibt den Ordner an, in dem der Bewertungsbericht gespeichert werden kann. (optionales Attribut)  
  
- `object-name:` Gibt die Objekte an, die für die Bewertungsbericht Generierung berücksichtigt werden (Sie kann einzelne Objektnamen oder einen Gruppen Objektnamen aufweisen).  
  
- `object-type:` Gibt den Typ des Objekts an, das im Object-Name-Attribut angegeben ist (wenn die Objekt Kategorie angegeben wird, wird der Objekttyp "Category" genannt).  
  
- `assessment-report-overwrite:` Gibt an, ob der Bewertungsberichts Ordner überschrieben werden soll, wenn er bereits vorhanden ist.  
  
    **Standardwert:** false. (optionales Attribut)  
  
- `write-summary-report-to:` Gibt den Pfad an, in dem der Bericht generiert wird.  
  
    Wenn nur der Ordner Pfad erwähnt wird, dann file **by Name &lt; &gt; XML** wird erstellt. (optionales Attribut)  
  
    Die Berichtserstellung hat zwei weitere Unterkategorien:  
  
    - `report-errors` (= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
    - `verbose` (= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
**Syntax Beispiel:**  
  
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
  
## <a name="migration-script-file-commands"></a>Befehle der Migrations Skriptdatei

Die Migrations Befehle Konvertieren das Ziel Datenbankschema in das Quell Schema und migriert Daten auf den Zielserver.  
  
Die standardmäßige Konsolenausgabe Einstellung für die Migrations Befehle ist der Ausgabebericht "vollständig", ohne dass eine ausführliche Fehlerberichterstattung vorliegt: nur eine Zusammenfassung des Stamm Knotens der Quell Objektstruktur.  
  
**Befehl**

Convert-Schema  
  
- Führt eine Schema Konvertierung von der Quelle in das Ziel Schema durch.  
  
- Wenn die Quell-oder Ziel Datenbankverbindung nicht vor dem Ausführen dieses Befehls erfolgt oder wenn die Verbindung mit dem Quell-oder Ziel Datenbankserver während der Ausführung des Befehls fehlschlägt, wird ein Fehler generiert, und die Konsolenanwendung wird beendet.  
  
**Skript**

- `conversion-report-folder:` Gibt den Ordner an, in dem der Bewertungsbericht gespeichert werden kann. (optionales Attribut)  
  
- `object-name:` Gibt die zum Umrechnen des Schemas berücksichtigten Quell Objekte an (Sie können einzelne Objektnamen oder einen Gruppen Objektnamen aufweisen).  
  
- `object-type:` Gibt den Typ des Objekts an, das im Object-Name-Attribut angegeben ist (wenn die Objekt Kategorie angegeben wird, wird der Objekttyp "Category" genannt).  
  
- `conversion-report-overwrite:` Gibt an, ob der Bewertungsberichts Ordner überschrieben werden soll, wenn er bereits vorhanden ist.  
  
    **Standardwert:** false. (optionales Attribut)  
  
- `write-summary-report-to:` Gibt den Pfad an, in dem der Bericht generiert wird.  
  
    Wenn nur der Ordner Pfad erwähnt wird, dann file by Name **schemaconversionreport &lt; n &gt; . XML** wird erstellt. (optionales Attribut)  
  
    Die Berichtserstellung hat zwei weitere Unterkategorien:  
  
    - `report-errors` (= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
    - `verbose` (= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
**Syntax Beispiel:**  
  
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
  
- Migriert die Quelldaten zum Ziel.  
  
**Skript**
  
- `object-name:` Gibt die zum Migrieren von Daten berücksichtigten Quell Objekte an (Sie können einzelne Objektnamen oder einen Gruppen Objektnamen aufweisen).  
  
- `object-type:` Gibt den Typ des Objekts an, das im Object-Name-Attribut angegeben ist (wenn die Objekt Kategorie angegeben wird, wird der Objekttyp "Category" genannt).  
  
- `write-summary-report-to:` Gibt den Pfad an, in dem der Bericht generiert wird.  
  
    Wenn nur der Ordner Pfad erwähnt wird, dann file by Name **datamigrationreport &lt; n &gt; . XML** wird erstellt. (optionales Attribut)  
  
    Die Berichtserstellung hat zwei weitere Unterkategorien:  
  
    - `report-errors` (= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
    - `verbose` (= "true/false", mit dem Standardwert "false" (optionale Attribute))  
  
**Syntax Beispiel:**  
  
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
  
Link-Tables: Dieser Befehl verknüpft die Quell Tabelle (Access) mit der Ziel Tabelle.  
  
**Skript**

**Syntax Beispiel:**  
  
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
  
unlink-Tables: Dieser Befehl entfernt die Verknüpfung der Quell Tabelle (Access) mit der Ziel Tabelle.  
  
**Skript**
  
**Syntax Beispiele:**  
  
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
  
## <a name="migration-preparation-script-file-commands"></a>Befehle zum Vorbereiten der Migrations Skriptdatei

Der Befehl Migrations Vorbereitung startet die Schema Zuordnung zwischen den Quell-und Ziel Datenbanken.  
  
**Befehl**
  
Map-Schema: Schema Zuordnung der Quelldatenbank zum Ziel Schema.  
  
**Skript**
  
- `source-schema` Gibt das Quell Schema an, das migriert werden soll.  
  
- `sql-server-schema` Gibt das Ziel Schema an, in dem Sie migriert werden soll.  
  
**Syntax Beispiel:**  
  
```xml  
<map-schema source-schema="source-schema"  
  
            sql-server-schema="target-schema"/>  
```  
  
## <a name="manageability-commands"></a>Verwaltbarkeitsbefehle

Mithilfe der verwaltbarkeitsbefehle können die Ziel Datenbankobjekte mit der Quelldatenbank synchronisiert werden.  
  
Die standardmäßige Konsolenausgabe Einstellung für die Migrations Befehle ist der Ausgabebericht "vollständig", ohne dass eine ausführliche Fehlerberichterstattung vorliegt: nur eine Zusammenfassung des Stamm Knotens der Quell Objektstruktur.  
  
**Befehl**

Synchronisieren-Ziel  
  
- Synchronisiert die Zielobjekte mit der Zieldatenbank.  
  
- Wenn dieser Befehl für die Quelldatenbank ausgeführt wird, erhalten Sie eine Fehlermeldung.  
  
- Wenn die Verbindung mit der Zieldatenbank vor dem Ausführen dieses Befehls nicht erfolgt oder bei der Ausführung des Befehls ein Fehler auftritt, wird ein Fehler generiert, und die Konsolenanwendung wird beendet.  
  
**Skript**
  
- `object-name:` Gibt die Zielobjekte an, die für die Synchronisierung mit der Zieldatenbank berücksichtigt werden (es können einzelne Objektnamen oder ein Gruppen Objektname vorhanden sein).  
  
- `object-type:` Gibt den Typ des Objekts an, das im Object-Name-Attribut angegeben ist (wenn die Objekt Kategorie angegeben wird, wird der Objekttyp "Category" genannt).  
  
- `on-error:` Gibt an, ob Synchronisierungs Fehler als Warnungen oder Fehler angegeben werden sollen. Verfügbare Optionen für "bei Fehler":  
  
    - Bericht-gesamt-als-Warnung  
  
    - Bericht-jeder-als-Warnung  
  
    - Fehler-Skript  
  
- `report-errors-to:` Gibt den Speicherort des Fehlerberichts für den Synchronisierungs Vorgang an (optionales Attribut), wenn nur der Ordner Pfad angegeben ist, dann wird file by Name **TargetSynchronizationReport.XML** erstellt.  
  
**Syntax Beispiel:**  
  
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
  
Refresh-from-Database  
  
- Aktualisiert die Quell Objekte aus der Datenbank.  
  
- Wenn dieser Befehl für die Zieldatenbank ausgeführt wird, wird ein Fehler generiert.  
  
**Skript**
  
Erfordert einen oder mehrere Metabasisknoten als Befehlszeilenparameter.  
  
- `object-name:` Gibt die Quell Objekte an, die für die Aktualisierung aus der Quelldatenbank berücksichtigt werden (Sie können einzelne Objektnamen oder ein Gruppen Objektname aufweisen).  
  
- `object-type:` Gibt den Typ des Objekts an, das im Object-Name-Attribut angegeben ist (wenn die Objekt Kategorie angegeben wird, wird der Objekttyp "Category" genannt).  
  
- `on-error:` Gibt an, ob Aktualisierungs Fehler als Warnungen oder Fehler angegeben werden sollen. Verfügbare Optionen für "bei Fehler":  
  
    - Bericht-gesamt-als-Warnung  
  
    - Bericht-jeder-als-Warnung  
  
    - Fehler-Skript  
  
- `report-errors-to:` Gibt den Speicherort des Fehlerberichts für den Aktualisierungs Vorgang an (optionales Attribut), wenn nur der Ordner Pfad angegeben ist, dann wird file by Name **SourceDBRefreshReport.XML** erstellt.  
  
**Syntax Beispiel:**  
  
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
  
## <a name="script-generation-script-file-commands"></a>Skripterstellung Skriptdatei Befehle

Mithilfe der Skript Generierungs Befehle wird die Konsolenausgabe in einer Skriptdatei gespeichert.  
  
**Befehl**
  
als Skript speichern  
  
Wird verwendet, um die Skripts der Objekte in einer Datei zu speichern, die bei Metabase = Target erwähnt wird. Dies ist eine Alternative zum Synchronisierungs Befehl, bei dem die Skripts in der Zieldatenbank ausgeführt werden.  
  
**Skript**
  
Erfordert einen oder mehrere Metabasisknoten als Befehlszeilenparameter.  
  
- `object-name:` Gibt die Objekte an, deren Skripts gespeichert werden sollen. (Es kann einzelne Objektnamen oder ein Gruppen Objektname aufweisen.)  
  
- `object-type:` Gibt den Typ des Objekts an, das im Object-Name-Attribut angegeben ist (wenn die Objekt Kategorie angegeben wird, wird der Objekttyp "Category" genannt).  
  
- `metabase:` Gibt an, ob es sich um die Quell-oder Ziel Metabase handelt.  
  
- `destination:` Gibt den Pfad oder den Ordner an, in dem das Skript gespeichert werden muss. Wenn der Dateiname nicht angegeben wird, wird ein Dateiname im Format (object_name-Attribut Wert). out angegeben.  
  
- `overwrite:` Wenn true, wird sie überschrieben, wenn die gleichen Dateinamen vorhanden sind. Sie kann die Werte (true/false) enthalten.  
  
**Syntax Beispiel:**  
  
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
  
## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Befehlszeilenoptionen finden Sie unter [Befehlszeilenoptionen in der SSMA-Konsole &#40;accesstosql&#41;](../../ssma/access/command-line-options-in-ssma-console-accesstosql.md) .  
  
Informationen zu Beispiel-Konsolen Skriptdateien finden Sie unter [Arbeiten mit dem Beispiel Konsolen Skript filesexecuting the SSMA Console &#40;accesstosql&#41;](../../ssma/access/working-sample-console-script-filesexecuting-ssma-console-accesstosql.md)  
  
Der nächste Schritt hängt von Ihren Projektanforderungen ab:  
  
- Informationen zum Angeben eines Kennworts oder zum Exportieren/Importieren von Kenn Wörtern finden Sie unter Verwalten von Kenn [Wörtern &#40;accesstosql&#41;](../../ssma/access/managing-passwords-accesstosql.md).  
  
- Informationen zum Erstellen von Berichten finden Sie unter [Erstellen von Berichten &#40;Access Token&#41;](../../ssma/access/generating-reports-accesstosql.md).  
  
- Informationen zur Behebung von Problemen in der-Konsole finden Sie unter [Problembehandlung &#40;Access Token&#41;](../../ssma/access/troubleshooting-accesstosql.md).  
