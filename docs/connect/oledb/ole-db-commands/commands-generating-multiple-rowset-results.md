---
title: Befehle, die Ergebnisse von mehreren Rowsets erzeugen | Microsoft-Dokumentation
description: Mehrere Rowsetergebnisse generierende Befehle
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- multiple rowsets
- rowsets [OLE DB], multiple
- OLE DB Driver for SQL Server, commands
- OLE DB Driver for SQL Server, multiple rowsets
- commands [OLE DB]
- multiple-rowset results
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 5374e1ccd1024993369091b431a025676bccf1f0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68016066"
---
# <a name="commands-generating-multiple-rowset-results"></a>Mehrere Rowsetergebnisse generierende Befehle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server kann mehrere Rowsets von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Anweisungen zurückgeben. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anweisungen geben unter folgenden Bedingungen mehrere Rowsetergebnisse zurück:  
  
-   SQL-Anweisungen im Batchmodus werden als einzelner Befehl gesendet.  
  
-   Gespeicherte Prozeduren implementieren einen Batch SQL-Anweisungen.  
  
## <a name="batches"></a>Batches  
 Der OLE DB-Treiber für SQL Server erkennt das Semikolon als Batch Trennzeichen für SQL-Anweisungen:  
  
```  
WCHAR*       wSQLString = L"SELECT * FROM Categories; "  
                          L"SELECT * FROM Products";  
```  
  
 Mehrere SQL-Anweisungen in einem Batch zu senden ist effizienter, als jede SQL-Anweisung einzeln auszuführen. Durch Senden eines Batches werden die Netzwerkroundtrips vom Client auf den Server reduziert.  
  
## <a name="stored-procedures"></a>Gespeicherte Prozeduren  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gibt ein Resultset für jede Anweisung in einer gespeicherten Prozedur zurück, sodass die meisten gespeicherten [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Prozeduren mehrere Resultsets zurückgeben.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Verwenden von 'IMultipleResults' zur Verarbeitung mehrerer Resultsets](../../oledb/ole-db-commands/using-imultipleresults-to-process-multiple-result-sets.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Befehle](../../oledb/ole-db-commands/commands.md)  
  
  
