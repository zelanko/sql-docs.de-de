---
title: Löschen von Datenbankobjekten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- deleting database objects
ms.assetid: dbb94fdf-c85b-477b-8e84-f830d259bade
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 5cdb612a422610e9c077aa7cb51bddba43df4216
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43034414"
---
# <a name="deleting-database-objects"></a>Löschen von Datenbankobjekten
  Sie könnten einfach nur die Datenbank löschen, um dieses Lernprogramm vollständig zu entfernen. In diesem Thema führen Sie jedoch die erforderlichen Schritte aus, um jede Aktion rückgängig zu machen, die Sie im Lernprogramm ausgeführt haben.  
  
### <a name="removing-permissions-and-objects"></a>Entfernen von Berechtigungen und Objekten  
  
1.  Bevor Sie Objekte löschen, stellen Sie sicher, dass Sie sich in der richtigen Datenbank befinden:  
  
    ```  
    USE TestData;  
    GO  
    ```  
  
2.  Führen Sie die `REVOKE` -Anweisung aus, um die Ausführungsberechtigung für `Mary` in der gespeicherten Prozedur zu entfernen:  
  
    ```  
    REVOKE EXECUTE ON pr_Names FROM Mary;  
    GO  
  
    ```  
  
3.  Führen Sie die `DROP` -Anweisung aus, um die Berechtigung für `Mary` zum Zugriff auf die `TestData` -Datenbank zu entfernen:  
  
    ```  
    DROP USER Mary;  
    GO  
  
    ```  
  
4.  Führen Sie die `DROP` -Anweisung aus, um die Berechtigung für `Mary` zum Zugriff auf die Instanz von [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]zu entfernen:  
  
    ```  
    DROP LOGIN [<computer_name>\Mary];  
    GO  
  
    ```  
  
5.  Verwenden Sie die `DROP` -Anweisung zum Entfernen der gespeicherten Prozedur `pr_Names`:  
  
    ```  
    DROP PROC pr_Names;  
    GO  
  
    ```  
  
6.  Verwenden Sie die `DROP` -Anweisung zum Entfernen der `vw_Names`-Sicht:  
  
    ```  
    DROP View vw_Names;  
    GO  
  
    ```  
  
7.  Verwenden Sie die `DELETE` -Anweisung zum Entfernen von Datenzeilen aus der `Products` -Tabelle:  
  
    ```  
    DELETE FROM Products;  
    GO  
  
    ```  
  
8.  Verwenden Sie die `DROP` -Anweisung zum Entfernen der `Products` -Tabelle:  
  
    ```  
    DROP Table Products;  
    GO  
  
    ```  
  
9. Es ist nicht möglich, die `TestData` -Datenbank zu entfernen, während Sie sich in der Datenbank befinden. Wechseln Sie daher den Kontext zu einer anderen Datenbank, und verwenden Sie dann die `DROP` -Anweisung, um die `TestData` -Datenbank zu entfernen.  
  
    ```  
    USE MASTER;  
    GO  
    DROP DATABASE TestData;  
    GO  
  
    ```  
  
 Damit ist das Lernprogramm zum Schreiben von [!INCLUDE[tsql](../includes/tsql-md.md)] -Anweisungen beendet. Beachten Sie, dass dieses Lernprogramm nur eine kurze Übersicht bietet und darin nicht alle Optionen der verwendeten Anweisungen beschrieben werden. Das Entwerfen und Erstellen einer effizienten Datenbankstruktur und das Konfigurieren des sicheren Zugriffs auf die Daten erfordern eine komplexere Datenbank als in diesem Lernprogramm gezeigt.  
  
## <a name="return-to-sql-server-tools-portal"></a>Zurück zum Portal für SQL Server-Tools  
 [Lernprogramm: Schreiben von Transact-SQL-Anweisungen](tutorial-writing-transact-sql-statements.md)  
  
## <a name="see-also"></a>Siehe auch  
 [REVOKE &#40;Transact-SQL&#41;](/sql/t-sql/statements/revoke-transact-sql)   
 [DROP USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-user-transact-sql)   
 [DROP LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-login-transact-sql)   
 [DROP PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-procedure-transact-sql)   
 [DROP VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-view-transact-sql)   
 [DELETE &#40;Transact-SQL&#41;](/sql/t-sql/statements/delete-transact-sql)   
 [DROP TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-table-transact-sql)   
 [DROP DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-database-audit-specification-transact-sql)  
  
  
