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
ms.openlocfilehash: dae8f1d98fb1758e9a9802883def1574bda68a78
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798207"
---
# <a name="list-job-category-information"></a>Auflisten von Informationen zu Auftragskategorien
  Auflisten von Informationen zu Auftrags Kategorien in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe [!INCLUDE[tsql](../../includes/tsql-md.md)] oder SQL Server Management Objects.  

  
##  <a name="Security"></a> Security  
 Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  

  
##  <a name="TSQL"></a> Verwenden von Transact-SQL  
  
#### <a name="to-list-job-category-information"></a>So listen Sie Informationen zu Auftragskategorien auf  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```sql
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
 Weitere Informationen finden Sie unter [sp_help_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-category-transact-sql).  
  
  
##  <a name="SMO"></a>Verwenden von SQL Server Management Objects  
 **So listen Sie Informationen zu Auftragskategorien auf**  
  
 Verwenden Sie die `JobCategory`-Klasse in einer von Ihnen ausgewählten Programmiersprache, z. B. Visual Basic, Visual C# oder PowerShell. Weitere Informationen finden Sie unter [SQL Server Management Objects &#40;SMO&#41; -Programmier Handbuch](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md).  
