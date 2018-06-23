---
title: TRUSTWORTHY-Datenbankeigenschaft | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-security
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TRUSTWORTHY database property
ms.assetid: 64b2a53d-4416-4a19-acc0-664a61b45348
caps.latest.revision: 21
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 126785af52f4a16b98b8274b66d9c26fc2ceee34
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36056891"
---
# <a name="trustworthy-database-property"></a>TRUSTWORTHY-Datenbankeigenschaft
  Die TRUSTWORTHY-Datenbankeigenschaft gibt an, ob die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz die Datenbank und ihre Inhalte als vertrauenswürdig einstuft. Standardmäßig ist diese Einstellung OFF; sie kann jedoch mithilfe der ALTER DATABASE-Anweisung auf ON festgelegt werden. Beispiel: `ALTER DATABASE AdventureWorks2012 SET TRUSTWORTHY ON;`.  
  
> [!NOTE]  
>  Um diese Option festlegen zu können, müssen Sie Mitglied der festen Serverrolle **sysadmin** sein.  
  
 Diese Eigenschaft kann zum Verringern bestimmter Risiken verwendet werden, die als Ergebnis des Anfügens einer Datenbank vorhanden sein können, die eines der folgenden Objekte enthält:  
  
-   Bösartige Assemblys mit einer EXTERNAL_ACCESS- oder UNSAFE-Berechtigungseinstellung. Weitere Informationen finden Sie unter [CLR Integration Security](../clr-integration/security/clr-integration-security.md).  
  
-   Bösartige Module, die für die Ausführung als Benutzer mit hohen Privilegien definiert wurden. Weitere Informationen finden Sie unter [EXECUTE AS-Klausel &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-clause-transact-sql).  
  
 In beiden Fällen ist eine bestimmte Berechtigungsstufe erforderlich, und es liegt ein dementsprechender Schutz durch geeignete Mechanismen vor, wenn diese im Kontext einer Datenbank verwendet werden, die bereits an eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angefügt ist. Wenn die Datenbank jedoch offline geschaltet wird, kann ein Benutzer, der Zugriff auf die Datenbankdatei besitzt, diese potenziell einer Instanz seiner Wahl von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beifügen und der Datenbank auf diese Weise bösartige Inhalte hinzufügen. Wenn Datenbanken in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]getrennt oder angefügt werden, werden bestimmte Berechtigungen für die Daten- und Protokolldateien festgelegt, die den Zugriff auf die Datenbankdateien einschränken.  
  
 Da eine Datenbank, die einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angefügt wird, nicht sofort vertrauenswürdig ist, darf sie erst auf Ressourcen außerhalb des Bereichs der Datenbank zugreifen, wenn sie explizit als vertrauenswürdig markiert wurde. Für Module, die für den Zugriff auf Ressourcen außerhalb der Datenbank konzipiert wurden, und Assemblys mit der EXTERNAL_ACCESS- bzw. UNSAFE-Berechtigungseinstellung müssen zusätzliche Anforderungen erfüllt werden, damit diese erfolgreich ausgeführt werden.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 
  [Sicherheitscenter für SQL Server-Datenbank-Engine und Azure SQL-Datenbank](security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
