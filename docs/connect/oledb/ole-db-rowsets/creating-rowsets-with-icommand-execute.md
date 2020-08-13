---
title: Erstellen von Rowsets mit ICommand::Execute (OLE DB-Treiber) | Microsoft-Dokumentation
description: Erstellen von Rowsets mit ICommand::Execute
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, creating
- Execute method
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 6f81e724808e77d1ff963f36058a2e1436da26df
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942385"
---
# <a name="creating-rowsets-with-icommandexecute"></a>Erstellen von Rowsets mit 'ICommand::Execute'
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Bei Rowsets, die mithilfe der **ICommand::Execute**-Methode erstellt wurden, können die gewünschten Eigenschaften im resultierenden Rowset den Befehlstext einschränken. Dies ist insbesondere für Consumer wichtig, die dynamischen Befehlstext unterstützen.  
  
 Der OLE DB-Treiber für SQL Server kann keine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Cursor zur Unterstützung der Ergebnisse mit mehreren Rowsets verwenden, die von vielen Befehlen generiert werden. Wenn ein Consumer ein Rowset anfordert, das Unterstützung durch [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Cursor benötigt, tritt ein Fehler auf, falls der Befehlstext mehr als ein einzelnes Rowset als Ergebnis generiert. Weitere Informationen finden Sie unter [Befehle, die mehrere Rowsetergebnisse erzeugen](../../oledb/ole-db-commands/commands-generating-multiple-rowset-results.md).  
  
 Scrollfähige Rowsets für den OLE DB-Treiber für SQL Server werden von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Cursorn unterstützt. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] erzwingt Einschränkungen für Cursor, die durch Änderungen anderer Benutzer der Datenbank beeinflusst werden können. Konkret kann die Reihenfolge der Zeilen in einigen Cursorn nicht verändert werden, und der Versuch, ein Rowset mithilfe eines Befehls zu erstellen, der eine SQL ORDER BY-Klausel enthält, kann fehlschlagen. Weitere Informationen finden Sie unter [Rowsets und SQL Server-Cursor](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rowsets](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
