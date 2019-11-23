---
title: Vollziehen des Austritts eines Zielservers aus einem Masterserver | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
ms.assetid: a6da262b-7b38-4ce4-bfd6-6a557c6e8a84
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3f51e8f62a6be442c123c5a1309293e204caf08f
ms.sourcegitcommit: a165052c789a327a3a7202872669ce039bd9e495
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72783221"
---
# <a name="defect-a-target-server-from-a-master-server"></a>Vollziehen des Austritts eines Zielservers aus einem Masterserver
  In diesem Thema wird beschrieben, wie Sie den Austritt eines Zielservers aus einem Masterserver in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)]oder SQL Server Management Objects (SMO) vollziehen. Führen Sie die folgenden Schritte auf dem Zielserver aus.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **Vollziehen des Austritts eines Zielservers mit:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [SMO](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> Berechtigungen  
 Zum Ausführen dieser gespeicherten Prozedur muss ein Benutzer Mitglied der festen Serverrolle `sysadmin` sein.  
  
##  <a name="SSMSProcedure"></a> Verwendung von SQL Server Management Studio  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>So tragen Sie bei einem Masterserver einen Zielserver aus  
  
1.  Erweitern Sie in **Objekt-Explorer**einen Server, der als Zielserver konfiguriert ist.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, zeigen Sie auf **Multiserveradministration**, und klicken Sie dann auf **Austragen**.  
  
3.  Klicken Sie auf **Ja** , um zu bestätigen, dass Sie diesen Zielserver bei einem Masterserver austragen möchten.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>So tragen Sie bei einem Masterserver einen Zielserver aus  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie auf der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
```sql
sp_msx_defect ;  
```  
  
 Weitere Informationen finden Sie unter [sp_msx_defect &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-defect-transact-sql).  
  
##  <a name="PowerShellProcedure"></a>Verwenden von SQL Server Management Objects (SMO)  
 Verwenden Sie `MsxDefect Method`.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Multiserverumgebung](create-a-multiserver-environment.md)   
 [Automatisierte Verwaltung in einem Unternehmen](automated-administration-across-an-enterprise.md)   
 [Vollziehen des Austritts mehrerer Zielserver aus einem Masterserver](defect-multiple-target-servers-from-a-master-server.md)  
