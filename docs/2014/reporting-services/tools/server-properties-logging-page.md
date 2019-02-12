---
title: Servereigenschaften (Seite „Verlauf“)|Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.logging.f1
ms.assetid: b338deab-4868-4951-9f22-0605add2fc95
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: cf85b6fbc2bccab8061ef227b5d0fb10de825477
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56015466"
---
# <a name="server-properties-logging-page"></a>Servereigenschaften (Seite Protokollierung)
  Verwenden Sie diese Seite, um Grenzwerte für die Berichtsausführungsdaten festzulegen, die von einem Berichtsserver aufgelistet werden. Die Ausführungsdaten werden intern in der Berichtsserverdatenbank gespeichert. Sie können die Berichtsaktivität eines Berichtsservers, der im einheitlichen Modus oder im integrierten SharePoint-Modus ausgeführt wird, nachverfolgen. Ist der Berichtsserver Teil einer Bereitstellung für horizontales Skalieren, zeichnet das Berichtsausführungsprotokoll die Berichtsaktivität der gesamten Bereitstellung in einer einzelnen Protokolldatei auf.  
  
 Um diese Seite zu öffnen, starten [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], eine Verbindung mit einem Berichtsserver herstellen, mit der rechten Maustaste in des Namens des Berichtsservers, und wählen **Eigenschaften**. Klicken Sie auf **Protokollierung** , um diese Seite zu öffnen.  
  
## <a name="options"></a>Optionen  
 **Protokollierung der Berichtsausführung aktivieren**  
 Klicken Sie auf diese Schaltfläche, um Informationen über die Berichtsaktivität zu erstellen und zu speichern. Ist diese Option aktiviert, verfolgt der Berichtsserver nach, welche Berichte verwendet werden, die Häufigkeit der Berichtsverarbeitung, der Typ des durchgeführten Berichtsvorgangs, das Ausgabeformat und wer den Bericht ausgeführt hat. Weitere Informationen zu den zusätzlichen Datenpunkten, die im Protokoll erfasst werden, finden Sie unter [Berichtsserver-Ausführungsprotokoll und die ExecutionLog3-Ansicht](../report-server/report-server-executionlog-and-the-executionlog3-view.md).  
  
 **Protokolleinträge entfernen, die älter sind als die folgende Anzahl von Tagen**  
 Geben Sie die Anzahl an Tagen an, nach denen die Protokolleinträge aus dem Berichtsausführungsprotokoll gelöscht werden. Der Standardwert ist 60 Tage.  
  
## <a name="see-also"></a>Siehe auch  
 [Festlegen von Berichtsservereigenschaften &#40;Management Studio&#41;](set-report-server-properties-management-studio.md)   
 [Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Reporting Services-Protokolldateien und Quellen](../report-server/reporting-services-log-files-and-sources.md)   
 [Berichtsserver im Management Studio (F1-Hilfe)](report-server-in-management-studio-f1-help.md)   
 [Berichtsserverausführungsprotokoll und die ExecutionLog3-Ansicht](../report-server/report-server-executionlog-and-the-executionlog3-view.md)  
  
  
