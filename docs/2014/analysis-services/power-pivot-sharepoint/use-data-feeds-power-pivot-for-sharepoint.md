---
title: Verwenden von Datenfeeds (PowerPivot für SharePoint) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 50140fdf-6fd1-41a1-9c14-8ecfb97ba2e1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6efccad47f0d6670c87aeb1e9cc9ef9ec654a138
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66070908"
---
# <a name="use-data-feeds-powerpivot-for-sharepoint"></a>Datenfeeds verwenden (PowerPivot für SharePoint)
  Datenfeeds sind einzelne oder mehrere Datenströme, die von einer Onlinedatenquelle generiert und in ein Zieldokument oder eine Zielanwendung gestreamt werden. Wenn Sie PowerPivot für Excel verwenden, können Datenfeeds Ihnen helfen, vorhandene Unternehmens- oder Geschäftsdaten von beliebigen Datenquellen in das Fenster PowerPivot in Ihrer Excel 2010-Arbeitsmappe abzurufen. Nachdem Sie einen Datenfeed in eine Arbeitsmappe importiert haben, können Sie später in allen Datenaktualisierungsvorgängen, die Sie auf einem SharePoint Server planen, darauf verweisen.  
  
 Wie Sie einen Datenfeed verwenden, hängt davon ab, ob Sie integrierte Exportfunktionen in Anwendungen verwenden, die Atom-Datenfeeds unterstützen, oder ob Sie benutzerdefinierte Datendienste erstellen und verwenden. Anwendungen, die in der Lage sind, Atom-XML-Daten zu veröffentlichen und zu lesen, unterstützen eine nahtlose Datenübertragung, die die Datenfeed- und Datendienstmechanismen für den Benutzer nicht erkennen lässt. Für den Benutzer werden einfach nur Daten von einer Anwendung in eine andere verschoben.  
  
 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und Microsoft SharePoint 2010 bieten Datenfeeds, die in PowerPivot-Arbeitsmappen verwendet werden können. Mithilfe der in diesem Thema enthaltenen Informationen erfahren Sie, wie auf Datenfeeds aus Berichten und Listen zugegriffen wird, über die Sie bereits verfügen.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Erforderliche Komponenten](#prereq)  
  
 [Erstellen eines Datenfeeds aus einer SharePoint-Liste](#sharepointlist)  
  
 [Erstellen eines Datenfeeds aus einem Reporting Services-Bericht](#rsreport)  
  
 [Erstellen eines Datenfeeds aus einem Datendienstdokument](#dsdoc)  
  
##  <a name="prereq"></a> Erforderliche Komponenten  
 Sie benötigen PowerPivot für Excel, um ein Datenfeed nach Excel 2010 zu importieren.  
  
 Sie müssen über einen Webdienst oder Datendienst verfügen, der Daten im Atom 1.0-Format bereitstellt. Sowohl [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] als auch SharePoint 2010 können Daten in diesem Format bereitstellen.  
  
 Bevor Sie eine SharePoint-Liste als Datenfeed exportieren können, müssen Sie ADO.NET Data Services auf dem SharePoint-Server installieren. Weitere Informationen finden Sie unter [Installieren von ADO.NET Data Services, um Datenfeedexporte von SharePoint-Listen zu unterstützen](../../sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).  
  
##  <a name="sharepointlist"></a> Erstellen eines Datenfeeds aus einer SharePoint-Liste  
 In einer SharePoint 2010-Farm verfügt eine SharePoint-Liste über eine Schaltfläche Als Datenfeed exportieren auf dem Listenmenüband. Sie können auf diese Schaltfläche klicken, um die Liste als Feed zu exportieren. Um optimale Ergebnisse zu erzielen, sollte Excel 2010 mit der PowerPivot-Clientanwendung auf der Arbeitsstation ausgeführt werden. Die PowerPivot-Clientanwendung wird als Reaktion auf den Datenfeedexport gestartet und erstellt eine neue PowerPivot-Tabelle, die die Liste enthält.  
  
1.  Öffnen Sie die Liste auf Ihrer SharePoint-Website.  
  
2.  Klicken Sie unter Listentools auf **Liste**.  
  
3.  Klicken Sie unter Verbinden und Exportieren auf **Als Datenfeed exportieren**.  
  
    > [!NOTE]  
    >  Die **als Datenfeed exportieren** Schaltfläche über PowerPivot zu SharePoint hinzugefügt wird. Wenn PowerPivot für SharePoint nicht installiert ist oder Sie die PowerPivot-Funktion nicht aktiviert haben, ist diese Schaltfläche nicht verfügbar.  
  
4.  Klicken Sie auf **öffnen** Wenn PowerPivot für Excel lokal installiert ist, oder klicken Sie auf **speichern** um das atomsvc-Dokument auf der Festplatte für Importvorgänge zu einem späteren Zeitpunkt zu speichern.  
  
5.  Wenn Sie **Öffnen**auswählen, verwenden Sie den Tabellenimport-Assistenten, um ein Datenfeed in ein Arbeitsblatt zu importieren. Der Datenfeed wird als neue Tabelle im PowerPivot-Fenster hinzugefügt.  
  
 Wenn ADO.NET Data Services 3.5.1 nicht auf dem SharePoint-Server installiert ist, tritt ein Fehler auf. Weitere Informationen über den Fehler und seine Behebung finden Sie unter [Installieren von ADO.NET Data Services, um Datenfeedexporte von SharePoint-Listen zu unterstützen](../../sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).  
  
##  <a name="rsreport"></a> Erstellen eines Datenfeeds aus einem Reporting Services-Bericht  
 Wenn Sie über eine SQL Server 2008 R2 Reporting Services-Bereitstellung verfügen, können Sie einen Datenfeed mithilfe der neuen Atom-Renderingerweiterung aus einem vorhandenen Bericht generieren. Um optimale Ergebnisse zu erzielen, sollte Excel 2010 mit dem PowerPivot-für Excel-Add-In auf der Arbeitsstation ausgeführt werden. Die PowerPivot-Clientanwendung wird in Reaktion auf den Datenfeedexport gestartet und fügt automatisch die gestreamten Tabellen und Spalten hinzu und verknüpft diese.  
  
 Anweisungen zum Exportieren eines Datenfeeds aus einem Bericht finden Sie unter [Generieren von Datenfeeds aus einem Bericht &#40;Berichts-Generator und SSRS&#41;](../../reporting-services/report-builder/generate-data-feeds-from-a-report-report-builder-and-ssrs.md) in der [Hilfedatei zum Berichts-Generator](https://go.microsoft.com/fwlink/?LinkId=154494).  
  
> [!NOTE]  
>  Zum Einrichten eines Zeitplans mit wiederholter Datenaktualisierung, durch den Berichtsdaten in eine in einer SharePoint-Bibliothek veröffentlichte PowerPivot-Arbeitsmappe erneut importiert werden, muss der Berichtsserver für die SharePoint-Integration konfiguriert sein. Weitere Informationen zum Verwenden von PowerPivot für SharePoint und Reporting Services zusammen finden Sie unter [Konfiguration und Verwaltung eines Berichtsservers &#40;Reporting Services SharePoint Mode&#41;](../../reporting-services/configure-administer-report-server-reporting-services-sharepoint-mode.md).  
  
##  <a name="dsdoc"></a> Erstellen eines Datenfeeds aus einem Datendienstdokument  
 Wenn Sie über einen benutzerdefinierten Datendienst verfügen, der Atom-Feeds generiert, haben Sie die Möglichkeit, die Daten für Benutzer und Anwendungen verfügbar zu machen. In einem *Datendienstdokument* (ATOMSVC-Datei) ist mindestens eine Verbindung mit Onlinequellen angegeben, die Daten im Atom-Übertragungsformat veröffentlichen. Datendienstdokumente können in einer *Datenfeedbibliothek*erstellt werden. Dabei handelt es sich um eine zweckgebundene Bibliothek, die einen allgemeinen Zugriffspunkt für die Durchsuchung von Datendienstdokumenten ermöglicht, die zu einem SharePoint Server veröffentlicht wurden. IT-Arbeiter, die die Berechtigung haben, in der Datenfeedbibliothek auf Datendienstdokumente zuzugreifen, können auf die SharePoint-URL des Dokuments verweisen, um die Datenfeeds in ihre Arbeitsmappen und Anwendungen zu importieren.  
  
1.  Öffnen Sie eine Datenfeedbibliothek, die vom Websiteadministrator erstellt wurde. Weitere Informationen finden Sie unter [erstellen oder Anpassen einer Datenfeedbibliothek &#40;PowerPivot für SharePoint&#41;](create-or-customize-a-data-feed-library-power-pivot-for-sharepoint.md).  
  
2.  Klicken Sie unter Bibliothekstools auf **Dokumente**.  
  
3.  Klicken Sie auf **Neues Dokument**.  
  
4.  Geben Sie einen Dateinamen und eine Beschreibung an.  
  
5.  Geben Sie eine oder mehrere URLs an, die den Feed bereitstellen:  
  
    1.  **Basis-URL** ist optional. Sie sollten dies angeben, wenn ein Datendienstdokument mehrere Feeds bereitstellt. Basis-URL sollte den Teil der URL angeben, der allen Feeds (z. B. der Servername und die Website) gemeinsam ist. Wenn Sie zu einem Reporting Services-Bericht ein Datendienstdokument erstellen, wäre die Basis-URL die Berichtsserver-URL und der Bericht.  
  
    2.  **Webdienst-URL** ist erforderlich. Ohne die Basis-URL muss dieser Wert http :// oder https:// in der Adresse enthalten. Wenn Sie eine Basis-URL angegeben haben, ist die Webdienst-URL der Teil, der der Basis-URL folgt. Wenn die vollständige URL lautet z. B. http://adventure-works/inventory/today.aspx, die Basis-URL wäre http://adventure-works/inventory, und die Webdienst-URL wäre/Today.aspx.  
  
         Die Webdienst-URL kann Parameter enthalten, die eine Teilmenge der Daten filtern oder auswählen. Die Anwendung oder der Dienst, die/der den Feed bereitstellt, muss die Parameter unterstützen, die Sie in der URL angeben.  
  
6.  Geben Sie einen **Tabellennamen**ein, eine Tabelle für jeden Feed. Dieser Wert ist erforderlich. Der Tabellenname wird von einer Clientanwendung verwendet, die den Datenfeed nutzt. In PowerPivot für Excel wird der Tabellenname verwendet, um Tabellen im PowerPivot-Fenster zu benennen, die die importierten Daten enthalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren der PowerPivot-Funktionsintegration für Websitesammlungen in der Zentraladministration](activate-power-pivot-integration-for-site-collections-in-ca.md)   
 [Freigeben von Datenfeeds mithilfe einer Datenfeedbibliothek &#40;PowerPivot für SharePoint&#41;](share-data-feeds-using-a-data-feed-library-power-pivot-for-sharepoint.md)  
  
  
