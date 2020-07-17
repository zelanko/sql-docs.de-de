---
title: Entfernen eines Steuerungspunkts für das Hilfsprogramm (SQL Server-Hilfsprogramm) | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie einen Steuerungspunkt für das SQL Server-Hilfsprogramm aus diesem entfernen. Sie können Transact-SQL verwenden, um eine gespeicherte Prozedur für diese Aufgabe auszuführen.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c048a416-900e-4c77-8243-e0f0d8b94068
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b55f0a51738b3c266a1ca088f332a7e13769a914
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773514"
---
# <a name="remove-a-utility-control-point-sql-server-utility"></a>Entfernen eines Steuerungspunkts für das Hilfsprogramm (SQL Server-Hilfsprogramm)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  In diesem Thema wird beschrieben, wie Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Steuerungspunkt für das Hilfsprogramm (UCP) von der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[tsql](../../includes/tsql-md.md)]entfernen können.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   **So entfernen Sie einen Steuerungspunkt für das Hilfsprogramm mit**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
 Bevor Sie den UCP aus dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Hilfsprogramm entfernen, die folgenden Bedingungen erfüllt sein. Die gespeicherte Prozedur führt die erforderlichen Überprüfungen im Rahmen des Vorgangs aus.  
  
-   Vor dem Ausführen dieser Prozedur müssen alle verwalteten Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus dem UCP entfernt werden. Beachten Sie dabei, dass der UCP eine verwaltete Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist. Weitere Informationen finden Sie unter [Entfernen einer Instanz von SQL Server aus dem SQL Server-Hilfsprogramm](../../relational-databases/manage/remove-an-instance-of-sql-server-from-the-sql-server-utility.md).  
  
-   Diese Prozedur muss auf einem Computer ausgeführt werden, der ein UCP ist.  
  
-   Wenn die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , aus der der UCP entfernt wurde, nur Datensammlungen enthält, die nicht von dem Hilfsprogramm stammen, wird die UMDW-Datenbank (sysutility_mdw) von der Prozedur nicht gelöscht. In diesem Fall muss die UMDW-Datenbank (sysutility_mdw) manuell gelöscht werden, bevor der UCP erneut erstellt werden kann.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Die Prozedur muss von einem Benutzer mit **sysadmin** -Berechtigungen ausgeführt werden, d. h. den gleichen Berechtigungen, die auch zum Erstellen eines UCP erforderlich sind.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-remove-a-utility-control-point"></a>So entfernen Sie einen Steuerungspunkt für das Hilfsprogramm  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
```  
EXEC msdb.dbo.sp_sysutility_ucp_remove;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Funktionen und Tasks im SQL Server-Hilfsprogramm](../../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [Verwenden des Hilfsprogramm-Explorers zum Verwalten des SQL Server-Hilfsprogramms](../../relational-databases/manage/use-utility-explorer-to-manage-the-sql-server-utility.md)   
 [Problembehandlung beim SQL Server-Hilfsprogramm](https://msdn.microsoft.com/library/f5f47c2a-38ea-40f8-9767-9bc138d14453)  
  
  
