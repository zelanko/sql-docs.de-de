---
title: Generieren von Berichten (SybaseToSQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Sybase Console,generating reports
- Sybase Console,refresh-from-database report
- Sybase Console,synchronize-target report
ms.assetid: 19278f6a-6d58-4867-9d71-c6228040466e
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: bb377e36f73bad59da35fabc2f6e9189544230e1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63126293"
---
# <a name="generating-reports-sybasetosql"></a>Generieren von Berichten (SybaseToSQL)
Die Berichte bestimmte Aktivitäten, die mithilfe der Befehle ausgeführt werden in der SSMA-Konsole auf Objektebene-Struktur generiert.  
  
Verwenden Sie das folgende Verfahren zum Generieren von Berichten:  
  
1.  Geben Sie die **Write-Summary-Meldung an** Parameter. Der verknüpfte Bericht wird als Dateiname gespeichert (falls angegeben), oder geben Sie im Ordner "". Der Dateiname ist System vordefiniert sein, wie in der Tabelle unten, wo, **&lt;n&gt;** ist die Anzahl von eindeutigen Dateinamen, die mit einer Ziffer bei jeder Ausführung desselben Befehls inkrementiert.  
  
    Die Berichte Vis gegenüber Befehle sind:  
  
    ||||  
    |-|-|-|  
    |**Sl. Nein.**|**Befehl**|**Titel des Berichts**|  
    |1|Generieren von Bewertungsbericht|AssessmentReport&lt;n&gt;.XML|  
    |2|convert-schema|SchemaConversionReport&lt;n&gt;.XML|  
    |3|migrate-data|DataMigrationReport&lt;n&gt;.XML|  
    |4|convert-sql-statement|ConvertSQLReport&lt;n&gt;.XML|  
    |5|Synchronisieren von Ziel|TargetSynchronizationReport&lt;n&gt;.XML|  
    |6|refresh-from-database|SourceDBRefreshReport&lt;n&gt;.XML|  
  
    > [!IMPORTANT]  
    > Ein Ausgabebericht unterscheidet sich von Bewertungsbericht. Die erste ist ein Bericht auf die Leistung eines ausgeführten Befehls beim, Letzteres ist ein XML-Bericht für die programmgesteuerte Nutzung.  
  
    Für den Befehlsoptionen für das Ausgabeberichte (von Sl. Nein. 2 bis 4 oben), finden Sie in der [Executing the SSMA Console ausführen &#40;SybaseToSQL&#41; ](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md) Abschnitt.  
  
2.  Geben Sie den Umfang der Informationen in den Ausgabebericht mithilfe der Einstellungen für die Ausführlichkeit der Bericht das gewünschte:  
  
    ||||  
    |-|-|-|  
    |**Sl. Nein.**|**Installationsbefehl und Parametersatz**|**Ausgabe-Beschreibung**|  
    |1|verbose="false"|Generiert einen zusammenfassenden Bericht der Aktivität.|  
    |2|verbose="true"|Generiert einen zusammengefassten und detaillierten Statusbericht für jede Aktivität an.|  
  
    > [!NOTE]  
    > Die oben angegebenen Einstellungen für die Ausführlichkeit gelten für generieren – Bewertungsbericht "," Convert-Schema "," Migrieren von Daten "," Convert-Sql-Anweisung Befehle zur Verfügung.  
  
3.  Geben Sie den Umfang der Informationen, die Sie in die Fehlerberichte, die mit den Einstellungen für Fehlerberichterstattung wünschen:  
  
    ||||  
    |-|-|-|  
    |**Sl. Nein.**|**Installationsbefehl und Parametersatz**|**Ausgabe-Beschreibung**|  
    |1|report-errors="false"|Keine Details zu Fehler / Warnung / Info-Nachrichten.|  
    |2|report-errors="true"|Detaillierter Fehler / Warnung / Info-Nachrichten.|  
  
    > [!NOTE]  
    > Die Einstellungen für Fehlerberichterstattung oben angegebenen gelten für generieren – Bewertungsbericht "," Convert-Schema "," Migrieren von Daten "," Convert-Sql-Anweisung Befehle zur Verfügung.  
  
```xml  
<generate-assessment-report  
  
    object-name="<object-name>"  
  
    object-type="<object-type>"  
  
    verbose="<true/false>"  
  
    report-erors="<true/false>"  
  
    write-summary-report-to="<file-name/folder-name>"  
  
    assessment-report-folder="<folder-name>"  
  
    assessment-report-overwrite="<true/false>"  
  
/>  
```  
  
### <a name="synchronize-target"></a>Synchronisieren von Ziel:  
Der Befehl **synchronisieren-Ziel** hat **Bericht-Fehler-to** -Parameter, der den Speicherort der Fehlerbericht für den Synchronisierungsvorgang angibt. Klicken Sie dann eine Datei namens **TargetSynchronizationReport&lt;n&gt;. XML** wird erstellt, an der angegebenen Position, in denen **&lt;n&gt;** ist die Anzahl von eindeutigen Dateinamen, die mit einer Ziffer bei jeder Ausführung desselben Befehls inkrementiert.  
  
**Hinweis**: Wenn der Ordnerpfad angegeben ist, wird 'Bericht-Fehler-to'-Parameter ein optionales Attribut für "zu synchronisieren: das Ziel des Befehls".  
  
```xml  
<!-- Example: Synchronize target entire Database with all attributes-->  
  
<synchronize-target  
  
    object-name="<object-name>"  
  
    on-error="<object-type>"  
  
    report-errors-to="<file-name/folder-name>"  
  
/>  
```  
**object-name:** Gibt an, die Objekte, die für die Synchronisierung (es kann auch zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt haben) in Betracht gezogen.  
  
**on-error:** Gibt an, ob die Synchronisierungsfehler als Warnungen oder Fehler angegeben. Verfügbare Optionen für in-Fehler:  
  
-   Bericht insgesamt als Warnung  
  
-   report-each-as-warning  
  
-   fail-script  
  
### <a name="refresh-from-database"></a>refresh-from-database:  
Der Befehl **Aktualisierung-in-Database** hat **Bericht-Fehler-to** -Parameter, der den Speicherort der Fehlerbericht für den Aktualisierungsvorgang angibt. Klicken Sie dann eine Datei namens **SourceDBRefreshReport&lt;n&gt;. XML** wird erstellt, an der angegebenen Position, in denen **&lt;n&gt;** ist die Anzahl von eindeutigen Dateinamen, die mit einer Ziffer bei jeder Ausführung desselben Befehls inkrementiert.  
  
**Hinweis**: Wenn der Ordnerpfad angegeben ist, wird 'Bericht-Fehler-to'-Parameter ein optionales Attribut für "zu synchronisieren: das Ziel des Befehls".  
  
```xml  
<!-- Example: Refresh entire Schema (with all attributes)-->  
  
<refresh-from-database  
  
    object-name="<object-name>"  
  
    object-type ="<object-type>"  
  
    on-error="report-total-as-warning/report-each-as-warning/fail-script"  
  
    report-errors-to="<file-name/folder-name> "  
  
/>  
```  
**object-name:** Gibt an, die Objekte, die für aktualisieren (es kann auch zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt haben) in Betracht gezogen.  
  
**on-error:** Gibt an, ob die datenaktualisierung Fehler als Warnungen oder Fehler angegeben. Verfügbare Optionen für in-Fehler:  
  
-   Bericht insgesamt als Warnung  
  
-   report-each-as-warning  
  
-   fail-script  
  
## <a name="see-also"></a>Siehe auch  
[Executing the SSMA Console ausführen (Sybase)](https://msdn.microsoft.com/ea8950b7-fabc-4aa4-89f8-9573a2617d70)  
  
