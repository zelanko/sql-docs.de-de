---
title: Entfernen eines Steuerungspunkts für das Hilfsprogramm (SQL Server-Hilfsprogramm) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c048a416-900e-4c77-8243-e0f0d8b94068
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9620394788729b28eb040d6e5293d39e188e2763
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37290922"
---
# <a name="remove-a-utility-control-point-sql-server-utility"></a>Entfernen eines Steuerungspunkts für das Hilfsprogramm (SQL Server-Hilfsprogramm)
  In diesem Thema wird beschrieben, wie Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Steuerungspunkt für das Hilfsprogramm (UCP) von der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[tsql](../../includes/tsql-md.md)]entfernen können.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So entfernen Sie einen Steuerungspunkt für das Hilfsprogramm mit**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
 Bevor Sie den UCP aus dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm entfernen, die folgenden Bedingungen erfüllt sein. Die gespeicherte Prozedur führt die erforderlichen Überprüfungen im Rahmen des Vorgangs aus.  
  
-   Vor dem Ausführen dieser Prozedur müssen alle verwalteten Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus dem UCP entfernt werden. Beachten Sie dabei, dass der UCP eine verwaltete Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist. Weitere Informationen finden Sie unter [Entfernen einer Instanz von SQL Server aus dem SQL Server-Hilfsprogramm](remove-an-instance-of-sql-server-from-the-sql-server-utility.md).  
  
-   Diese Prozedur muss auf einem Computer ausgeführt werden, der ein UCP ist.  
  
-   Wenn die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , aus der der UCP entfernt wurde, nur Datensammlungen enthält, die nicht von dem Hilfsprogramm stammen, wird die UMDW-Datenbank (sysutility_mdw) von der Prozedur nicht gelöscht. In diesem Fall muss die UMDW-Datenbank (sysutility_mdw) manuell gelöscht werden, bevor der UCP erneut erstellt werden kann.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Diese Prozedur muss ausgeführt werden, von einem Benutzer mit `sysadmin` Berechtigungen die gleichen Berechtigungen, die zum Erstellen eines UCP erforderlich sind.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-remove-a-utility-control-point"></a>So entfernen Sie einen Steuerungspunkt für das Hilfsprogramm  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
```  
EXEC msdb.dbo.sp_sysutility_ucp_remove;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen und Tasks im SQL Server-Hilfsprogramm](sql-server-utility-features-and-tasks.md)   
 [Verwenden des Hilfsprogramm-Explorers zum Verwalten des SQL Server-Hilfsprogramms](use-utility-explorer-to-manage-the-sql-server-utility.md)   
 [Problembehandlung beim SQL Server-Hilfsprogramm](../../database-engine/troubleshoot-the-sql-server-utility.md)  
  
  
