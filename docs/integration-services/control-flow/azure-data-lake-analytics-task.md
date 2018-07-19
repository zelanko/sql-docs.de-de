---
title: Azure Data Lake Analytics-Task | Microsoft-Dokumentation
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
ms.openlocfilehash: 395d790069294aed541f9756fa7caefbb62f9a7b
ms.sourcegitcommit: 44e9bf62f2c75449c17753ed66bf85c43928dbd5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2018
ms.locfileid: "37854420"
---
# <a name="azure-data-lake-analytics-task"></a>Azure Data Lake Analytics-Task

Mithilfe des Azure Data Lake Analytics-Tasks können Benutzer U-SQL-Aufträge an den Azure Data Lake Analytics-Dienst übermitteln. [Azure Data Lake Analytics (ADLA)](https://azure.microsoft.com/services/data-lake-analytics/).

Der Azure Data Lake Analytics-Task ist eine Komponente des [SQL Server Integration Services-Feature Packs (SSIS) für Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

## <a name="configure-the-azure-data-lake-analytics-task"></a>Konfigurieren des Azure Data Lake Analytics-Tasks

Ziehen Sie den Azure Data Lake Analytics-Task von der SSIS-Toolbox in die Designercanvas, um diesen zu einem Paket hinzuzufügen. Doppelklicken Sie anschließend auf den Task, oder klicken Sie mit der rechten Maustaste darauf, und klicken Sie auf **Bearbeiten**, um das Dialogfeld **Azure Data Lake Analytics-Task-Editor** zu öffnen. Sie können Eigenschaften programmgesteuert oder mit dem SSIS-Designer festlegen.

## <a name="general-page-configuration"></a>Konfiguration auf der Seite „Allgemein“

Über die Seite **Allgemein** können Sie den Azure Data Lake Analytics-Task konfigurieren und das U-SQL-Skript bereitstellen, dass den Task übermittelt. Weitere Informationen zur U-SQL-Sprache finden Sie in der [U-SQL-Sprachreferenz](https://msdn.microsoft.com/azure/data-lake-analytics/u-sql/u-sql-language-reference).

### <a name="basic-configuration"></a>Basiskonfiguration

- **Name:** Gibt den Namen des Azure Data Lake Analytics-Tasks an.
- **Beschreibung:** Gibt die Beschreibung des Azure Data Lake Analytics-Tasks an.

### <a name="u-sql-configuration"></a>U-SQL-Konfiguration

Für die U-SQL-Konfiguration gibt es zwei Einstellungen: **SourceType** und dynamische Optionen basierend auf dem Wert **SourceType**. 

- **SourceType:** Gibt die Quelle des U-SQL-Skripts an. Das Skript wird während der SSIS-Paketausführung an ein Azure Data Lake Analytics-Konto übermittelt. Für diese Eigenschaft sind die in der folgenden Tabelle aufgeführten drei Optionen verfügbar.

|Wert|Beschreibung|  
|-----------|-----------------|  
|**DirectInput**|Gibt das U-SQL-Skript durch den Inline-Editor an. Bei Auswahl dieses Werts wird die dynamische Option **USQLStatement** angezeigt.|  
|**FileConnection**|Legt eine lokale .usql-Datei fest, die das U-SQL-Skript enthält. Bei Auswahl dieser Option wird die dynamische Option **FileConnection** angezeigt.|  
|**Variable**|Legt eine lokale SSIS-Variable fest, die das U-SQL-Skript enthält. Bei Auswahl dieses Wertes wird die dynamische Option **SourceVariable**angezeigt.|

- **SourceType (dynamische Optionen):** Legt den Inhalt des Skripts für die U-SQL-Abfrage fest. 

|SourceType|Dynamische Optionen|  
|-----------|-----------------|  
|**SourceType = DirectInput**|Geben Sie die zu übermittelnde U-SQL-Abfrage direkt in das Optionsfeld ein, oder klicken Sie auf die Schaltfläche zum Durchsuchen (...), um die U-SQL-Abfrage im Dialogfeld **U-SQL-Abfrage eingeben** anzugeben.|  
|**SourceType = FileConnection**|Wählen Sie einen vorhandenen Dateiverbindungs-Manager aus, oder klicken Sie auf <**Neue Verbindung...**>, um eine neue Dateiverbindung zu erstellen. **Verwandte Themen:** [Dateiverbindungs-Manager](../../integration-services/connection-manager/file-connection-manager.md), [Dateiverbindungs-Manager-Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)|  
|**SourceType = Variable**|Wählen Sie eine vorhandene Variable aus, oder klicken Sie auf \<**Neue Variable...**>, um eine neue Variable zu erstellen. **Verwandte Themen:** [Integration Services-Variablen (SSIS)](../../integration-services/integration-services-ssis-variables.md), [Hinzufügen einer Variable](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)|


### <a name="job-configuration"></a>Auftragskonfiguration
In der Auftragskonfiguration werden die Eigenschaften für die U-SQL-Auftragsübermittlung festgelegt.

- **AzureDataLakeAnalyticsConnection:** Gibt das Azure Data Lake Analytics-Konto für die Übermittlung des U-SQL-Skripts an. Wählen Sie die Verbindung aus einer Liste definierter Verbindungs-Manager aus. Klicken Sie zum Erstellen einer neuen Verbindung auf <**Neue Verbindung...**>. Verwandter Artikel: [Azure Data Lake Analytics-Verbindungs-Manager](../../integration-services/connection-manager/azure-data-lake-analytics-connection-manager.md)

- **JobName:** Gibt den Namen des U-SQL-Auftrags an. 
- **AnalyticsUnits:** Gibt die Anzahl der Analytics-Einheiten des U-SQL-Auftrags an.
- **Priority:** Gibt die Priorität des U-SQL-Auftrags an. Für die Priorität kann ein Wert von 0 bis 1000 festgelegt werden, wobei ein niedrigerer Wert für eine höhere Priorität steht.
- **RuntimeVersion:** Gibt die Azure Data Lake Analytics-Runtimeversion des U-SQL-Auftrags an. Die Standardeinstellung lautet „Standard“. In der Regel müssen Sie diese Eigenschaft nicht ändern.
- **Synchronous:** Ein boolescher Wert gibt an, ob der Task auf den Abschluss der Auftragsausführung wartet, oder nicht. Wird diese Option auf TRUE gesetzt, wird der Task als „erfolgreich“ gekennzeichnet, nachdem der Auftrag abgeschlossen ist. Wird die Option auf FALSE gesetzt, wird der Task als „erfolgreich“ gekennzeichnet, sobald der Auftrag die Vorbereitungsphase durchlaufen hat.

|Wert|Beschreibung|
|-----------|-----------------|
|TRUE|Das Taskergebnis basiert auf dem Ausführungsergebnis des U-SQL-Auftrags. Auftrag erfolgreich --> Task erfolgreich; Auftrag nicht erfolgreich --> Task nicht erfolgreich; Task erfolgreich oder nicht erfolgreich --> Task wird abgeschlossen.|
|FALSE|Das Taskergebnis basiert auf dem Übermittlungs- und Vorbereitungsergebnis des U-SQL-Auftrags. Auftragsübermittlung erfolgreich und Vorbereitungsphase abgeschlossen --> Task erfolgreich; Auftragsübermittlung nicht erfolgreich oder Vorbereitungsphase des Auftrags nicht erfolgreich --> Task nicht erfolgreich; Task erfolgreich oder nicht erfolgreich --> Task wird abgeschlossen.|

- **TimeOut:** Legt ein Zeitlimit in Sekunden für die Auftragsausführung fest. Der Auftrag wird abgebrochen, und der Task wird als „nicht erfolgreich“ gekennzeichnet, sobald das Zeitlimit für den Auftrag überschritten wurde. Die „TimeOut“-Eigenschaft ist nicht verfügbar, wenn „Synchronous“ auf FALSE gesetzt ist. Die „TimeOut“-Eigenschaft ist nicht verfügbar, wenn **Synchronous** auf **FALSE** gesetzt ist.

## <a name="parameter-mapping-page-configuration"></a>Konfiguration auf der Seite „Parameterzuordnung“

Über die Seite **Parameterzuordnung** des Dialogfelds **Azure Data Lake Analytics-Task-Editor** können Sie Variablen zu Parametern (U-SQL-Variablen) im U-SQL-Skript zuordnen.

- **Variablenname:** Nachdem Sie auf **Hinzufügen** geklickt und damit eine neue Parameterzuordnung hinzugefügt haben, wählen Sie in der Liste eine Systemvariable oder eine benutzerdefinierte Variable aus, oder klicken Sie auf \<**Neue Variable...**>, um mithilfe des Dialogfelds **Variable hinzufügen** eine neue Variable hinzuzufügen. **Verwandte Themen:** [Integration Services-Variablen &#40;SSIS&#41;](../../integration-services/integration-services-ssis-variables.md)  

- **Parametername:** Geben Sie einen Parameter- bzw. Variablennamen im U-SQL-Skript an. Stellen Sie sicher, dass der Parametername mit dem @-Zeichen beginnt, z.B. @Param1. 

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

Im oben gezeigten Skriptbeispiel sind die Eingabe- und Ausgabepfade in den Parametern **@in** und **@out** definiert. Die Werte für die Parameter **@in** und **@out** im U-SQL-Skript werden dynamisch durch die konfigurierte Parameterzuordnung übergeben.

|Variablenname|Parametername|
|-------------|--------------|
|Benutzer: Variable1|@in|
|Benutzer: Variable2|@out| 

## <a name="expression-page-configuration"></a>Konfiguration auf der Seite „Ausdruck“

Alle Eigenschaften der Konfiguration auf der Seite „Allgemein“ können als Eigenschaftsausdruck zugewiesen werden, um ein dynamisches Update der Eigenschaft zur Runtime zu ermöglichen. **Verwandte Themen:** [Verwenden von Eigenschaftsausdrücken in Paketen](../../integration-services/expressions/use-property-expressions-in-packages.md)

## <a name="see-also"></a>Weitere Informationen finden Sie unter
- [Azure Data Lake Analytics-Verbindungs-Manager](../../integration-services/connection-manager/azure-data-lake-analytics-connection-manager.md)
- [Azure Data Lake Store-Dateisystemtask](../../integration-services/control-flow/azure-data-lake-store-file-system-task.md)
- [Azure Data Lake Store Connection Manager (Azure Data Lake Store-Verbindungs-Manager)](../../integration-services/connection-manager/azure-data-lake-store-connection-manager.md)

