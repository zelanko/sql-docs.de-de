---
title: Aufheben der Unterdrückung von Warnungen für das Ausführen von benutzerdefinierten Berichten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 0deed900-c910-4d12-aac0-6ab9e39eb068
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ed653b16fe524f364ba89f13e00715b725080033
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62824393"
---
# <a name="unsuppress-run-custom-report-warnings"></a>Aufheben der Unterdrückung von Warnungen für das Ausführen von benutzerdefinierten Berichten
  Für benutzerdefinierte Berichte gibt es zwei Warndialogfelder. In diesem Thema wird beschrieben, wie die Unterdrückung der Anzeige dieser Felder in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]aufgehoben werden kann.  
  
 Standardmäßig wird das Dialogfeld **Benutzerdefinierten Bericht ausführen** vor dem Ausführen eines benutzerdefinierten Berichts angezeigt. Wenn Sie das Kontrollkästchen **Diese Meldung nicht mehr anzeigen** aktivieren, wird das Dialogfeld nicht mehr angezeigt. Standardmäßig wird das Dialogfeld **Benutzerdefinierten Bericht ausführen** auch dann angezeigt, wenn Sie einen benutzerdefinierten Bericht öffnen und dann auf einen Link klicken, um einen anderen benutzerdefinierten Bericht zu öffnen. In diesem Dialogfeld wird der vollständige Pfad zur benutzerdefinierten Drillthroughberichtsdatei angezeigt. Wenn Sie das Kontrollkästchen **Diese Meldung nicht mehr anzeigen** aktivieren, wird das Dialogfeld nicht mehr angezeigt.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-unsuppress-the-main-custom-report-warning-dialog-box"></a>So heben Sie die Unterdrückung des Warndialogfelds für den benutzerdefinierten Hauptbericht auf  
  
1.  Stellen Sie \<eine Verbindung mit dem *Server*>\\<*Freigabe*>|\<*Laufwerk* her\\> \Dokumente\>und Einstellungen<USERPROFILE \Anwendungsdaten\Microsoft\Microsoft SQL server\120\tools\shell\reports.Xml.  
  
2.  Klicken Sie mit `reports.xml`der rechten Maustaste, und klicken Sie dann auf **Bearbeiten**.  
  
3.  Ändern**\<Sie suppresswarning>\<true/SuppressWarning> \<auf suppresswarning>\<false/SuppressWarning>**.  
  
4.  Starten Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] neu.  
  
#### <a name="to-unsuppress-the-drill-through-custom-report-warning-dialog-box"></a>So heben Sie die Unterdrückung des Warndialogfelds für den benutzerdefinierten Drillthroughbericht auf  
  
1.  Stellen Sie \<eine Verbindung mit dem *Server*>\\<*Freigabe*>|\<*Laufwerk* her\\> \Dokumente\>und Einstellungen<USERPROFILE \Anwendungsdaten\Microsoft\Microsoft SQL server\120\tools\shell\reports.Xml.  
  
2.  Klicken Sie mit `reports.xml`der rechten Maustaste, und klicken Sie auf **Bearbeiten**  
  
3.  Ändern ** \<Sie suppressdrilldurchlauf Warning>\<true/SuppressDrillthroughWarning>\<auf suppressdrilldurchlauf Warning>\<false/SuppressDrillthroughWarning>**.  
  
4.  Starten Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] neu.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzerdefinierte Berichte in Management Studio](custom-reports-in-management-studio.md)   
 [Hinzufügen eines benutzerdefinierten Berichts zu Management Studio](add-a-custom-report-to-management-studio.md)   
 [Verwenden benutzerdefinierter Berichte mit Eigenschaften von Objekt-Explorer-Knoten](use-custom-reports-with-object-explorer-node-properties.md)  
  
  
