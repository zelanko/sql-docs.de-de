---
title: Veraltete Sicherung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 307a4ad0-675a-4f97-9a3c-cedd61bdfae5
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 702d49974dc77aad02b9cf79a1ebeff2ed03dc25
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148348"
---
# <a name="outdated-backup"></a>Obsolete Sicherung
  Diese Regel überprüft, ob aktuelle Sicherungen einer Datenbank existieren. Die Planung regelmäßiger Sicherungen ist wichtig, um die Datenbanken vor Datenverlust aufgrund vieler verschiedener Fehler zu schützen. Die geeignete Häufigkeit der Datensicherung hängt vom Wiederherstellungsmodell der Datenbank und von den Unternehmensrichtlinien hinsichtlich potenziellen Datenverlusts ab sowie davon, wie oft die Datenbank aktualisiert wird. Wird die Datenbank häufig aktualisiert, steigt die Gefahr des Datenverlusts zwischen den Sicherungsvorgängen stark an.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Wir empfehlen, dass Sie Sicherungen häufig genug ausführen, um Datenbanken vor Datenverlust zu schützen.  
  
 Sowohl das einfache als auch das vollständige Wiederherstellungsmodell erfordern Datensicherungen. In beiden Wiederherstellungsmodellen können Sie jede vollständige Sicherung mit differenziellen Sicherungen ergänzen, um das Risiko eines Datenverlusts zu verringern.  
  
 Für Datenbanken, die das vollständige Wiederherstellungsmodell verwenden, empfehlen wir häufige Protokollsicherungen. Von einer Produktionsdatenbank mit sehr wichtigen Daten sollten Protokollsicherungen in der Regel alle 1 bis 15 Minuten erstellt werden.  
  
> [!NOTE]  
>  Die empfohlene Methode zur Planung von Sicherungen ist ein Datenbankwartungsplan.  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Sichern und Wiederherstellen von Systemdatenbanken &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [Wiederherstellungsmodelle &#40;SQL Server&#41;](../backup-restore/recovery-models-sql-server.md)  
  
 [Erstellen einer differenziellen Datenbanksicherung &#40;SQL Server&#41;](../backup-restore/create-a-differential-database-backup-sql-server.md)  
  
 [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md)  
  
 [Wartungspläne](../maintenance-plans/maintenance-plans.md)  
  
 [Transaktionsprotokollsicherungen &#40;SQL Server&#41;](../backup-restore/transaction-log-backups-sql-server.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  