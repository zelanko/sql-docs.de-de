---
title: Generieren von Berichten (AccessToSQL) | Microsoft-Dokumentation
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: abb4264a-622e-4215-af5b-14e309b8a399
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: fe6f45b2e35761fac5f8c49012b1eb370645bcb1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62759494"
---
# <a name="generating-reports-accesstosql"></a>Generieren von Berichten (AccessToSQL)
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
    |4|Synchronisieren von Ziel|TargetSynchronizationReport&lt;n&gt;.XML|  
    |5|refresh-from-database|SourceDBRefreshReport&lt;n&gt;.XML|  
  
    > [!IMPORTANT]  
    > Ein Ausgabebericht unterscheidet sich von Bewertungsbericht. Die erste ist ein Bericht auf die Leistung eines ausgeführten Befehls beim, Letzteres ist ein XML-Bericht für die programmgesteuerte Nutzung.  
  
    Für den Befehlsoptionen für das Ausgabeberichte (von Sl. Nein. 2 bis 4 oben), finden Sie in der [Executing the SSMA Console ausführen &#40;AccessToSQL&#41; ](../../ssma/access/executing-the-ssma-console-accesstosql.md) Abschnitt.  
  
2.  Geben Sie den Umfang der Informationen in den Ausgabebericht mithilfe der Einstellungen für die Ausführlichkeit der Bericht das gewünschte:  
  
    ||||  
    |-|-|-|  
    |**Sl. Nein.**|**Installationsbefehl und Parametersatz**|**Ausgabe-Beschreibung**|  
    |1|verbose="false"|Generiert einen zusammenfassenden Bericht der Aktivität.|  
    |2|verbose="true"|Generiert einen zusammengefassten und detaillierten Statusbericht für jede Aktivität an.|  
  
    > [!NOTE]  
    > Die oben angegebenen Einstellungen für die Ausführlichkeit gelten für generieren – Bewertungsbericht, Convert-Schema, das Migrieren von Datenbefehlen.  
  
3.  Geben Sie den Umfang der Informationen, die Sie in die Fehlerberichte, die mit den Einstellungen für Fehlerberichterstattung wünschen:  
  
    ||||  
    |-|-|-|  
    |**Sl. Nein.**|**Installationsbefehl und Parametersatz**|**Ausgabe-Beschreibung**|  
    |1|report-errors="false"|Keine Details zu Fehler / Warnung / Info-Nachrichten.|  
    |2|report-errors="true"|Detaillierter Fehler / Warnung / Info-Nachrichten.|  
  
    > [!NOTE]  
    > Die Einstellungen für Fehlerberichterstattung oben angegebenen gelten für generieren – Bewertungsbericht, Convert-Schema, das Migrieren von Datenbefehlen.  
  
**Beispiel:**  
  
```xml  
<generate-assessment-report  
  
    object-name="testschema"  
  
    object-type="Schemas"  
  
    verbose="yes"  
  
    report-erors="yes"  
  
    write-summary-report-to="$AssessmentFolder$\Report1.xml"  
  
    assessment-report-folder="$AssessmentFolder$\assesment_report"  
  
    assessment-report-overwrite="true"  
  
/>  
```  
  
### <a name="synchronize-target"></a>Synchronisieren von Ziel:  
Der Befehl **synchronisieren-Ziel** hat **Bericht-Fehler-to** -Parameter, der den Speicherort der Fehlerbericht für den Synchronisierungsvorgang angibt. Klicken Sie dann eine Datei namens **TargetSynchronizationReport&lt;n&gt;. XML** wird erstellt, an der angegebenen Position, in denen **&lt;n&gt;** ist die Anzahl von eindeutigen Dateinamen, die mit einer Ziffer bei jeder Ausführung desselben Befehls inkrementiert.  
  
**Hinweis**: Wenn der Ordnerpfad angegeben ist, wird 'Bericht-Fehler-to'-Parameter ein optionales Attribut für "zu synchronisieren: das Ziel des Befehls".  
  
```xml  
<!-- Example: Synchronize target entire Database with all attributes-->  
  
<synchronize-target  
  
    object-name="$TargetDB$.dbo"  
  
    on-error="fail-script"  
  
    report-errors-to="$SynchronizationReports$"  
  
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
  
    object-name="$SourceDatabaseStandard$"  
  
    object-type ="Databases"  
  
    on-error="fail-script"  
  
    report-errors-to="$RefreshDBFolder$\RefreshReport.xml"  
  
/>  
```  
**object-name:** Gibt an, die Objekte, die für aktualisieren (es kann auch zu individuellen-Objektnamen oder einen Gruppennamen für das Objekt haben) in Betracht gezogen.  
  
**on-error:** Gibt an, ob die datenaktualisierung Fehler als Warnungen oder Fehler angegeben. Verfügbare Optionen für in-Fehler:  
  
-   Bericht insgesamt als Warnung  
  
-   report-each-as-warning  
  
-   fail-script  
  
## <a name="see-also"></a>Siehe auch  
[Ausführen der SSMA-Konsole (Datenzugriff)](https://msdn.microsoft.com/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
