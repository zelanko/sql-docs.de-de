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
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62824393"
---
# <a name="unsuppress-run-custom-report-warnings"></a>Aufheben der Unterdrückung von Warnungen für das Ausführen von benutzerdefinierten Berichten
  Für benutzerdefinierte Berichte gibt es zwei Warndialogfelder. In diesem Thema wird beschrieben, wie die Unterdrückung der Anzeige dieser Felder in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]aufgehoben werden kann.  
  
 Standardmäßig wird das Dialogfeld **Benutzerdefinierten Bericht ausführen** vor dem Ausführen eines benutzerdefinierten Berichts angezeigt. Wenn Sie das Kontrollkästchen **Diese Meldung nicht mehr anzeigen** aktivieren, wird das Dialogfeld nicht mehr angezeigt. Standardmäßig wird das Dialogfeld **Benutzerdefinierten Bericht ausführen** auch dann angezeigt, wenn Sie einen benutzerdefinierten Bericht öffnen und dann auf einen Link klicken, um einen anderen benutzerdefinierten Bericht zu öffnen. In diesem Dialogfeld wird der vollständige Pfad zur benutzerdefinierten Drillthroughberichtsdatei angezeigt. Wenn Sie das Kontrollkästchen **Diese Meldung nicht mehr anzeigen** aktivieren, wird das Dialogfeld nicht mehr angezeigt.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-unsuppress-the-main-custom-report-warning-dialog-box"></a>So heben Sie die Unterdrückung des Warndialogfelds für den benutzerdefinierten Hauptbericht auf  
  
1.  Herstellen einer Verbindung mit \< *Server*>\\<*Freigabe*>|\<*Laufwerk*> \ Dokumente und Einstellungen\\< UserProfile\>\Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml.  
  
2.  Mit der rechten Maustaste `reports.xml`, und klicken Sie dann auf **bearbeiten**.  
  
3.  Änderung **\<SuppressWarning > true\</SuppressWarning > um \<SuppressWarning > false\</SuppressWarning >** .  
  
4.  Starten Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] neu.  
  
#### <a name="to-unsuppress-the-drill-through-custom-report-warning-dialog-box"></a>So heben Sie die Unterdrückung des Warndialogfelds für den benutzerdefinierten Drillthroughbericht auf  
  
1.  Herstellen einer Verbindung mit \< *Server*>\\<*Freigabe*>|\<*Laufwerk*> \ Dokumente und Einstellungen\\< UserProfile\>\Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.xml.  
  
2.  Mit der rechten Maustaste `reports.xml`, und klicken Sie auf **bearbeiten**.  
  
3.  Änderung  **\<SuppressDrillthroughWarning > true\</SuppressDrillthroughWarning > um \<SuppressDrillthroughWarning > false\</SuppressDrillthroughWarning >** .  
  
4.  Starten Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] neu.  
  
## <a name="see-also"></a>Siehe auch  
 [Benutzerdefinierte Berichte in Management Studio](custom-reports-in-management-studio.md)   
 [Hinzufügen eines benutzerdefinierten Berichts zu Management Studio](add-a-custom-report-to-management-studio.md)   
 [Verwenden benutzerdefinierter Berichte mit Eigenschaften von Objekt-Explorer-Knoten](use-custom-reports-with-object-explorer-node-properties.md)  
  
  
