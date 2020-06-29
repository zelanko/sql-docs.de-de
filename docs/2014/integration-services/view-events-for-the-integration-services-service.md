---
title: Anzeigen von Ereignissen für den Integration Services-Dienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- events [Integration Services]
- service [Integration Services], events
- Integration Services service, events
ms.assetid: 37e23946-10d1-4116-8568-8fd24067102e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 57340afcbe1914b5e54ded06c8a7384ff33fd901
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85420137"
---
# <a name="view-events-for-the-integration-services-service"></a>Anzeigen von Ereignissen für den Integration Services-Dienst
  Es gibt zwei Tools, in denen Sie Ereignisse für den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst anzeigen können:  
  
-   Das Dialogfeld **Protokolldatei-Viewer** in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Das Dialogfeld **Protokolldatei-Viewer** enthält Optionen zum Exportieren, Filtern und Durchsuchen des Protokolls. Weitere Informationen zu den Optionen im Dialogfeld **Protokolldatei-Viewer**finden Sie unter [Protokolldatei-Viewer (F1-Hilfe)](../relational-databases/logs/log-file-viewer-f1-help.md).  
  
-   Die Windows-Ereignisanzeige.  
  
 Eine Beschreibung der vom [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst protokollierten Ereignisse finden Sie unter [Ereignisprotokollierung durch den Integration Services-Dienst](service/events-logged-by-the-integration-services-service.md).  
  
### <a name="to-view-service-events-for-integration-services-in-sql-server-management-studio"></a>So zeigen Sie Dienstereignisse für Integration Services in SQL Server Management Studio an  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Klicken Sie im Menü **Datei** auf **Objekt-Explorer verbinden**.  
  
3.  Wählen Sie im Dialogfeld **Verbindung mit Server herstellen** den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Servertyp aus, wählen Sie den Server aus, mit dem die Verbindung hergestellt werden soll, oder suchen Sie ihn, und klicken Sie anschließend auf **Verbinden**.  
  
4.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , und klicken Sie anschließend auf **Protokolle anzeigen**.  
  
5.  Wählen Sie [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] SQL Server Integration Services **aus, um die**-Ereignisse anzuzeigen. Die Option **NT-Ereignisse** ist automatisch ausgewählt und wird durch die Option **SQL Server Integration Services** deaktiviert.  
  
### <a name="to-view-service-events-for-integration-services-in-windows-event-viewer"></a>So zeigen Sie Dienstereignisse für Integration Services in der Windows-Ereignisanzeige an  
  
1.  Wenn Sie die klassische Ansicht verwenden, klicken Sie in der **Systemsteuerung**auf **Verwaltung**. Wenn Sie die Kategorieansicht verwenden, klicken Sie auf **Leistung und Wartung** und dann auf **Verwaltung**.  
  
2.  Klicken Sie auf **Ereignisanzeige**.  
  
3.  Klicken Sie im Dialogfeld **Ereignisanzeige** auf **Anwendung**.  
  
4.  Suchen Sie im **Anwendungs** -Snap-In einen Eintrag in der Spalte **Quelle** , die den Wert **SQLISService**enthält. Klicken Sie mit der rechten Maustaste auf den Eintrag und anschließend auf **Eigenschaften**.  
  
5.  Klicken Sie wahlweise auf den Nach-Oben- oder Nach-Unten-Pfeil, um das vorherige oder nächste Ereignis anzuzeigen.  
  
6.  Klicken Sie wahlweise auf das Symbol "In Zwischenablage speichern", um die Ereignisinformationen zu kopieren.  
  
7.  Zeigen Sie die Ereignisdaten in Byte oder Wörtern an.  
  
8.  Klicken Sie auf **OK**.  
  
9. Klicken Sie im Menü **Datei** auf **Beenden** , um das Dialogfeld **Ereignisanzeige** zu schließen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten des Integration Services Dienstanbieter](../../2014/integration-services/manage-the-integration-services-service.md)   
 [Hinzufügen eines Protokolls für Datenfluss-Leistungsindikatoren](performance/performance-counters.md)  
  
  
