---
title: Anzeigen des Status einer gespiegelten Datenbank (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- states [SQL Server], database mirroring
- database mirroring [SQL Server], states
ms.assetid: 544f4194-253e-4c57-96ca-31c16301434f
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4ec5f60fb16e9e4b654045bcb65b8ea6d9c6937e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36057014"
---
# <a name="view-the-state-of-a-mirrored-database-sql-server-management-studio"></a>Anzeigen des Status einer gespiegelten Datenbank (SQL Server Management Studio)
  Während einer Datenbank-Spiegelungssitzung können Sie im Dialogfeld **Datenbankeigenschaften** auf der Seite **Wird gespiegelt** den Status anzeigen.  
  
### <a name="to-view-the-status-of-a-database-mirroring-session"></a>So zeigen Sie den Status der Datenbank-Spiegelungssitzung an  
  
1.  Nachdem Sie eine Verbindung mit der Prinzipalserverinstanz hergestellt haben, klicken Sie im Objekt-Explorer auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie **Datenbanken**, und wählen Sie die zu spiegelnde Datenbank aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Datenbank, wählen Sie **Tasks**aus, und klicken Sie dann auf **Spiegeln**. Dadurch wird die Seite **Spiegelung** im Dialogfeld **Datenbankeigenschaften** geöffnet.  
  
4.  Nach Beginn der Spiegelung wird im Fensterbereich **Status** der Status der Datenbank-Spiegelungssitzung angezeigt, und zwar ab dem Zeitpunkt, an dem Sie die Seite **Wird gespiegelt** ausgewählt oder auf die Schaltfläche **Aktualisieren** geklickt haben. Folgende Werte sind für den Status möglich:  
  
    |Status|Erklärung|  
    |------------|-----------------|  
    |\<leer>|Es ist keine Datenbank-Spiegelungssitzung vorhanden und keine Aktivität auf der Seite **Spiegelung** anzuzeigen.|  
    |Angehalten|Die Prinzipaldatenbank wird ausgeführt, sendet jedoch keine Protokolle an den Spiegelserver. Die Spiegelkopie der Datenbank ist nicht verfügbar.|  
    |Keine Verbindung|Die Prinzipalserverinstanz kann keine Verbindung mit dem Partner oder mit der Zeugenserverinstanz herstellen (soweit vorhanden).|  
    |Wird synchronisiert|Der Inhalt der Spiegeldatenbank hält mit dem Inhalt der Prinzipaldatenbank nicht Schritt. Die Prinzipalserverinstanz sendet Protokolldatensätze an die Spiegelserverinstanz, die die Änderungen auf die Spiegeldatenbank anwendet, um ein Rollforward dafür auszuführen.<br /><br /> Zu Beginn einer Datenbank-Spiegelungssitzung weisen die Spiegel- und Prinzipaldatenbanken den Wird synchronisiert-Status auf.|  
    |Failover|In der Prinzipalserverinstanz wurde ein manuelles Failover (Rollentausch) gestartet, aber noch nicht von der Spiegeldatenbank akzeptiert.|  
    |Synchronisiert|Die Spiegeldatenbank enthält die gleichen Daten wie die Prinzipaldatenbank. Manuelles und automatisches Failover sind *nur* im Synchronisiert-Status möglich.|  
  
## <a name="see-also"></a>Siehe auch  
 [Spiegelungsstatus &#40;SQL Server&#41;](mirroring-states-sql-server.md)  
  
  