---
title: Festlegen der Sortierung benutzerdefinierter Datenbanken übereinstimmend zu jener der Master- und model-Datenbanken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c686446f-dae1-4b05-a3df-837b3422988d
caps.latest.revision: 12
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: eb6c695c33266fabe9a2b044a66429f781d0c4e2
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43810166"
---
# <a name="set-the-collation-of-user-defined-databases-to-match-those-of-the-master-and-model-databases"></a>Festlegen der Sortierung benutzerdefinierter Datenbanken übereinstimmend zu jener der master- und model-Datenbanken
  Diese Regel überprüft, ob benutzerdefinierte Datenbanken unter Verwendung einer Datenbanksortierung definiert sind, die mit der Sortierung der master- oder model-Datenbank übereinstimmt.  
  
## <a name="best-practices-recommendations"></a>Empfehlungen zu Best Practices  
 Es wird empfohlen, dass die Sortierungen benutzerdefinierter Datenbanken mit der Sortierung der Datenbanken 'master' oder 'model' übereinstimmen. Andernfalls können Sortierungskonflikte auftreten, die verhindern könnten, dass Code ausgeführt wird. Wenn beispielsweise eine gespeicherte Prozedur eine Tabelle mit einer temporären Tabelle verknüpft und die Sortierungen der benutzerdefinierten Datenbank und der model-Datenbank unterschiedlich sind, kann [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] den Batch beenden und einen Sortierungskonfliktfehler zurückgeben. Dies ist darauf zurückzuführen, dass temporäre Tabellen in der tempdb-Datenbank erstellt werden, deren Sortierung auf der der model-Datenbank basiert.  
  
 Wenn Sortierungskonfliktfehler auftreten, ziehen Sie eine der folgenden Lösungen in Betracht:  
  
-   Exportieren Sie die Daten aus der Benutzerdatenbank, und importieren Sie sie in neue Tabellen, die dieselbe Sortierung aufweisen wie die master- und model-Datenbanken.  
  
-   Erstellen Sie die Systemdatenbanken so neu, dass sie eine Sortierung verwenden, die mit der Sortierung der Benutzerdatenbank übereinstimmt. Weitere Informationen zum Neuerstellen der Systemdatenbanken finden Sie unter [Neuerstellen von Systemdatenbanken](../relational-databases/databases/system-databases.md).  
  
-   Ändern Sie alle gespeicherten Prozeduren, die Benutzertabellen mit Tabellen in der tempdb-Datenbank verknüpfen so, dass die Tabellen in der tempdb-Datenbank unter Verwendung der Sortierung der Benutzerdatenbank erstellt werden. Fügen Sie zu diesem Zweck den Spaltendefinitionen der temporären Tabelle die Klausel `COLLATE database_default` hinzu, wie im folgenden Beispiel gezeigt:  
  
    ```  
    CREATE TABLE #temp1 ( c1 int, c2 varchar(30) COLLATE database_default )  
    ```  
  
## <a name="for-more-information"></a>Weitere Informationen  
 [Festlegen oder Ändern der Datenbanksortierung](../relational-databases/collations/set-or-change-the-database-collation.md)  
  
 [Festlegen oder Ändern der Spaltensortierung](../relational-databases/collations/set-or-change-the-column-collation.md)  
  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [COLLATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/collations)  
  
 [sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [Microsoft Knowledge Base-Artikel 325335 befolgen](http://go.microsoft.com/fwlink/?linkid=117751)  
  
 [Vorgehensweise: Installieren von SQLServer 2008 über die Eingabeaufforderung](http://go.microsoft.com/fwlink/?LinkId=81585)  
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen und Erzwingen von Best Practices mit der richtlinienbasierten Verwaltung](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
