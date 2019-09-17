---
title: Die Verlaufs Tabellen für große Sicherungen oder Wiederherstellungen lassen das Upgrade scheinbar nicht Antworten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- backup history tables
- history tables
ms.assetid: f88d86ec-324b-4518-b6d7-1af7e7265812
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e4d994eb6d345ab98e6cd51a44c7c90a74bafd3a
ms.sourcegitcommit: f76b4e96c03ce78d94520e898faa9170463fdf4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2019
ms.locfileid: "70874603"
---
# <a name="large-backup-or-restore-history-tables-make-upgrade-appear-to-not-respond"></a>Das Upgrade reagiert bei Verlaufstabellen für große Sicherungen oder Wiederherstellungen anscheinend nicht mehr
  In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] wurden einigen Verlaufstabellen für Sicherungen und Wiederherstellungen neue Spalten hinzugefügt. Zum Aktualisieren dieser Tabellen müssen die neuen Spalten hinzugefügt werden. Wenn mindestens eine dieser Tabellen viele Zeilen enthält, steht das Upgrade bei der ALTER TABLE-Anweisung, die der Tabelle Spalten hinzufügt, über einen langen Zeitraum still.  
  
## <a name="component"></a>Komponente  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Beschreibung  
 Das Upgrade kann anscheinend nicht mehr reagieren, wenn eine der folgenden Sicherungs-oder Wiederherstellungs Verlaufs Tabellen eine große Anzahl von Zeilen enthält:  
  
-   **backupfile**  
  
-   **backupmediafamily**  
  
-   **backupmediaset**  
  
-   **backupset**  
  
-   **restorefile**  
  
-   **restorefilegroup**  
  
-   **restorehistory**  
  
 Wenn eine dieser Tabellen 10.000 oder mehr Zeilen hat, meldet der Upgrade Advisor einen Nichtkompatibilitätsfehler. Er gibt nicht an, welche Tabelle die zulässige Anzahl an Zeilen übersteigt. Die erste Tabelle, die 10.000 Zeilen übersteigt, verursacht den Fehler.  
  
## <a name="corrective-action"></a>Korrekturmaßnahme  
 Es empfiehlt sich vor dem Upgrade einer Datenbank, die Anzahl der Zeilen auf unter 10.000 zu reduzieren, falls eine der Tabellen mehr als 10.000 Zeilen besitzt. Um Zeilen in allen diesen Tabellen zu reduzieren, können Sie die gespeicherte Prozedur **sp_delete_backuphistory** ausführen. Diese Prozedur löscht die Einträge in allen Verlaufstabellen für Sicherungen und Wiederherstellungen der Sicherungssätze, die älter sind als das angegebene Datum. Weitere Informationen finden Sie unter [sp_delete_backuphistory &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql).  
  
> [!NOTE]  
>  Sie können eine Datenbank aktualisieren, deren Verlaufstabellen für Sicherungen und Wiederherstellungen mehr als 10.000 Zeilen besitzen. Beim Ändern großer Tabellen entsteht jedoch der Eindruck, dass das Upgrade still steht. Je größer die Tabellen sind, um so länger dauert das Setup.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine Upgradeprobleme](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 Upgrade Advisor &#91;neu&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
