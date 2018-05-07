---
title: Mehrere Rowsetergebnisse generierende Befehle | Microsoft Docs
description: Mehrere rowsetergebnisse generierende Befehle
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- OLE DB Driver for SQL Server, commands
- OLE DB Driver for SQL Server, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: e0c3e581d5776e2f36756fc4bd09c1f76dd70841
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="commands-generating-multiple-rowset-results"></a>Mehrere Rowsetergebnisse generierende Befehle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Der OLE DB-Treiber für SQL Server kann mehrere Rowsets von zurückgeben [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Anweisungen. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anweisungen geben unter folgenden Bedingungen mehrere Rowsetergebnisse zurück:  
  
-   SQL-Anweisungen im Batchmodus werden als einzelner Befehl gesendet.  
  
-   Gespeicherte Prozeduren implementieren einen Batch SQL-Anweisungen.  
  
## <a name="batches"></a>Batches  
 Der OLE DB-Treiber für SQL Server erkennt das Semikolon als Batchtrennzeichen für SQL-Anweisungen:  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 Mehrere SQL-Anweisungen in einem Batch zu senden ist effizienter, als jede SQL-Anweisung einzeln auszuführen. Durch Senden eines Batches werden die Netzwerkroundtrips vom Client auf den Server reduziert.  
  
## <a name="stored-procedures"></a>Gespeicherte Prozeduren  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gibt ein Resultset für jede Anweisung in einer gespeicherten Prozedur zurück, sodass die meisten gespeicherten [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Prozeduren mehrere Resultsets zurückgeben.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Verwenden IMultipleResults, um mehrere Resultsets verarbeiten](../../oledb/ole-db-commands/using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Befehle](../../oledb/ole-db-commands/commands.md)  
  
  
