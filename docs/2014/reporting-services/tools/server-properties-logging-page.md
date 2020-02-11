---
title: Servereigenschaften (Seite „Verlauf“)|Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.logging.f1
ms.assetid: b338deab-4868-4951-9f22-0605add2fc95
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2a04c27fd790a1ad5c4ba453b43af5983a6440e3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66099530"
---
# <a name="server-properties-logging-page"></a>Servereigenschaften (Seite Protokollierung)
  Verwenden Sie diese Seite, um Grenzwerte für die Berichtsausführungsdaten festzulegen, die von einem Berichtsserver aufgelistet werden. Die Ausführungsdaten werden intern in der Berichtsserverdatenbank gespeichert. Sie können die Berichtsaktivität eines Berichtsservers, der im einheitlichen Modus oder im integrierten SharePoint-Modus ausgeführt wird, nachverfolgen. Ist der Berichtsserver Teil einer Bereitstellung für horizontales Skalieren, zeichnet das Berichtsausführungsprotokoll die Berichtsaktivität der gesamten Bereitstellung in einer einzelnen Protokolldatei auf.  
  
 Um diese Seite zu öffnen, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]starten Sie, stellen eine Verbindung mit einem Berichts Server her, klicken mit der rechten Maustaste auf den Namen des Berichts Servers und wählen **Eigenschaften**aus. Klicken Sie auf **Protokollierung** , um diese Seite zu öffnen.  
  
## <a name="options"></a>Tastatur  
 **Protokollierung der Berichts Ausführung aktivieren**  
 Klicken Sie auf diese Schaltfläche, um Informationen über die Berichtsaktivität zu erstellen und zu speichern. Ist diese Option aktiviert, verfolgt der Berichtsserver nach, welche Berichte verwendet werden, die Häufigkeit der Berichtsverarbeitung, der Typ des durchgeführten Berichtsvorgangs, das Ausgabeformat und wer den Bericht ausgeführt hat. Weitere Informationen zu zusätzlichen Datenpunkten, die im Protokoll aufgezeichnet werden, finden Sie unter [Berichts Server-Ausführungs Protokoll und die ExecutionLog3-Sicht](../report-server/report-server-executionlog-and-the-executionlog3-view.md).  
  
 **Protokolleinträge entfernen, die älter sind als die folgende Anzahl von Tagen**  
 Geben Sie die Anzahl an Tagen an, nach denen die Protokolleinträge aus dem Berichtsausführungsprotokoll gelöscht werden. Der Standardwert ist 60 Tage.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Festlegen von Berichtsservereigenschaften &#40;Management Studio&#41;](set-report-server-properties-management-studio.md)   
 [Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Reporting Services-Protokolldateien und Quellen](../report-server/reporting-services-log-files-and-sources.md)   
 [Berichtsserver im Management Studio (F1-Hilfe)](report-server-in-management-studio-f1-help.md)   
 [Berichtsserverausführungsprotokoll und die ExecutionLog3-Ansicht](../report-server/report-server-executionlog-and-the-executionlog3-view.md)  
  
  
