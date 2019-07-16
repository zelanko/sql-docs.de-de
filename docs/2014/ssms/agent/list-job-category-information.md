---
title: Auflisten von Informationen zu Auftragskategorien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ac903ecb951e98e29dcd6521f8c9623f8cc62768
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68189151"
---
# <a name="list-job-category-information"></a>Auflisten von Informationen zu Auftragskategorien
  Wie Sie auftragskategorieinformationen in auflisten [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[tsql](../../includes/tsql-md.md)] oder SQL Server Management Objects.  

  
##  <a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  

  
##  <a name="TSQL"></a> Verwenden von Transact-SQL  
  
#### <a name="to-list-job-category-information"></a>So listen Sie Informationen zu Auftragskategorien auf  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [Sp_help_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-category-transact-sql).  
  
  
##  <a name="SMO"></a> Verwendung von SQL Server Management Objects  
 **So listen Sie Informationen zu Auftragskategorien auf**  
  
 Verwenden Sie die `JobCategory`-Klasse in einer von Ihnen ausgewählten Programmiersprache, z. B. Visual Basic, Visual C# oder PowerShell. Weitere Informationen finden Sie unter [SQL Server Management Objects &#40;SMO&#41; Programming Guide](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md).  
  
  
  
