---
description: Erstellen von Berichten (DB2ToSQL)
title: Erstellen von Berichten (DB2ToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 69ef5fd9-190d-4c58-8199-b3f77d5e1883
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 20c7e28e46f4a522f1532db69bf4e7260dced0da
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "91987426"
---
# <a name="generating-reports-db2tosql"></a>Erstellen von Berichten (DB2ToSQL)
Die Berichte bestimmter Aktivitäten, die mithilfe von Befehlen ausgeführt werden, werden in der SSMA-Konsole auf Objektstruktur Ebene generiert.  
  
Verwenden Sie das folgende Verfahren, um Berichte zu generieren:  
  
1.  Geben Sie den Parameter " **Write-Summary-Report-to" an** . Der zugehörige Bericht wird als Dateiname (sofern angegeben) oder in dem von Ihnen angegebenen Ordner gespeichert. Der Dateiname ist vom System vordefiniert, wie in der folgenden Tabelle erwähnt, wobei ** &lt; n &gt; ** die eindeutige Dateinummer ist, die bei jeder Ausführung desselben Befehls mit einer Ziffer schrittweise erhöht wird.  
  
    Die Berichte vis-a-vis-Befehle lauten:  
  
    |SL. Nein.|Get-Help|Berichtstitel|  
    |-|-|-|  
    |1|generieren-Assessment-Bericht|Gutamentreport &lt; n &gt; . Basi|  
    |2|Convert-Schema|Schemaconversionreport &lt; n &gt; . Basi|  
    |3|Migrieren von Daten|Datamigrationreport &lt; n &gt; . Basi|  
    |4|Convert-SQL-Anweisung|Conversqlreport &lt; n &gt; . Basi|  
    |5|Synchronisieren-Ziel|Targetsynchronizationreport &lt; n &gt; . Basi|  
    |6|Refresh-from-Database|Sourcedbrefreshreport &lt; n &gt; . Basi|  
  
    > [!IMPORTANT]  
    > Ein Ausgabebericht unterscheidet sich vom Bewertungsbericht. Bei der ersten handelt es sich um einen Bericht zur Leistung eines ausgeführten Befehls, bei dem es sich um einen XML-Bericht für die programmgesteuerte Nutzung handelt.  
  
    Für die Befehlsoptionen für Ausgabe Berichte (von SL. Nein. 2-4 oben) finden Sie im Abschnitt [Ausführen der SSMA-Konsole &#40;DB2ToSQL&#41;](../../ssma/db2/executing-the-ssma-console-db2tosql.md) .  
  
2.  Geben Sie den Umfang der im Ausgabebericht gewünschten Details mithilfe der berichtsausführlichkeits-Einstellungen an:  
  
    |SL. Nein.|Befehl und Parameter|Ausgabe Beschreibung|  
    |-|-|-|  
    |1|Verbose = "false"|Generiert einen zusammengefassten Bericht der Aktivität.|  
    |2|Verbose = "true"|Generiert einen zusammengefassten und detaillierten Statusbericht für jede Aktivität.|  
  
    > [!NOTE]  
    > Die oben angegebenen berichtsausführlichkeits-Einstellungen gelten für die Befehle Generate-Assessment-Report, Convert-Schema, Migration-Data, Convert-SQL-Statement.  
  
3.  Geben Sie den Umfang der von Ihnen gewünschten Details in den Fehlerberichten mithilfe der Einstellungen für die Fehlerberichterstattung an:  
  
    |SL. Nein.|Befehl und Parameter|Ausgabe Beschreibung|  
    |-|-|-|  
    |1|Report-Errors = "false"|Keine Details zu Fehler-/Warnungs-/Information-Meldungen.|  
    |2|Report-Errors = "true"|Ausführliche Fehler-/Warnungs-/Information-Meldungen.|  
  
    > [!NOTE]  
    > Die oben angegebenen Einstellungen für die Fehlerberichterstattung gelten für die Befehle "Generate-Assessment-Report", "Convert-Schema", "Migration-Data" und "Convert-SQL-Statement".  
  
**Beispiel:**  
  
```  
<generate-assessment-report  
  
   object-name="<object-name>"  
  
   object-type="<object-type>"  
  
   verbose="<true/false>"  
  
   report-erors="<true/false>"  
  
   write-summary-report-to="<file-name/folder-name>"  
  
   assessment-report-folder="<folder-name>"  
  
   assessment-report-overwrite="<true/false>"/>  
```  
  
### <a name="synchronize-target"></a>Synchronisieren-Ziel:  
Der Befehl " **Synchronisieren-Target** " weist einen **Report-Errors-to-Parameter auf** , der den Speicherort des Fehlerberichts für den Synchronisierungs Vorgang angibt. Anschließend wird eine Datei namens **targetsynchronizationreport &lt; n angezeigt &gt; . XML** wird an der angegebenen Position erstellt, wobei ** &lt; n &gt; ** die eindeutige Dateinummer ist, die mit jeder Ausführung desselben Befehls mit einer Ziffer Inkrementen erhöht.  
  
**Hinweis:** Wenn der Ordner Pfad angegeben ist, wird der Parameter "Report-Errors-to" ein optionales Attribut für den Befehl "Synchronisieren-Ziel".  
  
```  
<!-- Example: Synchronize target entire Database with all attributes-->  
  
<synchronize-target  
  
   object-name="<object-name>"  
  
   on-error="report-total-as-warning/report-each-as-warning/fail-script"  
  
   report-errors-to="<file-name/folder-name>"/>  
```  
**Objektname:** Gibt die für die Synchronisierung berücksichtigten Objekte an (Sie kann auch individuellen-Objektnamen oder einen Gruppen Objektnamen aufweisen).  
  
**bei Fehler:** Gibt an, ob Synchronisierungs Fehler als Warnungen oder Fehler angegeben werden sollen. Verfügbare Optionen für "bei Fehler":  
  
-   Bericht-gesamt-als-Warnung  
  
-   Bericht-jeder-als-Warnung  
  
-   Fehler-Skript  
  
### <a name="refresh-from-database"></a>Refresh-from-Database:  
Der Befehl **Refresh-from-Database** weist einen **Report-Errors-to-Parameter auf** , der den Speicherort des Fehlerberichts für den Aktualisierungs Vorgang angibt. Anschließend wird eine Datei namens **sourcedbrefreshreport &lt; n angezeigt &gt; . XML** wird an der angegebenen Position erstellt, wobei ** &lt; n &gt; ** die eindeutige Dateinummer ist, die mit jeder Ausführung desselben Befehls mit einer Ziffer Inkrementen erhöht.  
  
**Hinweis:** Wenn der Ordner Pfad angegeben ist, wird der Parameter "Report-Errors-to" ein optionales Attribut für den Befehl "Synchronisieren-Ziel".  
  
```  
<!-- Example: Refresh entire Schema (with all attributes)-->  
  
<refresh-from-database  
  
   object-name="<object-name>"  
  
   object-type ="<object-type>"  
  
   on-error="report-total-as-warning/report-each-as-warning/fail-script"  
  
   report-errors-to="<file-name/folder-name>"/>  
```  
**Objektname:** Gibt die Objekte an, die für die Aktualisierung berücksichtigt werden (Sie können auch individuellen-Objektnamen oder ein Gruppen Objektname aufweisen).  
  
**bei Fehler:** Gibt an, ob Aktualisierungs Fehler als Warnungen oder Fehler angegeben werden sollen. Verfügbare Optionen für "bei Fehler":  
  
-   Bericht-gesamt-als-Warnung  
  
-   Bericht-jeder-als-Warnung  
  
-   Fehler-Skript  
  
## <a name="see-also"></a>Weitere Informationen  
[Ausführen der SSMA-Konsole](./executing-the-ssma-console-db2tosql.md)  
