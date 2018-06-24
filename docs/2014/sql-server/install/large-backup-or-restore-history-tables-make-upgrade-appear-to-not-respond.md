---
title: Verlaufstabellen für große Backup- oder Restore lassen das Upgrade scheinbar nicht reagieren | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- backup history tables
- history tables
ms.assetid: f88d86ec-324b-4518-b6d7-1af7e7265812
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1b7d3f6c5734f743d83a712cea745c3816bcdbc0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049858"
---
# <a name="large-backup-or-restore-history-tables-make-upgrade-appear-to-not-respond"></a>Das Upgrade reagiert bei Verlaufstabellen für große Sicherungen oder Wiederherstellungen anscheinend nicht mehr
  In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] wurden einigen Verlaufstabellen für Sicherungen und Wiederherstellungen neue Spalten hinzugefügt. Zum Aktualisieren dieser Tabellen müssen die neuen Spalten hinzugefügt werden. Wenn mindestens eine dieser Tabellen viele Zeilen enthält, steht das Upgrade bei der ALTER TABLE-Anweisung, die der Tabelle Spalten hinzufügt, über einen langen Zeitraum still.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Der Upgradevorgang steht scheinbar still, wenn eine der folgenden Verlaufstabellen für Sicherungen oder Wiederherstellungen viele Zeilen enthält.  
  
-   **backupfile**  
  
-   **backupmediafamily**  
  
-   **backupmediaset**  
  
-   **backupset**  
  
-   **restorefile**  
  
-   **restorefilegroup**  
  
-   **restorehistory**  
  
 Wenn eine dieser Tabellen 10.000 oder mehr Zeilen hat, meldet der Upgrade Advisor einen Nichtkompatibilitätsfehler. Er gibt nicht an, welche Tabelle die zulässige Anzahl an Zeilen übersteigt. Die erste Tabelle, die 10.000 Zeilen übersteigt, verursacht den Fehler.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Es empfiehlt sich vor dem Upgrade einer Datenbank, die Anzahl der Zeilen auf unter 10.000 zu reduzieren, falls eine der Tabellen mehr als 10.000 Zeilen besitzt. Um Zeilen in allen diesen Tabellen zu reduzieren, führen Sie die **Sp_delete_backuphistory** gespeicherte Prozedur. Diese Prozedur löscht die Einträge in allen Verlaufstabellen für Sicherungen und Wiederherstellungen der Sicherungssätze, die älter sind als das angegebene Datum. Weitere Informationen finden Sie unter [sp_delete_backuphistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql).  
  
> [!NOTE]  
>  Sie können eine Datenbank aktualisieren, deren Verlaufstabellen für Sicherungen und Wiederherstellungen mehr als 10.000 Zeilen besitzen. Beim Ändern großer Tabellen entsteht jedoch der Eindruck, dass das Upgrade still steht. Je größer die Tabellen sind, um so länger dauert das Setup.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine-Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
