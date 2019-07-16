---
title: Aktualisieren von Arbeitsmappen und planmäßige Datenaktualisierungen (SharePoint 2013) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5f0d49d6aeb8231dbffb56b42fe1151ae90d0e41
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68181311"
---
# <a name="upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013"></a>Aktualisieren von Arbeitsmappen und planmäßige Datenaktualisierungen (SharePoint 2013)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  In diesem Thema wird die Verwendung von Arbeitsmappen beschrieben, die in [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Umgebungen früherer Versionen erstellt wurden. Außerdem wird erläutert, wie [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Arbeitsmappen aktualisiert werden, um die Vorteile neuer, in diesem Release eingeführter Features zu nutzen. Weitere Informationen zu neuen Funktionen finden Sie unter [Neuigkeiten in Power Pivot](http://go.microsoft.com/fwlink/?LinkID=203917).  
  
> [!WARNING]  
>  Für das Upgrade von Arbeitsmappen, die automatisch auf dem Server aktualisiert werden, kann kein Rollback ausgeführt werden. Sobald eine Arbeitsmappe aktualisiert wurde, bleibt sie auf diesem Stand. Um eine frühere Version zu verwenden, können Sie die vorherige Arbeitsmappe erneut in SharePoint veröffentlichen, eine frühere Version wiederherstellen oder die Arbeitsmappe wiederverwenden. Weitere Informationen zum Wiederherstellen oder Wiederverwenden eines Dokuments in SharePoint finden Sie unter [Planen des Schutzes von Inhalten mit Papierkörben und der Versionsverwaltung](http://go.microsoft.com/fwlink/?LinkId=238669).  
  
  
##  <a name="bkmk_overview"></a> Übersicht über das Aktualisieren von Arbeitsmappen  
 Eine [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Arbeitsmappe ist eine Excel-Arbeitsmappe, die eingebettete [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Daten enthält. Das Aktualisieren einer Arbeitsmappe bietet zwei Vorteile:  
  
-   Die neuen Funktionen in [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)]werden verwendet.  
  
-   Ermöglicht planmäßige Datenaktualisierungen für Arbeitsmappen, die mit einem [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] Analysis Services-Server im SharePoint-Modus ausgeführt werden.  
  
> [!IMPORTANT]  
>  Da Sie kein Rollback für eine aktualisierte Arbeitsmappe ausführen können, sollten Sie eine Kopie der Datei erstellen, wenn Sie sie in der vorherigen Version von [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)]oder in einer früheren Version von [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]verwenden möchten.  
  
 In der folgenden Tabelle sind die Unterstützung und das Verhalten von [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Arbeitsmappen auf Grundlage der Umgebung aufgeführt, in der die Arbeitsmappe erstellt wurde. Das beschriebene Verhalten umfasst die allgemeine Benutzerfreundlichkeit, die unterstützten Upgradeoptionen zum Aktualisieren der Arbeitsmappe auf die jeweilige Umgebung und das Verhalten einer Arbeitsmappe, die noch nicht aktualisiert wurde, bei planmäßigen Datenaktualisierungen.  
  
### <a name="workbook-behavior-and-upgrade-options"></a>Verhalten von Arbeitsmappen und Upgradeoptionen  
  
|Erstellt in|\<|Unterstützung und Verhalten|>|  
|----------------|--------|--------------------------|--------|  
||**2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für SharePoint 2010**|**2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für SharePoint 2010**|**2012 SP1 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für SharePoint 2013**|  
|**2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für Excel 2010**|Alle Funktionen|**Benutzerfreundlichkeit:** Benutzer können mit der Arbeitsmappe im Browser interagieren und sie als Datenquelle für andere Lösungen.<br /><br /> **Upgrade:** Arbeitsmappen werden automatisch in der Dokumentbibliothek upgegradet, wenn für die automatische Upgrades aktiviert sind die [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Systemdienst in der SharePoint-Farm<br /><br /> **Planmäßige datenaktualisierung:** NICHT unterstützt. Arbeitsmappe muss aktualisiert werden.|**Benutzerfreundlichkeit:** Benutzer können mit der Arbeitsmappe interagieren und sie als Datenquelle für andere Lösungen.<br /><br /> **Upgrade:** Automatisches Upgrade ist nicht verfügbar. Benutzer müssen 2008 R2-Arbeitsmappen manuell auf die 2012-Version oder die Office 2013-Version aktualisieren.<br /><br /> **Planmäßige datenaktualisierung:** NICHT unterstützt. Arbeitsmappe muss aktualisiert werden.|  
|**2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für Excel**|Nicht unterstützt|Alle Funktionen|**Benutzerfreundlichkeit:** Benutzer können mit der Arbeitsmappe im Browser interagieren und sie als Datenquelle für andere Lösungen. Planmäßige Datenaktualisierung ist verfügbar.<br /><br /> **Upgrade:** Automatisches Upgrade wird nicht unterstützt. Benutzer können Arbeitsmappen manuell auf die Office 2013-Version aktualisieren.<br /><br /> **Planmäßige Datenaktualisierung:** unterstützt.|  
|**Excel 2013**|Nicht unterstützt|Nicht unterstützt|Alle Funktionen|  
  
##  <a name="bkmk_to_2012sp1_from_2008r2"></a> Aktualisieren von Arbeitsmappen der Version 2008 R2 auf SQL Server 2012 Service Pack 1 (SP1)-Arbeitsmappen  
 In diesem Abschnitt wird das Upgrade von SQL Server 2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für Excel 2010-Arbeitsmappen auf SQL Server 2012 SP1 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für Excel 2013-Arbeitsmappen beschrieben.  
  
 **Verändertes Programmverhalten:** SQL Server 2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Arbeitsmappen werden nicht automatisch aktualisiert, wenn sie in SQL Server 2012 SP1 verwendet werden [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für SharePoint 2013. Aus diesem Grund können in SQL Server 2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Arbeitsmappen keine planmäßigen Datenaktualisierungen ausgeführt werden.  
  
 Arbeitsmappen der Version 2008 R2 werden zwar in [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für SharePoint 2013 geöffnet, unterstützen aber keine planmäßigen Datenaktualisierungen. Wenn Sie den Aktualisierungsverlauf überprüfen, wird eine mit der folgenden vergleichbare Fehlermeldung angezeigt:  
  
 "Die Arbeitsmappe enthält ein nicht unterstütztes [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Modell. Das [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Modell in der Arbeitsmappe weist das Format von SQL Server 2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für Excel 2010 auf. Die folgenden [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Modelle werden unterstützt:  
  
-   SQL Server 2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für Excel 2010.  
  
-   SQL Server 2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für Excel 2013.  
  
 **Wie Sie eine Arbeitsmappe zu aktualisieren:** Die planmäßigen datenaktualisierungen funktionieren erst, nachdem Sie die Arbeitsmappe auf eine Arbeitsmappe 2012 aktualisiert. Um die Arbeitsmappe und das darin enthaltene Modell zu aktualisieren, führen Sie eines der folgenden Verfahren aus:  
  
-   Laden Sie die Arbeitsmappe herunter, und öffnen Sie sie in einer Microsoft Excel 2010-Version, für die das SQL Server 2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Add-In für Excel installiert wurde.  
  
     Öffnen Sie das [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Fenster, und aktualisieren Sie das [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Modell.  
  
     Speichern Sie dann die Arbeitsmappe, und veröffentlichen Sie sie erneut in SharePoint.  
  
-   Laden Sie die Arbeitsmappe herunter, und öffnen Sie sie in Microsoft Excel 2013.  
  
     Öffnen Sie das [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Fenster, und aktualisieren Sie das [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Modell.  
  
     Speichern Sie dann die Arbeitsmappe, und veröffentlichen Sie sie auf dem SharePoint-Server erneut.  
  
 Weitere Informationen zu Änderungen an Analysis Services-Funktionen finden Sie unter [Verändertes Verhalten von Analysis Services-Funktionen in SQL Server 2016](../../../analysis-services/behavior-changes-to-analysis-services-features-in-sql-server-2016.md).  
  
 Weitere Informationen zum Aktualisierungsverlauf finden Sie unter [Anzeigen des Verlaufs von Datenaktualisierungen &#40;Power Pivot für SharePoint&#41;](../../../analysis-services/power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md).  
  
##  <a name="bkmk_to_2012sp1_from_2012"></a> Aktualisieren von Versionen, die mit dem 2012 Power Pivot-Add-In für Excel erstellt wurden, auf Office 2013-Arbeitsmappen  
 In diesem Abschnitt wird das Upgrade **von** SQL Server 2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für Excel 2010-Arbeitsmappen **auf** SQL Server 2012 SP1 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] in Excel 2013 beschrieben.  
  
 Durch ein Upgrade der Arbeitsmappe wird der folgende Fehler behoben, der beim Versuch auftritt, für eine Arbeitsmappe in einer vorherigen Version eine planmäßige Datenaktualisierung auszuführen:  
  
 "Aktualisierungsvorgang für Arbeitsmappen, die mit früheren Version von erstellt [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ist nicht verfügbar."  
  
 **So aktualisieren Sie eine Arbeitsmappe**  
  
1.  Aktualisieren Sie jede Arbeitsmappe manuell, indem Sie sie in Microsoft Excel 2013 öffnen.  
  
2.  Um die Arbeitsmappe und das darin enthaltene Modell zu aktualisieren, laden Sie die Arbeitsmappe herunter und öffnen sie in Microsoft Excel 2013.  
  
3.  Öffnen Sie das [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Fenster, und aktualisieren Sie das [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Modell.  
  
4.  Speichern Sie dann die Arbeitsmappe, und veröffentlichen Sie sie auf dem SharePoint 2013-Server erneut.  
  
##  <a name="bkmk_to_2012_from_2008R2"></a> Aktualisieren von Versionen, die mit dem 2008 R2 Power Pivot-Add-In für Excel 2010 erstellt wurden, auf SQL Server 2012-Arbeitsmappen  
 In diesem Abschnitt wird das Upgrade **von** SQL Server 2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für Excel 2010-Arbeitsmappen **auf** SQL Server 2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für Excel 2010 beschrieben.  
  
 Durch ein Upgrade der Arbeitsmappe wird der folgende Fehler behoben, der beim Versuch auftritt, für eine Arbeitsmappe in einer vorherigen Version eine planmäßige Datenaktualisierung auszuführen:  
  
 "Aktualisierungsvorgang für Arbeitsmappen, die mit früheren Version von erstellt [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] ist nicht verfügbar."  
  
 **So aktualisieren Sie eine Arbeitsmappe**  
  
 Es gibt zwei Upgrademöglichkeiten:  
  
1.  Aktualisieren Sie jede Arbeitsmappe manuell, indem Sie sie auf einem Computer, der über die [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] -Version von [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für Excel verfügt, in Excel öffnen und dann erneut auf dem Server veröffentlichen. Wenn Sie die Arbeitsmappe in der neueren Version des Add-Ins öffnen, werden die folgenden internen Vorgänge ausgeführt: Der Datenanbieter in der Verbindungszeichenfolge der Arbeitsmappendaten wird auf MSOLAP.5 aktualisiert, die Metadaten werden aktualisiert, und Beziehungen werden zum Anpassen an eine neuere Implementierung neu erstellt.  
  
2.  Alternativ kann ein SharePoint-Administrator die automatische Upgradefunktion für den [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Systemdienst in einer SharePoint-Farm aktivieren, um eine [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)][!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Arbeitsmappe bei der Ausführung einer planmäßigen Datenaktualisierung automatisch zu aktualisieren (dabei werden nur Arbeitsmappen aktualisiert, die für die planmäßige Datenaktualisierung konfiguriert wurden).  
  
    > [!NOTE]  
    >  Das automatische Upgrade ist eine Serverkonfigurationsfunktion; Sie können sie nicht für bestimmte Arbeitsmappen, Bibliotheken oder Websitesammlungen aktivieren oder deaktivieren.  
  
 **So konfigurieren Sie ein automatisches Upgrade während der Datenaktualisierung**  
  
 Um das automatische Upgrade zu verwenden, müssen Sie im [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]-Konfigurationstool das Kontrollkästchen **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]-Arbeitsmappen automatisch aktualisieren, um die Datenaktualisierung vom Server zu ermöglichen** aktivieren, um das automatische Upgrade zu verwenden. Innerhalb des Tools befindet sich das Kontrollkästchen auf der Seite **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]-Systemdienst aktualisieren** und auf der Seite **[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]-Dienstanwendung erstellen**, wenn Sie eine neue Installation konfigurieren.  
  
 Sie können das folgende Cmdlet ausführen, um zu überprüfen, ob das automatische Upgrade aktiviert ist:  
  
```  
PS C:\Windows\system32> Get-PowerPivotSystemService  
```  
  
 Die Ausgabe von Get-PowerPivotSystemService ist eine Liste von Eigenschaften und entsprechenden Werten. Daraufhin sollten Sie **WorkbookUpgradeOnDataRefresh** in der Eigenschaftsliste sehen. Es ist auf **true** festgelegt, wenn das automatische Upgrade aktiviert ist. Wenn es **false**ist, fahren Sie mit dem nächsten Schritt fort, um das automatische Arbeitsmappenupgrade zu aktivieren.  
  
 Um das automatische Arbeitsmappenupgrade zu aktivieren, führen Sie den folgenden Befehl aus:  
  
```  
PS C:\Windows\system32> Set-PowerPivotSystemService -WorkbookUpgradeOnDataRefresh:$true -Confirm:$false  
```  
  
 Nachdem Sie die Arbeitsmappe aktualisiert haben, können Sie die planmäßige Datenaktualisierung und neue Funktionen im [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] für Excel-Add-In verwenden.  
  
##  <a name="bkmk_runold"></a> Ausführen mehrerer Arbeitsmappenversionen auf einem neueren Server  
 Sie können ältere und neuere Versionen von [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Arbeitsmappen auf einer [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] -Instanz von [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)]nebeneinander ausführen.  
  
 Je nachdem, wie Sie den Server installiert haben, müssen Sie **möglicherweise** eine frühere Version des OLE DB-Anbieters für Analysis Services installieren, bevor Sie auf ältere und neuere Arbeitsmappen auf demselben Server zugreifen können.  
  
 Beachten Sie, dass die Veröffentlichung von Arbeitsmappen neuerer Versionen auf SQL Server-Instanzen früherer Versionen von [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] nicht unterstützt wird. Eine [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] -Instanz lädt keine Arbeitsmappe, die in der [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] -Version von [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)]erstellt wurde, und eine SQL Server 2012-Instanz lädt keine Office 2013-Arbeitsmappen mit erweiterten Datenmodellen, die mit der [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] -Version von [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] in Excel erstellt wurden.  
  
###  <a name="bkmk_msolapxslx"></a> So überprüfen Sie die MSOLAP-Datenanbieterinformationen in einer Power Pivot-Arbeitsmappe  
 Gehen Sie folgendermaßen vor, um zu überprüfen, welcher OLE DB-Anbieter in einer [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Arbeitsmappe verwendet wird. Zum Überprüfen der Datenverbindungsinformationen muss das [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)] -Add-In nicht installiert sein.  
  
1.  Klicken Sie in Excel auf der Registerkarte "Daten" auf **Verbindungen**. Klicken Sie auf **Eigenschaften**.  
  
2.  Auf der Registerkarte **Definition** wird die Anbieterversion zu Beginn der Verbindungszeichenfolge angezeigt.  
  
     **Provider=MSOLAP.5** gibt an, dass die Arbeitsmappe Version [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]aufweist.  
  
     **Provider=MSOLAP.4** gibt [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]als Version an.  
  
     **Data Source=$Embedded$** gibt an, dass die Arbeitsmappe eine [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Arbeitsmappe ist und eine eingebettete Datenbank verwendet.  
  
###  <a name="bkmk_msolappc"></a> So überprüfen Sie die aktuelle Version des MSOLAP-Datenanbieters auf einem lokalen Computer  
 Gehen Sie folgendermaßen vor, um zu überprüfen, um welchen OLE DB-Anbieter es sich bei der aktuellen Version auf dem Server oder der Arbeitsstation mit [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] -Arbeitsmappen handelt. Kenntnis der aktuellen Version ist für die Behebung von Datenverbindungsfehlern nach dem Upgrade hilfreich.  
  
1.  Gehen Sie im Registrierungs-Editor zu HKEY_CLASSES_ROOT.  
  
2.  Führen Sie einen Bildlauf nach unten zu MSOLAP durch. Überprüfen Sie, ob MSOLAP.5 unter den auf dem System installierten OLAP-Anbietern aufgeführt ist. Überprüfen Sie, ob für MSOLAP | CurVer die Option MSOLAP.5 festgelegt ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Migrieren von Power Pivot zu SharePoint 2013](../../../analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013.md)   
 [Upgraden von PowerPivot für SharePoint](../../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)   
 [Neuigkeiten in Analysis Services](../../../analysis-services/what-s-new-in-analysis-services.md)   
 [Anzeigen des Verlaufs von Datenaktualisierungen &#40;Power Pivot für SharePoint&#41;](../../../analysis-services/power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
  
