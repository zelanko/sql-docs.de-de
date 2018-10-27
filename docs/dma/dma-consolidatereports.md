---
title: Ein Unternehmen zu bewerten und Konsolidieren von assessmentberichten (SQL Server) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie mit DMA ein Unternehmens zu bewerten und Konsolidieren von assessmentberichten vor dem Upgrade von SQL Server oder die Migration zu Azure SQL-Datenbank.
ms.custom: ''
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: pochiraju
ms.author: rajpo
manager: craigg
ms.openlocfilehash: b7212118f018b616b1f82f3ed91aced97482e9c6
ms.sourcegitcommit: eddf8cede905d2adb3468d00220a347acd31ae8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2018
ms.locfileid: "49960784"
---
# <a name="assess-an-enterprise-and-consolidate-assessment-reports-with-dma"></a>Ein Unternehmen zu bewerten und Konsolidieren von assessmentberichten mit DMA

Die folgenden schrittweisen Anweisungen helfen Ihnen die im Data Migration Assistant verwenden, um eine erfolgreiche skalierte Bewertung für ein Upgrade auf einen lokalen SQL Server oder die Ausführung von SQL Server auf virtuellen Azure-Computern oder für die Migration zu Azure SQL-Datenbank auszuführen.

## <a name="prerequisites"></a>Erforderliche Komponenten

- Geben Sie einen Tools-Computer in Ihrem Netzwerk aus dem DMA initiiert wird. Stellen Sie sicher, dass es sich bei diesem Computer Verbindungen mit Ihrem SQL Server-Ziele vorhanden sind.
- Herunterladen und installieren:
    - [Data Migration Assistant](https://www.microsoft.com/download/details.aspx?id=53595) Version 3.6 oder höher.
    - [PowerShell](http://aka.ms/wmf5download) V5. 0 oder höher.
    - [.NET Framework](https://www.microsoft.com/download/details.aspx?id=30653) v4. 5 oder höher.
    - [SSMS](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) 17.0 oder höher.
    - [Power BI Desktop](https://docs.microsoft.com/power-bi/desktop-get-the-desktop).
- Herunterladen und extrahieren:
    - Die [DMA Berichte Power BI-Vorlage](https://msdnshared.blob.core.windows.net/media/2018/04/PowerBI-Reports1.zip).
    - Die [LoadWarehouse Skript](https://msdnshared.blob.core.windows.net/media/2018/10/LoadWarehouse.zip).

## <a name="loading-the-powershell-modules"></a>Laden die PowerShell-Module
Die PowerShell-Module in der PowerShell-Module-Verzeichnis zu speichern, können Sie rufen die Module, ohne dass sie vor der Verwendung explizit zu laden.

Führen Sie die folgenden Schritte aus, um die Module zu laden:
1. Navigieren Sie zu c:\Programme\Microsoft Files\WindowsPowerShell\Modules, und erstellen Sie einen Ordner mit dem Namen **DataMigrationAssistant**.
2. Öffnen der [PowerShell-Module](https://msdnshared.blob.core.windows.net/media/2018/10/PowerShell-Modules.zip), und speichern Sie sie in den Ordner, die Sie erstellt haben.

      ![PowerShell-Module](../dma/media//dma-consolidatereports/dma-powershell-modules.png)

    Jeder Ordner enthält die zugeordneten psm1-Datei, wie in der folgenden Abbildung gezeigt:

   ![PowerShell-Module psm1-Dateien](../dma/media//dma-consolidatereports/dma-powershell-modules-psm1-files.png)

   > [!NOTE]
   > Die Ordner und die darin enthaltenen psm1-Datei müssen den gleichen Namen verfügen.

   > [!IMPORTANT]
   > Sie müssen die PowerShell-Dateien zu entsperren, nach dem Speichern in das Verzeichnis "WindowsPowerShell", um sicherzustellen, dass die Module, die ordnungsgemäß geladen. Um eine PowerShell-Datei zu entsperren, Öffnen der Datei, die Option **Eigenschaften**, wählen die **Unblock** Textfeld ein, und wählen Sie dann **Ok**.

   ![Eigenschaften der psm1-Datei](../dma/media//dma-consolidatereports/dma-psm1-file-properties.png)

    PowerShell sollte diese Module jetzt automatisch geladen, wenn eine neue PowerShell-Sitzung gestartet wird.

## <a name="create-inventory"></a> Erstellen Sie eine Inventur der SQL-Server
Vor dem Ausführen des PowerShell-Skripts, um Ihre SQL Server zu bewerten, müssen Sie eine Inventur der SQL Server zu erstellen, die Sie bewerten möchten.

Diese Inventur kann eine von zwei Formen aufweisen:
- Excel-CSV-Datei
- SQL Server-Tabelle

### <a name="if-using-a-csv-file"></a>Wenn Sie eine CSV-Datei verwenden.
Verwendung von Csv-Datei zum Importieren der Daten sicherzustellen, dass nur zwei Spalten mit Daten – **Instanzname** und **Datenbanknamen**, und dass die Spalten keine Kopfzeilen enthalten.
 
 ![Inhalt der CSV-Datei](../dma/media//dma-consolidatereports/dma-csv-file-contents.png)

### <a name="if-using-sql-server-table"></a>Bei Verwendung von SQL Server-Tabelle
Erstellen Sie eine Datenbank namens **EstateInventory** und eine Tabelle namens **DatabaseInventory**. Die Tabelle mit den Inventurdaten kann eine beliebige Anzahl von Spalten aufweisen, solange die folgende vier Spalten vorhanden sind:
- ServerName
- InstanceName
- DatabaseName
- AssessmentFlag

![Inhalt der SQL Server-Tabelle](../dma/media//dma-consolidatereports/dma-sql-server-table-contents.png)

Wenn dieser Datenbank nicht auf dem Computer des Tools befindet, stellen Sie sicher, dass die Tools-Computer über eine Netzwerkverbindung mit SQL Server-Instanz verfügt.

Der Vorteil der Verwendung einer SQL Server-Tabelle über eine CSV-Datei ist, dass Sie die Spalte zur Kennzeichnung Bewertung verwenden können, steuern die Instanz oder Datenbank, ruft für die Bewertung,, erleichtern übernommen, Bewertungen in kleinere Blöcke zu trennen.  Sie können dann mehrere Bewertungen umfassen (siehe Abschnitt zum Ausführen einer Bewertung von später in diesem Artikel), dies ist einfacher als mehrere CSV-Dateien zu verwalten.

Bedenken Sie, dass abhängig von der Anzahl von Objekten und ihrer Komplexität, eine Bewertung kann ein außergewöhnlich lange (Stunden +), dauern daher ist es ratsam, um die Bewertung in verwaltbare Teile zu trennen.

## <a name="running-a-scaled-assessment"></a>Eine skalierte Bewertung wird ausgeführt
Nach dem Laden die PowerShell-Module in das Modulverzeichnis, und erstellen eine Inventur, müssen Sie eine skalierte Bewertung ausgeführt wird, öffnen PowerShell, und die DmaDataCollector-Funktion ausführt.
 
  ![Angebote für DmaDataCollector-Funktion](../dma/media//dma-consolidatereports/dma-dmaDataCollector-function-listing.png)

Die Parameter der Funktion DmaDataCollector zugeordnet werden in der folgenden Tabelle beschrieben.

|Parameter  |Description
|---------|---------|
|**getServerListFrom** | Ihr Inventar. Mögliche Werte sind **SqlServer** und **CSV**.<br/>Weitere Informationen finden Sie unter [Erstellung eines Inventars aus SQL Server-Instanzen](#create-inventory). |
|**serverName** | Die Namen der SQL Server-Instanz des Bestands Verwendung **SqlServer** in die **GetServerListFrom** Parameter. |
|**databaseName** | Die Datenbank, die die Bestandstabelle hosten. |
|**%Assessmentname** | Der Name des der DMA-Bewertung. |
|**TargetPlatform** | Der Zieltyp für die Bewertung, den Sie ausführen möchten.  Mögliche Werte sind **"azuresqldatabase"**, **SQLServer2012**, **SQLServer2014**, **SQLServer2016**,  **SQLServerLinux2017**, und **SQLServerWindows2017**. |
|**AuthenticationMethod** | Die Authentifizierungsmethode für die Verbindung mit der SQL Server-Ziele, die Sie bewerten möchten. Mögliche Werte sind **SQLAuth** und **WindowsAuth**. |
|**OutputLocation** | Das Verzeichnis, in dem die JSON-Speicherung Bewertung der Ausgabedatei. Abhängig von der Anzahl der Datenbanken, die bewertet wird und die Anzahl der Objekte in Datenbanken können die Bewertungen außergewöhnlich lange dauern. Nachdem alle Bewertungen abgeschlossen haben, wird die Datei geschrieben werden. |

Ist ein unerwarteter Fehler, wird das Befehlsfenster, das von diesem Prozess initiiert hat, ruft beendet.  Überprüfen Sie das Fehlerprotokoll, um zu bestimmen, warum ein Fehler aus.
 
  ![Speicherort des Fehlerprotokolls](../dma/media//dma-consolidatereports/dma-error-log-file-location.png)

## <a name="consuming-the-assessment-json-file"></a>Nutzen die Bewertung der JSON-Datei

Nach Abschluss der Bewertung können Sie sich nun um die Daten in SQL Server für die Analyse importieren. Um die Bewertung der JSON-Datei nutzen zu können, öffnen Sie PowerShell, und führen Sie die DmaProcessor-Funktion.
 
  ![Liste der DmaProcessor-Funktion](../dma/media//dma-consolidatereports/dma-dmaProcessor-function-listing.png)

Die Parameter der Funktion DmaProcessor zugeordnet werden in der folgenden Tabelle beschrieben.

|Parameter  |Description
|---------|---------|
|**processTo**  | Der Speicherort, zu dem die JSON-Datei verarbeitet werden. Mögliche Werte sind **SQLServer** und **"azuresqldatabase"**. |
|**serverName** | Die SQL Server-Instanz, auf die Daten verarbeitet werden.  Bei Angabe von **"azuresqldatabase"** für die **ProcessTo** Parameter, fügen Sie dann nur die Namen der SQL Server (nicht enthalten. database.windows.net). Sie werden für zwei Anmeldungen aufgefordert werden, bei der Azure SQL-Datenbank als Ziel; die erste ist der Anmeldeinformationen Ihres Azure-Mandanten, während die zweite die administratoranmeldung für den Azure SQL-Server ist. |
|**CreateDMAReporting** | Die Stagingdatenbank, für die Verarbeitung der JSON-Datei zu erstellen.  Wenn die Datenbank bereits vorhanden ist, und legen Sie diesen Parameter auf einen, klicken Sie dann Objekte nicht erstellt.  Dieser Parameter ist hilfreich für Sie neu erstellen ein einzelnes Objekt, das gelöscht wurde. |
|**CreateDataWarehouse** | Erstellt die Datawarehouse, das von Power BI-Bericht verwendet wird. |
|**databaseName** | Der Name der Datenbank DMAReporting. |
|**warehouseName** | Der Name des Datawarehouse-Datenbank. |
|**jsonDirectory** | Das Verzeichnis, das JSON-Bewertung-Dateien enthält.  Wenn mehrere JSON-Dateien in das Verzeichnis vorhanden sind, sie verarbeitet werden einzeln nacheinander. |

Die Funktion DmaProcessor dauert nur einige Sekunden, um eine einzelne Datei zu verarbeiten.

## <a name="loading-the-data-warehouse"></a>Laden das Datawarehouse
Nachdem die DmaProcessor Abschluss der Verarbeitung der Assessment-Dateien hat, werden die Daten in die Datenbank DMAReporting in der Tabelle ReportData geladen werden. An diesem Punkt müssen Sie das Datawarehouse zu laden.

1. Verwenden Sie das Skript LoadWarehouse, alle fehlenden Werte in den Dimensionen aufgefüllt.

    Das Skript übernimmt die Daten aus der ReportData-Tabelle in der Datenbank DMAReporting und in das Warehouse zu laden.  Wenn während dieses Ladevorgangs Fehler vorhanden sind, sind sie wahrscheinlich ein Ergebnis der fehlenden Einträge in den Dimensionstabellen.

2. Laden Sie das Datawarehouse.
 
      ![LoadWarehouse Inhalt geladen](../dma/media//dma-consolidatereports/dma-LoadWarehouse-loaded.png)

## <a name="set-your-database-owners"></a>Legen Sie Ihre Besitzer von Datenbanken
Während es nicht erforderlich ist, um den größtmöglichen Nutzen, die von Berichten, es wird empfohlen, Sie die Datenbankbesitzer, in legen der **DimDBOwner** dimension, und aktualisieren Sie dann **DBOwnerKey** in die  **FactAssessment** Tabelle.  Durch dieses Verfahren ermöglicht die Aufteilen in Slices und Filtern des Power BI-Berichts basierend auf bestimmten Datenbankbesitzer.

Sie können auch das LoadWarehouse-Skript verwenden, um die grundlegenden TSQL-Anweisungen für die Sie festlegen, die Datenbankbesitzer bereitzustellen.

  ![Besitzer der LoadWarehouse-Einstellung](../dma/media//dma-consolidatereports/dma-LoadWarehouse-set-owners.png)

## <a name="dma-reports"></a>DMA-Berichte

1. Öffnen Sie die DMA-Berichte Power BI-Vorlage in Power BI Desktop.
2. Geben Sie die Serverdetails, die auf Ihre **DMAWarehouse** Datenbank, und wählen Sie dann **Load**.

    > [!IMPORTANT]
    > Drücken Sie EINGABETASTE, um akzeptiert die Werte nicht.

      ![Geladene DMA Berichte Power BI-Vorlage](../dma/media//dma-consolidatereports/dma-reports-powerbi-template-loaded.png)

   Nachdem der Bericht die Daten aktualisiert hat die **DMAWarehouse** Datenbank daraufhin mit einem Bericht, der dem folgenden ähnelt.

   ![Ansicht "Bericht" DMAWarehouse](../dma/media//dma-consolidatereports/dma-DMAWarehouse-report.png)

   > [!TIP]
   > Wenn Sie die Daten, die Sie erwartet, nicht angezeigt werden, versuchen Sie, die aktive Lesezeichen zu ändern.  Weitere Informationen finden Sie im Abschnitt Funktionalität.

## <a name="working-with-dma-reports"></a>Arbeiten mit DMA-Berichten
Um einen Bericht über DMA zu arbeiten, verwenden Sie Slicer zum Filtern nach:
- Der Instanzname.
- Datenbankname
- Teamname

Sie können Lesezeichen auch verwenden, den reporting Kontext zwischen wechseln:
- Cloud-Bewertungen
- Lokale Bewertungen

  ![DMA Bericht Lesezeichen](../dma/media//dma-consolidatereports/dma-report-bookmarks.png)

> [!NOTE]
> Wenn Sie nur eine Bewertung der Azure SQL-Datenbank ausführen, werden nur Cloud Berichte gefüllt. Wenn Sie nur eine lokale Bewertung durchführen, werden dagegen nur für lokale Berichte aufgefüllt. Aber wenn Sie sowohl Azure als auch eine lokale Bewertung führen und dann beide Bewertungen in das Warehouse laden, können Sie zwischen Cloud und lokale Berichte gedrückter STRG-Taste das entsprechende Symbol wechseln.

## <a name="reports-visuals"></a>Visualisierungen für Berichte
Die Details in den Power BI-Berichten angezeigt wird in den folgenden Abschnitten angezeigt.

### <a name="readiness-"></a>Bereitschaft %

  ![Prozentsatz der DMA-Bereitschaft](../dma/media//dma-consolidatereports/dma-readiness-percentage.png)

Dieses visuelle Element wird aktualisiert, die basierend auf den Auswahlkontext (alles, Instanz, die Datenbank [ein Vielfaches von]).

### <a name="readiness-count"></a>Anzahl der Bereitschaft

  ![Anzahl der DMA-Bereitschaft](../dma/media//dma-consolidatereports/dma-readiness-count.png)

Dieses visuelle Element zeigt die Anzahl der Datenbanken, die sind bereit, die Anzahl der Datenbanken zu migrieren, die noch nicht zur Migration bereit sind.

### <a name="readiness-bucket"></a>Bereitschaft bucket

  ![DMA-Bereitschaft bucket](../dma/media//dma-consolidatereports/dma-readiness-bucket.png)

Dieses visuelle Element zeigt eine Aufschlüsselung der Datenbanken, indem die folgenden Bereitschaft Buckets:
- 100 % BEREIT
- 75 BIS 99 % BEREIT
- 50 – 75 % BEREIT
- NICHT BEREIT

### <a name="issues-word-cloud"></a>Wortwolke Probleme
 
  ![DMA-Probleme WordCloud](../dma/media//dma-consolidatereports/dma-issues-word-cloud.png)

Dieses visuelle Element zeigt die Probleme, die derzeit in auftreten, in den Auswahlkontext (alles, Instanz, die Datenbank [ein Vielfaches von]). Je größer wird das Wort auf dem Bildschirm größer die Anzahl der Probleme in dieser Kategorie. Wenn der Mauszeiger über ein Wort bewegen, zeigt die Anzahl der Probleme in dieser Kategorie.

### <a name="database-readiness"></a>Datenbank-Bereitschaft

  ![Bereitschaftsbericht für die DMA-Datenbank](../dma/media//dma-consolidatereports/dma-database-readiness-report.png)

Dieser Abschnitt ist der primäre Teil des Berichts, der die Bereitschaft einer Datenbank-Instanz angezeigt wird. Dieser Bericht enthält eine Hierarchie Drilldown von:
- InstanceDatabase
- ChangeCategory
- Titel
- ObjectType
- ImpactedObjectName

 ![Drilldown des Berichts DMA-Datenbank-Bereitschaft](../dma/media//dma-consolidatereports/dma-database-readiness-report-drilldown.png)

Dieser Bericht dient auch als Filter Punkt für die Erstellung des Berichts für die Wiederherstellung-planen.

Um einen Drilldown in den Bericht für die Wiederherstellung-Plan durchzuführen, mit der rechten Maustaste auf einen Datenpunkt in diesem Diagramm, zeigen Sie auf **Drillthrough**, und wählen Sie dann **Wiederherstellung Pläne**.

Dieser Task filtert den Wiederherstellung Plan Bericht der aktuellen Hierarchieebene basierend auf den Punkt, an dem Sie die Drillthrough-Option auswählen.

  ![DMA-Datenbank-Bereitschaft Drilldown des Berichts gefiltert](../dma/media//dma-consolidatereports/dma-database-readiness-report-drilldown-filtered.png)

  ![Planen der Wiederherstellung DMA-Bericht](../dma/media//dma-consolidatereports/dma-remediation-plan-report.png)

Sie können auch den Aktionsplans-Bericht auf einem eigenen, erstellen Sie eine benutzerdefinierte Wartung Plan verwenden, mithilfe der Filter in der **Visualisierungen Filter** Blatt.
 
  ![Bericht-Filteroptionen DMA Wartung planen](../dma/media//dma-consolidatereports/dma-remediation-plan-report-filter-options.png)

### <a name="script-disclaimer"></a>Haftungsausschluss für Skripts
*In diesem Artikel angegebenen Beispielskripts werden nicht unter keinem Microsoft-standardsupportprogramm oder-Dienst unterstützt. Alle Skripts werden wie besehen und ohne Garantien jeglicher Art bereitgestellt. Microsoft schließt darüber hinaus aller konkludente GEWÄHRLEISTUNGEN, einschließlich, aber nicht beschränkt auf konkludente GEWÄHRLEISTUNGEN der Handelsüblichkeit oder Eignung für einen bestimmten Zweck. Das gesamte Risiko aus der Verwendung oder Leistung der Beispielskripts und Dokumentationen, liegt bei Ihnen. In keinem Fall sollte Microsoft, seinen Autoren oder Benutzer, die andernfalls in die Erstellung, Produktion oder Bereitstellung der Skripts für Schäden haftbar gemacht werden keinerlei (einschließlich, aber nicht beschränkt auf Schäden durch Datenverlust Gewinn, Unterbrechung des Geschäftsbetriebs, Verlust von Geschäftsdaten, Folge- oder) aus aus der Verwendung von oder keine der Beispielskripts oder der Dokumentation verwendet werden können, auch wenn Microsoft die Möglichkeit solcher Schäden hingewiesen wurde.  Suchen Sie die Berechtigung, bevor Sie diese Skripts auf anderen Websites/Repositories/Blogs Berichtsdaten.*
