---
title: Anzeigen des Status einer gespiegelten Datenbank (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- states [SQL Server], database mirroring
- database mirroring [SQL Server], states
ms.assetid: 544f4194-253e-4c57-96ca-31c16301434f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9ef1c67955944277c7a8b6dd7ec1289fb8a2d280
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68050593"
---
# <a name="view-the-state-of-a-mirrored-database-sql-server-management-studio"></a>Anzeigen des Status einer gespiegelten Datenbank (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
    |Wird synchronisiert|Der Inhalt der Spiegeldatenbank liegt zeitlich hinter dem Inhalt der Prinzipaldatenbank. Die Prinzipalserverinstanz sendet Protokolldatensätze an die Spiegelserverinstanz, die die Änderungen auf die Spiegeldatenbank anwendet, um ein Rollforward dafür auszuführen.<br /><br /> Zu Beginn einer Datenbank-Spiegelungssitzung weisen die Spiegel- und Prinzipaldatenbanken den Wird synchronisiert-Status auf.|  
    |Failover|In der Prinzipalserverinstanz wurde ein manuelles Failover (Rollentausch) gestartet, aber noch nicht von der Spiegeldatenbank akzeptiert.|  
    |Synchronisiert|Die Spiegeldatenbank enthält die gleichen Daten wie die Prinzipaldatenbank. Manuelles und automatisches Failover sind *nur* im Synchronisiert-Status möglich.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Spiegelungsstatus &#40;SQL Server&#41;](../../database-engine/database-mirroring/mirroring-states-sql-server.md)  
  
  
