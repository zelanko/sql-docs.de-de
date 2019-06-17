---
title: Löschen einer Datenbankmomentaufnahme (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- removing database snapshots
- deleting database snapshots
- database snapshots [SQL Server], deleting
ms.assetid: ad70ec97-d5fb-41aa-b72a-915e74b61b76
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d1387b6321ace59ec8a0c13ed03444553f4adf85
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62871916"
---
# <a name="drop-a-database-snapshot-transact-sql"></a>Löschen einer Datenbankmomentaufnahme (Transact-SQL)
  Wenn Sie eine Datenbank-Momentaufnahme löschen, wird er aus [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] gelöscht. Außerdem werden die Sparsedateien gelöscht, die von der Momentaufnahme verwendet werden. Wenn Sie eine Datenbank-Momentaufnahme löschen, werden alle Benutzerverbindungen damit beendet.  
  
## <a name="security"></a>Sicherheit  
  
###  <a name="Permissions"></a> Berechtigungen  
 Jeder Benutzer mit DROP DATABASE-Berechtigungen kann eine Datenbank-Momentaufnahme löschen.  
  
##  <a name="TsqlProcedure"></a> Löschen einer Datenbank-Momentaufnahme (mit Transact-SQL)  
 **So löschen Sie eine Datenbank-Momentaufnahme**  
  
1.  Identifizieren Sie die Datenbank-Momentaufnahme, die Sie löschen möchten. Sie können die Momentaufnahmen einer Datenbank in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]anzeigen. Weitere Informationen finden Sie unter [Anzeigen einer Datenbankmomentaufnahme &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md)anzeigen.  
  
2.  Geben Sie eine [DROP DATABASE](/sql/t-sql/statements/drop-database-audit-specification-transact-sql) -Anweisung aus, und geben Sie den Namen der Datenbank-Momentaufnahme an, die gelöscht werden soll. Die Syntax lautet wie folgt:  
  
     DROP DATABASE *database_snapshot_name* [ **,** ...*n* ]  
  
     Dabei ist *database_snapshot_name* der Name der Datenbank-Momentaufnahme, die gelöscht werden soll.  
  
####  <a name="TsqlExample"></a> Beispiel (Transact-SQL)  
 In diesem Beispiel wird eine Datenbank-Momentaufnahme namens SalesSnapshot0600 ohne Auswirkungen auf die Quelldatenbank gelöscht.  
  
```  
DROP DATABASE SalesSnapshot0600 ;  
```  
  
 Alle Benutzerverbindungen mit SalesSnapshot0600 werden beendet, und alle von der Momentaufnahme verwendeten Sparsedateien des NTFS-Dateisystems werden gelöscht.  
  
> [!NOTE]  
>  Informationen zum Verwenden von Sparsedateien für Datenbank-Momentaufnahmen finden Sie unter [Datenbankmomentaufnahmen &#40;SQL Server&#41;](database-snapshots-sql-server.md)anzeigen.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Erstellen einer Datenbankmomentaufnahme &#40;Transact-SQL&#41;](create-a-database-snapshot-transact-sql.md)  
  
-   [Anzeigen einer Datenbankmomentaufnahme &#40;SQL Server&#41;](view-a-database-snapshot-sql-server.md)  
  
-   [Wiederherstellen einer Datenbank zu einer Datenbank-Momentaufnahme](revert-a-database-to-a-database-snapshot.md)  
  

  
## <a name="see-also"></a>Siehe auch  
 [DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql)   
 [Datenbankmomentaufnahmen &#40;SQL Server&#41;](database-snapshots-sql-server.md)  
  
  
