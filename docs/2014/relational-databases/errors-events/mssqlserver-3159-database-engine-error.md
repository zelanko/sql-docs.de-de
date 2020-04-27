---
title: MSSQLSERVER_3159 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3159 (Database Engine error)
ms.assetid: c93c1003-0e3a-40aa-9873-44a0f5b8b57e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0373952a28a901519d1d40e92750af3da72f94e5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62868881"
---
# <a name="mssqlserver_3159"></a>MSSQLSERVER_3159
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|3159|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LDDB_LOGNOTBACKEDUP|  
|Meldungstext|Das Protokollfragment für die "%ls"-Datenbank wurde nicht gesichert. Sichern Sie das Protokoll mit BACKUP LOG WITH NORECOVERY, falls es Daten enthält, die Sie nicht verlieren möchten. Verwenden Sie die WITH REPLACE- oder WITH STOPAT-Klausel der RESTORE-Anweisung, um den Inhalt des Protokolls zu überschreiben.|  
  
## <a name="explanation"></a>Erklärung  
 In den meisten Fällen ist es bei Verwendung des vollständigen oder des massenprotokollierten Wiederherstellungsmodells in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erforderlich, das Protokollfragment zu sichern, um die Protokolldatensätze aufzuzeichnen, die noch nicht gesichert wurden. Eine Protokollsicherung des Protokollfragments, die unmittelbar vor einem Wiederherstellungsvorgang erstellt wurde, wird als Sicherung des Protokollfragments bezeichnet.  
  
 Wenn Sie eine Datenbank bis zum Zeitpunkt des Fehlers wiederherstellen, ist die Sicherung des Protokollfragments im Wiederherstellungsplan die letzte relevante Sicherung. Wenn Sie das Protokollfragment nicht sichern können, kann eine Datenbank nur bis zum Ende der letzten Sicherung wiederhergestellt werden, die vor dem Fehler erstellt wurde.  
  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist es normalerweise erforderlich, eine Sicherung des Protokollfragments auszuführen, bevor die Wiederherstellung einer Datenbank gestartet wird. Durch die Sicherung des Protokollfragments wird Datenverlust verhindert und die Protokollkette intakt gehalten. Nicht für alle Wiederherstellungsszenarien ist jedoch eine Sicherung des Protokollfragments erforderlich. Es ist keine Sicherung des Protokollfragments erforderlich, wenn der Wiederherstellungspunkt in einer früheren Protokollsicherung enthalten ist oder wenn Sie die Datenbank verschieben oder ersetzen (überschreiben) und sie nicht für einen Zeitpunkt nach der letzten Sicherung wiederherstellen müssen. Wenn die Protokolldateien beschädigt sind und keine Sicherung des Protokollfragments erstellt werden kann, müssen Sie zudem die Datenbank ohne Verwendung einer Sicherung des Protokollfragments wiederherstellen. Dabei gehen alle Transaktionen verloren, die nach der letzten Protokollsicherung ausgeführt wurden. Weitere Informationen finden Sie im Folgenden unter „Wiederherstellen ohne Verwendung einer Sicherung des Protokollfragments“.  
  
> [!CAUTION]  
>  REPLACE sollte selten und nur nach sorgfältiger Überlegung verwendet werden.  
  
## <a name="user-action"></a>Benutzeraktion  
 Nehmen Sie eine Sicherung des Protokollfragments vor, und wiederholen Sie den Wiederherstellungsvorgang.  
  
 Wenn Sie das Protokollfragment nicht sichern können, verwenden Sie in Ihren RESTORE-Anweisungen WITH STOPAT oder WITH REPLACE.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wiederherstellen einer SQL Server Datenbank zu einem bestimmten Zeitpunkt &#40;vollständigen Wiederherstellungs Modell&#41;](../backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)   
 [Sichern Sie das Transaktionsprotokoll, wenn die Datenbank &#40;SQL Server beschädigt ist&#41;](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)   
 [Sichern eines Transaktions Protokolls &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md)   
 [Sicherungen des Protokollfragments &#40;SQL Server&#41;](../backup-restore/tail-log-backups-sql-server.md)  
  
  
