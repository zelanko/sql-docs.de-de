---
title: Auflisten von Informationen zu Auftragskategorien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 69abea91334f53993fec78e2204cee1573afd780
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48181580"
---
# <a name="list-job-category-information"></a>Auflisten von Informationen zu Auftragskategorien
  Wie Sie auftragskategorieinformationen in auflisten [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mit [!INCLUDE[tsql](../../includes/tsql-md.md)] oder SQL Server Management Objects.  

  
##  <a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implement SQL Server Agent Security](implement-sql-server-agent-security.md).  

  
##  <a name="TSQL"></a> Verwenden von Transact-SQL  
  
#### <a name="to-list-job-category-information"></a>So listen Sie Informationen zu Auftragskategorien auf  
  
1.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit einer [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Instanz her.  
  
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
  
 Verwenden der `JobCategory` Klasse, indem Sie eine Programmiersprache, die Sie, wie z. B. Visual Basic, Visual c# oder PowerShell auswählen... Weitere Informationen finden Sie unter [SQL Server Management Objects &#40;SMO&#41; Programming Guide](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md).  
  
  
  
