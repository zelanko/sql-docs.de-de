---
title: Azure Data Lake Analytics-Task | Microsoft-Dokumentation
description: Mithilfe der Data Lake Analytics-Tasks können Sie U-SQL-Aufträge an den Azure Data Lake Analytics-Dienst übermitteln.
ms.custom: ''
ms.date: 05/18/2018
ms.prod: sql
ms.prod_service: integration-services
ms.component: control-flow
ms.reviewer: douglasl
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSTASK.F1
- SQL14.DTS.DESIGNER.AFPADLSTASK.F1
author: yanancai
ms.author: yanacai
manager: craigg
ms.openlocfilehash: b402ebedc1a0f827501da7ecfcb2494c2dbc1dd1
ms.sourcegitcommit: 84cc5ed00833279da3adbde9cb6133a4e788ed3f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2018
ms.locfileid: "39216811"
---
# <a name="azure-data-lake-analytics-task"></a>Azure Data Lake Analytics-Task

Mithilfe der Data Lake Analytics-Tasks können Sie U-SQL-Aufträge an den Azure Data Lake Analytics-Dienst übermitteln. Der Task ist eine Komponente des [SQL Server Integration Services-Feature Packs (SSIS) für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Allgemeine Hintergrundinformationen finden Sie unter [Azure Data Lake Analytics](https://azure.microsoft.com/services/data-lake-analytics/).

## <a name="configure-the-task"></a>Konfigurieren des Task

Ziehen Sie den Task von der SSIS-Toolbox in die Designercanvas, um diesen zu einem Paket hinzuzufügen. Doppelklicken Sie dann auf den Task, oder klicken Sie mit der rechten Maustaste auf den Task und wählen Sie **Bearbeiten**. Das Dialogfeld **Azure Data Lake Analytics-Task-Editor** wird geöffnet. Sie können Eigenschaften programmgesteuert oder mit dem SSIS-Designer festlegen.

## <a name="general-page-configuration"></a>Konfiguration auf der Seite „Allgemein“

Über die Seite **Allgemein** können Sie den Task konfigurieren und das U-SQL-Skript bereitstellen, dass den Task übermittelt. Weitere Informationen zur U-SQL-Sprache finden Sie in der [U-SQL-Sprachreferenz](https://msdn.microsoft.com/azure/data-lake-analytics/u-sql/u-sql-language-reference).

### <a name="basic-configuration"></a>Basiskonfiguration

Geben Sie den Namen und die Beschreibung der Task an.

### <a name="u-sql-configuration"></a>U-SQL-Konfiguration

Für die U-SQL-Konfiguration gibt es zwei Einstellungen: **SourceType** und dynamische Optionen basierend auf dem Wert **SourceType**. 

**SourceType:** Gibt die Quelle des U-SQL-Skripts an. Das Skript wird während der SSIS-Paketausführung an ein Data Lake Analytics-Konto übermittelt. Die Optionen für diese Eigenschaft sind:

|value|und Beschreibung|  
|-----------|-----------------|  
|**DirectInput**|Gibt das U-SQL-Skript durch den Inline-Editor an. Bei Auswahl dieses Werts wird die dynamische Option **USQLStatement** angezeigt.|  
|**FileConnection**|Legt eine lokale .usql-Datei fest, die das U-SQL-Skript enthält. Bei Auswahl dieser Option wird die dynamische Option **FileConnection** angezeigt.|  
|**Variable**|Legt eine lokale SSIS-Variable fest, die das U-SQL-Skript enthält. Bei Auswahl dieses Wertes wird die dynamische Option **SourceVariable**angezeigt.|

**SourceType (dynamische Optionen):** Legt den Inhalt des Skripts für die U-SQL-Abfrage fest. 

|SourceType|Dynamische Optionen|  
|-----------|-----------------|  
|**SourceType = DirectInput**|Geben Sie die zu übermittelnde U-SQL-Abfrage direkt in das Optionsfeld ein, oder wählen Sie die Schaltfläche zum Durchsuchen (...), um die U-SQL-Abfrage im Dialogfeld **U-SQL-Abfrage eingeben** anzugeben.|  
|**SourceType = FileConnection**|Wählen Sie einen vorhandenen Dateiverbindungs-Manager aus, oder wählen Sie <**Neue Verbindung...**>, um eine neue Dateiverbindung zu erstellen. Weitere Informationen finden Sie in [File Connection Manager](../../integration-services/connection-manager/file-connection-manager.md) und [Dateiverbindungs-Manager-Editor](../../integration-services/connection-manager/file-connection-manager-editor.md).|  
|**SourceType = Variable**|Wählen Sie eine vorhandene Variable aus, oder wählen Sie \<**Neue Variable...**>, um eine neue Variable zu erstellen. Weitere Informationen finden Sie in [Integration Services-Variablen&#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md) und [Hinzufügen einer Variable](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5).|


### <a name="job-configuration"></a>Auftragskonfiguration
In der Auftragskonfiguration werden die Eigenschaften für die U-SQL-Auftragsübermittlung festgelegt.

- **AzureDataLakeAnalyticsConnection:** Gibt das Data Lake Analytics-Konto für die Übermittlung des U-SQL-Skripts an. Wählen Sie die Verbindung aus einer Liste definierter Verbindungs-Manager aus. Klicken Sie zum Erstellen einer neuen Verbindung auf <**Neue Verbindung...**>. Weitere Informationen finden Sie in [Azure Data Lake Analytics-Verbindungs-Manager](../../integration-services/connection-manager/azure-data-lake-analytics-connection-manager.md).

- **JobName:** Gibt den Namen des U-SQL-Auftrags an. 
- **AnalyticsUnits:** Gibt die Anzahl der Analytics-Einheiten des U-SQL-Auftrags an.
- **Priority:** Gibt die Priorität des U-SQL-Auftrags an. Sie können einen Wert zwischen 0 und 1.000 angeben. Je niedriger die Zahl ist, desto höher ist die Priorität.
- **RuntimeVersion:** Gibt die Data Lake Analytics-Runtimeversion des U-SQL-Auftrags an. Die Standardeinstellung lautet „Standard“. In der Regel müssen Sie diese Eigenschaft nicht ändern.
- **Synchronous:** Ein boolescher Wert gibt an, ob der Task auf den Abschluss der Auftragsausführung wartet, oder nicht. Wenn der Wert auf „true“ festgelegt wird, ist die Aufgabe nach Abschluss des Auftrags als **erfolgreich** gekennzeichnet. Wenn der Wert auf „false“ festgelegt wird, ist die Aufgabe nach als **erfolgreich** gekennzeichnet, wenn der Auftrag die Vorbereitungsphase durchlaufen hat.

  |value|und Beschreibung|
  |-----------|-----------------|
  |Wahr|Das Taskergebnis basiert auf dem Ausführungsergebnis des U-SQL-Auftrags. Auftragsausführung erfolgreich > Aufgabe erfolgreich. Fehler beim Auftrag > Fehler in der Aufgabe. Aufgabe erfolgreich oder mit Fehler > Aufgabe wird abgeschlossen.|
  |False|Das Taskergebnis basiert auf dem Übermittlungs- und Vorbereitungsergebnis des U-SQL-Auftrags. Auftragsübermittlung ist erfolgreich und durchläuft die Vorbereitungsphase > Aufgabe ist erfolgreich. Fehler in Auftragsübermittlung oder Fehler in der Vorbereitungsphase des Auftrags > Fehler in Aufgabe. Aufgabe erfolgreich oder mit Fehler > Aufgabe wird abgeschlossen.|

- **TimeOut:** Legt ein Zeitlimit in Sekunden für die Auftragsausführung fest. Wenn beim Auftrag ein Timeout auftritt, wird der Auftrag storniert und als fehlerhaft gekennzeichnet. Diese Eigenschaft ist nicht verfügbar, wenn **Synchronous** auf „false“ gesetzt ist.

## <a name="parameter-mapping-page-configuration"></a>Konfiguration auf der Seite „Parameterzuordnung“

Über die Seite **Parameterzuordnung** des Dialogfelds **Azure Data Lake Analytics-Task-Editor** können Sie Variablen zu Parametern (U-SQL-Variablen) im U-SQL-Skript zuordnen.

- **Variable Name:** Nachdem Sie eine Parameterzuordnung durch Auswahl von **Hinzufügen** hinzugefügt haben, wählen Sie eine System- oder benutzerdefinierte Variable aus der Liste aus. Alternativ können Sie <**Neue Variable...** > auswählen, um über das Dialogfeld **Variable hinzufügen** eine neue Variable hinzuzufügen. Weitere Informationen finden Sie unter [Integration Services-Variablen &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md).  

- **Parametername:** Geben Sie einen Parameter- bzw. Variablennamen im U-SQL-Skript an. Stellen Sie sicher, dass der Parametername mit dem \@-Zeichen beginnt, z.B. \@Param1. 

Hier sehen Sie ein Beispiel für die Übergabe von Parametern an ein U-SQL-Skript.

**Beispiel-U-SQL-Skript**
```
@searchlog =
    EXTRACT UserId          int,
            Start           DateTime,
            Region          string,
            Query           string,
            Duration        int,
            Urls            string,
            ClickedUrls     string
    FROM @in
    USING Extractors.Tsv(nullEscape:"#NULL#");

@rs1 =
    SELECT Start, Region, Duration
    FROM @searchlog
WHERE Region == "en-gb";

@rs1 =
    SELECT Start, Region, Duration
    FROM @rs1
    WHERE Start <= DateTime.Parse("2012/02/19");

OUTPUT @rs1   
    TO @out
      USING Outputters.Tsv(quoting:false, dateTimeFormat:null);
```

Beachten Sie, dass die Eingabe- und Ausgabepfade in den Parametern **\@in** and **\@out** definiert sind. Die Werte für die Parameter **\@in** und **\@out** im U-SQL-Skript werden dynamisch durch die konfigurierte Parameterzuordnung übergeben.

|Variablenname|Parametername|
|-------------|--------------|
|Benutzer: Variable1|\@in|
|Benutzer: Variable2|\@out| 

## <a name="expression-page-configuration"></a>Konfiguration auf der Seite „Ausdruck“

Alle Eigenschaften in der Konfiguration auf der Seite „Allgemein“ können als Eigenschaftsausdruck zugewiesen werden, um ein dynamisches Update der Eigenschaft zur Runtime zu ermöglichen. Weitere Informationen finden Sie unter [Verwenden von Eigenschaftsausdrücken in Paketen](../../integration-services/expressions/use-property-expressions-in-packages.md).

## <a name="see-also"></a>Siehe auch
- [Azure Data Lake Analytics-Verbindungs-Manager](../../integration-services/connection-manager/azure-data-lake-analytics-connection-manager.md)
- [Azure Data Lake Store-Dateisystemtask](../../integration-services/control-flow/azure-data-lake-store-file-system-task.md)
- [Azure Data Lake Store Connection Manager (Azure Data Lake Store-Verbindungs-Manager)](../../integration-services/connection-manager/azure-data-lake-store-connection-manager.md)

