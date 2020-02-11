---
title: Ändern der Zielwiederherstellungszeit einer Datenbank (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/13/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: e466419a-d8a4-48f7-8d97-13a903ad6b15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 72ac6ac92da531d0f653e0fc03d88d170b7706e5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62743216"
---
# <a name="change-the-target-recovery-time-of-a-database-sql-server"></a>Ändern der Zielwiederherstellungszeit einer Datenbank (SQL Server)
  In diesem Thema wird beschrieben, wie die Zielwiederherstellungszeit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]geändert wird. Standardmäßig ist die Zielwiederherstellungszeit 0, und die Datenbank verwendet *automatische Prüfpunkte* (die durch die Serveroption **Wiederherstellungsintervall** gesteuert werden). Das Festlegen der Zielwiederherstellungszeit auf größer 0 führt dazu, dass die Datenbank die *indirekten Prüfpunkte* verwendet und eine Obergrenze der Wiederherstellungszeit für diese Datenbank festlegt.  
  
> [!NOTE]  
>  Die Obergrenze, die für eine bestimmte Datenbank durch die Wiederherstellungszeiteinstellung für das Ziel angegeben wird, könnte überschritten werden, wenn eine Transaktion mit langer Laufzeit übermäßig lange UNDO-Zeiten verursacht.  
  
-   Vorbereitungen **:**[Einschränkungen](#Restrictions), [Sicherheit](#Security)    
  
-   So **Ändern Sie die Ziel Wiederherstellungszeit mit:**[SQL Server Management Studio](#SSMSProcedure) oder [Transact-SQL](#TsqlProcedure)    
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Restrictions"></a>  
  
> [!CAUTION]  
>  Im Fall einer Arbeitsauslastung für Onlinetransaktionen bei einer Datenbank, die für indirekte Prüfpunkte konfiguriert ist, kann eine Verringerung der Leistung auftreten. Indirekte Prüfpunkte stellen sicher, dass die Anzahl der modifizierten Seiten unter einem bestimmten Schwellenwert liegt, sodass die Datenbankwiederherstellung innerhalb der Zielwiederherstellungszeit abgeschlossen wird. Die Konfigurationsoption „Wiederherstellungsintervall“ ermittelt die Wiederherstellungszeit über die Anzahl der Transaktionen. Im Gegensatz dazu greifen indirekte Prüfpunkte auf die Anzahl der modifizierten Seiten zurück. Wenn für eine Datenbank, die eine große Anzahl von DML-Vorgängen empfängt, indirekte Prüfpunkte aktiviert sind, können beim Schreiben im Hintergrund leere modifizierte Puffer aggressiv auf den Datenträger geleert werden. Dadurch wird sichergestellt, dass der Zeitaufwand für die Wiederherstellung innerhalb der Zielwiederherstellungszeit der Datenbank liegt. Dies kann auf bestimmten Systemen zusätzliche E/A-Aktivitäten verursachen, die zu einem Leistungsengpass beitragen können, wenn das Datenträgersubsystem über oder nahe dem E/A-Schwellenwert arbeitet.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die ALTER-Berechtigung für die Datenbank.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 **So ändern Sie die Ziel Wiederherstellungszeit**  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie diese Instanz.  
  
2.  Klicken Sie mit der rechten Maustaste auf die Datenbank, die geändert werden soll, und klicken Sie auf den Befehl **Eigenschaften** .  
  
3.  Klicken Sie im Dialogfeld **Datenbankeigenschaften** auf die Seite **Optionen** .  
  
4.  Geben Sie im Bereich **Wiederherstellung** im Feld **Zielwiederherstellungszeit (Sekunden)** die Anzahl von Sekunden als gewünschte Obergrenze der Wiederherstellungszeit für diese Datenbank an.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **So ändern Sie die Ziel Wiederherstellungszeit**  
  
1.  Stellen Sie eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her, auf der sich die Datenbank befindet.  
  
2.  Verwenden Sie die folgende [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options)-Anweisung wie folgt:  
  
     TARGET_RECOVERY_TIME **=** _target_recovery_time_ {Sekunden | Minuten  
  
     *target_recovery_time*  
     Gibt bei einem Wert von größer 0 (Standardwert) die Obergrenze der Wiederherstellungszeit für die angegebene Datenbank im Fall eines Absturzes an.  
  
     SECONDS  
     Gibt an, dass *target_recovery_time* die Anzahl von Sekunden darstellt.  
  
     MINUTES  
     Gibt an, dass *target_recovery_time* die Anzahl von Minuten darstellt.  
  
     Im folgenden Beispiel wird die Zielwiederherstellungszeit der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank auf `60` Sekunden festgelegt.  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET TARGET_RECOVERY_TIME = 60 SECONDS;  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbankprüfpunkte &#40;SQL Server&#41;](database-checkpoints-sql-server.md)   
 [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
