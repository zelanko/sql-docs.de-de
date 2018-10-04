---
title: Verteilte Ad-hoc-Abfragen (Serverkonfigurationsoption) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- OPENROWSET function, ad hoc distributed queries option
- Ad Hoc Distributed Queries option
- ad hoc distributed queries
- 7415 (Database Engine Error)
- OPENDATASOURCE function, ad hoc distributed queries option
- ad hoc access
ms.assetid: 5b982015-e196-44c3-83b8-275fb9d769b2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: edd15d3d18b7b4d4d7a03689548186829389889f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48093292"
---
# <a name="ad-hoc-distributed-queries-server-configuration-option"></a>Ad Hoc Distributed Queries (Serverkonfigurationsoption)
  Standardmäßig ist es in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht zulässig, dass für verteilte Ad-hoc-Abfragen OPENROWSET und OPENDATASOURCE verwendet werden. Wird diese Option auf 1 festgelegt, ist in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Ad-hoc-Zugriff zulässig. Wenn diese Option nicht festgelegt oder auf 0 festgelegt wird, ist in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kein Ad-hoc-Zugriff zulässig.  
  
 Verteilte Ad-hoc-Abfragen verwenden die OPENROWSET- und OPENDATASOURCE-Funktionen, um eine Verbindung mit Remotedatenquellen herzustellen, die OLE DB verwenden. OPENROWSET und OPENDATASOURCE sollten nur für Verweise auf OLE DB-Datenquellen verwendet werden, auf die selten zugegriffen wird. Definieren Sie einen Verbindungsserver für Datenquellen, auf die mehr als nur wenige Male zugegriffen wird.  
  
> [!IMPORTANT]  
>  Das Aktivieren der Verwendung von Ad-hoc-Namen bedeutet, dass jede authentifizierte Anmeldung an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf den Anbieter zugreifen kann. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Administratoren sollten diese Funktion für Anbieter aktivieren, auf die von jeder lokalen Anmeldung sicher zugegriffen werden kann.  
  
## <a name="remarks"></a>Hinweise  
 Der Versuch, eine Ad-hoc-Verbindung ohne die Option **Ad Hoc Distributed Queries** herzustellen, verursacht den folgenden Fehler: Meldung 7415, Ebene 16, Status 1, Zeile 1  
  
 Der Ad-hoc-Zugriff auf den OLE DB-Anbieter 'Microsoft.ACE.OLEDB.12.0' wurde verweigert. Sie müssen auf diesen Anbieter über einen Verbindungsserver zugreifen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden 'Ad Hoc Distributed Queries' aktiviert und anschließend ein Server mit dem Namen `Seattle1` mithilfe der `OPENROWSET` -Funktion abgefragt.  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
sp_configure 'Ad Hoc Distributed Queries', 1;  
RECONFIGURE;  
GO  
  
SELECT a.*  
FROM OPENROWSET('SQLNCLI', 'Server=Seattle1;Trusted_Connection=yes;',  
     'SELECT GroupName, Name, DepartmentID  
      FROM AdventureWorks2012.HumanResources.Department  
      ORDER BY GroupName, Name') AS a;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Serverkonfigurationsoptionen &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [Verbindungsserver &amp;amp;#40;Datenbank-Engine&amp;amp;#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql)   
 [OPENDATASOURCE (Transact-SQL)](/sql/t-sql/functions/opendatasource-transact-sql)   
 [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)  
  
  
