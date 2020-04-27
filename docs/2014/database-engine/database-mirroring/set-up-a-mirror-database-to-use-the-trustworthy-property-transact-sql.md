---
title: Einrichten der TRUSTWORTHY-Eigenschaft für eine Spiegeldatenbank (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- TRUSTWORTHY database option
- mirror database [SQL Server]
- database mirroring [SQL Server], security
ms.assetid: 6993b076-78ef-453e-b0ea-e341b8e5ee3e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 29cafc7e9669ca322571ff171961dd64cab114cf
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62754336"
---
# <a name="set-up-a-mirror-database-to-use-the-trustworthy-property-transact-sql"></a>Einrichten der TRUSTWORTHY-Eigenschaft für eine Spiegeldatenbank (Transact-SQL)
  Beim Sichern einer Datenbank wird die TRUSTWORTHY-Datenbankeigenschaft auf OFF festgelegt. Deshalb ist TRUSTWORTHY bei einer neuen Spiegeldatenbank immer auf OFF festgelegt. Muss die Datenbank nach einem Failover vertrauenswürdig sein, sind zusätzliche Installationsschritte nach dem Beginn der Spiegelung erforderlich.  
  
> [!NOTE]  
>  Informationen zu dieser Datenbankeigenschaft finden Sie unter [TRUSTWORTHY-Datenbankeigenschaft](../../relational-databases/security/trustworthy-database-property.md).  
  
## <a name="procedure"></a>Verfahren  
  
#### <a name="to-setup-a-mirror-database-to-use-the-trustworthy-property"></a>So richten Sie die TRUSTWORTHY-Eigenschaft für eine Spiegeldatenbank ein  
  
1.  Stellen Sie auf der Prinzipalserverinstanz sicher, dass die TRUSTWORTHY-Eigenschaft für die Prinzipaldatenbank aktiviert ist.  
  
    ```  
    SELECT name, database_id, is_trustworthy_on FROM sys.databases   
    ```  
  
     Weitere Informationen finden Sie unter [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql).  
  
2.  Stellen Sie nach dem Beginn der Spiegelung sicher, dass die Datenbank derzeit die Prinzipaldatenbank ist, die Sitzung derzeit im synchronen Betriebsmodus ausgeführt wird und die Sitzung bereits synchronisiert ist.  
  
    ```  
    SELECT database_id, mirroring_role, mirroring_safety_level_desc, mirroring_state_desc FROM sys.database_mirroring  
    ```  
  
     Weitere Informationen finden Sie unter [sys.database_mirroring &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql).  
  
3.  Nach dem Synchronisieren der Spiegelungssitzung führen Sie manuell ein Failover zur Spiegeldatenbank aus.  
  
     Dies ist entweder mithilfe von SQL Server Management Studio oder Transact-SQL möglich:  
  
    -   [Manueller Failover für eine Datenbank-Spiegelungssitzung &#40;SQL Server Management Studio&#41;](manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   [Ausführen des manuellen Failovers einer Datenbank-Spiegelungssitzung &#40;Transact-SQL&#41;](manually-fail-over-a-database-mirroring-session-transact-sql.md)  
  
4.  Aktivieren Sie die TRUSTWORTHY-Datenbankeigenschaft mithilfe des folgenden ALTER DATABASE-Befehls:  
  
    ```  
    ALTER DATABASE <database_name> SET TRUSTWORTHY ON  
    ```  
  
     Weitere Informationen finden Sie unter [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).  
  
5.  Führen Sie optional erneut ein Failover aus, um zur ursprünglichen Prinzipaldatenbank zurückzukehren.  
  
6.  Wechseln Sie optional in den asynchronen Modus für hohe Leistung, indem Sie SAFETY auf OFF festlegen und sicherstellen, dass WITNESS ebenfalls auf OFF festgelegt ist.  
  
     In Transact-SQL:  
  
    -   [Ändern der Transaktionssicherheit in einer Datenbank-Spiegelungssitzung (Transact-SQL)](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)  
  
    -   [Entfernen des Zeugen aus einer Datenbank-Spiegelungssitzung &#40;SQL Server&#41;](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
     In SQL Server Management Studio:  
  
    -   [Einrichten einer Datenbank-Spiegelungssitzung mithilfe der Windows-Authentifizierung (SQL Server Management Studio)](establish-database-mirroring-session-windows-authentication.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [TRUSTWORTHY-Datenbankeigenschaft](../../relational-databases/security/trustworthy-database-property.md)   
 [Einrichten einer verschlüsselten Spiegeldatenbank](set-up-an-encrypted-mirror-database.md)  
  
  
